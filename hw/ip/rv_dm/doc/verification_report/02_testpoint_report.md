# rv_dm Testpoint Report

## abstractcmd_status

Verify the functionality of abstract command by reading tl_mem_ral.abstractcmd0-9
registers.

- Program jtag_dmi_ral.dmcontrol.haltreq to 1'b1.
- Verify that the 'debug_req_o' is set to 1.
- Acknowledge haltreq by setting tl_mem_ral.halted to 0.
- Send a valid abstract command (command type AccessRegister).
- Verify that the jtag_dmi_ral.abstractcs.busy is set to 1.
- Read tl_mem_ral.abstractcmd0-9 registers to verify that due to executing specific
  abstract command we can read instructions stored in these registers.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_abstractcmd_status">rv_dm_abstractcmd_status</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgabstract_command">RV_DM.DBG.ABSTRACT_COMMAND</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## bad_sba

Verify attempts to make bad SBA accesses results in the error sticky bits getting set.

- Enable debug by setting lc_hw_debug_en to true and activate the dm.
- Build on the previous `sba` test and randomly inject errors in the following
  ways:
  - Inject a response error on the TL response channel (d_error = 1) and verify that
    the sberror bit is set to 2.
  - Inject a randomized SBA access that is not aligned to the size of the transfer and
    verify that the sberror bit is set to 3.
  - Inject a randomized SBA access that is greater that the supported transfer size and
    verify that the sberror bit is set to 4.
  - Inject an integrity error on the TL response channel and verify that the sberror
    bit is set to 7. Verify that an alert is seen. Reset the DUT.
  - Inject a new SBA traffic before the previous one completes - verify that the
    sbbusyerror asserts. This is achieved by setting a large TL response delay (TODO).
  - Have more than one of these types of errors trigger at the same time.

Note: The following error scenarios are not supported by the design:

- pulp-platform/riscv-dbg#128: response timeout (sberror = 1) is not implemented.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_bad_sba_tl_access">rv_dm_bad_sba_tl_access</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgsba">RV_DM.DBG.SBA</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## chip_jtag_csr_rw (dragonfly)

Verify accessibility of all the CSRs in the chip over JTAG.

- Shuffle the list of CSRs first to remove the effect of ordering.
- Write all CSRs via JTAG interface with a random value.
- Shuffle the list of CSRs yet again.
- Read all CSRs back and check their values for correctness while adhering to the CSR's
  access policies.
- Accesses to CSRs external to `rv_dm` go through RV_DM SBA interface into the `xbar`.

For silicon validation, instead of randomised testing to all CSRs, one CSR for each IP is tested.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_jtag_csr_rw-dragonfly">chip_jtag_csr_rw (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## chip_jtag_csr_rw (egret)

Verify accessibility of all the CSRs in the chip over JTAG.

- Shuffle the list of CSRs first to remove the effect of ordering.
- Write all CSRs via JTAG interface with a random value.
- Shuffle the list of CSRs yet again.
- Read all CSRs back and check their values for correctness while adhering to the CSR's
  access policies.
- Accesses to CSRs external to `rv_dm` go through RV_DM SBA interface into the `xbar`.

For silicon validation, instead of randomised testing to all CSRs, one CSR for each IP is tested.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_jtag_csr_rw-egret">chip_jtag_csr_rw (egret)</a></td>
  <td><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## chip_jtag_mem_access (dragonfly)

Verify accessibility of all the memories in the chip over JTAG.

This test will target the following memories in the chip:
  sram_main, sram_ret, acc i|dmem, ROM

- Shuffle the list of memories first to remove the effect of ordering.
- Write a location in a randomly chosen set of addresses within each memory via JTAG
  interface with random values.
- For read-only memories:
   - In simulation preload the memory with random data via backdoor.
   - For silicon choose some known values and addresses in these memories and shuffle
     these to choose one from each for the test.
- Shuffle the list of memories again.
- Read the previously written addresses in the memories back again and check the read
  value for correctness. Pick some random addresses to verify in case of read-only
  memories.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_jtag_mem_access-dragonfly">chip_jtag_mem_access (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgsba">RV_DM.DBG.SBA</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## chip_jtag_mem_access (egret)

Verify accessibility of all the memories in the chip over JTAG.

This test will target the following memories in the chip:
  sram_main, sram_ret, acc i|dmem, ROM

- Shuffle the list of memories first to remove the effect of ordering.
- Write a location in a randomly chosen set of addresses within each memory via JTAG
  interface with random values.
- For read-only memories:
   - In simulation preload the memory with random data via backdoor.
   - For silicon choose some known values and addresses in these memories and shuffle
     these to choose one from each for the test.
- Shuffle the list of memories again.
- Read the previously written addresses in the memories back again and check the read
  value for correctness. Pick some random addresses to verify in case of read-only
  memories.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_jtag_mem_access-egret">chip_jtag_mem_access (egret)</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgsba">RV_DM.DBG.SBA</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## chip_rv_dm_access_after_wakeup (dragonfly)
Verify RV_DM works after wakes up from sleep.

- Put the chip into sleep mode and then wake up (both deep sleep and normal sleep).
- If waking up from normal sleep, an activation should not be required for RV_DM CSR
  accesses to work.
- If waking up from deep sleep, an activation is required for RV_DM CSR accesses to work.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rv_dm_access_after_wakeup-dragonfly">chip_sw_rv_dm_access_after_wakeup (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## chip_rv_dm_access_after_wakeup (egret)
Verify RV_DM works after wakes up from sleep.

- Put the chip into sleep mode and then wake up (both deep sleep and normal sleep).
- If waking up from normal sleep, an activation should not be required for RV_DM CSR
  accesses to work.
- If waking up from deep sleep, an activation is required for RV_DM CSR accesses to work.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rv_dm_access_after_wakeup-egret">chip_sw_rv_dm_access_after_wakeup (egret)</a></td>
  <td><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## chip_rv_dm_control_status (egret)
Verify the functionality of dmcontrol/dmstatus

- Write 0 to hartsel (select Ibex)
- Check dmstatus indicates havereset for Ibex (power-on reset)
- Write 1 to ackhavereset
- Check dmstatus does not indicate havereset for Ibex
- Write all 1s to hartsel
- Read back hartsel and check value is 0 (hartsel is WARL)
- Halt Ibex with a write to haltreq
- Check dmstatus reflects halted status
- Resume Ibex for a write to resumereq
- Check dmstatus reflects halted status

NDM reset behaviour covered by chip_rv_dm_ndm_reset_req


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
  <td><a href="01_feature_report.md#rv_dmdbgdmcontrol_reg">RV_DM.DBG.DMCONTROL_REG</a><br><a href="01_feature_report.md#rv_dmdbgdmstatus_reg">RV_DM.DBG.DMSTATUS_REG</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## chip_rv_dm_dtm (egret)
Verify basic DTM functionality

- Select Ibex CPU with write to hartsel
- Read hartinfo and check value is as expected
- Write random values to data0 and data1
- Read back the values from data0 and data1 and check it matches
  the written value


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
  <td><a href="01_feature_report.md#rv_dmdbgdata_regs">RV_DM.DBG.DATA_REGS</a><br><a href="01_feature_report.md#rv_dmdbghartinfo_reg">RV_DM.DBG.HARTINFO_REG</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## chip_rv_dm_jtag (egret)
Verify basic JTAG functionality

- Read IDCODE, check it is the expected value
- Attempt to write IDCODE, check the expected value remains
  after a read
- Check functionality of BYPASS
- Read DTMCS ensure value is as expected


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
  <td><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## chip_rv_dm_lc_disabled (dragonfly)
Verify that the debug capabilities are disabled in certain life cycle stages.

## Procedure

- Put life cycle in a random life cycle state.
- Verify that the rv_dm bus device is inaccessible from the CPU as well as external JTAG
  if the life cycle state is not in TEST_UNLOCKED*, DEV or RMA.
- The bus access check is performed by randomly reading or writing a CSR inside the
  RV_DM and checking whether the TL-UL bus errors out.
- The JTAG access check is performed by writing and then reading a register that is
  accessible via the TAP/DMI inside the RV_DM. If the JTAG wires are gated, it is
  expected that the RV_DM returns all-zero instead of the written value.
- X-ref'ed with `chip_tap_strap_sampling`

### Late debug enable

- In DEV life cycle stage test the following scenarios:
  - rv_dm is accessible via CPU and JTAG when OTP DIS_RV_DM_LATE_DEBUG is set to true.
  - rv_dm is accessible via CPU only when OTP DIS_RV_DM_LATE_DEBUG is set to false and
    the late_debug_enable register is set to false.
  - rv_dm is accessible via CPU and JTAG when OTP DIS_RV_DM_LATE_DEBUG is set to false
    and the late_debug_enable register is set to true.

## Silicon validation

- For post silicon validation the test cannot change lifecycle mode. Instead it must
  discover the lifecycle of the device it is being run against and act appropriately
  (noting in particular it will not be able to execute code on Ibex in some life cycle
  states).


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_rv_dm_lc_disabled-dragonfly">chip_rv_dm_lc_disabled (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## chip_rv_dm_lc_disabled (egret)
Verify that the debug capabilities are disabled in certain life cycle stages.

## Procedure

- Put life cycle in a random life cycle state.
- Verify that the rv_dm bus device is inaccessible from the CPU as well as external JTAG
  if the life cycle state is not in TEST_UNLOCKED*, DEV or RMA.
- The bus access check is performed by randomly reading or writing a CSR inside the
  RV_DM and checking whether the TL-UL bus errors out.
- The JTAG access check is performed by writing and then reading a register that is
  accessible via the TAP/DMI inside the RV_DM. If the JTAG wires are gated, it is
  expected that the RV_DM returns all-zero instead of the written value.
- X-ref'ed with `chip_tap_strap_sampling`

### Late debug enable

- In DEV life cycle stage test the following scenarios:
  - rv_dm is accessible via CPU and JTAG when OTP DIS_RV_DM_LATE_DEBUG is set to true.
  - rv_dm is accessible via CPU only when OTP DIS_RV_DM_LATE_DEBUG is set to false and
    the late_debug_enable register is set to false.
  - rv_dm is accessible via CPU and JTAG when OTP DIS_RV_DM_LATE_DEBUG is set to false
    and the late_debug_enable register is set to true.

## Silicon validation

- For post silicon validation the test cannot change lifecycle mode. Instead it must
  discover the lifecycle of the device it is being run against and act appropriately
  (noting in particular it will not be able to execute code on Ibex in some life cycle
  states).


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_rv_dm_lc_disabled-egret">chip_rv_dm_lc_disabled (egret)</a></td>
  <td><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## chip_rv_dm_ndm_reset_req (dragonfly)
Verify non-debug reset request initiated from RV_DM when the chip is awake.

- Program some CSRs / mem that are under life cycle reset tree and system reset tree.
- Configure RV_DM to send NDM reset request to reset system reset tree.
- While NDM reset is ongoing, ensure the RV_DM debug module registers can still be
  accessed.
- Read the programmed CSRs / mem to ensure that everything under system reset tree is
  reset to the original values, while values under life cycle reset will be preserved.
- Read CSRs / mem in the debug domain to ensure that the values survive the reset.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_rv_dm_ndm_reset_req-dragonfly">chip_rv_dm_ndm_reset_req (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgndm_reset">RV_DM.DBG.NDM_RESET</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## chip_rv_dm_ndm_reset_req (egret)
Verify non-debug reset request initiated from RV_DM when the chip is awake.

- Program some CSRs / mem that are under life cycle reset tree and system reset tree.
- Configure RV_DM to send NDM reset request to reset system reset tree.
- While NDM reset is ongoing, ensure the RV_DM debug module registers can still be
  accessed.
- Read the programmed CSRs / mem to ensure that everything under system reset tree is
  reset to the original values, while values under life cycle reset will be preserved.
- Read CSRs / mem in the debug domain to ensure that the values survive the reset.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_rv_dm_ndm_reset_req-egret">chip_rv_dm_ndm_reset_req (egret)</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgndm_reset">RV_DM.DBG.NDM_RESET</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## chip_rv_dm_perform_debug (dragonfly)

Verify that ROM can be debugged in appropriate life cycle states.

- X-ref'ed with rom_e2e_jtag_debug from rom testplan.

`CREATOR_SW_CFG_ROM_EXEC_EN` should be set to `0`.

- Verify that ROM can be debugged in TEST, DEV, and RMA life cycle states.
  - Test debugging with commands to GDB connected via OpenOCD and JTAG (or the
    SystemVerilog based JTAG debugger model in case of DV simulations).
  - Read back GDB responses to check they match expected behaviour
  - Connect a debugger and verify that ROM halts very early in `rom_start.S`.
  - Trial the following activities within GDB, ensuring the correct
    behaviour is seen:
    - Halting execution and resetting
    - Setting, hitting and deleting breakpoints using all available hardware breakpoints
    - Single stepping
      - In particular single step over `wfi`
    - Reading and writing all registers
    - Reading all CSRs and writing some (write set TBD)
    - Reading and writing memory (both SRAM and device)
    - Setting the PC to jump to some location
    - Executing code from GDB (using the call command)
  - Verify that ROM fails to boot with `BFV:0142500d`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rom_e2e_jtag_debug_dev-dragonfly">rom_e2e_jtag_debug_dev (dragonfly)</a><br><a href="03_test_report.md#rom_e2e_jtag_debug_rma-dragonfly">rom_e2e_jtag_debug_rma (dragonfly)</a><br><a href="03_test_report.md#rom_e2e_jtag_debug_test_unlocked0-dragonfly">rom_e2e_jtag_debug_test_unlocked0 (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rv_dmdbggdb">RV_DM.DBG.GDB</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## chip_rv_dm_perform_debug (egret)

Verify that ROM can be debugged in appropriate life cycle states.

- X-ref'ed with rom_e2e_jtag_debug from rom testplan.

`CREATOR_SW_CFG_ROM_EXEC_EN` should be set to `0`.

- Verify that ROM can be debugged in TEST, DEV, and RMA life cycle states.
  - Test debugging with commands to GDB connected via OpenOCD and JTAG (or the
    SystemVerilog based JTAG debugger model in case of DV simulations).
  - Read back GDB responses to check they match expected behaviour
  - Connect a debugger and verify that ROM halts very early in `rom_start.S`.
  - Trial the following activities within GDB, ensuring the correct
    behaviour is seen:
    - Halting execution and resetting
    - Setting, hitting and deleting breakpoints using all available hardware breakpoints
    - Single stepping
      - In particular single step over `wfi`
    - Reading and writing all registers
    - Reading all CSRs and writing some (write set TBD)
    - Reading and writing memory (both SRAM and device)
    - Setting the PC to jump to some location
    - Executing code from GDB (using the call command)
  - Verify that ROM fails to boot with `BFV:0142500d`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rom_e2e_jtag_debug_dev-egret">rom_e2e_jtag_debug_dev (egret)</a><br><a href="03_test_report.md#rom_e2e_jtag_debug_rma-egret">rom_e2e_jtag_debug_rma (egret)</a><br><a href="03_test_report.md#rom_e2e_jtag_debug_test_unlocked0-egret">rom_e2e_jtag_debug_test_unlocked0 (egret)</a></td>
  <td><a href="01_feature_report.md#rv_dmdbggdb">RV_DM.DBG.GDB</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rv_dm_access_after_hw_reset (dragonfly)
Verify RV_DM works after a watchdog or escalated reset.

- Access some RV_DM CSRs both before and after resets.
- An activation would be required, as the tap strap would also be sampled again.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rv_dm_access_after_escalation_reset-dragonfly">chip_sw_rv_dm_access_after_escalation_reset (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rv_dm_access_after_hw_reset (egret)
Verify RV_DM works after a watchdog or escalated reset.

- Access some RV_DM CSRs both before and after resets.
- An activation would be required, as the tap strap would also be sampled again.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rv_dm_access_after_escalation_reset-egret">chip_sw_rv_dm_access_after_escalation_reset (egret)</a></td>
  <td><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rv_dm_jtag_tap_sel (egret)
Verify ability to select all available TAPs.

- Put life cycle on DEV, TEST_UNLOCKED or RMA state, so that TAPs can be selected between life cycle
  RV_DM and DFT.
- Verify the TAP is selected correctly.
- X-ref'ed with chip_sw_tap_strap_sampling.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_tap_straps_rma-egret">chip_tap_straps_rma (egret)</a></td>
  <td><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rv_dm_ndm_reset_req_when_cpu_halted (dragonfly)
Verify non-debug reset request initiated from RV_DM when the CPU  is in halted state.

- Initialize the DUT in a HW-debug enabled life cycle state.
- Activate the RISCV debug module.
- Run some SW test on the CPU.
- Initiate a CPU halt request via JTAG.
- Wait for the CPU to be in halted state via JTAG by polling dmstatus.anyhalted.
- Deassert the CPU haltreq and verify that we are still in halted state.
- (Optional) Using the abstract command, read the dcsr register to verify the cause
  reflects the debug halt request.
- Issue an NDM reset request. All non-debug parts of the chip should reset. Read the
  dmstatus.anyhalted / dvstatus.allhalted and verify that they are cleared.
- Verify that the debug logic is fully accessible during this time, while the NDM reset
  is being processed and the chip is rebooted, by continuously accessing the DMI
  register space in `rv_dm` over JTAG.
- De-assert the NDM reset request and wait for the CPU to reboot and finish the post-NDM
  reset phase of the test.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rv_dm_ndm_reset_req_when_cpu_halted-dragonfly">chip_sw_rv_dm_ndm_reset_req_when_cpu_halted (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgabstract_command">RV_DM.DBG.ABSTRACT_COMMAND</a><br><a href="01_feature_report.md#rv_dmdbgdmstatus_reg">RV_DM.DBG.DMSTATUS_REG</a><br><a href="01_feature_report.md#rv_dmdbgndm_reset">RV_DM.DBG.NDM_RESET</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rv_dm_ndm_reset_req_when_cpu_halted (egret)
Verify non-debug reset request initiated from RV_DM when the CPU  is in halted state.

- Initialize the DUT in a HW-debug enabled life cycle state.
- Activate the RISCV debug module.
- Run some SW test on the CPU.
- Initiate a CPU halt request via JTAG.
- Wait for the CPU to be in halted state via JTAG by polling dmstatus.anyhalted.
- Deassert the CPU haltreq and verify that we are still in halted state.
- (Optional) Using the abstract command, read the dcsr register to verify the cause
  reflects the debug halt request.
- Issue an NDM reset request. All non-debug parts of the chip should reset. Read the
  dmstatus.anyhalted / dvstatus.allhalted and verify that they are cleared.
- Verify that the debug logic is fully accessible during this time, while the NDM reset
  is being processed and the chip is rebooted, by continuously accessing the DMI
  register space in `rv_dm` over JTAG.
- De-assert the NDM reset request and wait for the CPU to reboot and finish the post-NDM
  reset phase of the test.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rv_dm_ndm_reset_req_when_cpu_halted-egret">chip_sw_rv_dm_ndm_reset_req_when_cpu_halted (egret)</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgndm_reset">RV_DM.DBG.NDM_RESET</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## cmderr_exception

Verify that if an exception occurs when executing a command then cmderr is set to 3.

- Start an abstract command.
- While it's running, write to the exception register over TL.
- Check that the cmderr field of abstractcs register is now 3.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_cmderr_exception">rv_dm_cmderr_exception</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgabstract_command">RV_DM.DBG.ABSTRACT_COMMAND</a><br><a href="01_feature_report.md#rv_dmdbgdmcontrol_reg">RV_DM.DBG.DMCONTROL_REG</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## cmderr_halt_resume

Verify that attempt to generate command error result in cmderr field of abstractcs
register are set.

- Try to execute abstract command when hart is not in halt/resume state.
- Assert unavailable signal through core interface.
- The abstract command could not be execute.
- Verify that the cmderr field of abstractcs register is set to 4.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_cmderr_halt_resume">rv_dm_cmderr_halt_resume</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgabstract_command">RV_DM.DBG.ABSTRACT_COMMAND</a><br><a href="01_feature_report.md#rv_dmdbghartinfo_reg">RV_DM.DBG.HARTINFO_REG</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## dataaddr_rw_access

Verify the read write access of the data registers through the memory mapped DataAddr register.

- Write random data to the shadowed data registers via the corresponding DataAddr registers.
- Read back the written data and verify that it matches the expected values.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_dataaddr_rw_access">rv_dm_dataaddr_rw_access</a></td>
  <td><a href="01_feature_report.md#rv_dmdbghartinfo_reg">RV_DM.DBG.HARTINFO_REG</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## halt_resume

Verify debug module halt/going/resume behavior.

- Request a halt over DMI, then send an abstract command.
- Check that the debug module reports itself to be busy.
- Check that the debug module's internal state machine is in the Go state.
- As the hart, respond to the message from the debug module to say that it has started handling it.
- Check the debug module still reports itself to be busy.
- Check that WHERETO points at the expected address (which contains the start of the abstract command)
- As the hart, tell the debug module that we have halted.
- Check the debug module no longer reports itself to be busy.
- Tell the debug module to resume again, by clearing the halt request and sending a resume request.
- Check the debug module now reports itself busy again (since it should be asking the hart to resume)
- Check flags to make sure the debug module is in the Resume state.
- As the hart, acknowledge the resume request.
- Check the debug module no longer reports itself to be busy.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_halt_resume_whereto">rv_dm_halt_resume_whereto</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgabstract_command">RV_DM.DBG.ABSTRACT_COMMAND</a><br><a href="01_feature_report.md#rv_dmdbghartinfo_reg">RV_DM.DBG.HARTINFO_REG</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## hart_unavail

Verify that the debugger can read the status of unavailable hart

- Set lc_hw_debug_en to true value and activate the dm.
- Randomly assert and de-assert the `unavailable` input (indicates the CPU is under
  reset). This ideally happens when ndmreset is issued by the debugger.
- Periodically issue reads to dmstatus register to verify allunavail matches the
  `unavailable` input value


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_hart_unavail">rv_dm_hart_unavail</a></td>
  <td><a href="01_feature_report.md#rv_dmdbghartinfo_reg">RV_DM.DBG.HARTINFO_REG</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## hartsel_warl

Check the WARL behaviour of the hartsel field in dmcontrol

- Write '1 to hartsel and then read dmcontrol back again.
- Check resulting value of hartsel equals the maximum hart index.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_hartsel_warl">rv_dm_hartsel_warl</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgdmcontrol_reg">RV_DM.DBG.DMCONTROL_REG</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## idcode

Verify that the JTAG IDCODE reads the correct value.

- Set a different JTAG ID code an rv_dm design parameter.
- Read the IDCODE register in JTAG DTM register space, via JTAG.
- Verify it reads back what was set.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_smoke">rv_dm_smoke</a></td>
  <td><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## jtag_dmi_cmderr_busy

Generate the "busy" command error in abstractcs.

- Start an abstract command executing (but don't allow it to stop)

- Write to one of command, abstractcs, abstractauto or access (read or write) the data
  or progbuf register.

- Read the abstractcs register and check that cmderr is now set to 1 (the encoding of
  "busy")


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_cmderr_busy">rv_dm_cmderr_busy</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgabstract_command">RV_DM.DBG.ABSTRACT_COMMAND</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## jtag_dmi_cmderr_not_supported

Generate the "not supported" command error in abstractcs

This command error is generated when trying to run an abstract command that is not
supported.

- Write a command to the command register where cmdtype is definitely not supported.
- Check that the cmderr field of abstractcs register is set to 2.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_cmderr_not_supported">rv_dm_cmderr_not_supported</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgabstract_command">RV_DM.DBG.ABSTRACT_COMMAND</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## jtag_dmi_csr_aliasing

Verify no aliasing within the JTAG DMI CSR address space.

See hw/dv/tools/dvsim/testplans/csr_testplan.hjson for more description, This follows
the same approach, but applies to the JTAG DMI regisers.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_jtag_dmi_csr_aliasing">rv_dm_jtag_dmi_csr_aliasing</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgabstract_command">RV_DM.DBG.ABSTRACT_COMMAND</a><br><a href="01_feature_report.md#rv_dmdbgdata_regs">RV_DM.DBG.DATA_REGS</a><br><a href="01_feature_report.md#rv_dmdbgdmcontrol_reg">RV_DM.DBG.DMCONTROL_REG</a><br><a href="01_feature_report.md#rv_dmdbgdmstatus_reg">RV_DM.DBG.DMSTATUS_REG</a><br><a href="01_feature_report.md#rv_dmdbghaltsum0_reg">RV_DM.DBG.HALTSUM0_REG</a><br><a href="01_feature_report.md#rv_dmdbghartinfo_reg">RV_DM.DBG.HARTINFO_REG</a><br><a href="01_feature_report.md#rv_dmdbgprogbuf">RV_DM.DBG.PROGBUF</a><br><a href="01_feature_report.md#rv_dmdbgsba">RV_DM.DBG.SBA</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## jtag_dmi_csr_bit_bash

Verify no aliasing within individual bits of JTAG DMI CSR.

See hw/dv/tools/dvsim/testplans/csr_testplan.hjson for more description, This follows
the same approach, but applies to the JTAG DMI regisers.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_jtag_dmi_csr_bit_bash">rv_dm_jtag_dmi_csr_bit_bash</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgabstract_command">RV_DM.DBG.ABSTRACT_COMMAND</a><br><a href="01_feature_report.md#rv_dmdbgdata_regs">RV_DM.DBG.DATA_REGS</a><br><a href="01_feature_report.md#rv_dmdbgdmcontrol_reg">RV_DM.DBG.DMCONTROL_REG</a><br><a href="01_feature_report.md#rv_dmdbgdmstatus_reg">RV_DM.DBG.DMSTATUS_REG</a><br><a href="01_feature_report.md#rv_dmdbghaltsum0_reg">RV_DM.DBG.HALTSUM0_REG</a><br><a href="01_feature_report.md#rv_dmdbghartinfo_reg">RV_DM.DBG.HARTINFO_REG</a><br><a href="01_feature_report.md#rv_dmdbgprogbuf">RV_DM.DBG.PROGBUF</a><br><a href="01_feature_report.md#rv_dmdbgsba">RV_DM.DBG.SBA</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## jtag_dmi_csr_hw_reset

Verify the reset values of JTAG DMI CSRs as indicated in the RAL specification.

See hw/dv/tools/dvsim/testplans/csr_testplan.hjson for more description, This follows
the same approach, but applies to the JTAG DMI regisers.

In these set of tests, the lc_hw_debug_en is set to true, scanmode & scan_rst_n inputs
to false.

Also, the dmcontrol[dmactive] field is set to 1 at the start, to ensure CSR accesses to
all other registers go through.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_jtag_dmi_csr_hw_reset">rv_dm_jtag_dmi_csr_hw_reset</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgabstract_command">RV_DM.DBG.ABSTRACT_COMMAND</a><br><a href="01_feature_report.md#rv_dmdbgdata_regs">RV_DM.DBG.DATA_REGS</a><br><a href="01_feature_report.md#rv_dmdbgdmcontrol_reg">RV_DM.DBG.DMCONTROL_REG</a><br><a href="01_feature_report.md#rv_dmdbgdmstatus_reg">RV_DM.DBG.DMSTATUS_REG</a><br><a href="01_feature_report.md#rv_dmdbghaltsum0_reg">RV_DM.DBG.HALTSUM0_REG</a><br><a href="01_feature_report.md#rv_dmdbghartinfo_reg">RV_DM.DBG.HARTINFO_REG</a><br><a href="01_feature_report.md#rv_dmdbgprogbuf">RV_DM.DBG.PROGBUF</a><br><a href="01_feature_report.md#rv_dmdbgsba">RV_DM.DBG.SBA</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## jtag_dmi_csr_rw

Verify accessibility of JTAG DMI CSRs as indicated in the RAL specification.

See hw/dv/tools/dvsim/testplans/csr_testplan.hjson for more description, This follows
the same approach, but applies to the JTAG DMI regisers.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_jtag_dmi_csr_rw">rv_dm_jtag_dmi_csr_rw</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgabstract_command">RV_DM.DBG.ABSTRACT_COMMAND</a><br><a href="01_feature_report.md#rv_dmdbgdata_regs">RV_DM.DBG.DATA_REGS</a><br><a href="01_feature_report.md#rv_dmdbgdmcontrol_reg">RV_DM.DBG.DMCONTROL_REG</a><br><a href="01_feature_report.md#rv_dmdbgdmstatus_reg">RV_DM.DBG.DMSTATUS_REG</a><br><a href="01_feature_report.md#rv_dmdbghaltsum0_reg">RV_DM.DBG.HALTSUM0_REG</a><br><a href="01_feature_report.md#rv_dmdbghartinfo_reg">RV_DM.DBG.HARTINFO_REG</a><br><a href="01_feature_report.md#rv_dmdbgprogbuf">RV_DM.DBG.PROGBUF</a><br><a href="01_feature_report.md#rv_dmdbgsba">RV_DM.DBG.SBA</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## jtag_dmi_debug_disabled

Verify that the JTAG DMI register space cannot be accessed if pinmux_hw_debug_en is a non
strict true value.

- Set pinmux_hw_debug_en to true and activate the dm.
- Write a known value to a randomly picked DMI CSR.
- Set pinmux_hw_debug_en to non-true value.
- Write a different value to the same DMI CSR.
- Attempt to read that DMI CSR - it should read all 0s.
- Note that the above steps are rendered moot because the JTAG DTM itself will not
  receive any incoming JTAG transactions.
- Set pinmux_hw_debug_en to true and again read the DMI CSR - it should reflect the
  originally written value.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_jtag_dmi_debug_disabled">rv_dm_jtag_dmi_debug_disabled</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgabstract_command">RV_DM.DBG.ABSTRACT_COMMAND</a><br><a href="01_feature_report.md#rv_dmdbgdata_regs">RV_DM.DBG.DATA_REGS</a><br><a href="01_feature_report.md#rv_dmdbgdmcontrol_reg">RV_DM.DBG.DMCONTROL_REG</a><br><a href="01_feature_report.md#rv_dmdbgdmstatus_reg">RV_DM.DBG.DMSTATUS_REG</a><br><a href="01_feature_report.md#rv_dmdbghaltsum0_reg">RV_DM.DBG.HALTSUM0_REG</a><br><a href="01_feature_report.md#rv_dmdbghartinfo_reg">RV_DM.DBG.HARTINFO_REG</a><br><a href="01_feature_report.md#rv_dmdbgprogbuf">RV_DM.DBG.PROGBUF</a><br><a href="01_feature_report.md#rv_dmdbgsba">RV_DM.DBG.SBA</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## jtag_dmi_dm_inactive


Verify that DMI writes to data other than dmcontrol.dmactive are ignored when dmactive
is false. All of these registers should return their reset values on reads.

- Write 0 to DMCONTROL.DMACTIVE to put the debug module into its reset state.
- Perform random DMI writes, constrained only by requiring that they don't write 1 to
  DMCONTROL.DMACTIVE.
- Write 1 to DMCONTROL.DMACTIVE to leave the reset state.
- Read DMI registers back and check they have their POR values.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_jtag_dmi_dm_inactive">rv_dm_jtag_dmi_dm_inactive</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgabstract_command">RV_DM.DBG.ABSTRACT_COMMAND</a><br><a href="01_feature_report.md#rv_dmdbgdata_regs">RV_DM.DBG.DATA_REGS</a><br><a href="01_feature_report.md#rv_dmdbgdmcontrol_reg">RV_DM.DBG.DMCONTROL_REG</a><br><a href="01_feature_report.md#rv_dmdbgdmstatus_reg">RV_DM.DBG.DMSTATUS_REG</a><br><a href="01_feature_report.md#rv_dmdbghaltsum0_reg">RV_DM.DBG.HALTSUM0_REG</a><br><a href="01_feature_report.md#rv_dmdbghartinfo_reg">RV_DM.DBG.HARTINFO_REG</a><br><a href="01_feature_report.md#rv_dmdbgprogbuf">RV_DM.DBG.PROGBUF</a><br><a href="01_feature_report.md#rv_dmdbgsba">RV_DM.DBG.SBA</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## jtag_dmi_failed_op

Verify that a failed DMI op is reflected properly in dtmcs register.

- Issue a random legal DMI write to a chosen DMI register.
- Before that access completes, issue another random legal DMI access.
- Read the dtmcs[dmistat] register to verify busy error.
- Clear it by writing to dtmcs[dmireset] register.
- Poll the DMI access for completion and verify that the first write completed
  successfully by doing a read-check.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_dmi_failed_op">rv_dm_dmi_failed_op</a></td>
  <td><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## jtag_dtm_csr_aliasing

Verify no aliasing within the JTAG DTM CSR address space.

See hw/dv/tools/dvsim/testplans/csr_testplan.hjson for more description, This follows
the same approach, but applies to the JTAG DTM regisers.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_jtag_dtm_csr_aliasing">rv_dm_jtag_dtm_csr_aliasing</a></td>
  <td><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## jtag_dtm_csr_bit_bash

Verify no aliasing within individual bits of JTAG DTM CSR.

See hw/dv/tools/dvsim/testplans/csr_testplan.hjson for more description, This follows
the same approach, but applies to the JTAG DTM regisers.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_jtag_dtm_csr_bit_bash">rv_dm_jtag_dtm_csr_bit_bash</a></td>
  <td><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## jtag_dtm_csr_hw_reset

Verify the reset values of JTAG DTM CSRs as indicated in the RAL specification.

See hw/dv/tools/dvsim/testplans/csr_testplan.hjson for more description, This follows
the same approach, but applies to the JTAG DTM regisers.

In these set of tests, the lc_hw_debug_en is set to true, scanmode & scan_rst_n inputs
to false.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_jtag_dtm_csr_hw_reset">rv_dm_jtag_dtm_csr_hw_reset</a></td>
  <td><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## jtag_dtm_csr_rw

Verify accessibility of JTAG DTM CSRs as indicated in the RAL specification.

See hw/dv/tools/dvsim/testplans/csr_testplan.hjson for more description, This follows
the same approach, but applies to the JTAG DTM regisers.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_jtag_dtm_csr_rw">rv_dm_jtag_dtm_csr_rw</a></td>
  <td><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## jtag_dtm_hard_reset

Verify that the debugger can cancel an on-going DMI transaction with a hard reset.

- Perform DMI register read and check the data value.
- Write 1 to dtmcs[dmihardreset] bit.
- Perform DMI register read and check the data value to make sure the reset doesn't
  create any harmful event.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_jtag_dtm_hard_reset">rv_dm_jtag_dtm_hard_reset</a></td>
  <td><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## jtag_dtm_idle_hint

Verify that the JTAG debugger does not need to stay any longer than the advertized idle
time indicated in dtmcs register.

- Read the dtmcs[idle] value and configure the JTAG DMI register adapter to insert that
  many delay between transactions.
- Issue random legal DMI accesses back to back and ensure that all of them complete
  successfully, without dmistat reflecting an error.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_jtag_dtm_idle_hint">rv_dm_jtag_dtm_idle_hint</a></td>
  <td><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## mem_tl_access_halted

Verify whether the selected hart has been halted or not.

- Set the haltreq bit of dmcontrol register.
- Write into memory mapped register called HALTED(0x100) through tl-device(mem_tl_if) interface.
- Verify that the anyhalted and allhalted bits of the dmstatus register are set.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_mem_tl_access_halted">rv_dm_mem_tl_access_halted</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgdmcontrol_reg">RV_DM.DBG.DMCONTROL_REG</a><br><a href="01_feature_report.md#rv_dmdbghartinfo_reg">RV_DM.DBG.HARTINFO_REG</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## mem_tl_access_resuming

 Verify whether the selected hart has been resumed or not.

- Write into memory mapped register called RESUMING(0x110) through tl-device interface.
- Verify that the anyresumeack and allresumeack bits of the dmstatus register are set.
- After that, set the resumereq bit of dmcontrol register.
- Verify that the anyresumeack and allresumeack bits of the dmstatus register are cleared.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_mem_tl_access_resuming">rv_dm_mem_tl_access_resuming</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgdmcontrol_reg">RV_DM.DBG.DMCONTROL_REG</a><br><a href="01_feature_report.md#rv_dmdbghartinfo_reg">RV_DM.DBG.HARTINFO_REG</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## ndmreset_req

Verify that the debugger can issue a non-debug reset to the rest of the system.

- Set lc_hw_debug_en / pinmux_hw_debug_en to true value and activate the dm.
- Pick a random set of write/readable CSRs in the debug RALs (JTAG DMI and debug
  memory). Write known values to them.
- Write the dmcontrol register to assert ndmreset - verify that the ndmreset output
  is asserted.
- Mimic the CPU going into reset by asserting the unavailable input.
- Set lc_hw_debug_en to something other than On (since it should no longer be needed).
  At this point the ndmreset output signal will drop. Keep pinmux_hw_debug_en set to On
  to keep the JTAG side open while the ndmreset is in progress.
- Read the dmstatus register to verify allunavail is asserted.
- De-assert the ndmreset by writing 0 to the dmcontrol register field, verify the
  ndmreset output deasserted as well.
- Mimic the CPU going out of reset by de-asserting unavailable input
  after some delay. Set lc_hw_debug_en to true again as well.
- Read the previously written registers back and verify that they reflect the previously
  written value, proving that ndmreset assertion had no effect on them.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_ndmreset_req">rv_dm_ndmreset_req</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgdmcontrol_reg">RV_DM.DBG.DMCONTROL_REG</a><br><a href="01_feature_report.md#rv_dmdbgndm_reset">RV_DM.DBG.NDM_RESET</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## progbuf_busy

Verify that writing on DM progbuf registers while abstract command is executing
causes jtag_dmi_ral.abstractcs.busy to be set to 1.

This is implemented by rv_dm_cmderr_busy, which chooses a random operation to generate
the busy command error. One possible operation is writing to progbuf[0].


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_cmderr_busy">rv_dm_cmderr_busy</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgabstract_command">RV_DM.DBG.ABSTRACT_COMMAND</a><br><a href="01_feature_report.md#rv_dmdbgprogbuf">RV_DM.DBG.PROGBUF</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## progbuf_exception

Verify that writing on tl_mem_ral.exception register while an abstract command
is executing causes jtag_dmi_ral.abstractcs.cmderr to be set to 3.

- Program jtag_dmi_ral.dmcontrol.haltreq to 1'b1.
- Verify that 'debug_req_o' is set to 1.
- Acknowledge haltreq by setting tl_mem_ral.halted to 0.
- Send access register abstract command with postexec bit set.
- Write on tl_mem_ral.exception register.
- Verify that jtag_dmi_ral.abstractcs.cmderr is set to 3.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_cmderr_exception">rv_dm_cmderr_exception</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgabstract_command">RV_DM.DBG.ABSTRACT_COMMAND</a><br><a href="01_feature_report.md#rv_dmdbgdmcontrol_reg">RV_DM.DBG.DMCONTROL_REG</a><br><a href="01_feature_report.md#rv_dmdbgprogbuf">RV_DM.DBG.PROGBUF</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## progbuf_read_write_execute

Verify the functionality of program buffer by writing random data on program buffer.

- Program jtag_dmi_ral.dmcontrol.haltreq to 1'b1.
- Verify that 'debug_req_o' is set to 1.
- Acknowledge haltreq by setting tl_mem_ral.halted to 0.
- Fill the program buffer by writing random data to jtag_dmi_ral.progbuf0-7
  registers.
- Read tl_mem_ral.program_buffer0-7 registers to
  verify that the data we wrote is what we read back.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_progbuf_read_write_execute">rv_dm_progbuf_read_write_execute</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgdmcontrol_reg">RV_DM.DBG.DMCONTROL_REG</a><br><a href="01_feature_report.md#rv_dmdbgprogbuf">RV_DM.DBG.PROGBUF</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## rom_read_access

Verify the read accessability of rom.

- Read from the addresses of rom and verify that it reads the expected data.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_rom_read_access">rv_dm_rom_read_access</a></td>
  <td><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## sba

Verify all types of accesses from JTAG to SBA.

- Enable debug by setting lc_hw_debug_en to true and activate the dm
- Write to SBA registers to inject randomized 8/16/32bit writes and reads.
- Randomize readonaddr and readondata settings and ensure those have the intended
  effect.
- Generate sbbusy = 1 scenario by picking a very large response delay, since JTAG
  accesses are much slower (SBA TL accesses tend to complete faster than JTAG can
  read the SBCS register).


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_delayed_resp_sba_tl_access">rv_dm_delayed_resp_sba_tl_access</a><br><a href="03_test_report.md#rv_dm_sba_tl_access">rv_dm_sba_tl_access</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgsba">RV_DM.DBG.SBA</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## sba_autoincrement

Verify the address autoincrement functionality of SBA.

- Enable debug by setting lc_hw_debug_en to true and activate the dm.
- Write to the SBCS register to inject randomized 8/16/32bit writes. Set the
  autoincrement bit.
- Pick a random address and write to sbaddress0 register.
- Write a random value to sbdata0, repeating a randomized number of times.
- Each write should trigger a new SBA TL write access with the address incremented with
  the transfer size. Verify that the SBA TL access shows up.
- Repeat the same procedure for reads. For reads, set the readondata register and read
  the sbdata0 a randomized number of times - each read should trigger a new SBA TL read
  access.
- Intermittently also generate busy and error conditions.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_autoincr_sba_tl_access">rv_dm_autoincr_sba_tl_access</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgsba">RV_DM.DBG.SBA</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## sba_debug_disabled

Verify that access to SBA interface is disabled if lc_hw_debug_en is set to a value
other than lc_ctrl_pkg::On.

- Set lc_hw_debug_en to non-true value and activate the dm.
- Attempt to send some legal randomized SBA accesses. Checks in the scoreboard will
  assert that no SBA TL accesses appear on the TL interface.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_sba_debug_disabled">rv_dm_sba_debug_disabled</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgsba">RV_DM.DBG.SBA</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## smoke

A basic smoke test.

- Read the DTM register `idcode` and verify that it reflects the correct value.
- Enable debug by setting lc_hw_debug_en to true.
- Write to the DMI register field dmcontrol[dmactive] via JTAG and verify that the
  `dmactive` output pin reflects the same value.
- Write to the DMI register field dmcontrol[haltreq] via JTAG and verify that the
  `debug_req` output pin reflects the same value.
- Write to the DMI register field dmcontrol[ndmreset] via JTAG and verify that the
  `ndmreset` output pin reflects the same value.
- Wiggle the `unavailable` input and read the DTM register field dmstatus[allunavail]
  to verify that it reflects the same value as the input signal.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_smoke">rv_dm_smoke</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgdmcontrol_reg">RV_DM.DBG.DMCONTROL_REG</a><br><a href="01_feature_report.md#rv_dmdbgdmstatus_reg">RV_DM.DBG.DMSTATUS_REG</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## stress_all

A 'bug hunt' test that stresses the DUT to its limits.

- Combine above sequences in one test and run as many of them as possible in parallel.
  Run the rest sequentially.
- Randomly inject a full device reset intermittently.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_stress_all">rv_dm_stress_all</a></td>
  <td><a href="01_feature_report.md#rv_dmdbgabstract_command">RV_DM.DBG.ABSTRACT_COMMAND</a><br><a href="01_feature_report.md#rv_dmdbgdata_regs">RV_DM.DBG.DATA_REGS</a><br><a href="01_feature_report.md#rv_dmdbgdmcontrol_reg">RV_DM.DBG.DMCONTROL_REG</a><br><a href="01_feature_report.md#rv_dmdbgdmstatus_reg">RV_DM.DBG.DMSTATUS_REG</a><br><a href="01_feature_report.md#rv_dmdbghaltsum0_reg">RV_DM.DBG.HALTSUM0_REG</a><br><a href="01_feature_report.md#rv_dmdbghartinfo_reg">RV_DM.DBG.HARTINFO_REG</a><br><a href="01_feature_report.md#rv_dmdbgndm_reset">RV_DM.DBG.NDM_RESET</a><br><a href="01_feature_report.md#rv_dmdbgprogbuf">RV_DM.DBG.PROGBUF</a><br><a href="01_feature_report.md#rv_dmdbgsba">RV_DM.DBG.SBA</a><br><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>

## tap_ctrl_transitions

Verify all JTAG TAP controller FSM transitions

This test should verify that the standardized JTAG TAP FSM is working correctly.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_dm_tap_fsm">rv_dm_tap_fsm</a><br><a href="03_test_report.md#rv_dm_tap_fsm_rand_reset">rv_dm_tap_fsm_rand_reset</a></td>
  <td><a href="01_feature_report.md#rv_dmjtagdtm">RV_DM.JTAG.DTM</a><br><a href="01_feature_report.md#rv_dmjtagfsm">RV_DM.JTAG.FSM</a></td>
</tr>
  </tbody>
</table>
