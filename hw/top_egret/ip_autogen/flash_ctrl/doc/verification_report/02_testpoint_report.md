# flash_ctrl Testpoint Report

## all_partitions

Sanity + both, legal data and info partitions are accessed. In future, support for
multiple info partitions may be added - those will be covered as well.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_rand_ops">flash_ctrl_rand_ops</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## asymmetric_read_path

Create 'fast' and 'slow' read path using scramble enable.
Send flash read request over slow path followed by fast path.
While return data comes from fast path first but they are expected
to be returned in request order.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_rd_ooo">flash_ctrl_rd_ooo</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_flash_creator_seed_wipe_on_rma (egret)
Verify that the creator seed is wiped by the flash ctrl on RMA entry.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_flash_rma_unlocked-egret">chip_sw_flash_rma_unlocked (egret)</a></td>
  <td><a href="01_feature_report.md#flash_ctrlrma">FLASH_CTRL.RMA</a></td>
</tr>
  </tbody>
</table>

## chip_sw_flash_ctrl_clock_freqs (egret)
Verify flash program and erase operations over the ctrl over a range of clock freqs.

- Enable jitter on the clock while performing erase, write and read operations
  to the flash.
- This sets the test for closed source where the flash access timing matters.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_flash_ctrl_clock_freqs-egret">chip_sw_flash_ctrl_clock_freqs (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_flash_ctrl_escalation_reset (egret)
Verify the flash ctrl fatal error does not disturb escalation process
and operation of ibex core.

Trigger an internal fatal fault (host_gnt_err) from flash_ctrl
and let it escalate to reset. Upon alert escalation reset,
the internal status should be clean and should not send out more alerts.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_flash_crash_alert-egret">chip_sw_flash_crash_alert (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_flash_ctrl_ops (egret)
Verify the SW can initiate flash operations via the controller.

Verify that the CPU can read / program and erase the flash mem. Pick an operation on
all data and info partitions. Erase both, bank and page. SW validates the reception of
prog empty, prog level, rd full, rd level and op done interrupts.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_flash_ctrl_ops-egret">chip_sw_flash_ctrl_ops (egret)</a><br><a href="03_test_report.md#chip_sw_flash_ctrl_ops_jitter_en-egret">chip_sw_flash_ctrl_ops_jitter_en (egret)</a></td>
  <td><a href="01_feature_report.md#flash_ctrlopprotocol_ctrl">FLASH_CTRL.OP.PROTOCOL_CTRL</a></td>
</tr>
  </tbody>
</table>

## chip_sw_flash_ctrl_write_clear (egret)
Verify the flash is able to process a second write to clear all bits
when ECC is enabled.

Configure memory protected entries to override the default flash configuration as follows:

1. ECC enabled, scrambling and high endurance disabled.
2. ECC and high endurance enabled, scrambling disabled.

Test the following sequence:

- Set one of the configuration options above.
- Erase target page.
- Write and verify intermediate value, different than all 1s or 0s.
- Write and verify all 0s.

The flash should not throw any errors on the second write.

Note: The hardware does not support this behavior when scrambling is enabled.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_flash_crash_alert-egret">chip_sw_flash_crash_alert (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_flash_host_access (egret)
Verify that the flash memory contents can be read by the CPU.

Nothing extra to do here - most SW based tests fetch code from flash.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_flash_ctrl_access-egret">chip_sw_flash_ctrl_access (egret)</a><br><a href="03_test_report.md#chip_sw_flash_ctrl_access_jitter_en-egret">chip_sw_flash_ctrl_access_jitter_en (egret)</a></td>
  <td><a href="01_feature_report.md#flash_ctrlophost_read">FLASH_CTRL.OP.HOST_READ</a></td>
</tr>
  </tbody>
</table>

## chip_sw_flash_idle_low_power (egret)
Verify flash_idle signaling to pwrmgr.

- Initiate flash program or erase over the controller.
- Program the pwrmgr to go into deep sleep.
- Issue a WFI.
- Ensure that the low power entry does not happen due to the ongoing flash operation.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_flash_ctrl_idle_low_power-egret">chip_sw_flash_ctrl_idle_low_power (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_flash_init (egret)
Verify that flash initialization routine works correctly.

- Initialize the flash ctrl by writing 1 to the INIT register.
- Poll the status register for the initialization to complete.
- Verify that during the init process, the flash ctrl requested keys from OTP. Verify
  with different sets of key values programmed in OTP.
- Verify the flash ctrl can read seeds when lc_seed_hw_rd_en is set, otherwise all 1s.
- Verify that the flash ctrl sent the creator and owner seeds to keymgr. Verify with
  different seed values.

- This test needs to execute as a boot rom image.
- In silicon, this will be covered by manuf_ft_provision_rma_token_and_personalization.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_flash_init-egret">chip_sw_flash_init (egret)</a></td>
  <td><a href="01_feature_report.md#flash_ctrlinfocreator_partition">FLASH_CTRL.INFO.CREATOR_PARTITION</a><br><a href="01_feature_report.md#flash_ctrlinfoowner_partition">FLASH_CTRL.INFO.OWNER_PARTITION</a><br><a href="01_feature_report.md#flash_ctrlinitroot_seeds">FLASH_CTRL.INIT.ROOT_SEEDS</a><br><a href="01_feature_report.md#flash_ctrlinitscrambling_keys">FLASH_CTRL.INIT.SCRAMBLING_KEYS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_flash_keymgr_seeds (egret)
Verify the creator and owner seeds are read on flash init provided lc_hw_seed_rd_en
is set.

X-ref'ed with keymgr test.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_keymgr_key_derivation-egret">chip_sw_keymgr_key_derivation (egret)</a></td>
  <td><a href="01_feature_report.md#flash_ctrlinfocreator_partition">FLASH_CTRL.INFO.CREATOR_PARTITION</a><br><a href="01_feature_report.md#flash_ctrlinfoowner_partition">FLASH_CTRL.INFO.OWNER_PARTITION</a><br><a href="01_feature_report.md#flash_ctrlinitroot_seeds">FLASH_CTRL.INIT.ROOT_SEEDS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_flash_lc_creator_seed_sw_rw_en (egret)
Verify the lc_creator_seed_sw_rw_en signal from LC ctrl.

- Transition from TEST_LOCKED to DEV/PROD to ESCALATION/SCRAP state via OTP and verify
  that this LC signal transitions from 0 to 1 and back to 0. Verify that the SW
  accessibility of the corresponding partition depending on the signal value.

In silicon, we cannot transition the chip or check this signal. The
accessibility of the partition should still be checked in each of
the relevant LC states.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_flash_ctrl_lc_rw_en-egret">chip_sw_flash_ctrl_lc_rw_en (egret)</a></td>
  <td><a href="01_feature_report.md#flash_ctrlinfocreator_partition">FLASH_CTRL.INFO.CREATOR_PARTITION</a></td>
</tr>
  </tbody>
</table>

## chip_sw_flash_lc_escalate_en (egret)
Verify the lc_escalate_en signal from LC ctrl.

- Trigger an LC escalation signal by generating an alert.
- Verify that all flash accesses are disabled when the escalation kicks in.
- Confirm flash accesses are disabled by erroring if the device executes the ISR.
- Use assertion based connectivity check to prove that this signal is connected to the
  flash ctrl.

X-ref with chip_sw_all_escalation_resets.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_all_escalation_resets-egret">chip_sw_all_escalation_resets (egret)</a></td>
  <td><a href="01_feature_report.md#flash_ctrlescalation">FLASH_CTRL.ESCALATION</a></td>
</tr>
  </tbody>
</table>

## chip_sw_flash_lc_iso_part_sw_rd_en (egret)
Verify the lc_iso_part_sw_rd_en signal from LC ctrl.

- Transition from DEV or PROD to ESCALATION/SCRAP state via OTP and verify
  that this LC signal transitions from 0 to 1 and back to 0. Verify that the SW
  accessibility of the corresponding partition depending on the signal value.

In silicon, we cannot transition the chip or check this signal. The
accessibility of the partition should still be checked in each of
the relevant LC states.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_flash_ctrl_lc_rw_en-egret">chip_sw_flash_ctrl_lc_rw_en (egret)</a></td>
  <td><a href="01_feature_report.md#flash_ctrlinfoisolated_partition">FLASH_CTRL.INFO.ISOLATED_PARTITION</a></td>
</tr>
  </tbody>
</table>

## chip_sw_flash_lc_iso_part_sw_wr_en (egret)
Verify the lc_creator_seed_sw_wr_en signal from LC ctrl.

- Transition from TEST_LOCKED to DEV/PROD to ESCALATION/SCRAP state via OTP and verify
  that this LC signal transitions from 0 to 1 and back to 0. Verify that the SW
  accessibility of the corresponding partition depending on the signal value.

In silicon, we cannot transition the chip or check this signal. The
accessibility of the partition should still be checked in each of
the relevant LC states.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_flash_ctrl_lc_rw_en-egret">chip_sw_flash_ctrl_lc_rw_en (egret)</a></td>
  <td><a href="01_feature_report.md#flash_ctrlinfoisolated_partition">FLASH_CTRL.INFO.ISOLATED_PARTITION</a></td>
</tr>
  </tbody>
</table>

## chip_sw_flash_lc_owner_seed_sw_rw_en (egret)
Verify the lc_owner_seed_sw_rw_en signal from LC ctrl.

- Transition from TEST_LOCKED to DEV/PROD to ESCALATION/SCRAP state via OTP and verify
  that this LC signal transitions from 0 to 1 and back to 0. Verify that the SW
  accessibility of the corresponding partition depending on the signal value.

In silicon, we cannot transition the chip or check this signal. The
accessibility of the partition should still be checked in each of
the relevant LC states.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_flash_ctrl_lc_rw_en-egret">chip_sw_flash_ctrl_lc_rw_en (egret)</a></td>
  <td><a href="01_feature_report.md#flash_ctrlinfoowner_partition">FLASH_CTRL.INFO.OWNER_PARTITION</a></td>
</tr>
  </tbody>
</table>

## chip_sw_flash_lc_seed_hw_rd_en (egret)
Verify the lc_seed_hw_rd_en signal from LC ctrl.

- Transition from TEST_LOCKED to DEV/PROD to ESCALATION/SCRAP state via OTP and verify
  that this LC signal transitions from 0 to 1 and back to 0. Verify that the flash ctrl
  does (or does not) read the creator and owner partitions to fetch the seeds for the
  keymgr.
- In silicon, this will be covered by manuf_ft_provision_rma_token_and_personalization.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_flash_ctrl_lc_rw_en-egret">chip_sw_flash_ctrl_lc_rw_en (egret)</a></td>
  <td><a href="01_feature_report.md#flash_ctrlinitroot_seeds">FLASH_CTRL.INIT.ROOT_SEEDS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_flash_memory_protection (egret)
Extend chip_sw_flash_ctrl_access test to over following features.
Perform READ/ PROGRAM/ ERASE operations over protected regions and pages of data and
info partitions.
Use set and reset values of corresponding read, program and erase enable bits.
Test boundary values of regions. Test overlap of regions in which lower
region wins arbitration.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_flash_ctrl_mem_protection-egret">chip_sw_flash_ctrl_mem_protection (egret)</a></td>
  <td><a href="01_feature_report.md#flash_ctrlmem_protection">FLASH_CTRL.MEM_PROTECTION</a></td>
</tr>
  </tbody>
</table>

## chip_sw_flash_prim_tl_access (egret)
Verify that the SW can read / write the prim tlul interface in flash phy.

- The prim tlul interface is a open source placeholder for the closed source CSRs that
  will be implemented in a translation 'shim'.
- Verify that this region can be read / written to by the SW in any LC state.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_prim_tl_access-egret">chip_prim_tl_access (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_flash_rma_unlocked (egret)
Verify the flash memory contents can be accessed after in RMA unlock.

- Provision an RMA_UNLOCK token in OTP.
- Repeat the following a few times:
  - Randomize the otp contents for device id, manufacturing state and RMA_UNLOCK token.
  - Reset the chip.
  - Ensure chip revision, device id and manufacturing state can be read through the LC JTAG.
- Enable RMA mode, and verify that the SW can access the flash after RMA completion.

- RMA entry should be done through the  JTAG interface.

- X-ref'ed with manuf_ft_provision_rma_token_and_personalization from the manufacturing
  testplan.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_flash_rma_unlocked-egret">chip_sw_flash_rma_unlocked (egret)</a></td>
  <td><a href="01_feature_report.md#flash_ctrlrma">FLASH_CTRL.RMA</a></td>
</tr>
  </tbody>
</table>

## chip_sw_flash_scramble (egret)
Verify flash scrambling via the controller.

- Extends the chip_flash_init test.
- Verify flash scrambling with different key values programmed in OTP.
- Verify read of scrambled contents via both, controller and direct host read.

- Program a new scramble key in OTP and reboot - this time we need to backdoor load the
  flash with new test image that is re-scrambled with the new key.
- Need to understand the bootstrapping requirements.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_flash_init-egret">chip_sw_flash_init (egret)</a></td>
  <td><a href="01_feature_report.md#flash_ctrlinitscrambling_keys">FLASH_CTRL.INIT.SCRAMBLING_KEYS</a><br><a href="01_feature_report.md#flash_ctrlopprotocol_ctrl">FLASH_CTRL.OP.PROTOCOL_CTRL</a></td>
</tr>
  </tbody>
</table>

## double_bit_err

Run read / write test and inject double bit error randomly for read transactions --
both direct and controller read.
Check op_status.err and err_code.rd_err are asserted for ctrl read and
tlul response error for host read.
Check fatal alert is asserted for reliability ecc errors (double bits) and
integrity ECC errors.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_derr_detect">flash_ctrl_derr_detect</a><br><a href="03_test_report.md#flash_ctrl_integrity">flash_ctrl_integrity</a><br><a href="03_test_report.md#flash_ctrl_read_word_sweep_derr">flash_ctrl_read_word_sweep_derr</a><br><a href="03_test_report.md#flash_ctrl_ro_derr">flash_ctrl_ro_derr</a><br><a href="03_test_report.md#flash_ctrl_rw_derr">flash_ctrl_rw_derr</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## erase_suspend

Perform erase suspend when erase is ongoing and also when erase is not ongoing.
Check if request is immediately cleared in case when no erase is ongoing.
Check if request is cleared in case when suspend is handled.
Read affected bank in order to verify erase suspension feature.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_erase_suspend">flash_ctrl_erase_suspend</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## error_mp

Perform accesses in order to provoke memory permission errors. Test the Software
interface (Erase, Program, Read). Related covergroup is sw_error_cg.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_error_mp">flash_ctrl_error_mp</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## error_prog_type

Perform accesses in order to provoke the 'program type' error.
Test via the Software interface. Related covergroup is sw_error_cg.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_error_prog_type">flash_ctrl_error_prog_type</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## error_prog_win

Perform accesses in order to provoke the 'program resolution' error.
Test via the Software interface. Related covergroup is sw_error_cg.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_error_prog_win">flash_ctrl_error_prog_win</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## error_read_seed

Create sw read error during hw seed read process.
Check all errors are properly detected.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_hw_read_seed_err">flash_ctrl_hw_read_seed_err</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## fetch_code

Verify the Code Fetch Feature.
Reads for instructions via the Hardware Interface are allowed if a specific value
is written to the EXEC csr.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_fetch_code">flash_ctrl_fetch_code</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## filesystem_support

Enable ECC and disable scrambling for all regions.
Initialize flash with erased state (FlashMemInitSet).
Execute random number of writes without writing the same location twice.
Record all write locations(Minimum resolution of location is 8bytes).
After that, execute write and read back test for random page and check

 - If the locations are in the written record, write data should be all 0 and
   readback data should match with the written data.
 - If the locations are not in the written record, write data should be random and
   readback data should match with the written data.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_fs_sup">flash_ctrl_fs_sup</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## flash_ctrl_connect

Check jtag input / output ports connectivity with lc_nvm_debug_en.
Connections are set only when lc_nvm_debug_en = On.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_connect">flash_ctrl_connect</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## flash_ctrl_disable

Set flash ctrl disable by hw (lc_escalate_en = On) or
sw (flash_ctrl.dis = MuBi4True). And try to access flash ctrl
and check the access attempt to be failed.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_disable">flash_ctrl_disable</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## full_memory_access

Entire memory is accessed by Controller and directly by Host. In addition, Data
partitions can be directly read by Software(Flash controller) and hardware hosts,
while Info partitions can be read only by the Flash controller.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_full_mem_access">flash_ctrl_full_mem_access</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## host_arb

Test arbitration within Flash Physical Controller by reading from both interfaces at
the same time. Perform continuously direct read data from host interface and at the
same time, perform all operations READ/PROGRAM/ERASE from the flash controller is in
progress. Perform parallel operations at addresses of different banks and also on same
bank. Expect that operations are successfully executed.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_phy_arb">flash_ctrl_phy_arb</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## host_controller_arb

Perform operations via the Flash Software Interface, and at the same time invoke a
Hardware RMA operation. This verifies the arbitration within the Flash Protocol
Controller. The arbiter should allow any outstanding Software operations to complete
before the RMA starts. When the RMA completes the RMA FSM remains in its final state
until Reset and software access is blocked.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_host_ctrl_arb">flash_ctrl_host_ctrl_arb</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## host_interleave

At same time, perform two read operations and the same time via host and via
controller. At same time, perform read operation via host and program
operation via controller. Perform mentioned parallel operations at different addresses
and on the same address. Expect that operations are successfully
executed.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_phy_arb">flash_ctrl_phy_arb</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## host_read_direct

Perform back-to-back direct reads via Host in order to test bandwidth of hardware host
interface. In addition, perform stalls to test pipeline structure. Enable scramble to
test pipeline structure.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_host_dir_rd">flash_ctrl_host_dir_rd</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## interrupts

Perform accesses in order to raise all interrupts given in register map.
Check behaviour of Interrupt Enable and Status Registers.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_intr_rd">flash_ctrl_intr_rd</a><br><a href="03_test_report.md#flash_ctrl_intr_rd_slow_flash">flash_ctrl_intr_rd_slow_flash</a><br><a href="03_test_report.md#flash_ctrl_intr_wr">flash_ctrl_intr_wr</a><br><a href="03_test_report.md#flash_ctrl_intr_wr_slow_flash">flash_ctrl_intr_wr_slow_flash</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## invalid_op

Send invalid command in order to check that it does not affect memory content.
Check that recovery alert is triggered.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_invalid_op">flash_ctrl_invalid_op</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## isolation_partition

Verify the isolated information partitions. Accessibility is controlled by Life
Cycle Controller.  Verify Partition can be erase, written and programmed, with
HW control, and wipes after an RMA.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_hw_rma">flash_ctrl_hw_rma</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## memory_protection

Perform READ/ PROGRAM/ ERASE operations over protected regions and pages of data and
info partitions. Use set and reset values of corresponding read, program and erase
enable bits. Test boundary values of regions. Test overlap of regions in which lower
region wins arbitration.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_mp_regions">flash_ctrl_mp_regions</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## mid_op_rst

Flash middle operation reset test. Send reset via power ready signal
in the middle of operation program, read, erase and erase suspend.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_mid_op_rst">flash_ctrl_mid_op_rst</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## program_reset

Reset controller at every state of programming operation and check
if controller doesn't have any residue for the next operation.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_prog_reset">flash_ctrl_prog_reset</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## rd_buff_eviction

Perform following sequences of operations: read/program/read and read/erase/read in
order to test read buffer eviction properly. Read should be executed by both Software
and Host interface. All combinations should be tested. Covergroup for this hazardous
behavior is eviction_cg.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_rd_buff_evict">flash_ctrl_rd_buff_evict</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## rd_buff_eviction_w_ecc

Run read eviction test with multiple memory protection configs.
Each config should enable read but randomize all other fields
including scramble and ecc enable.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_re_evict">flash_ctrl_re_evict</a><br><a href="03_test_report.md#flash_ctrl_rw_evict">flash_ctrl_rw_evict</a><br><a href="03_test_report.md#flash_ctrl_rw_evict_all_en">flash_ctrl_rw_evict_all_en</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## read_write_overflow

Send following error transactions with normal traffic and see
any catastrophic event happens.

  - Program flash size longer than 64 bytes.
    This wil cause prog_win_err.
  - Read flash from controller without setting start op.
  - Issue rd_fifo read more that CONTROL.NUM field value.
    Both will cause d_error in tlul response.

Each transaction is terminated gracefully and should not cause
data path lock up. Also error status should be check per each
transaction.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_oversize_error">flash_ctrl_oversize_error</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## rma_hw_if

Perform RMA entry requests and check afterwards that the  software has no access to
the Flash.  After RMA entry, verify that the content of the flash is wiped out.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_hw_rma">flash_ctrl_hw_rma</a><br><a href="03_test_report.md#flash_ctrl_hw_rma_reset">flash_ctrl_hw_rma_reset</a><br><a href="03_test_report.md#flash_ctrl_lcmgr_intg">flash_ctrl_lcmgr_intg</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## rma_write_process_error

Verify error handling process during the RMA wipe process.
In normal RMA process, inject bit error at the write path
(tb.dut.u_eflash.gen_flash_cores[0].u_core.gen_prog_data.u_prog.pack_data).
This should make debug_state to flash_ctrl_env_pkg::FlashLcIvalid and
fatal error (std_fault_status.lcmgr_err) should be triggered.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_hw_prog_rma_wipe_err">flash_ctrl_hw_prog_rma_wipe_err</a><br><a href="03_test_report.md#flash_ctrl_rma_err">flash_ctrl_rma_err</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## scramble

Enable scrambling, along with randomized scramble keys. Program a fresh chunk of
memory and read back (both, via controller and host) to ensure data integrity. On
program, verify via backdoor scrambling was done on the raw data correctly. When
reading via host, read the same memory via host multiple times back-to-back and ensure
the timing is correct (subsequent reads should be faster). When scrambling is not
enabled, ensure that the raw data is written and read back.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_read_word_sweep">flash_ctrl_read_word_sweep</a><br><a href="03_test_report.md#flash_ctrl_ro">flash_ctrl_ro</a><br><a href="03_test_report.md#flash_ctrl_rw">flash_ctrl_rw</a><br><a href="03_test_report.md#flash_ctrl_wo">flash_ctrl_wo</a><br><a href="03_test_report.md#flash_ctrl_write_word_sweep">flash_ctrl_write_word_sweep</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## secret_partition

Verify the secret information partitions. Accessibility is controlled by the Life Cycle Controller
Seeds are read upon flash controller initialization and sent to the Key Manager, additionally verify
that scramble Keys are Read from the OTP and sent into the Flash Ctrl.  Also verify that programmed
Secret Partitions retain their values through a Reset Cycle.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_hw_sec_otp">flash_ctrl_hw_sec_otp</a><br><a href="03_test_report.md#flash_ctrl_otp_reset">flash_ctrl_otp_reset</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## single_bit_err

Run read only or read write test with randomly injected single bit error.
All single bit error should be corrected and all read data should be
matched with expected written value.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_read_word_sweep_serr">flash_ctrl_read_word_sweep_serr</a><br><a href="03_test_report.md#flash_ctrl_ro_serr">flash_ctrl_ro_serr</a><br><a href="03_test_report.md#flash_ctrl_rw_serr">flash_ctrl_rw_serr</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## singlebit_err_address

Run read / write test and inject a single bit error randomly either direct
or controller read. Once error is injected a certain transaction, wait for the
transaction to be completed and compare ecc_single_err_addr register with the
expected value. Do this for multiple rounds for both banks.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_serr_address">flash_ctrl_serr_address</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## singlebit_err_counter

Run read / write test and inject single bit error randomly for read transactions. -
both direct and controller read - Adjust error injection ratio s.t. counter is not
saturated.
Compare counter values for both bank with expected counter values.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_serr_counter">flash_ctrl_serr_counter</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## smoke

Randomly read, program or erase (page or a bank) a randomized chunk of flash memory.
Only the data partition is accessed. No extra features enabled. Flash memory is
invalidated and the targeted chunk is initialized with random data for reads and all 1s
for writes. Interrupts are not enabled, Completion is ascertained through polling. The
success of each operation is verified via backdoor.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_smoke">flash_ctrl_smoke</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## smoke_hw

Perform host direct read on the single page of Data partition. First Flash memory is
initialized with random values and then it is being read directly by Host interface.
Finally, backdoor read is used for checking read data.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_smoke_hw">flash_ctrl_smoke_hw</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## stress_all


- combine above sequences in one test to run sequentially, except csr sequence
- randomly add reset between each sequence


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_stress_all">flash_ctrl_stress_all</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## sw_op

Perform flash protocol controller read, program and erase on the single page of one
bank within Data partition. Finally perform read on same location in order to test
if previous operation was done successfully.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#flash_ctrl_sw_op">flash_ctrl_sw_op</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>
