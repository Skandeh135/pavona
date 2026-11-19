# csrng Testpoint Report

## alerts

Verify recov_alert asserts when recov_alert_sts becomes non-zero.
Verify each respective bit of recov_alert_sts asserts when:

- Either of the 3 values in the control register are not valid kMultiBitBool values.
- When an initiate or reseed command is sent where flag0 is not a valid kMultiBitBool value.
- The genbits bus value is equal to the prior valid value.
- When an illegal command is used (0x0,0x6-0xf).

Verify that writing zeros to the recoverable alert status register resets all the status bits.
Verify fatal_alert asserts when:

- An illegal state is reached.
- The AES block raises a fatal alert.
- There is an integrity failure on the bus (this is covered by an automated test).


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#csrng_alert">csrng_alert</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_csrng_edn_cmd (dragonfly)
Verify incoming command interface from EDN.

- Have each EDN instance issue an instantiate, reseed and generate command to CSRNG.
- On each command done, verify the reception of edn_cmd_req_done interrupt.
- Run ACC randomness test to test the output from EDN0 and EDN1.
- Check the data returned to EDN via connectivity assertion checks.

Notes for silicon targets:

- In silicon, the connectivity cannot be checked using assertions.
  However, checking that the ACC randomness test finishes allows to quickly assess if both EDNs deliver any entropy which is very fundamental.


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
  <td><a href="01_feature_report.md#csrnginterfacehardware0">CSRNG.INTERFACE.HARDWARE0</a><br><a href="01_feature_report.md#csrnginterfacehardware1">CSRNG.INTERFACE.HARDWARE1</a><br><a href="01_feature_report.md#csrngmodenondeterministic">CSRNG.MODE.NONDETERMINISTIC</a></td>
</tr>
  </tbody>
</table>

## chip_sw_csrng_edn_cmd (egret)
Verify incoming command interface from EDN.

- Have each EDN instance issue an instantiate, reseed and generate command to CSRNG.
- On each command done, verify the reception of edn_cmd_req_done interrupt.
- Run ACC randomness test to test the output from EDN0 and EDN1.
- Check the data returned to EDN via connectivity assertion checks.

Notes for silicon targets:

- In silicon, the connectivity cannot be checked using assertions.
  However, checking that the ACC randomness test finishes allows to quickly assess if both EDNs deliver any entropy which is very fundamental.


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
  <td><a href="01_feature_report.md#csrnginterfacehardware0">CSRNG.INTERFACE.HARDWARE0</a><br><a href="01_feature_report.md#csrnginterfacehardware1">CSRNG.INTERFACE.HARDWARE1</a><br><a href="01_feature_report.md#csrngmodenondeterministic">CSRNG.MODE.NONDETERMINISTIC</a></td>
</tr>
  </tbody>
</table>

## chip_sw_csrng_fuse_en_sw_app_read (dragonfly)
Verify the fuse input to CSRNG.

- Initialize the OTP with the fuse that control whether the SW can read the CSRNG state
  enabled.
- Issue an instantiate command to request entropy.
- Verify that SW can read the internal state values.
- Reset the chip and repeat the steps above, but this time, initialized the OTP with
  fuse disabled.
- Verify that the SW reads back all zeros when reading the internal state values.

Notes for silicon targets:

- The current understanding is that the en_csrng_sw_app_read OTP switch controlling the CSRNG.READ_INT_STATE feature will need to be enabled also in the PROD life-cycle state for validation and known-answer testing.
  Thus, burning the en_csrng_sw_app_read OTP fuses is not advisable for silicon validation.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_csrng_fuse_en_sw_app_read_test-dragonfly">chip_sw_csrng_fuse_en_sw_app_read_test (dragonfly)</a></td>
  <td><a href="01_feature_report.md#csrnginterfacesoftware">CSRNG.INTERFACE.SOFTWARE</a><br><a href="01_feature_report.md#csrngread_int_state">CSRNG.READ_INT_STATE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_csrng_fuse_en_sw_app_read (egret)
Verify the fuse input to CSRNG.

- Initialize the OTP with the fuse that control whether the SW can read the CSRNG state
  enabled.
- Issue an instantiate command to request entropy.
- Verify that SW can read the internal state values.
- Reset the chip and repeat the steps above, but this time, initialized the OTP with
  fuse disabled.
- Verify that the SW reads back all zeros when reading the internal state values.

Notes for silicon targets:

- The current understanding is that the en_csrng_sw_app_read OTP switch controlling the CSRNG.READ_INT_STATE feature will need to be enabled also in the PROD life-cycle state for validation and known-answer testing.
  Thus, burning the en_csrng_sw_app_read OTP fuses is not advisable for silicon validation.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_csrng_fuse_en_sw_app_read_test-egret">chip_sw_csrng_fuse_en_sw_app_read_test (egret)</a></td>
  <td><a href="01_feature_report.md#csrnginterfacesoftware">CSRNG.INTERFACE.SOFTWARE</a><br><a href="01_feature_report.md#csrngread_int_state">CSRNG.READ_INT_STATE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_csrng_known_answer_tests (dragonfly)
Verify our ability to run known-answer tests in SW.

- Configure the software instance in deterministic mode with the expected seed (as per
  the NIST-specified test for CTR_DRBG operation).
  Read the DRBG internal K and V state using INT_STATE_VAL register and compare the obtained values against the test vector expected values.
- Perform generate operations as required by the test vector.
- Compare the results to test expectations.

Notes for silicon targets:

- For the INT_STATE_VAL register to provide read access to the internal K and V state, the en_csrng_sw_app_read OTP switch needs to be in the `kMultiBitBool8True` position.
  The current understanding is that this will need to be enabled also in the PROD life-cycle state for validation and known-answer testing.
  Thus, the test doesn't need to be run in a secure environment.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_csrng_kat_test-dragonfly">chip_sw_csrng_kat_test (dragonfly)</a></td>
  <td><a href="01_feature_report.md#csrnginterfacesoftware">CSRNG.INTERFACE.SOFTWARE</a><br><a href="01_feature_report.md#csrngmodedeterministic">CSRNG.MODE.DETERMINISTIC</a><br><a href="01_feature_report.md#csrngread_int_state">CSRNG.READ_INT_STATE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_csrng_known_answer_tests (egret)
Verify our ability to run known-answer tests in SW.

- Configure the software instance in deterministic mode with the expected seed (as per
  the NIST-specified test for CTR_DRBG operation).
  Read the DRBG internal K and V state using INT_STATE_VAL register and compare the obtained values against the test vector expected values.
- Perform generate operations as required by the test vector.
- Compare the results to test expectations.

Notes for silicon targets:

- For the INT_STATE_VAL register to provide read access to the internal K and V state, the en_csrng_sw_app_read OTP switch needs to be in the `kMultiBitBool8True` position.
  The current understanding is that this will need to be enabled also in the PROD life-cycle state for validation and known-answer testing.
  Thus, the test doesn't need to be run in a secure environment.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_csrng_kat_test-egret">chip_sw_csrng_kat_test (egret)</a></td>
  <td><a href="01_feature_report.md#csrnginterfacesoftware">CSRNG.INTERFACE.SOFTWARE</a><br><a href="01_feature_report.md#csrngmodedeterministic">CSRNG.MODE.DETERMINISTIC</a><br><a href="01_feature_report.md#csrngread_int_state">CSRNG.READ_INT_STATE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_csrng_lc_hw_debug_en (dragonfly)
Verify the effect of LC HW debug enable on CSRNG.

lc_hw_debug_en is used to diversify the csrng seed.

- Configure ENTROPY_SRC into bypassing the conditioner and directly inject known
  entropy.
- Instantiate CSRNG in non-deterministic mode and have it load the known entropy from ENTROPY_SRC while in the TEST_UNLOCKED or DEV life-cycle state (HW_DEBUG_EN = 1).
- Retrieve entropy from CSRNG and save it in flash and reset the system.
- Run the process again and ensure the exact same result can be reproduced (similar to
  KAT).
- Advance the device to PROD or PROD_END life-cycle state (HW_DEBUG_EN = 0).
- Again configure ENTROPY_SRC to bypass the conditioner and use direct injection.
- Again instantiate CSRNG in non-deterministic mode and have it load the known entropy from ENTROPY_SRCw while in the new state.
- The newly fetched entropy and the old entropy stored in flash should not match.

Notes for silicon targets:

- This test goes through life-cycle stages that will permanently change the characteristic of the chip.
- These tests will need to be done in secure environments where there is access to chips in the TEST_UNLOCKED or DEV life-cycle states.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_csrng_lc_hw_debug_en_test-dragonfly">chip_sw_csrng_lc_hw_debug_en_test (dragonfly)</a></td>
  <td><a href="01_feature_report.md#csrnginterfacesoftware">CSRNG.INTERFACE.SOFTWARE</a><br><a href="01_feature_report.md#csrnglifecycledebugenable">CSRNG.LIFECYCLE.DEBUGENABLE</a><br><a href="01_feature_report.md#csrngmodenondeterministic">CSRNG.MODE.NONDETERMINISTIC</a></td>
</tr>
  </tbody>
</table>

## chip_sw_csrng_lc_hw_debug_en (egret)
Verify the effect of LC HW debug enable on CSRNG.

lc_hw_debug_en is used to diversify the csrng seed.

- Configure ENTROPY_SRC into bypassing the conditioner and directly inject known
  entropy.
- Instantiate CSRNG in non-deterministic mode and have it load the known entropy from ENTROPY_SRC while in the TEST_UNLOCKED or DEV life-cycle state (HW_DEBUG_EN = 1).
- Retrieve entropy from CSRNG and save it in flash and reset the system.
- Run the process again and ensure the exact same result can be reproduced (similar to
  KAT).
- Advance the device to PROD or PROD_END life-cycle state (HW_DEBUG_EN = 0).
- Again configure ENTROPY_SRC to bypass the conditioner and use direct injection.
- Again instantiate CSRNG in non-deterministic mode and have it load the known entropy from ENTROPY_SRCw while in the new state.
- The newly fetched entropy and the old entropy stored in flash should not match.

Notes for silicon targets:

- This test goes through life-cycle stages that will permanently change the characteristic of the chip.
- These tests will need to be done in secure environments where there is access to chips in the TEST_UNLOCKED or DEV life-cycle states.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_csrng_lc_hw_debug_en_test-egret">chip_sw_csrng_lc_hw_debug_en_test (egret)</a></td>
  <td><a href="01_feature_report.md#csrnginterfacesoftware">CSRNG.INTERFACE.SOFTWARE</a><br><a href="01_feature_report.md#csrnglifecycledebugenable">CSRNG.LIFECYCLE.DEBUGENABLE</a><br><a href="01_feature_report.md#csrngmodenondeterministic">CSRNG.MODE.NONDETERMINISTIC</a></td>
</tr>
  </tbody>
</table>

## cmds

Verify all csrng commands req/status behave as predicted on all applications: HW0, HW1 and SW.
Verify above for all valid values of acmd, clen, flags, glen.
Verify for multiple hw app interfaces running in parallel.
Verify sw/hw app interfaces running in parallel.
Verify main_sm_state for sw/hw apps.
Verify that genbits generates the amount specified by glen.
Verify fips bit is set to the inverse of flag0 that was used on the last initialize or reseed.
Verify that if otp_en_csrng_sw_app_read is set, genbits and int_state_value registers are readable, and unreadable otherwise.
Verify that when AES_HALT is set during a generate command that no request is sent to the AES block.
Verify commands with continuous/non-continuous valid.
Verify that if FIPS bit drops at input from entropy source that the generated block also has FIPS low.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#csrng_cmds">csrng_cmds</a></td>
  <td><a href="01_feature_report.md#csrnginterfacehardware0">CSRNG.INTERFACE.HARDWARE0</a><br><a href="01_feature_report.md#csrnginterfacehardware1">CSRNG.INTERFACE.HARDWARE1</a><br><a href="01_feature_report.md#csrnginterfacesoftware">CSRNG.INTERFACE.SOFTWARE</a><br><a href="01_feature_report.md#csrngread_int_state">CSRNG.READ_INT_STATE</a></td>
</tr>
  </tbody>
</table>

## err

Verify err_code register bits assert when:

- An error has been detected in any of the internal fifos and the corresponding write/read/state bits.
- An illegal state is reached in any of the 6 state machines.
- An error is detected in the generate command counter.

Verify that the err_code register clears all bits after reset.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#csrng_err">csrng_err</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## interrupts

This test verifies the behavior of the Interrupt State Register.
Verify cs_cmd_req_done interrupt asserts when glen number of genbit words have been generated.
Verify cs_entropy_req interrupt asserts when instantiate or reseed is called with flag0
set to false.
Verify cs_hw_inst_exc interrupt asserts when any of the application interfaces responds with a CSRNG_ERROR response status signal.
Verify cs_fatal_err interrupt asserts when any bit of err_code register is set.
Verify that each interrupt clears back to 0 after writing the corresponding interrupt state bit.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#csrng_intr">csrng_intr</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## life cycle

Verify lifecycle hardware debug mode.
When lc_hw_debug_en_i is set to on, the seed from the entropy source must be xor'ed with the diversification value.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#csrng_cmds">csrng_cmds</a></td>
  <td><a href="01_feature_report.md#csrnglifecycledebugenable">CSRNG.LIFECYCLE.DEBUGENABLE</a></td>
</tr>
  </tbody>
</table>

## smoke

Verify that sending an instantiate command via the SW path returns OK.
Instantiate the CSRNG with `flag0` set to `true` and `clen` set to 12.
Verify that sending a generate command via the SW path returns `glen=1` number of words followed by an OK.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#csrng_smoke">csrng_smoke</a></td>
  <td><a href="01_feature_report.md#csrnginterfacesoftware">CSRNG.INTERFACE.SOFTWARE</a></td>
</tr>
  </tbody>
</table>

## stress_all

Combine the other individual testpoints while injecting TL errors and running CSR tests in parallel.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#csrng_stress_all">csrng_stress_all</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>
