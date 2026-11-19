# entropy_src Testpoint Report

## alerts

Verify that all recoverable alerts are asserted as expected.
Any alerts not encountered as part of the usual entropy_src_rng test will be generated
by the `entropy_src_functional_alerts` test.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#entropy_src_functional_alerts">entropy_src_functional_alerts</a><br><a href="03_test_report.md#entropy_src_rng">entropy_src_rng</a></td>
  <td><a href="01_feature_report.md#entropy_srcrng_bit_enable">ENTROPY_SRC.RNG_BIT_ENABLE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_entropy_src_ast_rng_req (dragonfly)
Verify the RNG req to AST.

- Enable ENTROPY_SRC in FIPS mode.
- Enable Firmware Override - Extract & Insert to route entropy received from AST to the observe FIFO.
- Verify that the observe FIFO depth is non-zero via SW - indicating the reception of data over the AST RNG interface.
- Verify the correctness of the received data with assertion based connectivity checks.

Notes for silicon targets:

- This test requires access to the ENTROPY_SRC.FW_OV.EXTRACT_AND_INSERT feature, which is gated by OTP.
  This test might thus need to be done in a secure facility.
- In silicon, it's not possible to check whether the values match.
  However, checking that the observe FIFO actually fills up is a very fundamental test prior to the validation testing.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_entropy_src_ast_rng_req-dragonfly">chip_sw_entropy_src_ast_rng_req (dragonfly)</a></td>
  <td><a href="01_feature_report.md#entropy_srcfw_ovextract_and_insert">ENTROPY_SRC.FW_OV.EXTRACT_AND_INSERT</a></td>
</tr>
  </tbody>
</table>

## chip_sw_entropy_src_ast_rng_req (egret)
Verify the RNG req to AST.

- Enable ENTROPY_SRC in FIPS mode.
- Enable Firmware Override - Extract & Insert to route entropy received from AST to the observe FIFO.
- Verify that the observe FIFO depth is non-zero via SW - indicating the reception of data over the AST RNG interface.
- Verify the correctness of the received data with assertion based connectivity checks.

Notes for silicon targets:

- This test requires access to the ENTROPY_SRC.FW_OV.EXTRACT_AND_INSERT feature, which is gated by OTP.
  This test might thus need to be done in a secure facility.
- In silicon, it's not possible to check whether the values match.
  However, checking that the observe FIFO actually fills up is a very fundamental test prior to the validation testing.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_entropy_src_ast_rng_req-egret">chip_sw_entropy_src_ast_rng_req (egret)</a></td>
  <td><a href="01_feature_report.md#entropy_srcfw_ovextract_and_insert">ENTROPY_SRC.FW_OV.EXTRACT_AND_INSERT</a></td>
</tr>
  </tbody>
</table>

## chip_sw_entropy_src_bypass_mode_health_tests (dragonfly)

Verify that ENTROPY_SRC:

- provides one initial seed in boot-time / bypass mode only,
- signals a recoverable alert if the total failure counter hits the threshold in boot-time / bypass mode.

Procedure:

- Disable the entropy complex.
- Configure loose health test threshold values for boot-time / bypass mode.
- Enable ENTROPY_SRC in boot-time / bypass mode.
- Enable CSRNG.
- Enable both EDNs in boot-time request mode.
- Trigger the execution of a cryptographic hardware block consuming entropy (e.g. AES) to test EDN0.
- Verify the entropy consuming endpoint finishes its operation.
- Trigger the execution of an ACC program requiring entropy from both EDN1 and EDN0.
- Verify the ACC program hangs.
- Disable the entropy complex.
- Configure unrealistically stringent health test threshold values for boot-time / bypass mode.
- Configure an alert threshold value of 1 in the ALERT_THRESHOLD register.
- Enable ENTROPY_SRC in boot-time / bypass mode.
- Enable CSRNG.
- Enable both EDNs in boot-time request mode.
- Verify that ENTROPY_SRC triggers a recoverable alert and sets the RECOV_ALERT_STS.ES_MAIN_SM_ALERT bit.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td>No tests</td>
  <td><a href="01_feature_report.md#entropy_srchealth_tests">ENTROPY_SRC.HEALTH_TESTS</a><br><a href="01_feature_report.md#entropy_srcmodebypass">ENTROPY_SRC.MODE.BYPASS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_entropy_src_bypass_mode_health_tests (egret)

Verify that ENTROPY_SRC:

- provides one initial seed in boot-time / bypass mode only,
- signals a recoverable alert if the total failure counter hits the threshold in boot-time / bypass mode.

Procedure:

- Disable the entropy complex.
- Configure loose health test threshold values for boot-time / bypass mode.
- Enable ENTROPY_SRC in boot-time / bypass mode.
- Enable CSRNG.
- Enable both EDNs in boot-time request mode.
- Trigger the execution of a cryptographic hardware block consuming entropy (e.g. AES) to test EDN0.
- Verify the entropy consuming endpoint finishes its operation.
- Trigger the execution of an ACC program requiring entropy from both EDN1 and EDN0.
- Verify the ACC program hangs.
- Disable the entropy complex.
- Configure unrealistically stringent health test threshold values for boot-time / bypass mode.
- Configure an alert threshold value of 1 in the ALERT_THRESHOLD register.
- Enable ENTROPY_SRC in boot-time / bypass mode.
- Enable CSRNG.
- Enable both EDNs in boot-time request mode.
- Verify that ENTROPY_SRC triggers a recoverable alert and sets the RECOV_ALERT_STS.ES_MAIN_SM_ALERT bit.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td>No tests</td>
  <td><a href="01_feature_report.md#entropy_srchealth_tests">ENTROPY_SRC.HEALTH_TESTS</a><br><a href="01_feature_report.md#entropy_srcmodebypass">ENTROPY_SRC.MODE.BYPASS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_entropy_src_csrng (dragonfly)
Verify the transfer of entropy bits to CSRNG.

Verify the entropy valid interrupt.
At the CSRNG, validate the reception of entropy req interrupt.

- Disable edn0, edn1, csrng and entropy_src, as these are enabled by the test ROM.
- Enable entropy_src in fips mode routing data to csrng.
- Enable csrng and enable the entropy request interrupt.
- Issue csrng instantiate and reseed commands. Check that for each csrng command,
  there is a corresponding entropy request interrupt.
- Generate output and ensure the data output is valid, and that csrng is not reporting
  any errors.
- Issue instantiate and reseed commands from edn0 and edn1. Check that for each
  command, there is a corresponding entropy request interrupt.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_entropy_src_csrng-dragonfly">chip_sw_entropy_src_csrng (dragonfly)</a></td>
  <td><a href="01_feature_report.md#entropy_srcmodefips">ENTROPY_SRC.MODE.FIPS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_entropy_src_csrng (egret)
Verify the transfer of entropy bits to CSRNG.

Verify the entropy valid interrupt.
At the CSRNG, validate the reception of entropy req interrupt.

- Disable edn0, edn1, csrng and entropy_src, as these are enabled by the test ROM.
- Enable entropy_src in fips mode routing data to csrng.
- Enable csrng and enable the entropy request interrupt.
- Issue csrng instantiate and reseed commands. Check that for each csrng command,
  there is a corresponding entropy request interrupt.
- Generate output and ensure the data output is valid, and that csrng is not reporting
  any errors.
- Issue instantiate and reseed commands from edn0 and edn1. Check that for each
  command, there is a corresponding entropy request interrupt.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_entropy_src_csrng-egret">chip_sw_entropy_src_csrng (egret)</a></td>
  <td><a href="01_feature_report.md#entropy_srcmodefips">ENTROPY_SRC.MODE.FIPS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_entropy_src_fips_mode_health_tests (dragonfly)

Verify that ENTROPY_SRC:

- provides continuous entropy in FIPS/CC compliant mode,
- works with different health test window sizes in FIPS mode,
- signals a recoverable alert and stops serving entropy if the total failure counter hits the threshold in FIPS mode.

Procedure:

- Disable the entropy complex.
- Configure realistic health test threshold values for FIPS/CC compliant mode.
- Enable ENTROPY_SRC in FIPS mode.
- Enable CSRNG.
- Enable both EDNs in auto request mode.
- Trigger the execution of various cryptographic hardware blocks consuming entropy to stress test the entropy complex.
- Verify that all entropy consuming endpoints can finish their operations and do not hang.
- Repeat the procedure with different health test window sizes for FIPS mode.
- Disable the entropy complex.
- Configure unrealistically stringent health test threshold values for FIPS mode.
- Configure a low alert threshold value in the ALERT_THRESHOLD register.
- Enable ENTROPY_SRC in FIPS mode.
- Enable CSRNG.
- Enable both EDNs in auto request mode and with low values for the generate length parameter to request fresh entropy more often.
- Trigger the execution of various cryptographic hardware blocks consuming entropy to stress test the entropy complex.
- Verify that ENTROPY_SRC triggers a recoverable alert and sets the RECOV_ALERT_STS.ES_MAIN_SM_ALERT bit.
- Verify that various entropy consuming endpoints hang as ENTROPY_SRC stops generating entropy after triggering the recoverable alert.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td>No tests</td>
  <td><a href="01_feature_report.md#entropy_srchealth_tests">ENTROPY_SRC.HEALTH_TESTS</a><br><a href="01_feature_report.md#entropy_srcmodefips">ENTROPY_SRC.MODE.FIPS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_entropy_src_fips_mode_health_tests (egret)

Verify that ENTROPY_SRC:

- provides continuous entropy in FIPS/CC compliant mode,
- works with different health test window sizes in FIPS mode,
- signals a recoverable alert and stops serving entropy if the total failure counter hits the threshold in FIPS mode.

Procedure:

- Disable the entropy complex.
- Configure realistic health test threshold values for FIPS/CC compliant mode.
- Enable ENTROPY_SRC in FIPS mode.
- Enable CSRNG.
- Enable both EDNs in auto request mode.
- Trigger the execution of various cryptographic hardware blocks consuming entropy to stress test the entropy complex.
- Verify that all entropy consuming endpoints can finish their operations and do not hang.
- Repeat the procedure with different health test window sizes for FIPS mode.
- Disable the entropy complex.
- Configure unrealistically stringent health test threshold values for FIPS mode.
- Configure a low alert threshold value in the ALERT_THRESHOLD register.
- Enable ENTROPY_SRC in FIPS mode.
- Enable CSRNG.
- Enable both EDNs in auto request mode and with low values for the generate length parameter to request fresh entropy more often.
- Trigger the execution of various cryptographic hardware blocks consuming entropy to stress test the entropy complex.
- Verify that ENTROPY_SRC triggers a recoverable alert and sets the RECOV_ALERT_STS.ES_MAIN_SM_ALERT bit.
- Verify that various entropy consuming endpoints hang as ENTROPY_SRC stops generating entropy after triggering the recoverable alert.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td>No tests</td>
  <td><a href="01_feature_report.md#entropy_srchealth_tests">ENTROPY_SRC.HEALTH_TESTS</a><br><a href="01_feature_report.md#entropy_srcmodefips">ENTROPY_SRC.MODE.FIPS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_entropy_src_fuse_en_fw_read (dragonfly)
Verify the fuse input entropy_src.

- Initialize the OTP with the fuse that controls whether the SW can read the entropy src
  enabled.
- Read the OTP and verify that the fuse is enabled.
- Read the entropy_data_fifo via SW and verify that it reads valid values.
- Reset the chip, but this time, initialize the OTP with the fuse disabled.
- Read the OTP and verify that fuse is disabled.
- Read the internal state via SW and verify that the entropy valid bit is zero.

Notes for silicon targets:

- The current understanding is that the en_entropy_src_fw_read OTP switch controlling the ENTROPY_SRC.ROUTE_TO_FIRMWARE feature will need to be enabled also in the PROD life-cycle state for validation and known-answer testing.
  Thus, burning the en_entropy_src_fw_read OTP fuses is not advisable for silicon validation.
  This particular test may be skipped in favor of chip_sw_entropy_src_known_answer_tests which also tests the ENTROPY_SRC.ROUTE_TO_FIRMWARE feature.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_entropy_src_fuse_en_fw_read_test-dragonfly">chip_sw_entropy_src_fuse_en_fw_read_test (dragonfly)</a></td>
  <td><a href="01_feature_report.md#entropy_srcroute_to_firmware">ENTROPY_SRC.ROUTE_TO_FIRMWARE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_entropy_src_fuse_en_fw_read (egret)
Verify the fuse input entropy_src.

- Initialize the OTP with the fuse that controls whether the SW can read the entropy src
  enabled.
- Read the OTP and verify that the fuse is enabled.
- Read the entropy_data_fifo via SW and verify that it reads valid values.
- Reset the chip, but this time, initialize the OTP with the fuse disabled.
- Read the OTP and verify that fuse is disabled.
- Read the internal state via SW and verify that the entropy valid bit is zero.

Notes for silicon targets:

- The current understanding is that the en_entropy_src_fw_read OTP switch controlling the ENTROPY_SRC.ROUTE_TO_FIRMWARE feature will need to be enabled also in the PROD life-cycle state for validation and known-answer testing.
  Thus, burning the en_entropy_src_fw_read OTP fuses is not advisable for silicon validation.
  This particular test may be skipped in favor of chip_sw_entropy_src_known_answer_tests which also tests the ENTROPY_SRC.ROUTE_TO_FIRMWARE feature.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_entropy_src_fuse_en_fw_read_test-egret">chip_sw_entropy_src_fuse_en_fw_read_test (egret)</a></td>
  <td><a href="01_feature_report.md#entropy_srcroute_to_firmware">ENTROPY_SRC.ROUTE_TO_FIRMWARE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_entropy_src_fw_extract_and_insert (dragonfly)
Verify that the software can observe samples fast enough to extract many contiguous samples.

Procedure:

- Disable the entropy complex.
- Disable health checks.
- Enable ENTROPY_SRC in FIPS mode.
- Configure OBSERVE_FIFO_THRESH to a sensible value.
- Enable Firmware Override - Extract & Insert.
- Enable CSRNG.
- Enable both EDNs in auto request mode.
- Trigger the execution of various cryptographic hardware blocks consuming entropy to stress test the entropy complex.
- Repeat until all entropy consuming endpoints have finished their operations:
  - Read 1000 samples from the observe FIFO.
  - Verify that the observe FIFO overflow status has not been set.
  - Insert the samples back into the entropy flow.
  - Let the observe FIFO overflow.
  - Empty the observe FIFO and discard any values read.

Tests:

- The procedure must be run once with ENTROPY_SRC.RNG_BIT_ENABLE disabled (4-bit / sample) and
  four times with the ENTROPY_SRC.RNG_BIT_ENABLE feature being enabled (once for every channel).
- The procedure must be tested with and without the conditioner (bypass mode).
- The procedure must be tested with a significant delay added between extracting and inserting the entropy.
- The procedure must be tested with a disablement and a re-enablement of ENTROPY_SRC.
  - To this end, ENTROPY_SRC must be disabled after it has produced entropy.
  - Whenever CSRNG has an outstanding entropy request ENTROPY_SRC can be enabled again.

Notes for silicon targets:

- This test requires access to the ENTROPY_SRC.ROUTE_TO_FIRMWARE and ENTROPY_SRC.FW_OV.EXTRACT_AND_INSERT features, which are gated by OTP.
  This test might thus need to be done in a secure facility.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td>No tests</td>
  <td><a href="01_feature_report.md#entropy_srcfw_ovextract_and_insert">ENTROPY_SRC.FW_OV.EXTRACT_AND_INSERT</a><br><a href="01_feature_report.md#entropy_srcmodefips">ENTROPY_SRC.MODE.FIPS</a><br><a href="01_feature_report.md#entropy_srcrng_bit_enable">ENTROPY_SRC.RNG_BIT_ENABLE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_entropy_src_fw_extract_and_insert (egret)
Verify that the software can observe samples fast enough to extract many contiguous samples.

Procedure:

- Disable the entropy complex.
- Disable health checks.
- Enable ENTROPY_SRC in FIPS mode.
- Configure OBSERVE_FIFO_THRESH to a sensible value.
- Enable Firmware Override - Extract & Insert.
- Enable CSRNG.
- Enable both EDNs in auto request mode.
- Trigger the execution of various cryptographic hardware blocks consuming entropy to stress test the entropy complex.
- Repeat until all entropy consuming endpoints have finished their operations:
  - Read 1000 samples from the observe FIFO.
  - Verify that the observe FIFO overflow status has not been set.
  - Insert the samples back into the entropy flow.
  - Let the observe FIFO overflow.
  - Empty the observe FIFO and discard any values read.

Tests:

- The procedure must be run once with ENTROPY_SRC.RNG_BIT_ENABLE disabled (4-bit / sample) and
  four times with the ENTROPY_SRC.RNG_BIT_ENABLE feature being enabled (once for every channel).
- The procedure must be tested with and without the conditioner (bypass mode).
- The procedure must be tested with a significant delay added between extracting and inserting the entropy.
- The procedure must be tested with a disablement and a re-enablement of ENTROPY_SRC.
  - To this end, ENTROPY_SRC must be disabled after it has produced entropy.
  - Whenever CSRNG has an outstanding entropy request ENTROPY_SRC can be enabled again.

Notes for silicon targets:

- This test requires access to the ENTROPY_SRC.ROUTE_TO_FIRMWARE and ENTROPY_SRC.FW_OV.EXTRACT_AND_INSERT features, which are gated by OTP.
  This test might thus need to be done in a secure facility.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td>No tests</td>
  <td><a href="01_feature_report.md#entropy_srcfw_ovextract_and_insert">ENTROPY_SRC.FW_OV.EXTRACT_AND_INSERT</a><br><a href="01_feature_report.md#entropy_srcmodefips">ENTROPY_SRC.MODE.FIPS</a><br><a href="01_feature_report.md#entropy_srcrng_bit_enable">ENTROPY_SRC.RNG_BIT_ENABLE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_entropy_src_fw_observe_many_contiguous (dragonfly)
Verify that the software can observe samples fast enough to extract many contiguous samples.

Procedure:

- Disable the entropy complex.
- Disable health checks.
- Enable ENTROPY_SRC in FIPS mode
- Enable Firmware Override - Observe.
- Repeat several times:
  - Collect 1000 contiguous samples from the observe FIFO:
    - Verify after reading each sample that the observe FIFO overflow status has not been set.
  - Let the observe FIFO overflow.
  - Drain the observe FIFO.

Tests:

- The procedure must be run once with ENTROPY_SRC.RNG_BIT_ENABLE disabled (4-bit / sample) and
  four times with the ENTROPY_SRC.RNG_BIT_ENABLE feature being enabled (once for every channel).

Notes for silicon targets:

- This test requires access to the ENTROPY_SRC.FW_OV.OBSERVE feature, which is gated by OTP.
  This test might thus need to be done in a secure facility.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td>No tests</td>
  <td><a href="01_feature_report.md#entropy_srcfw_ovobserve">ENTROPY_SRC.FW_OV.OBSERVE</a><br><a href="01_feature_report.md#entropy_srcmodefips">ENTROPY_SRC.MODE.FIPS</a><br><a href="01_feature_report.md#entropy_srcrng_bit_enable">ENTROPY_SRC.RNG_BIT_ENABLE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_entropy_src_fw_observe_many_contiguous (egret)
Verify that the software can observe samples fast enough to extract many contiguous samples.

Procedure:

- Disable the entropy complex.
- Disable health checks.
- Enable ENTROPY_SRC in FIPS mode
- Enable Firmware Override - Observe.
- Repeat several times:
  - Collect 1000 contiguous samples from the observe FIFO:
    - Verify after reading each sample that the observe FIFO overflow status has not been set.
  - Let the observe FIFO overflow.
  - Drain the observe FIFO.

Tests:

- The procedure must be run once with ENTROPY_SRC.RNG_BIT_ENABLE disabled (4-bit / sample) and
  four times with the ENTROPY_SRC.RNG_BIT_ENABLE feature being enabled (once for every channel).

Notes for silicon targets:

- This test requires access to the ENTROPY_SRC.FW_OV.OBSERVE feature, which is gated by OTP.
  This test might thus need to be done in a secure facility.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td>No tests</td>
  <td><a href="01_feature_report.md#entropy_srcfw_ovobserve">ENTROPY_SRC.FW_OV.OBSERVE</a><br><a href="01_feature_report.md#entropy_srcmodefips">ENTROPY_SRC.MODE.FIPS</a><br><a href="01_feature_report.md#entropy_srcrng_bit_enable">ENTROPY_SRC.RNG_BIT_ENABLE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_entropy_src_known_answer_tests (dragonfly)
Verify our ability to run known-answer tests in SW.

- Enable ENTROPY_SRC in FIPS mode.
- Enable Firmware Override - Extract & Insert.
- Feed NIST test-defined entropy sequences into ENTROPY_SRC via the FW_OV_WR_DATA register.
- Trigger the hardware conditioner.
- Read the conditioned entropy from ENTROPY_SRC via the ENTROPY_DATA register; verify that it reads the expected values.

Notes for silicon targets:

- This test requires access to the ENTROPY_SRC.ROUTE_TO_FIRMWARE and ENTROPY_SRC.FW_OV.EXTRACT_AND_INSERT features, which are gated by OTP.
  This test might thus need to be done in a secure facility.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_entropy_src_kat_test-dragonfly">chip_sw_entropy_src_kat_test (dragonfly)</a></td>
  <td><a href="01_feature_report.md#entropy_srcfw_ovextract_and_insert">ENTROPY_SRC.FW_OV.EXTRACT_AND_INSERT</a><br><a href="01_feature_report.md#entropy_srcroute_to_firmware">ENTROPY_SRC.ROUTE_TO_FIRMWARE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_entropy_src_known_answer_tests (egret)
Verify our ability to run known-answer tests in SW.

- Enable ENTROPY_SRC in FIPS mode.
- Enable Firmware Override - Extract & Insert.
- Feed NIST test-defined entropy sequences into ENTROPY_SRC via the FW_OV_WR_DATA register.
- Trigger the hardware conditioner.
- Read the conditioned entropy from ENTROPY_SRC via the ENTROPY_DATA register; verify that it reads the expected values.

Notes for silicon targets:

- This test requires access to the ENTROPY_SRC.ROUTE_TO_FIRMWARE and ENTROPY_SRC.FW_OV.EXTRACT_AND_INSERT features, which are gated by OTP.
  This test might thus need to be done in a secure facility.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_entropy_src_kat_test-egret">chip_sw_entropy_src_kat_test (egret)</a></td>
  <td><a href="01_feature_report.md#entropy_srcfw_ovextract_and_insert">ENTROPY_SRC.FW_OV.EXTRACT_AND_INSERT</a><br><a href="01_feature_report.md#entropy_srcroute_to_firmware">ENTROPY_SRC.ROUTE_TO_FIRMWARE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_entropy_src_validation (dragonfly)

Enable validation of the four channels of the digital noise source / physical true random number generator (PTRNG) at the ENTROPY_SRC input, and verify that ENTROPY_SRC allows observing raw entropy through the observe FIFO while serving entropy to consumers.

Procedure:

- Disable the entropy complex.
- Configure realistic health test threshold values for FIPS/CC compliant mode.
- Enable ENTROPY_SRC in FIPS mode.
- Enable Firmware Override - Observe.
- Enable CSRNG.
- Enable both EDNs in auto request mode.
- Trigger the execution of various cryptographic hardware blocks consuming entropy to stress test the entropy complex.
- Verify that all entropy consuming endpoints can finish their operations and do not hang.
- Verify that the observe FIFO depth is non-zero and read out post-health test entropy for validation testing.
- Repeat the procedure four times with the ENTROPY_SRC.RNG_BIT_ENABLE feature being enabled (once for every channel).

Notes for silicon targets:

- This test requires access to the ENTROPY_SRC.FW_OV.OBSERVE feature, which is gated by OTP.
  This test might thus need to be done in a secure facility.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td>No tests</td>
  <td><a href="01_feature_report.md#entropy_srcfw_ovobserve">ENTROPY_SRC.FW_OV.OBSERVE</a><br><a href="01_feature_report.md#entropy_srcmodefips">ENTROPY_SRC.MODE.FIPS</a><br><a href="01_feature_report.md#entropy_srcrng_bit_enable">ENTROPY_SRC.RNG_BIT_ENABLE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_entropy_src_validation (egret)

Enable validation of the four channels of the digital noise source / physical true random number generator (PTRNG) at the ENTROPY_SRC input, and verify that ENTROPY_SRC allows observing raw entropy through the observe FIFO while serving entropy to consumers.

Procedure:

- Disable the entropy complex.
- Configure realistic health test threshold values for FIPS/CC compliant mode.
- Enable ENTROPY_SRC in FIPS mode.
- Enable Firmware Override - Observe.
- Enable CSRNG.
- Enable both EDNs in auto request mode.
- Trigger the execution of various cryptographic hardware blocks consuming entropy to stress test the entropy complex.
- Verify that all entropy consuming endpoints can finish their operations and do not hang.
- Verify that the observe FIFO depth is non-zero and read out post-health test entropy for validation testing.
- Repeat the procedure four times with the ENTROPY_SRC.RNG_BIT_ENABLE feature being enabled (once for every channel).

Notes for silicon targets:

- This test requires access to the ENTROPY_SRC.FW_OV.OBSERVE feature, which is gated by OTP.
  This test might thus need to be done in a secure facility.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td>No tests</td>
  <td><a href="01_feature_report.md#entropy_srcfw_ovobserve">ENTROPY_SRC.FW_OV.OBSERVE</a><br><a href="01_feature_report.md#entropy_srcmodefips">ENTROPY_SRC.MODE.FIPS</a><br><a href="01_feature_report.md#entropy_srcrng_bit_enable">ENTROPY_SRC.RNG_BIT_ENABLE</a></td>
</tr>
  </tbody>
</table>

## conditioning

Verify genbits seeds in bypass mode as predicted.
Verify genbits seeds after sha3 conditioning as predicted.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#entropy_src_rng">entropy_src_rng</a></td>
  <td><a href="01_feature_report.md#entropy_srcmodebypass">ENTROPY_SRC.MODE.BYPASS</a><br><a href="01_feature_report.md#entropy_srcrng_bit_enable">ENTROPY_SRC.RNG_BIT_ENABLE</a></td>
</tr>
  </tbody>
</table>

## external_health_tests

Verify the external health test (XHT) interface and functionality, including continuous
and windowed functionality and different high/low thresholds and watermarks.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#entropy_src_rng_with_xht_rsps">entropy_src_rng_with_xht_rsps</a></td>
  <td><a href="01_feature_report.md#entropy_srchealth_tests_ext">ENTROPY_SRC.HEALTH_TESTS_EXT</a></td>
</tr>
  </tbody>
</table>

## firmware

Verify ability to access entropy register based on value of efuse input
Verify sw_regupd, me_regwen bits enables/disables write access to control registers
Verify control registers are read-only while DUT is enabled
Verify registers at End-Of-Test


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#entropy_src_fw_ov">entropy_src_fw_ov</a><br><a href="03_test_report.md#entropy_src_rng">entropy_src_rng</a><br><a href="03_test_report.md#entropy_src_smoke">entropy_src_smoke</a></td>
  <td><a href="01_feature_report.md#entropy_srcroute_to_firmware">ENTROPY_SRC.ROUTE_TO_FIRMWARE</a></td>
</tr>
  </tbody>
</table>

## firmware_mode

Verify health_checks aren't active
Verify bypass active
Verify read FIFO

- Random FIFO depths


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#entropy_src_fw_ov">entropy_src_fw_ov</a></td>
  <td><a href="01_feature_report.md#entropy_srcfw_ovobserve">ENTROPY_SRC.FW_OV.OBSERVE</a><br><a href="01_feature_report.md#entropy_srcmodebypass">ENTROPY_SRC.MODE.BYPASS</a><br><a href="01_feature_report.md#entropy_srcroute_to_firmware">ENTROPY_SRC.ROUTE_TO_FIRMWARE</a></td>
</tr>
  </tbody>
</table>

## firmware_ov_read_contiguous_data

Verify that firmware can read 1024 unaltered, contiguous symbols from the noise source.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#entropy_src_fw_ov_contiguous">entropy_src_fw_ov_contiguous</a></td>
  <td><a href="01_feature_report.md#entropy_srcfw_ovextract_and_insert">ENTROPY_SRC.FW_OV.EXTRACT_AND_INSERT</a><br><a href="01_feature_report.md#entropy_srcfw_ovobserve">ENTROPY_SRC.FW_OV.OBSERVE</a><br><a href="01_feature_report.md#entropy_srcroute_to_firmware">ENTROPY_SRC.ROUTE_TO_FIRMWARE</a></td>
</tr>
  </tbody>
</table>

## functional_errors

Verify that all possible classes of fatal errors (FIFOs, Counters, state machine
exceptions, etc.) have been generated.  These errors typically violate assumptions
made by the scoreboard, and thus cannot be managed by other tests.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#entropy_src_functional_errors">entropy_src_functional_errors</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## health_checks

Verify AdaptProp, RepCnt, RepCntSym, Bucket, Markov health check results
match predicted.

- Generate passing and failing raw entropy streams
- Random window sizes
- Default and random hi/lo bypass/fips thresholds
- Enables/fail counts/clears
- Verify hi/lo bypass/fips watermarks
- Verify External health check behaves as predicted
- Verify outputs match internal reg values/entropy bus
- Pulse inputs and verify captured
- Verify health testing stops when no demand for entropy


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#entropy_src_rng">entropy_src_rng</a></td>
  <td><a href="01_feature_report.md#entropy_srchealth_tests">ENTROPY_SRC.HEALTH_TESTS</a><br><a href="01_feature_report.md#entropy_srchealth_tests_ext">ENTROPY_SRC.HEALTH_TESTS_EXT</a><br><a href="01_feature_report.md#entropy_srcmodebypass">ENTROPY_SRC.MODE.BYPASS</a><br><a href="01_feature_report.md#entropy_srcmodefips">ENTROPY_SRC.MODE.FIPS</a><br><a href="01_feature_report.md#entropy_srcrng_bit_enable">ENTROPY_SRC.RNG_BIT_ENABLE</a></td>
</tr>
  </tbody>
</table>

## interrupts

Verify es_entropy_valid interrupt asserts as predicted.
Verify es_observe_fifo_ready interrupt asserts as predicted.
Verify es_health_test_failed interrupt asserts as predicted.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#entropy_src_intr">entropy_src_intr</a><br><a href="03_test_report.md#entropy_src_rng">entropy_src_rng</a></td>
  <td><a href="01_feature_report.md#entropy_srcrng_bit_enable">ENTROPY_SRC.RNG_BIT_ENABLE</a></td>
</tr>
  </tbody>
</table>

## rng_max_rate

Verify RNG entropy at maximum production rate


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#entropy_src_rng_max_rate">entropy_src_rng_max_rate</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## rng_mode

Verify rng entropy

- Random FIFO depths
- Random rates
- Verify single_bit_mode for all bit_selector values

Verify FIPS bits match predicted


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#entropy_src_rng">entropy_src_rng</a></td>
  <td><a href="01_feature_report.md#entropy_srcmodefips">ENTROPY_SRC.MODE.FIPS</a><br><a href="01_feature_report.md#entropy_srcrng_bit_enable">ENTROPY_SRC.RNG_BIT_ENABLE</a></td>
</tr>
  </tbody>
</table>

## smoke

Enable entropy_src, wait for interrupt, verify entropy.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#entropy_src_smoke">entropy_src_smoke</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## stress_all

Combine the individual test points while injecting TL errors and
running CSR tests in parallel.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#entropy_src_stress_all">entropy_src_stress_all</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>
