# entropy_src Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="entropy_srcfw_ovextract_and_insert">
      <td>ENTROPY_SRC.FW_OV.EXTRACT_AND_INSERT</td>
      <td>If this feature is enabled, firmware can extract entropy bits by reading from the !!FW_OV_RD_DATA register (observe FIFO) and insert entropy bits into the entropy flow by writing the !!FW_OV_WR_DATA register.This is can be useful for performing additional health tests and/or firmware-based conditioning.Note that it is possible to perform hardware conditioning of the inserted entropy bits.However, firmware has to manually trigger the conditioner via the !!FW_OV_SHA3_START register.Note that the post-health test entropy bits collected in the observe FIFO do not continue to flow through the hardware pipeline.Only entropy bits inserted by firmware through !!FW_OV_WR_DATA may eventually reach the block hardware interface.Note that for this feature to work the `otp_en_entropy_src_fw_over` input from OTP needs to be set to `kMultiBitBool8True`.</td>
    </tr>
    <tr id="entropy_srcfw_ovobserve">
      <td>ENTROPY_SRC.FW_OV.OBSERVE</td>
      <td>If this feature is enabled, firmware can monitor the post-health test entropy via !!FW_OV_RD_DATA register (observe FIFO).This can be useful, e.g., for validation testing.Note that the post-health test entropy bits collected in the observe FIFO continue to flow through the hardware pipeline and may eventually reach the hardware interface.Note that for this to work the `otp_en_entropy_src_fw_over` input from OTP needs to be set to `kMultiBitBool8True`.</td>
    </tr>
    <tr id="entropy_srchealth_tests">
      <td>ENTROPY_SRC.HEALTH_TESTS</td>
      <td>To screen the raw noise bits provided by the digital noise source / physical true random number generator (PTRNG) for statistical defects, ENTROPY_SRC implements multiple health tests which include:- Repetition Count and Adaptive Proportion tests as recommended by NIST SP 800-90B.- Bucket and Markov tests to look for correlations between the individual noise channels.Firmware can configure the threshold values separately for each health test.In case of health test failures, an interrupt is signaled.In addition, per-health-test failure counters are incremented.Firmware can configure threshold values for these per-health-test counters as well as for the total failure counter.In case any of these thresholds are hit, ENTROPY_SRC halts, signals a recoverable alert and sets the !!RECOV_ALERT_STS.ES_MAIN_SM_ALERT bit.Firmware then has to disable and re-enable ENTROPY_SRC to continue entropy generation and health testing.Firmware can configure the window size for the health tests.Note that currently, only a window size of 384 is supported and tested for boot-time / bypass mode.</td>
    </tr>
    <tr id="entropy_srchealth_tests_ext">
      <td>ENTROPY_SRC.HEALTH_TESTS_EXT</td>
      <td>In addition to the internal health tests, ENTROPY_SRC features an interface for vendor-defined health tests implemented externally to ENTROPY_SRC.Note: Egret does not implement external vendor-defined health tests.</td>
    </tr>
    <tr id="entropy_srcmodebypass">
      <td>ENTROPY_SRC.MODE.BYPASS</td>
      <td>The boot-time / bypass mode is designed to provide an initial seed's worth of entropy with lower latency than the normal FIPS/CC compliant mode during chip boot up.This mode bypasses the hardware conditioning of ENTROPY_SRC and instead outputs raw entropy.However, health tests are still performed.Note that currently, only a window size of 384 bits for the health tests is supported and tested for boot-time / bypass mode.</td>
    </tr>
    <tr id="entropy_srcmodefips">
      <td>ENTROPY_SRC.MODE.FIPS</td>
      <td>The FIPS/CC compliant mode is the primary mode of operation in which ENTROPY_SRC can generate entropy compliant with NIST SP 800-90B and AIS31 recommendations.In this mode, once the raw entropy has been health tested, it is passed into the hardware conditioner block which compresses the bits to ideally improve the min-entropy value compared to the digital noise source / physical true random number generator (PTRNG).The window size for the health tests and the conditioning is configurable by firmware with a default of 2048 bits.Note that ENTROPY_SRC uses the `es_fips` bit of the hardware interface to indicate whether the generated entropy is indeed FIPS/CC compliant.For this to be true the following prerequisites must be met in addition to running in FIPS/CC compliant mode:- !!CONF.RNG_BIT_ENABLE must be set to `kMultiBitBool4False` (see ENTROPY_SRC.RNG_BIT_ENABLE).- At most one of the !!ENTROPY_CONTROL.ES_ROUTE and !!ENTROPY_CONTROL.ES_TYPE fields needs to be set to `kMultiBitBool4True` but not both (see ENTROPY_SRC.ROUTE_TO_FIRMWARE).</td>
    </tr>
    <tr id="entropy_srcrng_bit_enable">
      <td>ENTROPY_SRC.RNG_BIT_ENABLE</td>
      <td>By default, ENTROPY_SRC uses all four channels of the digital noise source / physical true random number generator (PTRNG).Optionally, it is possible to use only one of the four channels which is useful for validation testing / using individual channels, e.g., in case of defects.Note that if only a single channel is used, ENTROPY_SRC will not generate FIPS qualified entropy (See also ENTROPY_SRC.MODE.FIPS).</td>
    </tr>
    <tr id="entropy_srcroute_to_firmware">
      <td>ENTROPY_SRC.ROUTE_TO_FIRMWARE</td>
      <td>By default, ENTROPY_SRC routes the generated entropy out of ENTROPY_SRC via the hardware interface for consumption by CSRNG.For validation testing, it is possible to instead route the generated entropy to the !!ENTROPY_DATA register to be read by firmware.Note that for this to work the `otp_en_entropy_src_fw_read` input from OTP needs to be `kMultiBitBool8True`.Further note that when routing entropy to firmware, 1) no entropy is being passed to the hardware interface, and 2) it is possible to optionally bypass the hardware conditioner using !!ENTROPY_CONTROL.ES_TYPE.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>ENTROPY_SRC.MODE.BYPASS</th>
    <th>ENTROPY_SRC.MODE.FIPS</th>
    <th>ENTROPY_SRC.HEALTH_TESTS</th>
    <th>ENTROPY_SRC.HEALTH_TESTS_EXT</th>
    <th>ENTROPY_SRC.RNG_BIT_ENABLE</th>
    <th>ENTROPY_SRC.ROUTE_TO_FIRMWARE</th>
    <th>ENTROPY_SRC.FW_OV.OBSERVE</th>
    <th>ENTROPY_SRC.FW_OV.EXTRACT_AND_INSERT</th>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#theory-of-operation">Theory of Operation</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#initialization-and-enabling">Initialization and Enabling</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#boot-time--bypass-mode">Boot-Time / Bypass Mode</a></th>
    <td><a href="../theory_of_operation.md#boot-time--bypass-mode">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#fipscc-compliant-mode">FIPS/CC Compliant Mode</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#fipscc-compliant-mode">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#startup-health-testing">Startup Health Testing</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#startup-health-testing">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#firmware-override-mode">Firmware Override Mode</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#firmware-override-mode">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#firmware-override-mode">X</a></td>
    <td><a href="../theory_of_operation.md#firmware-override-mode">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#health-tests">Health Tests</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#health-tests">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#health-test-failure-alert">Health Test Failure Alert</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#health-test-failure-alert">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#routing-entropy-to-firmware">Routing Entropy to Firmware</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#routing-entropy-to-firmware">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#disabling">Disabling</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#block-diagram">Block Diagram</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#design-details">Design Details</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#entropy-dropping-and-conditioner-back-pressure">Entropy Dropping and Conditioner Back Pressure</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#security">Security</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#main-state-machine-diagram">Main State Machine Diagram</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#entropy-source-hardware-interface">Entropy Source Hardware Interface</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#ptrng-hardware-interface">PTRNG Hardware Interface</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#repetition-count-test">Repetition Count Test</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#adaptive-proportion-test">Adaptive Proportion Test</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#bucket-test">Bucket Test</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#markov-test">Markov Test</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#external-health-tests">External Health Tests</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#external-health-tests">X</a></td>
    <td><a href="../theory_of_operation.md#external-health-tests">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>
</div>
</div>


## Feature -> Testpoint Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Testpoints↓ : Features→</th>
    <th>ENTROPY_SRC.MODE.BYPASS</th>
    <th>ENTROPY_SRC.MODE.FIPS</th>
    <th>ENTROPY_SRC.HEALTH_TESTS</th>
    <th>ENTROPY_SRC.HEALTH_TESTS_EXT</th>
    <th>ENTROPY_SRC.RNG_BIT_ENABLE</th>
    <th>ENTROPY_SRC.ROUTE_TO_FIRMWARE</th>
    <th>ENTROPY_SRC.FW_OV.OBSERVE</th>
    <th>ENTROPY_SRC.FW_OV.EXTRACT_AND_INSERT</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#firmware">firmware</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#firmware">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#firmware_mode">firmware_mode</a></th>
    <td><a href="02_testpoint_report.md#firmware_mode">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#firmware_mode">X</a></td>
    <td><a href="02_testpoint_report.md#firmware_mode">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#rng_mode">rng_mode</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#rng_mode">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#rng_mode">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#rng_max_rate">rng_max_rate</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#health_checks">health_checks</a></th>
    <td><a href="02_testpoint_report.md#health_checks">X</a></td>
    <td><a href="02_testpoint_report.md#health_checks">X</a></td>
    <td><a href="02_testpoint_report.md#health_checks">X</a></td>
    <td><a href="02_testpoint_report.md#health_checks">X</a></td>
    <td><a href="02_testpoint_report.md#health_checks">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#conditioning">conditioning</a></th>
    <td><a href="02_testpoint_report.md#conditioning">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#conditioning">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#interrupts">interrupts</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#interrupts">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#alerts">alerts</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#alerts">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#stress_all">stress_all</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#functional_errors">functional_errors</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#firmware_ov_read_contiguous_data">firmware_ov_read_contiguous_data</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#firmware_ov_read_contiguous_data">X</a></td>
    <td><a href="02_testpoint_report.md#firmware_ov_read_contiguous_data">X</a></td>
    <td><a href="02_testpoint_report.md#firmware_ov_read_contiguous_data">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#external_health_tests">external_health_tests</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#external_health_tests">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_entropy_src_ast_rng_req-dragonfly">chip_sw_entropy_src_ast_rng_req (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_ast_rng_req-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_entropy_src_csrng-dragonfly">chip_sw_entropy_src_csrng (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_csrng-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_entropy_src_fuse_en_fw_read-dragonfly">chip_sw_entropy_src_fuse_en_fw_read (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_fuse_en_fw_read-dragonfly">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_entropy_src_known_answer_tests-dragonfly">chip_sw_entropy_src_known_answer_tests (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_known_answer_tests-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_known_answer_tests-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_entropy_src_bypass_mode_health_tests-dragonfly">chip_sw_entropy_src_bypass_mode_health_tests (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_bypass_mode_health_tests-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_bypass_mode_health_tests-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_entropy_src_fips_mode_health_tests-dragonfly">chip_sw_entropy_src_fips_mode_health_tests (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_fips_mode_health_tests-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_fips_mode_health_tests-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_entropy_src_validation-dragonfly">chip_sw_entropy_src_validation (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_validation-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_validation-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_validation-dragonfly">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_entropy_src_fw_observe_many_contiguous-dragonfly">chip_sw_entropy_src_fw_observe_many_contiguous (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_fw_observe_many_contiguous-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_fw_observe_many_contiguous-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_fw_observe_many_contiguous-dragonfly">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_entropy_src_fw_extract_and_insert-dragonfly">chip_sw_entropy_src_fw_extract_and_insert (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_fw_extract_and_insert-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_fw_extract_and_insert-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_fw_extract_and_insert-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_entropy_src_ast_rng_req-egret">chip_sw_entropy_src_ast_rng_req (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_ast_rng_req-egret">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_entropy_src_csrng-egret">chip_sw_entropy_src_csrng (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_csrng-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_entropy_src_fuse_en_fw_read-egret">chip_sw_entropy_src_fuse_en_fw_read (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_fuse_en_fw_read-egret">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_entropy_src_known_answer_tests-egret">chip_sw_entropy_src_known_answer_tests (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_known_answer_tests-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_known_answer_tests-egret">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_entropy_src_bypass_mode_health_tests-egret">chip_sw_entropy_src_bypass_mode_health_tests (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_bypass_mode_health_tests-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_bypass_mode_health_tests-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_entropy_src_fips_mode_health_tests-egret">chip_sw_entropy_src_fips_mode_health_tests (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_fips_mode_health_tests-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_fips_mode_health_tests-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_entropy_src_validation-egret">chip_sw_entropy_src_validation (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_validation-egret">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_validation-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_validation-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_entropy_src_fw_observe_many_contiguous-egret">chip_sw_entropy_src_fw_observe_many_contiguous (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_fw_observe_many_contiguous-egret">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_fw_observe_many_contiguous-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_fw_observe_many_contiguous-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_entropy_src_fw_extract_and_insert-egret">chip_sw_entropy_src_fw_extract_and_insert (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_fw_extract_and_insert-egret">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_fw_extract_and_insert-egret">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_entropy_src_fw_extract_and_insert-egret">X</a></td>
  </tr>
</table>
</div>
</div>
