# edn Testpoint Report

## alerts

Verify recov_alert_sts asserts/clears as predicted.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#edn_alert">edn_alert</a></td>
  <td><a href="01_feature_report.md#ednbus_cmp_alert">EDN.BUS_CMP_ALERT</a></td>
</tr>
  </tbody>
</table>

## chip_sw_edn_auto_mode (dragonfly)
Verify EDN operation in auto request mode.

Verify that EDN delivers entropy in auto request mode.

Procedure:

- Disable the entropy complex.
- Enable ENTROPY_SRC in FIPS mode.
- Enable CSRNG.
- Enable EDN0 and EDN1 in auto request mode and with non-deterministic seeds (flag0 = kMultiBitBool4False for Instantiate and Reseed commands).
- Trigger the execution of various cryptographic hardware blocks consuming entropy to stress test the EDNs.
- Verify that all entropy consuming endpoints can finish their operations and do not hang.
- Repeat the procedure with different EDN configurations.
  In particular, modify:
  - The command length or amount of optional additional data.
  - The generate length parameter.
  - The MAX_NUM_REQS_BETWEEN_RESEEDS register.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_edn_auto_mode-dragonfly">chip_sw_edn_auto_mode (dragonfly)</a></td>
  <td><a href="01_feature_report.md#ednmodeauto">EDN.MODE.AUTO</a></td>
</tr>
  </tbody>
</table>

## chip_sw_edn_auto_mode (egret)
Verify EDN operation in auto request mode.

Verify that EDN delivers entropy in auto request mode.

Procedure:

- Disable the entropy complex.
- Enable ENTROPY_SRC in FIPS mode.
- Enable CSRNG.
- Enable EDN0 and EDN1 in auto request mode and with non-deterministic seeds (flag0 = kMultiBitBool4False for Instantiate and Reseed commands).
- Trigger the execution of various cryptographic hardware blocks consuming entropy to stress test the EDNs.
- Verify that all entropy consuming endpoints can finish their operations and do not hang.
- Repeat the procedure with different EDN configurations.
  In particular, modify:
  - The command length or amount of optional additional data.
  - The generate length parameter.
  - The MAX_NUM_REQS_BETWEEN_RESEEDS register.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_edn_auto_mode-egret">chip_sw_edn_auto_mode (egret)</a></td>
  <td><a href="01_feature_report.md#ednmodeauto">EDN.MODE.AUTO</a></td>
</tr>
  </tbody>
</table>

## chip_sw_edn_boot_mode (dragonfly)
Verify EDN operation in boot-time request mode.

Verify that EDN delivers entropy in boot-time request mode and that the `edn_fips` bit correctly signals to endpoints whether the delivered entropy is derived from a FIPS/CC compliant seed or not.

Procedure:

- Disable the entropy complex.
- Enable ENTROPY_SRC in boot-time mode, e.g., by setting CONF.FIPS_ENABLE to kMultiBitBool4False.
- Enable CSRNG.
- Enable EDN1 (the one connected to ACC RND) in boot-time request mode.
- Disable ENTROPY_SRC.
- Since EDN1 provides entropy only to the ACC, CSRNG will be idle.
- Enable ENTROPY_SRC in FIPS mode.
- Enable EDN0 (the one connected to ACC URND and other endpoints) in auto request mode.
- Launch an ACC program consuming entropy via both the RND and the URND interface.
- Verify that the ACC program completes (entropy available) and that ACC sets ERR_BITS.RND_FIPS_CHK_FAIL to indicate the reception of non-FIPS/CC-compliant entropy over the RND interface.
- Consume entropy through rv_core_ibex.RND_DATA and verify, using rv_core_ibex.RND_STATUS, that the received bits are FIPS compliant.
- Disable the entropy complex.
- Enable ENTROPY_SRC in FIPS mode.
- Enable CSRNG.
- Enable EDN1 (the one connected to ACC RND) in auto request mode.
- Disable ENTROPY_SRC.
- Enable ENTROPY_SRC in boot-time mode.
- Enable EDN0 (the one connected to ACC URND and other endpoints) in boot-time request mode.
- Launch an ACC program consuming entropy via both the RND and the URND interface.
- Verify that the ACC program completes (entropy available) and that ACC does not set ERR_BITS.RND_FIPS_CHK_FAIL.
- Consume entropy through rv_core_ibex.RND_DATA and verify, using rv_core_ibex.RND_STATUS, that the received bits are FIPS NON-compliant.
- Disable the entropy complex.
- Enable ENTROPY_SRC in FIPS mode.
- Enable CSRNG.
- Enable EDN1 and EDN0 in auto request mode and with non-deterministic seeds (flag0 = kMultiBitBool4False for Instantiate and Reseed commands).
- Re-launch the ACC program.
- Verify that the ACC program completes (entropy available) and that ACC does not set ERR_BITS.RND_FIPS_CHK_FAIL.
- Consume entropy through rv_core_ibex.RND_DATA and verify, using rv_core_ibex.RND_STATUS, that the received bits are FIPS compliant.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_edn_boot_mode-dragonfly">chip_sw_edn_boot_mode (dragonfly)</a></td>
  <td><a href="01_feature_report.md#ednmodeauto">EDN.MODE.AUTO</a><br><a href="01_feature_report.md#ednmodeboot">EDN.MODE.BOOT</a><br><a href="01_feature_report.md#edntrack_seed_compliance">EDN.TRACK_SEED_COMPLIANCE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_edn_boot_mode (egret)
Verify EDN operation in boot-time request mode.

Verify that EDN delivers entropy in boot-time request mode and that the `edn_fips` bit correctly signals to endpoints whether the delivered entropy is derived from a FIPS/CC compliant seed or not.

Procedure:

- Disable the entropy complex.
- Enable ENTROPY_SRC in boot-time mode, e.g., by setting CONF.FIPS_ENABLE to kMultiBitBool4False.
- Enable CSRNG.
- Enable EDN1 (the one connected to ACC RND) in boot-time request mode.
- Disable ENTROPY_SRC.
- Since EDN1 provides entropy only to the ACC, CSRNG will be idle.
- Enable ENTROPY_SRC in FIPS mode.
- Enable EDN0 (the one connected to ACC URND and other endpoints) in auto request mode.
- Launch an ACC program consuming entropy via both the RND and the URND interface.
- Verify that the ACC program completes (entropy available) and that ACC sets ERR_BITS.RND_FIPS_CHK_FAIL to indicate the reception of non-FIPS/CC-compliant entropy over the RND interface.
- Consume entropy through rv_core_ibex.RND_DATA and verify, using rv_core_ibex.RND_STATUS, that the received bits are FIPS compliant.
- Disable the entropy complex.
- Enable ENTROPY_SRC in FIPS mode.
- Enable CSRNG.
- Enable EDN1 (the one connected to ACC RND) in auto request mode.
- Disable ENTROPY_SRC.
- Enable ENTROPY_SRC in boot-time mode.
- Enable EDN0 (the one connected to ACC URND and other endpoints) in boot-time request mode.
- Launch an ACC program consuming entropy via both the RND and the URND interface.
- Verify that the ACC program completes (entropy available) and that ACC does not set ERR_BITS.RND_FIPS_CHK_FAIL.
- Consume entropy through rv_core_ibex.RND_DATA and verify, using rv_core_ibex.RND_STATUS, that the received bits are FIPS NON-compliant.
- Disable the entropy complex.
- Enable ENTROPY_SRC in FIPS mode.
- Enable CSRNG.
- Enable EDN1 and EDN0 in auto request mode and with non-deterministic seeds (flag0 = kMultiBitBool4False for Instantiate and Reseed commands).
- Re-launch the ACC program.
- Verify that the ACC program completes (entropy available) and that ACC does not set ERR_BITS.RND_FIPS_CHK_FAIL.
- Consume entropy through rv_core_ibex.RND_DATA and verify, using rv_core_ibex.RND_STATUS, that the received bits are FIPS compliant.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_edn_boot_mode-egret">chip_sw_edn_boot_mode (egret)</a></td>
  <td><a href="01_feature_report.md#ednmodeauto">EDN.MODE.AUTO</a><br><a href="01_feature_report.md#ednmodeboot">EDN.MODE.BOOT</a><br><a href="01_feature_report.md#edntrack_seed_compliance">EDN.TRACK_SEED_COMPLIANCE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_edn_entropy_reqs (dragonfly)
Verify the entropy requests from all peripherals.

Verify that there are no misconnects between each peripheral requesting entropy.
TODO: system level scenario: have all entropy sources request entropy in the same test
one after to show boot to post boot load, cycling all entropy blocks off and on again.
Ensure there are no deadlocks and everything works as expected.
X'ref'ed with each IP test that requests entropy from EDN.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_csrng_edn_concurrency-dragonfly">chip_sw_csrng_edn_concurrency (dragonfly)</a><br><a href="03_test_report.md#chip_sw_edn_entropy_reqs-dragonfly">chip_sw_edn_entropy_reqs (dragonfly)</a><br><a href="03_test_report.md#chip_sw_entropy_src_ast_rng_req-dragonfly">chip_sw_entropy_src_ast_rng_req (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_edn_entropy_reqs (egret)
Verify the entropy requests from all peripherals.

Verify that there are no misconnects between each peripheral requesting entropy.
TODO: system level scenario: have all entropy sources request entropy in the same test
one after to show boot to post boot load, cycling all entropy blocks off and on again.
Ensure there are no deadlocks and everything works as expected.
X'ref'ed with each IP test that requests entropy from EDN.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_csrng_edn_concurrency-egret">chip_sw_csrng_edn_concurrency (egret)</a><br><a href="03_test_report.md#chip_sw_edn_entropy_reqs-egret">chip_sw_edn_entropy_reqs (egret)</a><br><a href="03_test_report.md#chip_sw_entropy_src_ast_rng_req-egret">chip_sw_entropy_src_ast_rng_req (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_edn_kat (dragonfly)
Perform a Known-Answer Test with EDN.

Verify that EDN delivers the expected entropy bits when running CSRNG in fully deterministic mode.

Procedure:

- Disable the entropy complex.
- Enable ENTROPY_SRC in FIPS mode.
- Enable CSRNG.
- Enable EDN1 in auto request mode.
- Enable EDN0 in auto request mode with the following configuration:
  - Use deterministic seeds (set flag0 = kMultiBitBool4True in all instantiate/reseed application command headers sent to CSRNG).
    This causes CSRNG to ignore the seed provided by ENTROPY_SRC and exclusively use the optional additional data provided by EDN.
  - Set the command length or amount of optional additional data for the Instantiate and Reseed commands to 12 words.
  - Set the generate length parameter for the Generate command to 4 blocks.
  - Provide the correct seed material for the Instantiate and Reseed commands.
  - For an example, refer to `chip_sw_csrng_kat_test`.
- Verify that EDN0 delivers the expected entropy bits using the rv_core_ibex.RND_DATA and rv_core_ibex.RND_STATUS registers.
- Disable the entropy complex.
- Enable ENTROPY_SRC in FIPS mode.
- Enable CSRNG.
- Enable EDN1 in auto request mode.
- Enable EDN0 in auto request mode with the following configuration:
  - Use deterministic seeds (set flag0 = kMultiBitBool4True in all instantiate/reseed application command headers sent to CSRNG).
  - Set the command length or amount of optional additional data for the Instantiate and Reseed commands to 12 words.
  - Set the generate length parameter for the Generate command to 1 block.
  - Set the max_num_reqs_between_reseeds parameter for the Generate command to 1.
  - Provide the correct seed material for the Instantiate and Reseed commands.
  - For an example, refer to `chip_sw_aes_masking_off_test`.
- Verify that EDN0 triggers a recoverable alert and sets the RECOV_ALERT_STS.EDN_BUS_CMP_ALERT bit as more entropy is consumed via rv_core_ibex.RND_DATA and CSRNG continues to provide the same entropy bits to EDN0.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_edn_kat-dragonfly">chip_sw_edn_kat (dragonfly)</a></td>
  <td><a href="01_feature_report.md#ednbus_cmp_alert">EDN.BUS_CMP_ALERT</a><br><a href="01_feature_report.md#ednmodeauto">EDN.MODE.AUTO</a></td>
</tr>
  </tbody>
</table>

## chip_sw_edn_kat (egret)
Perform a Known-Answer Test with EDN.

Verify that EDN delivers the expected entropy bits when running CSRNG in fully deterministic mode.

Procedure:

- Disable the entropy complex.
- Enable ENTROPY_SRC in FIPS mode.
- Enable CSRNG.
- Enable EDN1 in auto request mode.
- Enable EDN0 in auto request mode with the following configuration:
  - Use deterministic seeds (set flag0 = kMultiBitBool4True in all instantiate/reseed application command headers sent to CSRNG).
    This causes CSRNG to ignore the seed provided by ENTROPY_SRC and exclusively use the optional additional data provided by EDN.
  - Set the command length or amount of optional additional data for the Instantiate and Reseed commands to 12 words.
  - Set the generate length parameter for the Generate command to 4 blocks.
  - Provide the correct seed material for the Instantiate and Reseed commands.
  - For an example, refer to `chip_sw_csrng_kat_test`.
- Verify that EDN0 delivers the expected entropy bits using the rv_core_ibex.RND_DATA and rv_core_ibex.RND_STATUS registers.
- Disable the entropy complex.
- Enable ENTROPY_SRC in FIPS mode.
- Enable CSRNG.
- Enable EDN1 in auto request mode.
- Enable EDN0 in auto request mode with the following configuration:
  - Use deterministic seeds (set flag0 = kMultiBitBool4True in all instantiate/reseed application command headers sent to CSRNG).
  - Set the command length or amount of optional additional data for the Instantiate and Reseed commands to 12 words.
  - Set the generate length parameter for the Generate command to 1 block.
  - Set the max_num_reqs_between_reseeds parameter for the Generate command to 1.
  - Provide the correct seed material for the Instantiate and Reseed commands.
  - For an example, refer to `chip_sw_aes_masking_off_test`.
- Verify that EDN0 triggers a recoverable alert and sets the RECOV_ALERT_STS.EDN_BUS_CMP_ALERT bit as more entropy is consumed via rv_core_ibex.RND_DATA and CSRNG continues to provide the same entropy bits to EDN0.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_edn_kat-egret">chip_sw_edn_kat (egret)</a></td>
  <td><a href="01_feature_report.md#ednbus_cmp_alert">EDN.BUS_CMP_ALERT</a><br><a href="01_feature_report.md#ednmodeauto">EDN.MODE.AUTO</a></td>
</tr>
  </tbody>
</table>

## chip_sw_edn_sw_mode (dragonfly)
Verify EDN operation in software port mode.

Verify that EDN delivers entropy in software port mode.

Procedure:

- Disable the entropy complex.
- Enable ENTROPY_SRC in FIPS mode.
- Enable CSRNG.
- Enable EDN1 in auto request mode.
- Enable EDN0 in software port mode.
- Trigger the execution of a cryptographic hardware block consuming entropy (e.g., AES) to test EDN0.
- Verify that the entropy consuming endpoint hangs.
- Provide the required commands to EDN0 via SW_CMD_REQ register to start generating and delivering entropy to consumers.
- Verify that the entropy consuming endpoint can finish its operations and does not hang.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_edn_sw_mode-dragonfly">chip_sw_edn_sw_mode (dragonfly)</a></td>
  <td><a href="01_feature_report.md#ednmodesw">EDN.MODE.SW</a></td>
</tr>
  </tbody>
</table>

## chip_sw_edn_sw_mode (egret)
Verify EDN operation in software port mode.

Verify that EDN delivers entropy in software port mode.

Procedure:

- Disable the entropy complex.
- Enable ENTROPY_SRC in FIPS mode.
- Enable CSRNG.
- Enable EDN1 in auto request mode.
- Enable EDN0 in software port mode.
- Trigger the execution of a cryptographic hardware block consuming entropy (e.g., AES) to test EDN0.
- Verify that the entropy consuming endpoint hangs.
- Provide the required commands to EDN0 via SW_CMD_REQ register to start generating and delivering entropy to consumers.
- Verify that the entropy consuming endpoint can finish its operations and does not hang.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_edn_sw_mode-egret">chip_sw_edn_sw_mode (egret)</a></td>
  <td><a href="01_feature_report.md#ednmodesw">EDN.MODE.SW</a></td>
</tr>
  </tbody>
</table>

## csrng_commands

Verify when no/some/all endpoints requesting (test arbiter).
Verify boot request mode behaves as predicted.
Verify BOOT_INS_CMD/BOOT_GEN_CMD registers.
Verify auto request mode behaves as predicted.
Verify RESEED_CMD/GENERATE_CMD/MAX_NUM_REQS_BETWEEN_RESEEDS registers.
Verify MAIN_SM_STATE register bits behave as predicted.
Verify all csrng commands (clen = 0-12, sw_mode, boot/auto_req_mode).
Verify with ready randomly asserting/deasserting


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#edn_genbits">edn_genbits</a></td>
  <td><a href="01_feature_report.md#ednmodeauto">EDN.MODE.AUTO</a><br><a href="01_feature_report.md#ednmodeboot">EDN.MODE.BOOT</a><br><a href="01_feature_report.md#ednmodesw">EDN.MODE.SW</a></td>
</tr>
  </tbody>
</table>

## disable

Disable EDN in all states and verify proper operation when re-enabled.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#edn_disable">edn_disable</a><br><a href="03_test_report.md#edn_disable_auto_req_mode">edn_disable_auto_req_mode</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## errs

Verify ERR_CODE asserts as predicted.
Verify ERR_CODE all reg bits via ERR_CODE_TEST.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#edn_err">edn_err</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## firmware

Verify SW_CMD_REQ/SW_CMD_STS registers/bits behave as predicted.
Verify software mode behaves as predicted.
Verify INSTANTIATE/GENERATE software cmds.
Verify cmd_fifo_reset bit causes fifos to reset.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#edn_genbits">edn_genbits</a></td>
  <td><a href="01_feature_report.md#ednmodesw">EDN.MODE.SW</a></td>
</tr>
  </tbody>
</table>

## genbits

Verify genbits input is transferred to endpoint(s) as predicted.
Verify fips bit(s) are properly transferred to endpoint.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#edn_genbits">edn_genbits</a></td>
  <td><a href="01_feature_report.md#edntrack_seed_compliance">EDN.TRACK_SEED_COMPLIANCE</a></td>
</tr>
  </tbody>
</table>

## interrupts

Verify intr_edn_cmd_req_done interrupt asserts/clears as predicted.
Verify intr_edn_fatal_err interrupt asserts/clears as predicted.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#edn_intr">edn_intr</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## smoke

Verify send instantiate/generate command
Verify single endpoint requests
Verify endpoint data = genbits data


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#edn_smoke">edn_smoke</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## stress_all

Combine the other individual testpoints while injecting TL errors and running CSR tests
in parallel.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#edn_stress_all">edn_stress_all</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>
