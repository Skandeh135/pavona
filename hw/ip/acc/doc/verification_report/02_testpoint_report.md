# acc Testpoint Report

## acc_mem_gnt_acc_err

Trigger a fault to cause the IMEM/DMEM grant signal to be false when req is asserted.
This in turn should cause dmem_missed_gnt/imem_missed_gnt to get asserted resulting
in a fatal alert (a bad_internal_state fatal error).


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#acc_mem_gnt_acc_err">acc_mem_gnt_acc_err</a></td>
  <td><a href="01_feature_report.md#accsecurewipe">ACC.SECUREWIPE</a></td>
</tr>
  </tbody>
</table>

## acc_non_sec_partial_wipe


See a local wipe signal be raised when a secure wipe is not running. When this happens, we
expect the RTL to stop with a fatal alert. The signals tracked are:

  - sec_wipe_mod_urnd_i in acc_alu_bignum
  - sec_wipe_zero_i in acc_controller
  - sec_wipe_base in acc_core
  - sec_wipe_wdr_q in acc_core
  - sec_wipe_stack_reset_i in acc_rf_base


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#acc_partial_wipe">acc_partial_wipe</a></td>
  <td><a href="01_feature_report.md#accsecurewipe">ACC.SECUREWIPE</a></td>
</tr>
  </tbody>
</table>

## back_to_back

Run sequences back-to-back

This runs several sequences back-to-back, without resets between
them. This should catch initialisation problems where not all state
is cleared between programs when there's no reset.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#acc_multi">acc_multi</a></td>
  <td><a href="01_feature_report.md#accrandom">ACC.RANDOM</a></td>
</tr>
  </tbody>
</table>

## chip_sw_acc_idle (dragonfly)
Verify the ACC idle signal to clkmgr.

- Write the ACC clk hint to 0 within clkmgr to indicate ACC clk can be gated
  and verify that the ACC clk hint status within clkmgr reads 0 (ACC is disabled).
- Write the ACC clk hint to 1 within clkmgr to indicate ACC clk can be enabled.
  Verify that the ACC clk hint status within clkmgr reads 1 (ACC is enabled).
- Start an ACC operation, write the ACC clk hint to 0 within clkmgr and verify that
  the ACC clk hint status within clkmgr reads 1 (ACC is enabled) before the
  ACC operation is complete.
- After the ACC operation is complete, verify that the ACC clk hint status within
  clkmgr now reads 0 again (ACC is disabled).
- Write the ACC clk hint to 1, read and check the ACC output for correctness.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_acc_randomness-dragonfly">chip_sw_acc_randomness (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_acc_idle (egret)
Verify the ACC idle signal to clkmgr.

- Write the ACC clk hint to 0 within clkmgr to indicate ACC clk can be gated
  and verify that the ACC clk hint status within clkmgr reads 0 (ACC is disabled).
- Write the ACC clk hint to 1 within clkmgr to indicate ACC clk can be enabled.
  Verify that the ACC clk hint status within clkmgr reads 1 (ACC is enabled).
- Start an ACC operation, write the ACC clk hint to 0 within clkmgr and verify that
  the ACC clk hint status within clkmgr reads 1 (ACC is enabled) before the
  ACC operation is complete.
- After the ACC operation is complete, verify that the ACC clk hint status within
  clkmgr now reads 0 again (ACC is disabled).
- Write the ACC clk hint to 1, read and check the ACC output for correctness.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_acc_randomness-egret">chip_sw_acc_randomness (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_acc_isa (dragonfly)
Run every ACC instruction and check final state.

Utilizing the existing ACC smoke test which uses every instruction
(hw/ip/acc/dv/smoke/smoke_test.s). Check the final register state matches the
expected values (in hw/ip/acc/dv/smoke/smoke_expected.txt). Check ACC completed
successfully without errors. This will require a modified version of the smoke test
which dumps register state to memory.

Following the smoke test run a new program just to dump out the register state to
dmem, check the values do not match the previous values from the smoke test run to
ensure the internal state secure wipe has worked.


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
  <td><a href="01_feature_report.md#accisa">ACC.ISA</a><br><a href="01_feature_report.md#accsecurewipe">ACC.SECUREWIPE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_acc_isa (egret)
Run every ACC instruction and check final state.

Utilizing the existing ACC smoke test which uses every instruction
(hw/ip/acc/dv/smoke/smoke_test.s). Check the final register state matches the
expected values (in hw/ip/acc/dv/smoke/smoke_expected.txt). Check ACC completed
successfully without errors. This will require a modified version of the smoke test
which dumps register state to memory.

Following the smoke test run a new program just to dump out the register state to
dmem, check the values do not match the previous values from the smoke test run to
ensure the internal state secure wipe has worked.


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
  <td><a href="01_feature_report.md#accisa">ACC.ISA</a><br><a href="01_feature_report.md#accsecurewipe">ACC.SECUREWIPE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_acc_keymgr (dragonfly)
Check the ACC keymgr connection is functional.

Setup the keymgr and any other blocks required to provide ACC with a valid sideload
key. Run an ACC program to read the key via the KEY_S[0|1]_[H|L] WSRs and write it to
dmem. Sanity check the returned value (e.g. != 0) and check ACC completed successfully
with no errors.


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
  <td><a href="01_feature_report.md#acckeymgr">ACC.KEYMGR</a></td>
</tr>
  </tbody>
</table>

## chip_sw_acc_keymgr (egret)
Check the ACC keymgr connection is functional.

Setup the keymgr and any other blocks required to provide ACC with a valid sideload
key. Run an ACC program to read the key via the KEY_S[0|1]_[H|L] WSRs and write it to
dmem. Sanity check the returned value (e.g. != 0) and check ACC completed successfully
with no errors.


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
  <td><a href="01_feature_report.md#acckeymgr">ACC.KEYMGR</a></td>
</tr>
  </tbody>
</table>

## chip_sw_acc_mem_scramble (dragonfly)
Verify the ACC can receive keys from the OTP to scramble the ACC imem and dmem.

- Initialize the entropy_src subsystem to enable OTP_CTRL fetch random data (already
  done by the test_rom startup code).
- Extract random address offsets from RV_CORE_IBEX_RND_DATA.
- Wait for ACC to be idle.
- Write random address offsets in ACC imem and dmem.
- Read back the written address offsets and compare against expected values. All values
  must match, no integrity errors must be triggered.
- Have ACC fetch new keys and nonces from the OTP_CTRL.
- Wait for ACC to be idle.
- Read back the written address offsets. Most reads should trigger integrity errors. It
  is possible that after re-scrambling the integrity bits are still valid. But this is
  expected to happen rarely. If the number of observed integrity errors is below a
  chosen threshold, the test fails.
- Verify the validity of EDN's output to OTP_CTRL via assertions
  (unique, non-zero data).


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_acc_mem_scramble-dragonfly">chip_sw_acc_mem_scramble (dragonfly)</a></td>
  <td><a href="01_feature_report.md#accmem_scramble">ACC.MEM_SCRAMBLE</a><br><a href="01_feature_report.md#accsecurewipe">ACC.SECUREWIPE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_acc_mem_scramble (egret)
Verify the ACC can receive keys from the OTP to scramble the ACC imem and dmem.

- Initialize the entropy_src subsystem to enable OTP_CTRL fetch random data (already
  done by the test_rom startup code).
- Extract random address offsets from RV_CORE_IBEX_RND_DATA.
- Wait for ACC to be idle.
- Write random address offsets in ACC imem and dmem.
- Read back the written address offsets and compare against expected values. All values
  must match, no integrity errors must be triggered.
- Have ACC fetch new keys and nonces from the OTP_CTRL.
- Wait for ACC to be idle.
- Read back the written address offsets. Most reads should trigger integrity errors. It
  is possible that after re-scrambling the integrity bits are still valid. But this is
  expected to happen rarely. If the number of observed integrity errors is below a
  chosen threshold, the test fails.
- Verify the validity of EDN's output to OTP_CTRL via assertions
  (unique, non-zero data).


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_acc_mem_scramble-egret">chip_sw_acc_mem_scramble (egret)</a></td>
  <td><a href="01_feature_report.md#accmem_scramble">ACC.MEM_SCRAMBLE</a><br><a href="01_feature_report.md#accsecurewipe">ACC.SECUREWIPE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_acc_op (dragonfly)
Verify an ACC operation.

- SW test directs the ACC engine to perform an ECDSA operation.
- SW validates the reception of the acc done interrupt once the operation is complete.
- SW verifies the correctness of the result with the expected value which is
  pre-computed using a reference model.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_acc_ecdsa_op_irq-dragonfly">chip_sw_acc_ecdsa_op_irq (dragonfly)</a><br><a href="03_test_report.md#chip_sw_acc_ecdsa_op_irq_jitter_en-dragonfly">chip_sw_acc_ecdsa_op_irq_jitter_en (dragonfly)</a></td>
  <td><a href="01_feature_report.md#accisa">ACC.ISA</a></td>
</tr>
  </tbody>
</table>

## chip_sw_acc_op (egret)
Verify an ACC operation.

- SW test directs the ACC engine to perform an ECDSA operation.
- SW validates the reception of the acc done interrupt once the operation is complete.
- SW verifies the correctness of the result with the expected value which is
  pre-computed using a reference model.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_acc_ecdsa_op_irq-egret">chip_sw_acc_ecdsa_op_irq (egret)</a><br><a href="03_test_report.md#chip_sw_acc_ecdsa_op_irq_jitter_en-egret">chip_sw_acc_ecdsa_op_irq_jitter_en (egret)</a></td>
  <td><a href="01_feature_report.md#accisa">ACC.ISA</a></td>
</tr>
  </tbody>
</table>

## chip_sw_acc_rnd_entropy (dragonfly)
Verify ACC can fetch RND numbers from the entropy src.

- SW initializes the entropy subsystem to generate randomness.
- SW loads an ACC app that executes instructions to read the RND bits.
- The ACC app ensures that the values when read consecutively do not match, and that no
  value is all 0s or all 1s, as a basic measure to ensure that the entropy subsystem is
  returning some data.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_acc_randomness-dragonfly">chip_sw_acc_randomness (dragonfly)</a></td>
  <td><a href="01_feature_report.md#accrandom">ACC.RANDOM</a></td>
</tr>
  </tbody>
</table>

## chip_sw_acc_rnd_entropy (egret)
Verify ACC can fetch RND numbers from the entropy src.

- SW initializes the entropy subsystem to generate randomness.
- SW loads an ACC app that executes instructions to read the RND bits.
- The ACC app ensures that the values when read consecutively do not match, and that no
  value is all 0s or all 1s, as a basic measure to ensure that the entropy subsystem is
  returning some data.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_acc_randomness-egret">chip_sw_acc_randomness (egret)</a></td>
  <td><a href="01_feature_report.md#accrandom">ACC.RANDOM</a></td>
</tr>
  </tbody>
</table>

## chip_sw_acc_urnd_entropy (dragonfly)
Verify ACC can fetch URND numbers from the entropy src.

- Similar to chip_acc_rnd_entropy, but verifies the URND bits.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_acc_randomness-dragonfly">chip_sw_acc_randomness (dragonfly)</a></td>
  <td><a href="01_feature_report.md#accrandom">ACC.RANDOM</a></td>
</tr>
  </tbody>
</table>

## chip_sw_acc_urnd_entropy (egret)
Verify ACC can fetch URND numbers from the entropy src.

- Similar to chip_acc_rnd_entropy, but verifies the URND bits.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_acc_randomness-egret">chip_sw_acc_randomness (egret)</a></td>
  <td><a href="01_feature_report.md#accrandom">ACC.RANDOM</a></td>
</tr>
  </tbody>
</table>

## illegal_bus_access

Trigger reads and writes to both DMEM and IMEM and expect a fatal alert for
ILLEGAL_BUS_ACCESS. Check that *mem_rdata_bus pins are at 0 when reads are done


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#acc_illegal_mem_acc">acc_illegal_mem_acc</a></td>
  <td><a href="01_feature_report.md#accsecurewipe">ACC.SECUREWIPE</a></td>
</tr>
  </tbody>
</table>

## internal_integrity

Corrupt internal state and expect an alert


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#acc_alu_bignum_mod_err">acc_alu_bignum_mod_err</a><br><a href="03_test_report.md#acc_controller_ispr_rdata_err">acc_controller_ispr_rdata_err</a><br><a href="03_test_report.md#acc_mac_bignum_acc_err">acc_mac_bignum_acc_err</a><br><a href="03_test_report.md#acc_urnd_err">acc_urnd_err</a></td>
  <td><a href="01_feature_report.md#accsecurewipe">ACC.SECUREWIPE</a></td>
</tr>
  </tbody>
</table>

## kmac_error

Create bad transactions for the AppIntf that force ACC into a fatal error.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#acc_kmac_err">acc_kmac_err</a></td>
  <td><a href="01_feature_report.md#accsecurewipe">ACC.SECUREWIPE</a></td>
</tr>
  </tbody>
</table>

## lc_escalation

Trigger the life cycle escalation input.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#acc_escalate">acc_escalate</a></td>
  <td><a href="01_feature_report.md#accsecurewipe">ACC.SECUREWIPE</a></td>
</tr>
  </tbody>
</table>

## mem_integrity

Inject ECC errors into DMEM and IMEM and expect an alert


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#acc_dmem_err">acc_dmem_err</a><br><a href="03_test_report.md#acc_imem_err">acc_imem_err</a></td>
  <td><a href="01_feature_report.md#accmem_scramble">ACC.MEM_SCRAMBLE</a><br><a href="01_feature_report.md#accsecurewipe">ACC.SECUREWIPE</a></td>
</tr>
  </tbody>
</table>

## multi_error

Run instructions that cause multiple SW errors in a cycle

These are directed tests, designed to exhaustively trigger all the
cases where a single instruction execution can fail for more than
one reason. Since each of these instructions causes the operation
to fail, we have to run an ACC operation for each. To do this, we
compile and run all the binaries in a collection of ISS unit tests.
We have coverage points to ensure we see every event we expect.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#acc_multi_err">acc_multi_err</a></td>
  <td><a href="01_feature_report.md#accisa">ACC.ISA</a></td>
</tr>
  </tbody>
</table>

## reset_recovery

Run two binaries, resetting the first at an arbitrary time

Running another binary after a sudden and unexpected reset via the
rst_ni signal will check that all state is properly re-initialized
after a reset. We'd expect X-propagation checks to catch most
problems like this, but an explicit reset sequence also adds the
relevant FSM/toggle coverage.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#acc_reset">acc_reset</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## single_binary

Run a single randomly-chosen binary

This test drives the main bulk of ACC testing. It picks a random
binary from a pre-generated set and runs it, comparing against the
model. We'll run this with a large number of seeds and use
functional coverage to track when verification of the internals of
the core is done.

Sometimes enable the "done" interrupt to check that it and the
error interrupt work correctly.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#acc_single">acc_single</a></td>
  <td><a href="01_feature_report.md#accisa">ACC.ISA</a><br><a href="01_feature_report.md#acckeymgr">ACC.KEYMGR</a><br><a href="01_feature_report.md#accmem_scramble">ACC.MEM_SCRAMBLE</a><br><a href="01_feature_report.md#accrandom">ACC.RANDOM</a></td>
</tr>
  </tbody>
</table>

## smoke

Smoke test, running a single fixed binary

This runs the binary from acc/dv/smoke/smoke_test.s, which is
designed to check most of the implemented instructions. The
unchanging binary should mean this basic test is particularly
appropriate for CI.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#acc_smoke">acc_smoke</a></td>
  <td><a href="01_feature_report.md#accisa">ACC.ISA</a><br><a href="01_feature_report.md#acckeymgr">ACC.KEYMGR</a><br><a href="01_feature_report.md#accmem_scramble">ACC.MEM_SCRAMBLE</a><br><a href="01_feature_report.md#accrandom">ACC.RANDOM</a></td>
</tr>
  </tbody>
</table>

## stress_all

Run assorted sequences back-to-back.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#acc_stress_all">acc_stress_all</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## sw_errs_fatal_chk

Set ctrl.software_errs_fatal.
When set software errors produce fatal errors, rather than recoverable errors.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#acc_sw_errs_fatal_chk">acc_sw_errs_fatal_chk</a></td>
  <td><a href="01_feature_report.md#accsecurewipe">ACC.SECUREWIPE</a></td>
</tr>
  </tbody>
</table>

## zero_state_err_urnd

Trigger the "state is zero" error in URND,
Check that fatal error is asserted.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#acc_zero_state_err_urnd">acc_zero_state_err_urnd</a></td>
  <td><a href="01_feature_report.md#accsecurewipe">ACC.SECUREWIPE</a></td>
</tr>
  </tbody>
</table>
