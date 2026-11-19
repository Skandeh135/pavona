# keymgr Testpoint Report

## cfgen_during_op

`cfg_regwen` is RO reg and it gates bunch of write access of other registers, which is
not tested in common CSR tests.

Stimulus and checks:
Test command and reg access gated by `cfg_regwen` is ignored during operation.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#keymgr_cfg_regwen">keymgr_cfg_regwen</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_keymgr_derive_attestation (egret)
Verify the Attestation CDI.

- For each keymgr operational state: `CreatorRootKey`, `OwnerIntKey` and `OwnerKey`:
  - Generate identity SW output for the Attestation CDI.
  - Generate ACC sideload output for the Attestation CDI.
- Ensure that the key output changes after calculating the previous steps after a
  keymgr advance operation.
- The keymgr shall be able to reproduce the same keys for a give device configuration
  and known set of inputs.
- The software binding registers must be locked after configuration until a keymgr
  advance operation.

Notes:

- The device initial state needs to be equivalent to the end state of the
  `manuf_ft_provision_rma_token_and_personalization` testpoint, otherwise the keymgr
  will fail to advance into operational states.
- Ensure the entropy complex is running in continuous mode, and that KMAC is configured
  to extract entropy from EDN.
- The test should check for any error or fault code status, to ensure all operations
  executed successfully.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_keymgr_derive_attestation-egret">chip_sw_keymgr_derive_attestation (egret)</a></td>
  <td><a href="01_feature_report.md#keymgrderiveattestation">KEYMGR.DERIVE.ATTESTATION</a><br><a href="01_feature_report.md#keymgrgenerateidentity">KEYMGR.GENERATE.IDENTITY</a><br><a href="01_feature_report.md#keymgrgenerateoutput">KEYMGR.GENERATE.OUTPUT</a></td>
</tr>
  </tbody>
</table>

## chip_sw_keymgr_derive_sealing (egret)
Verify the Sealing CDI.

Same as `chip_sw_keymgr_derive_attestation`, except using Sealing CDI outputs.

To test key versioning:

- Configure the max version register for each keymgr operational state.
- Test a valid and an invalid key version when generating SW and sideload keys.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_keymgr_derive_sealing-egret">chip_sw_keymgr_derive_sealing (egret)</a></td>
  <td><a href="01_feature_report.md#keymgrderivesealing">KEYMGR.DERIVE.SEALING</a><br><a href="01_feature_report.md#keymgrgenerateidentity">KEYMGR.GENERATE.IDENTITY</a><br><a href="01_feature_report.md#keymgrgenerateoutput">KEYMGR.GENERATE.OUTPUT</a><br><a href="01_feature_report.md#keymgrkey_versioning">KEYMGR.KEY_VERSIONING</a></td>
</tr>
  </tbody>
</table>

## chip_sw_keymgr_key_derivation (egret)
Verify the keymgr advances to all states and generate identity / SW output.

- In the SW test, write fixed value to OTP for root_key and write creator and owner
  seeds in flash. And then reboot the chip.
- In the SV sequence, backdoor read Device ID and ROM digest through CSRs.
- For HardwareRevisionSecret, use the constant values in design.
- Configure the keymgr and advance to `CreatorRootKey` and `OwnerIntermediateKey`.
- Check keymgr internal keys after advance operations.
- Generate identity / SW output for the Sealing CDI.
   - No need to test the Attestation CDI in chip-level as the only difference is to
     use another set of CSR values, and the rest of inputs are the same as the Sealing
     CDI.
- KMAC should finish hashing successfully (not visible to SW) and return digest to
  keymgr.
- Read keymgr CSRs `SW_SHARE*` and verify the return values.
- Advance to `Disabled` and verify keymgr enters the state successfully.

- For each operation, wait for the interrupt `op_done` to be triggered and check CSR
  `op_status` is `DONE_SUCCESS`.

- Note: there are 3 ways of calculating the expected digest for comparison. Any of them
  is acceptable.
  - Use SW to calculate that, and it will also exercise the Ibex.
  - SW sends all the keys through CSRs to KMAC to generate the digest data.
  - DV calls C functions to generate and backdoor load to a specific memory location
    for SW. (Adopt this approach.)

X-ref'ed with kmac test.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_keymgr_key_derivation-egret">chip_sw_keymgr_key_derivation (egret)</a><br><a href="03_test_report.md#chip_sw_keymgr_key_derivation_jitter_en-egret">chip_sw_keymgr_key_derivation_jitter_en (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_keymgr_sideload_acc (egret)
Verify the keymgr sideload interface to ACC.

Load ACC binary image, the rest is similar to `chip_keymgr_sideload_kmac`, except
sideloading to acc.

Clear the sideload key once done.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_keymgr_sideload_acc-egret">chip_sw_keymgr_sideload_acc (egret)</a></td>
  <td><a href="01_feature_report.md#keymgrsideloadacc">KEYMGR.SIDELOAD.ACC</a></td>
</tr>
  </tbody>
</table>

## chip_sw_keymgr_sideload_aes (egret)
Verify the keymgr sideload interface to AES.

Same as `chip_keymgr_sideload_kmac`, except, sideload to AES.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_keymgr_sideload_aes-egret">chip_sw_keymgr_sideload_aes (egret)</a></td>
  <td><a href="01_feature_report.md#keymgrsideloadaes">KEYMGR.SIDELOAD.AES</a></td>
</tr>
  </tbody>
</table>

## chip_sw_keymgr_sideload_kmac (egret)
Verify the keymgr sideload interface to KMAC.

- Configure the keymgr and advance to the `OwnerIntKey` state.
- Request keymgr to generate hw key for KMAC sideload key slot.
- Request KMAC operation with sideload key configuration.
- Verify the digest for correctness (should match the DV-side result).
- Clear keymgr's KMAC sideload key slot.
- Request KMAC operation with sideload key configuration.
- Verify the digest value has changed.
- Request keymgr to derive the same key for the KMAC sideload key slot.
- Request KMAC operation with sideload key configuration.
- In simulation environments, verify the digest for correctness (should match the
  DV-side result again).

Notes for silicon targets:

- The device needs to be personalized before the test can be executed. See
  `manuf_ft_provision_rma_token_and_personalization` for more details.
- Sideload is expected to work in the following keymgr states: `CreatorRootKey`,
  `OwnerIntKey` and `OwnerKey`. The test program should try to cover as many states
  as possible given the initial device state.
- Key derivations must be reproducible across boot cycles during regular operating
  conditions.

X-ref'ed with chip_kmac_app_keymgr test.

For SV2 X-ref'ed with chip_sw_kmac_kmac_key_sideload.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_keymgr_sideload_kmac-egret">chip_sw_keymgr_sideload_kmac (egret)</a></td>
  <td><a href="01_feature_report.md#keymgrsideloadkmac">KEYMGR.SIDELOAD.KMAC</a></td>
</tr>
  </tbody>
</table>

## chip_sw_keymgr_sideload_kmac_error (egret)

Verify the effect of KMAC returning an error during a keymgr operation.

- Configure keymgr to enter any of the 3 working states.
- Issue a keymgr operation.
- While the KMAC is actively computing the digest, glitch the KMAC app sparse FSM to
  trigger a fault.
- Verify that KMAC returns an error signal to the keymgr via checking keymgr CSRs, when
  the operation is done:
  - Check `op_status` is set to `DONE_ERROR`.
  - Check `fault_status.kmac_done` is set to 1.


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
  <td>No features</td>
</tr>
  </tbody>
</table>

## direct_to_disabled_state

Stimulus and checks:
Directly go to `StDisabled` from any state and check `StDisabled` is entered correctly.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#keymgr_direct_to_disabled">keymgr_direct_to_disabled</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## invalid_hw_input

Verify `keymgr` behavior with invalid data patterns.

Stimulus:

- Drive all 0s or 1s on any of these inputs - flash seeds, otp_key, diversification ID,
  Rom digest etc.
- Make sure all cases are covered in `csr_debug_cg`.

Checks:

- Check interrupts `err` is triggered.
- Check alert `recov_operation_err` is triggered and err_code is `INVALID_KMAC_DATA`.
- Check SW output isn't updated and working state remains the same.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#keymgr_hwsw_invalid_input">keymgr_hwsw_invalid_input</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## invalid_sw_input

Verify `keymgr` behavior with invalid key version.

Stimulus:
Randomize KEY_VERSION and MAX_*_VER registers.

Checks:
when KEY_VERSION > MAX_*_VER

- Check interrupts `err` is triggered.
- Check alert `recov_operation_err` is triggered and err_code is `INVALID_KMAC_INPUT`.
- Check KMAC output key is corrupted and working state remains the same.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#keymgr_sw_invalid_input">keymgr_sw_invalid_input</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## kmac_error_response

Verify `keymgr` behavior on error response received from `KMAC` after sending data to
it.

Stimulus:

- Drive error from KMAC interface when VALID is high.
- Or drive all 0s or 1s as KMAC input digest data

Checks:
Same as above entry - "invalid_cmd".


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#keymgr_kmac_rsp_err">keymgr_kmac_rsp_err</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## lc_disable

Life cycle can disable keymgr and let keymgr wipe secret immediately.

Stimulus:
Test life cycle disables keymgr in any state.

Checks:

- If keymgr is not initialized, check it can't be initialized until life cycle enables
  keymgr.
- If keymgr is in a valid state after `StReset`, key output to KMAC is wiped immediately
  and SW output will be invalid after OP is done.
- If keymgr in disabled state, check the behavior is consistent with normal behavior.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#keymgr_lc_disable">keymgr_lc_disable</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## random

Extend from smoke to randomize all SW input data

- Fully randomize SW inputs: rom_ext_desc_*, software_binding_*, salt_*, max_*_key_ver,
  *_key_ver_regwen.
- Randomize key_version any value less than max_*_key_ver, to avoid triggerring
  `invalid_kmac_input` error.
- Fully randomize HW inputs from flash, otp and life cycle.
- Randomize *sw_binding_regwen. Ensure this gates the *_sw_binding and it will
  be cleared after a successful advance operation.

Most of other sequences are derived from this to have similar init and sequence.

Stimulus and checks are the same as smoke.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#keymgr_random">keymgr_random</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## sec_cm_additional_check

Verify the outcome of injecting faults to security countermeasures.

Stimulus:
As mentioned in `prim_count_check`, `prim_one_hot_check` and `prim_fsm_check`.

Checks:

- Besides checking alert and `fault_status`, issue an operation after injecting faults,
  then ensure that `op_status` is failed and design enters `StInvalid`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#keymgr_sec_cm">keymgr_sec_cm</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## sideload

Keymgr contains HW sideload interfaces to output keys for KMAC, AES, ACC.

Stimulus:

- Generate a keymgr output to HW sideload interface, exercising all the sideload
  interfaces.
- Randomly program any value to Sideload_clear after any operation.

Checks:
Verify the sideload data and status for correctness.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#keymgr_sideload">keymgr_sideload</a><br><a href="03_test_report.md#keymgr_sideload_acc">keymgr_sideload_acc</a><br><a href="03_test_report.md#keymgr_sideload_aes">keymgr_sideload_aes</a><br><a href="03_test_report.md#keymgr_sideload_kmac">keymgr_sideload_kmac</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## smoke

Smoke test accessing a major datapath within the keymgr.
Test operations (advance, gen-id and gen-sw-out) in every state

Stimulus:

- Go through state from `StReset` to `StDisabled`.
- Issue gen-id, gen-sw-output operation in each state, including invalid operations in
  states other than normal operating states (`StCreatorRootKey`, `StOwnerIntKey` and
  `StOwnerRootKey`).
- Randomize `CDI_SEL` and `DEST_SEL`.
- Use default/fixed values for HW/SW inputs.

Checks:

- Check STATUS reg for each operation.
- Check interrupts `op_done` is triggered when operation is done.
- Check `err` and alert `recov_operation_err` are triggered after invalid operation.
- Check KMAC key, KMAC data and output SW data for correctness.
- For invalid operations, check KMAC key, KMAC data and output SW data don't match to
  any of saved meaningful data, which are collected from valid operations. This
  checking method is also applied to other error cases.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#keymgr_smoke">keymgr_smoke</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## stress_all


- Combine above sequences in one test to run sequentially, except csr sequence and
  keymgr_cfg_regwen (requires zero_delays).
- Randomly add reset between each sequence.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#keymgr_stress_all">keymgr_stress_all</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## sync_async_fault_cross

Verify `keymgr` behavior with invalid data patterns.

Stimulus:
Create these 2 direct tests:

- Sync (transactional) fault occurs followed by async (non-transactional) fault.
- Async (non-transactional) fault occurs followed by sync (transactional) fault.

Checks:

- Check interrupts `err` is triggered.
- Check alert `fatal_fault_err` is triggered.
- Check `fault_status` is updated correctly.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#keymgr_sync_async_fault_cross">keymgr_sync_async_fault_cross</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>
