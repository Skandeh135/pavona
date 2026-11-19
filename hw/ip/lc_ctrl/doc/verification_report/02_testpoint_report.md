# lc_ctrl Testpoint Report

## chip_lc_scrap (dragonfly)
Ensure it is possible to enter scrap state from every legal life cycle state.

-  Request transition to SCRAP state using the JTAG interface.
-  It should be possible to transition from every legal state using external clock.
-  Where it is allowed, transition using internal clocks should also be checked.
-  After transition, verify that the device is in SCRAP state through LC read.
-  Verify while in SCRAP state:
   - RV JTAG interface is unavailable.
   - Ibex is not executing.
   - RV_DM is unreachable by the stub CPU.

- X-ref'd with manuf_scrap from the manufacturing testplan.
- X-ref'd with chip_lc_test_locked.
- X-ref'd with chip_tap_strap_sampling


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_lc_ctrl_rand_to_scrap-dragonfly">chip_sw_lc_ctrl_rand_to_scrap (dragonfly)</a><br><a href="03_test_report.md#chip_sw_lc_ctrl_raw_to_scrap-dragonfly">chip_sw_lc_ctrl_raw_to_scrap (dragonfly)</a><br><a href="03_test_report.md#chip_sw_lc_ctrl_rma_to_scrap-dragonfly">chip_sw_lc_ctrl_rma_to_scrap (dragonfly)</a><br><a href="03_test_report.md#chip_sw_lc_ctrl_test_locked0_to_scrap-dragonfly">chip_sw_lc_ctrl_test_locked0_to_scrap (dragonfly)</a></td>
  <td><a href="01_feature_report.md#lc_ctrlstatescrap">LC_CTRL.STATE.SCRAP</a></td>
</tr>
  </tbody>
</table>

## chip_lc_scrap (egret)
Ensure it is possible to enter scrap state from every legal life cycle state.

-  Request transition to SCRAP state using the JTAG interface.
-  It should be possible to transition from every legal state using external clock.
-  Where it is allowed, transition using internal clocks should also be checked.
-  After transition, verify that the device is in SCRAP state through LC read.
-  Verify while in SCRAP state:
   - RV JTAG interface is unavailable.
   - Ibex is not executing.
   - RV_DM is unreachable by the stub CPU.

- X-ref'd with manuf_scrap from the manufacturing testplan.
- X-ref'd with chip_lc_test_locked.
- X-ref'd with chip_tap_strap_sampling


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_lc_ctrl_rand_to_scrap-egret">chip_sw_lc_ctrl_rand_to_scrap (egret)</a><br><a href="03_test_report.md#chip_sw_lc_ctrl_raw_to_scrap-egret">chip_sw_lc_ctrl_raw_to_scrap (egret)</a><br><a href="03_test_report.md#chip_sw_lc_ctrl_rma_to_scrap-egret">chip_sw_lc_ctrl_rma_to_scrap (egret)</a><br><a href="03_test_report.md#chip_sw_lc_ctrl_test_locked0_to_scrap-egret">chip_sw_lc_ctrl_test_locked0_to_scrap (egret)</a></td>
  <td><a href="01_feature_report.md#lc_ctrlstatescrap">LC_CTRL.STATE.SCRAP</a></td>
</tr>
  </tbody>
</table>

## chip_lc_test_locked (dragonfly)
Transition from TEST_UNLOCKED to TEST_LOCKED using LC JTAG interface.

-  Check in TEST_UNLOCKED RV JTAG interface is available.
-  Verify When in TEST_LOCKED state:
   - RV JTAG interface is unavailable.
   - Ibex is not executing.
   - RV_DM is unreachable by the stub CPU.

- X-ref'd with manuf_cp_test_lock from the manufacturing testplan.
- X-ref'd with chip_lc_scrap.
- X-ref'd with chip_tap_strap_sampling
- X-ref'd with chip_sw_lc_walkthrough
- X-ref'd with chip_rv_dm_lc_disabled


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_rv_dm_lc_disabled-dragonfly">chip_rv_dm_lc_disabled (dragonfly)</a><br><a href="03_test_report.md#chip_sw_lc_walkthrough_testunlocks-dragonfly">chip_sw_lc_walkthrough_testunlocks (dragonfly)</a></td>
  <td><a href="01_feature_report.md#lc_ctrlstatetest_locked">LC_CTRL.STATE.TEST_LOCKED</a></td>
</tr>
  </tbody>
</table>

## chip_lc_test_locked (egret)
Transition from TEST_UNLOCKED to TEST_LOCKED using LC JTAG interface.

-  Check in TEST_UNLOCKED RV JTAG interface is available.
-  Verify When in TEST_LOCKED state:
   - RV JTAG interface is unavailable.
   - Ibex is not executing.
   - RV_DM is unreachable by the stub CPU.

- X-ref'd with manuf_cp_test_lock from the manufacturing testplan.
- X-ref'd with chip_lc_scrap.
- X-ref'd with chip_tap_strap_sampling
- X-ref'd with chip_sw_lc_walkthrough
- X-ref'd with chip_rv_dm_lc_disabled


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_rv_dm_lc_disabled-egret">chip_rv_dm_lc_disabled (egret)</a><br><a href="03_test_report.md#chip_sw_lc_walkthrough_testunlocks-egret">chip_sw_lc_walkthrough_testunlocks (egret)</a></td>
  <td><a href="01_feature_report.md#lc_ctrlstatetest_locked">LC_CTRL.STATE.TEST_LOCKED</a></td>
</tr>
  </tbody>
</table>

## chip_sw_lc_ctrl_alert_handler_escalation (dragonfly)
Verify that the escalation signals from the alert handler are connected to LC ctrl.

- Trigger an alert to initiate the escalations.
- Check that the escalation signals are connected to the LC ctrl:
  - First escalation has no effect on the LC ctrl.  Read LC_STATE CSR to confirm
    this is the case.
  - Second escalation should cause the `lc_escalation_en` output to be asserted and for
    the LC_STATE to transition to scrap state.  Confirm by reading the LC_STATE CSR
  - Verify that all decoded outputs except for escalate_en are
    disabled. X-ref'ed with the respective IP tests that consume these signals.

In silicon and FPGA test targets, verify that the device debug interfaces are not
accessible when testing in `TEST_UNLOCKED`, `DEV` or `RMA` states.

X-ref'ed with chip_sw_lc_ctrl_broadcast test, which verifies the connectivity of the LC
decoded outputs to other IPs.
X-ref'ed with alert_handler's escalation test.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_alert_handler_escalation-dragonfly">chip_sw_alert_handler_escalation (dragonfly)</a></td>
  <td><a href="01_feature_report.md#lc_ctrllogical_scrap">LC_CTRL.LOGICAL_SCRAP</a></td>
</tr>
  </tbody>
</table>

## chip_sw_lc_ctrl_alert_handler_escalation (egret)
Verify that the escalation signals from the alert handler are connected to LC ctrl.

- Trigger an alert to initiate the escalations.
- Check that the escalation signals are connected to the LC ctrl:
  - First escalation has no effect on the LC ctrl.  Read LC_STATE CSR to confirm
    this is the case.
  - Second escalation should cause the `lc_escalation_en` output to be asserted and for
    the LC_STATE to transition to scrap state.  Confirm by reading the LC_STATE CSR
  - Verify that all decoded outputs except for escalate_en are
    disabled. X-ref'ed with the respective IP tests that consume these signals.

In silicon and FPGA test targets, verify that the device debug interfaces are not
accessible when testing in `TEST_UNLOCKED`, `DEV` or `RMA` states.

X-ref'ed with chip_sw_lc_ctrl_broadcast test, which verifies the connectivity of the LC
decoded outputs to other IPs.
X-ref'ed with alert_handler's escalation test.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_alert_handler_escalation-egret">chip_sw_alert_handler_escalation (egret)</a></td>
  <td><a href="01_feature_report.md#lc_ctrllogical_scrap">LC_CTRL.LOGICAL_SCRAP</a></td>
</tr>
  </tbody>
</table>

## chip_sw_lc_ctrl_broadcast (dragonfly)
Verify broadcast signals from lc_ctrl.

- Preload the LC partition in the otp_ctrl with the following states: RMA, DEV,
  TEST_LOCKED[N] & SCRAP.
- Verify that the following broadcast signals are having the right effect in the
  respective IPs that consume them:
  - lc_dft_en_o: impacts pinmux, pwrmgr, otp_ctrl, AST
  - lc_hw_debug_en_o: impacts pinmux, pwrmgr, sram_ctrl (main and ret) & the rv_dm
  - lc_keymgr_en_o: impacts keymgr
  - lc_clk_byp_req_o: impacts clkmgr (handshake with lc_clk_byp_ack_i)
  - lc_flash_rma_req_o: impacts flash_ctrl (handshake with lc_flash_ram_ack_i)
  - lc_flash_rma_seed_o: impacts flash_ctrl
  - lc_check_byp_en_o: impacts otp_ctrl
  - lc_creator_seed_sw_rw_en_o: impacts flash_ctrl & otp_ctrl
  - lc_owner_seed_sw_rw_en_o: impacts flash_ctrl
  - lc_iso_part_sw_rd_en_o: impacts flash_ctrl
  - lc_iso_part_sw_wr_en_o: impacts flash_ctrl
  - lc_seed_hw_rd_en_o: impacts flash_ctrl & otp_ctrl
- These outputs are enabled per the
  [life cycle architecture spec](../../../../../doc/security/specs/device_life_cycle/#architecture).

X-ref'ed with the respective IP tests that consume these signals.

Note that the following signals are already verified with connectivity tests and SVAs:

  - lc_dft_en_o (AST connection)
  - lc_cpu_en_o (rv_core_ibex)
  - lc_nvm_debug_en_o (flash_ctrl)
  - lc_escalate_en_o (multiple)


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_prim_tl_access-dragonfly">chip_prim_tl_access (dragonfly)</a><br><a href="03_test_report.md#chip_rv_dm_lc_disabled-dragonfly">chip_rv_dm_lc_disabled (dragonfly)</a><br><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_lc-dragonfly">chip_sw_clkmgr_external_clk_src_for_lc (dragonfly)</a><br><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_sw_fast_dev-dragonfly">chip_sw_clkmgr_external_clk_src_for_sw_fast_dev (dragonfly)</a><br><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_sw_fast_rma-dragonfly">chip_sw_clkmgr_external_clk_src_for_sw_fast_rma (dragonfly)</a><br><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_sw_fast_test_unlocked0-dragonfly">chip_sw_clkmgr_external_clk_src_for_sw_fast_test_unlocked0 (dragonfly)</a><br><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_sw_slow_dev-dragonfly">chip_sw_clkmgr_external_clk_src_for_sw_slow_dev (dragonfly)</a><br><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_sw_slow_rma-dragonfly">chip_sw_clkmgr_external_clk_src_for_sw_slow_rma (dragonfly)</a><br><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_sw_slow_test_unlocked0-dragonfly">chip_sw_clkmgr_external_clk_src_for_sw_slow_test_unlocked0 (dragonfly)</a><br><a href="03_test_report.md#chip_sw_flash_ctrl_lc_rw_en-dragonfly">chip_sw_flash_ctrl_lc_rw_en (dragonfly)</a><br><a href="03_test_report.md#chip_sw_flash_rma_unlocked-dragonfly">chip_sw_flash_rma_unlocked (dragonfly)</a><br><a href="03_test_report.md#chip_sw_keymgr_key_derivation-dragonfly">chip_sw_keymgr_key_derivation (dragonfly)</a><br><a href="03_test_report.md#chip_sw_lc_ctrl_transition-dragonfly">chip_sw_lc_ctrl_transition (dragonfly)</a><br><a href="03_test_report.md#chip_sw_otp_ctrl_lc_signals_dev-dragonfly">chip_sw_otp_ctrl_lc_signals_dev (dragonfly)</a><br><a href="03_test_report.md#chip_sw_otp_ctrl_lc_signals_prod-dragonfly">chip_sw_otp_ctrl_lc_signals_prod (dragonfly)</a><br><a href="03_test_report.md#chip_sw_otp_ctrl_lc_signals_rma-dragonfly">chip_sw_otp_ctrl_lc_signals_rma (dragonfly)</a><br><a href="03_test_report.md#chip_sw_otp_ctrl_lc_signals_test_unlocked0-dragonfly">chip_sw_otp_ctrl_lc_signals_test_unlocked0 (dragonfly)</a><br><a href="03_test_report.md#chip_sw_rom_ctrl_integrity_check-dragonfly">chip_sw_rom_ctrl_integrity_check (dragonfly)</a><br><a href="03_test_report.md#chip_sw_sram_ctrl_execution_main-dragonfly">chip_sw_sram_ctrl_execution_main (dragonfly)</a><br><a href="03_test_report.md#chip_tap_straps_dev-dragonfly">chip_tap_straps_dev (dragonfly)</a><br><a href="03_test_report.md#chip_tap_straps_prod-dragonfly">chip_tap_straps_prod (dragonfly)</a><br><a href="03_test_report.md#chip_tap_straps_rma-dragonfly">chip_tap_straps_rma (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_lc_ctrl_broadcast (egret)
Verify broadcast signals from lc_ctrl.

- Preload the LC partition in the otp_ctrl with the following states: RMA, DEV,
  TEST_LOCKED[N] & SCRAP.
- Verify that the following broadcast signals are having the right effect in the
  respective IPs that consume them:
  - lc_dft_en_o: impacts pinmux, pwrmgr, otp_ctrl, AST
  - lc_hw_debug_en_o: impacts pinmux, pwrmgr, sram_ctrl (main and ret) & the rv_dm
  - lc_keymgr_en_o: impacts keymgr
  - lc_clk_byp_req_o: impacts clkmgr (handshake with lc_clk_byp_ack_i)
  - lc_flash_rma_req_o: impacts flash_ctrl (handshake with lc_flash_ram_ack_i)
  - lc_flash_rma_seed_o: impacts flash_ctrl
  - lc_check_byp_en_o: impacts otp_ctrl
  - lc_creator_seed_sw_rw_en_o: impacts flash_ctrl & otp_ctrl
  - lc_owner_seed_sw_rw_en_o: impacts flash_ctrl
  - lc_iso_part_sw_rd_en_o: impacts flash_ctrl
  - lc_iso_part_sw_wr_en_o: impacts flash_ctrl
  - lc_seed_hw_rd_en_o: impacts flash_ctrl & otp_ctrl
- These outputs are enabled per the
  [life cycle architecture spec](../../../../../doc/security/specs/device_life_cycle/#architecture).

X-ref'ed with the respective IP tests that consume these signals.

Note that the following signals are already verified with connectivity tests and SVAs:

  - lc_dft_en_o (AST connection)
  - lc_cpu_en_o (rv_core_ibex)
  - lc_nvm_debug_en_o (flash_ctrl)
  - lc_escalate_en_o (multiple)


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_prim_tl_access-egret">chip_prim_tl_access (egret)</a><br><a href="03_test_report.md#chip_rv_dm_lc_disabled-egret">chip_rv_dm_lc_disabled (egret)</a><br><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_lc-egret">chip_sw_clkmgr_external_clk_src_for_lc (egret)</a><br><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_sw_fast_dev-egret">chip_sw_clkmgr_external_clk_src_for_sw_fast_dev (egret)</a><br><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_sw_fast_rma-egret">chip_sw_clkmgr_external_clk_src_for_sw_fast_rma (egret)</a><br><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_sw_fast_test_unlocked0-egret">chip_sw_clkmgr_external_clk_src_for_sw_fast_test_unlocked0 (egret)</a><br><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_sw_slow_dev-egret">chip_sw_clkmgr_external_clk_src_for_sw_slow_dev (egret)</a><br><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_sw_slow_rma-egret">chip_sw_clkmgr_external_clk_src_for_sw_slow_rma (egret)</a><br><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_sw_slow_test_unlocked0-egret">chip_sw_clkmgr_external_clk_src_for_sw_slow_test_unlocked0 (egret)</a><br><a href="03_test_report.md#chip_sw_flash_ctrl_lc_rw_en-egret">chip_sw_flash_ctrl_lc_rw_en (egret)</a><br><a href="03_test_report.md#chip_sw_flash_rma_unlocked-egret">chip_sw_flash_rma_unlocked (egret)</a><br><a href="03_test_report.md#chip_sw_keymgr_key_derivation-egret">chip_sw_keymgr_key_derivation (egret)</a><br><a href="03_test_report.md#chip_sw_lc_ctrl_transition-egret">chip_sw_lc_ctrl_transition (egret)</a><br><a href="03_test_report.md#chip_sw_otp_ctrl_lc_signals_dev-egret">chip_sw_otp_ctrl_lc_signals_dev (egret)</a><br><a href="03_test_report.md#chip_sw_otp_ctrl_lc_signals_prod-egret">chip_sw_otp_ctrl_lc_signals_prod (egret)</a><br><a href="03_test_report.md#chip_sw_otp_ctrl_lc_signals_rma-egret">chip_sw_otp_ctrl_lc_signals_rma (egret)</a><br><a href="03_test_report.md#chip_sw_otp_ctrl_lc_signals_test_unlocked0-egret">chip_sw_otp_ctrl_lc_signals_test_unlocked0 (egret)</a><br><a href="03_test_report.md#chip_sw_rom_ctrl_integrity_check-egret">chip_sw_rom_ctrl_integrity_check (egret)</a><br><a href="03_test_report.md#chip_sw_sram_ctrl_execution_main-egret">chip_sw_sram_ctrl_execution_main (egret)</a><br><a href="03_test_report.md#chip_tap_straps_dev-egret">chip_tap_straps_dev (egret)</a><br><a href="03_test_report.md#chip_tap_straps_prod-egret">chip_tap_straps_prod (egret)</a><br><a href="03_test_report.md#chip_tap_straps_rma-egret">chip_tap_straps_rma (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_lc_ctrl_debug_access (dragonfly)
Verify debug access for each lifecycle state.

For each lifecycle state verify the debug and CPU access to make sure it matches the
specification.


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
  <td><a href="01_feature_report.md#lc_ctrlstatedev">LC_CTRL.STATE.DEV</a><br><a href="01_feature_report.md#lc_ctrlstateprod">LC_CTRL.STATE.PROD</a><br><a href="01_feature_report.md#lc_ctrlstateprod_end">LC_CTRL.STATE.PROD_END</a><br><a href="01_feature_report.md#lc_ctrlstateraw">LC_CTRL.STATE.RAW</a><br><a href="01_feature_report.md#lc_ctrlstaterma">LC_CTRL.STATE.RMA</a><br><a href="01_feature_report.md#lc_ctrlstatescrap">LC_CTRL.STATE.SCRAP</a><br><a href="01_feature_report.md#lc_ctrlstatetest_locked">LC_CTRL.STATE.TEST_LOCKED</a><br><a href="01_feature_report.md#lc_ctrlstatetest_unlocked">LC_CTRL.STATE.TEST_UNLOCKED</a></td>
</tr>
  </tbody>
</table>

## chip_sw_lc_ctrl_debug_access (egret)
Verify debug access for each lifecycle state.

For each lifecycle state verify the debug and CPU access to make sure it matches the
specification.


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
  <td><a href="01_feature_report.md#lc_ctrlstatedev">LC_CTRL.STATE.DEV</a><br><a href="01_feature_report.md#lc_ctrlstateprod">LC_CTRL.STATE.PROD</a><br><a href="01_feature_report.md#lc_ctrlstateprod_end">LC_CTRL.STATE.PROD_END</a><br><a href="01_feature_report.md#lc_ctrlstateraw">LC_CTRL.STATE.RAW</a><br><a href="01_feature_report.md#lc_ctrlstaterma">LC_CTRL.STATE.RMA</a><br><a href="01_feature_report.md#lc_ctrlstatescrap">LC_CTRL.STATE.SCRAP</a><br><a href="01_feature_report.md#lc_ctrlstatetest_locked">LC_CTRL.STATE.TEST_LOCKED</a><br><a href="01_feature_report.md#lc_ctrlstatetest_unlocked">LC_CTRL.STATE.TEST_UNLOCKED</a></td>
</tr>
  </tbody>
</table>

## chip_sw_lc_ctrl_init (dragonfly)
Verify the LC ctrl initialization on power up.

Verify that the chip powers up correctly on POR.

- The pwrmgr initiates a handshake with OTP ctrl and later, with LC ctrl in subsequent
  FSM states. Ensure that the whole power up sequence does not hang.
- Verify with connectivity assertion checks, the handshake signals are connected.
- Ensure that no interrupts or alerts are triggered.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_lc_ctrl_transition-dragonfly">chip_sw_lc_ctrl_transition (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_lc_ctrl_init (egret)
Verify the LC ctrl initialization on power up.

Verify that the chip powers up correctly on POR.

- The pwrmgr initiates a handshake with OTP ctrl and later, with LC ctrl in subsequent
  FSM states. Ensure that the whole power up sequence does not hang.
- Verify with connectivity assertion checks, the handshake signals are connected.
- Ensure that no interrupts or alerts are triggered.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_lc_ctrl_transition-egret">chip_sw_lc_ctrl_transition (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_lc_ctrl_jtag_access (dragonfly)
Verify enable to access LC ctrl via JTAG.

Using the JTAG agent, write and read LC ctrl CSRs, verify the read value for
correctness. Repeat test with clk_ext configuration.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_tap_straps_dev-dragonfly">chip_tap_straps_dev (dragonfly)</a><br><a href="03_test_report.md#chip_tap_straps_prod-dragonfly">chip_tap_straps_prod (dragonfly)</a><br><a href="03_test_report.md#chip_tap_straps_rma-dragonfly">chip_tap_straps_rma (dragonfly)</a></td>
  <td><a href="01_feature_report.md#lc_ctrlaccessext_clk">LC_CTRL.ACCESS.EXT_CLK</a><br><a href="01_feature_report.md#lc_ctrlaccessjtag">LC_CTRL.ACCESS.JTAG</a></td>
</tr>
  </tbody>
</table>

## chip_sw_lc_ctrl_jtag_access (egret)
Verify enable to access LC ctrl via JTAG.

Using the JTAG agent, write and read LC ctrl CSRs, verify the read value for
correctness. Repeat test with clk_ext configuration.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_tap_straps_dev-egret">chip_tap_straps_dev (egret)</a><br><a href="03_test_report.md#chip_tap_straps_prod-egret">chip_tap_straps_prod (egret)</a><br><a href="03_test_report.md#chip_tap_straps_rma-egret">chip_tap_straps_rma (egret)</a></td>
  <td><a href="01_feature_report.md#lc_ctrlaccessext_clk">LC_CTRL.ACCESS.EXT_CLK</a><br><a href="01_feature_report.md#lc_ctrlaccessjtag">LC_CTRL.ACCESS.JTAG</a></td>
</tr>
  </tbody>
</table>

## chip_sw_lc_ctrl_key_div (dragonfly)
Verify the keymgr div output to keymgr.

- Verify in different LC states, LC ctrl outputs the correct `key_div_o` to keymgr.
- Verify that the keymgr uses the given `key_div_o` value to compute the keys.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_keymgr_key_derivation_prod-dragonfly">chip_sw_keymgr_key_derivation_prod (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_lc_ctrl_key_div (egret)
Verify the keymgr div output to keymgr.

- Verify in different LC states, LC ctrl outputs the correct `key_div_o` to keymgr.
- Verify that the keymgr uses the given `key_div_o` value to compute the keys.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_keymgr_key_derivation_prod-egret">chip_sw_keymgr_key_derivation_prod (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_lc_ctrl_kmac_error (dragonfly)

Verify the effect of KMAC returning an error during the hash generation of LC tokens.

- Follow the steps in `chip_sw_lc_ctrl_kmac_req` test.
- While the KMAC is actively computing the digest, glitch the KMAC app sparse FSM to
  trigger a fault.
- Verify that KMAC returns an error signal to the LC controller.
- TBD


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

## chip_sw_lc_ctrl_kmac_error (egret)

Verify the effect of KMAC returning an error during the hash generation of LC tokens.

- Follow the steps in `chip_sw_lc_ctrl_kmac_req` test.
- While the KMAC is actively computing the digest, glitch the KMAC app sparse FSM to
  trigger a fault.
- Verify that KMAC returns an error signal to the LC controller.
- TBD


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

## chip_sw_lc_ctrl_kmac_req (dragonfly)
Verify the token requested from KMAC.

- For conditional transition, the LC ctrl will send out a token request to KMAC.
- Verify that the KMAC returns a hashed token, which should match one of the
  transition token CSRs.

X-ref'ed with chip_kmac_lc_req.
X-ref'ed manuf_cp_unlock_raw
X-ref'ed manuf_cp_test_lock
X-ref'ed manuf_ft_exit_token
X-ref'ed manuf_rma_entry


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_lc_ctrl_transition-dragonfly">chip_sw_lc_ctrl_transition (dragonfly)</a></td>
  <td><a href="01_feature_report.md#lc_ctrlauthenticated_transitions">LC_CTRL.AUTHENTICATED_TRANSITIONS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_lc_ctrl_kmac_req (egret)
Verify the token requested from KMAC.

- For conditional transition, the LC ctrl will send out a token request to KMAC.
- Verify that the KMAC returns a hashed token, which should match one of the
  transition token CSRs.

X-ref'ed with chip_kmac_lc_req.
X-ref'ed manuf_cp_unlock_raw
X-ref'ed manuf_cp_test_lock
X-ref'ed manuf_ft_exit_token
X-ref'ed manuf_rma_entry


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_lc_ctrl_transition-egret">chip_sw_lc_ctrl_transition (egret)</a></td>
  <td><a href="01_feature_report.md#lc_ctrlauthenticated_transitions">LC_CTRL.AUTHENTICATED_TRANSITIONS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_lc_ctrl_otp_hw_cfg0 (dragonfly)
Verify the device_ID and ID_state CSRs.

- Preload the hw_cfg0 partition in OTP ctrl with random data.
- Read the device ID and the ID state CSRs to verify their correctness.
- Reset the chip and repeat the first 2 steps to verify a different set of values.

In silicon and FPGA targets, verify that the DeviceID read via JTAG matches the
value read from Ibex.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_lc_ctrl_otp_hw_cfg0-dragonfly">chip_sw_lc_ctrl_otp_hw_cfg0 (dragonfly)</a></td>
  <td><a href="01_feature_report.md#lc_ctrlaccessjtag">LC_CTRL.ACCESS.JTAG</a></td>
</tr>
  </tbody>
</table>

## chip_sw_lc_ctrl_otp_hw_cfg0 (egret)
Verify the device_ID and ID_state CSRs.

- Preload the hw_cfg0 partition in OTP ctrl with random data.
- Read the device ID and the ID state CSRs to verify their correctness.
- Reset the chip and repeat the first 2 steps to verify a different set of values.

In silicon and FPGA targets, verify that the DeviceID read via JTAG matches the
value read from Ibex.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_lc_ctrl_otp_hw_cfg0-egret">chip_sw_lc_ctrl_otp_hw_cfg0 (egret)</a></td>
  <td><a href="01_feature_report.md#lc_ctrlaccessjtag">LC_CTRL.ACCESS.JTAG</a></td>
</tr>
  </tbody>
</table>

## chip_sw_lc_ctrl_transitions (dragonfly)
Verify the LC ctrl can transit from one state to another valid state with the
correct tokens.

- Preload OTP image with a LC state and required tokens to transfer to next state.
- Initiate an LC ctrl state transition via SW if CPU is enabled, or via JTAG interface
  if CPU is disable.
- Ensure that the LC program request is received by the OTP ctrl.
- Verify the updated data output from OTP ctrl to LC ctrl is correct.
- Ensure that there is no background or otp_init error.
- Verify that the LC ctrl has transitioned to the programmed state after a reboot.

Re-randomize the lc_transition tokens and repeat the sequence above.

X-ref'ed chip_sw_otp_ctrl_program.
X-ref'ed manuf_cp_unlock_raw
X-ref'ed manuf_cp_test_lock
X-ref'ed manuf_ft_exit_token


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_lc_ctrl_transition-dragonfly">chip_sw_lc_ctrl_transition (dragonfly)</a></td>
  <td><a href="01_feature_report.md#lc_ctrlauthenticated_transitions">LC_CTRL.AUTHENTICATED_TRANSITIONS</a><br><a href="01_feature_report.md#lc_ctrlstateraw">LC_CTRL.STATE.RAW</a><br><a href="01_feature_report.md#lc_ctrlstatetest_locked">LC_CTRL.STATE.TEST_LOCKED</a><br><a href="01_feature_report.md#lc_ctrlstatetest_unlocked">LC_CTRL.STATE.TEST_UNLOCKED</a></td>
</tr>
  </tbody>
</table>

## chip_sw_lc_ctrl_transitions (egret)
Verify the LC ctrl can transit from one state to another valid state with the
correct tokens.

- Preload OTP image with a LC state and required tokens to transfer to next state.
- Initiate an LC ctrl state transition via SW if CPU is enabled, or via JTAG interface
  if CPU is disable.
- Ensure that the LC program request is received by the OTP ctrl.
- Verify the updated data output from OTP ctrl to LC ctrl is correct.
- Ensure that there is no background or otp_init error.
- Verify that the LC ctrl has transitioned to the programmed state after a reboot.

Re-randomize the lc_transition tokens and repeat the sequence above.

X-ref'ed chip_sw_otp_ctrl_program.
X-ref'ed manuf_cp_unlock_raw
X-ref'ed manuf_cp_test_lock
X-ref'ed manuf_ft_exit_token


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_lc_ctrl_transition-egret">chip_sw_lc_ctrl_transition (egret)</a></td>
  <td><a href="01_feature_report.md#lc_ctrlauthenticated_transitions">LC_CTRL.AUTHENTICATED_TRANSITIONS</a><br><a href="01_feature_report.md#lc_ctrlstateraw">LC_CTRL.STATE.RAW</a><br><a href="01_feature_report.md#lc_ctrlstatetest_locked">LC_CTRL.STATE.TEST_LOCKED</a><br><a href="01_feature_report.md#lc_ctrlstatetest_unlocked">LC_CTRL.STATE.TEST_UNLOCKED</a></td>
</tr>
  </tbody>
</table>

## chip_sw_lc_ctrl_volatile_raw_unlock (dragonfly)
Configure VOLATILE_RAW_UNLOCK via LC TAP interface and enable CPU execution.

- Pre-load OTP image with RAW lc_state.
- Initiate the LC transition to test_unlocked0 state using the
  VOLATILE_RAW_UNLOCK mode of operation.

If this top-level is expected to support VOLATILE_RAW_UNLOCK:

- As part of the transition to test_unlocked0, switch the TAP interface to rv_dm.
- Enable ROM execution via rv_dm, and perform POR.
- Initiate a second transition to test_unlocked0 using VOLATILE_RAW_UNLOCK.
- Verify that the CPU is able to execute.
- Test ext_clk injection before enabling ROM execution.

If this top-level is NOT expected to support VOLATILE_RAW_UNLOCK:

- Check that the VOLATILE_RAW_UNLOCK bit in the transition control register stays 0
  when it is programmed to 1.
- Check that the transition results in a token error (the real RAW unlock transition
  expects the unhashed token instead of the hashed token supplied for volatile RAW unlock).


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_lc_ctrl_volatile_raw_unlock-dragonfly">chip_sw_lc_ctrl_volatile_raw_unlock (dragonfly)</a><br><a href="03_test_report.md#chip_sw_lc_ctrl_volatile_raw_unlock_ext_clk_48mhz-dragonfly">chip_sw_lc_ctrl_volatile_raw_unlock_ext_clk_48mhz (dragonfly)</a><br><a href="03_test_report.md#rom_volatile_raw_unlock-dragonfly">rom_volatile_raw_unlock (dragonfly)</a></td>
  <td><a href="01_feature_report.md#lc_ctrlaccessext_clk">LC_CTRL.ACCESS.EXT_CLK</a><br><a href="01_feature_report.md#lc_ctrlaccessjtag">LC_CTRL.ACCESS.JTAG</a><br><a href="01_feature_report.md#lc_ctrlauthenticated_transitions">LC_CTRL.AUTHENTICATED_TRANSITIONS</a><br><a href="01_feature_report.md#lc_ctrlstateraw">LC_CTRL.STATE.RAW</a><br><a href="01_feature_report.md#lc_ctrlstatetest_unlocked">LC_CTRL.STATE.TEST_UNLOCKED</a></td>
</tr>
  </tbody>
</table>

## chip_sw_lc_ctrl_volatile_raw_unlock (egret)
Configure VOLATILE_RAW_UNLOCK via LC TAP interface and enable CPU execution.

- Pre-load OTP image with RAW lc_state.
- Initiate the LC transition to test_unlocked0 state using the
  VOLATILE_RAW_UNLOCK mode of operation.

If this top-level is expected to support VOLATILE_RAW_UNLOCK:

- As part of the transition to test_unlocked0, switch the TAP interface to rv_dm.
- Enable ROM execution via rv_dm, and perform POR.
- Initiate a second transition to test_unlocked0 using VOLATILE_RAW_UNLOCK.
- Verify that the CPU is able to execute.
- Test ext_clk injection before enabling ROM execution.

If this top-level is NOT expected to support VOLATILE_RAW_UNLOCK:

- Check that the VOLATILE_RAW_UNLOCK bit in the transition control register stays 0
  when it is programmed to 1.
- Check that the transition results in a token error (the real RAW unlock transition
  expects the unhashed token instead of the hashed token supplied for volatile RAW unlock).


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_lc_ctrl_volatile_raw_unlock-egret">chip_sw_lc_ctrl_volatile_raw_unlock (egret)</a><br><a href="03_test_report.md#chip_sw_lc_ctrl_volatile_raw_unlock_ext_clk_48mhz-egret">chip_sw_lc_ctrl_volatile_raw_unlock_ext_clk_48mhz (egret)</a><br><a href="03_test_report.md#rom_volatile_raw_unlock-egret">rom_volatile_raw_unlock (egret)</a></td>
  <td><a href="01_feature_report.md#lc_ctrlaccessext_clk">LC_CTRL.ACCESS.EXT_CLK</a><br><a href="01_feature_report.md#lc_ctrlaccessjtag">LC_CTRL.ACCESS.JTAG</a><br><a href="01_feature_report.md#lc_ctrlauthenticated_transitions">LC_CTRL.AUTHENTICATED_TRANSITIONS</a><br><a href="01_feature_report.md#lc_ctrlstateraw">LC_CTRL.STATE.RAW</a><br><a href="01_feature_report.md#lc_ctrlstatetest_unlocked">LC_CTRL.STATE.TEST_UNLOCKED</a></td>
</tr>
  </tbody>
</table>

## chip_sw_lc_walkthrough (dragonfly)
Walk through the life cycle stages from RAW state and resetting the chip each time.

- Pre-load OTP image with RAW lc_state.
- Initiate the LC transition to one of the test unlock state.
- Program test_unlock_token, test_exit_token, rma_unlock_token into OTP partitions.
- Move forward to next valid LC states via JTAG interface or SW interface if CPU is
  enabled.

Verify that the features that should indeed be disabled are indeed disabled.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_lc_walkthrough_dev-dragonfly">chip_sw_lc_walkthrough_dev (dragonfly)</a><br><a href="03_test_report.md#chip_sw_lc_walkthrough_prod-dragonfly">chip_sw_lc_walkthrough_prod (dragonfly)</a><br><a href="03_test_report.md#chip_sw_lc_walkthrough_prodend-dragonfly">chip_sw_lc_walkthrough_prodend (dragonfly)</a><br><a href="03_test_report.md#chip_sw_lc_walkthrough_rma-dragonfly">chip_sw_lc_walkthrough_rma (dragonfly)</a><br><a href="03_test_report.md#chip_sw_lc_walkthrough_testunlocks-dragonfly">chip_sw_lc_walkthrough_testunlocks (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_lc_walkthrough (egret)
Walk through the life cycle stages from RAW state and resetting the chip each time.

- Pre-load OTP image with RAW lc_state.
- Initiate the LC transition to one of the test unlock state.
- Program test_unlock_token, test_exit_token, rma_unlock_token into OTP partitions.
- Move forward to next valid LC states via JTAG interface or SW interface if CPU is
  enabled.

Verify that the features that should indeed be disabled are indeed disabled.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_lc_walkthrough_dev-egret">chip_sw_lc_walkthrough_dev (egret)</a><br><a href="03_test_report.md#chip_sw_lc_walkthrough_prod-egret">chip_sw_lc_walkthrough_prod (egret)</a><br><a href="03_test_report.md#chip_sw_lc_walkthrough_prodend-egret">chip_sw_lc_walkthrough_prodend (egret)</a><br><a href="03_test_report.md#chip_sw_lc_walkthrough_rma-egret">chip_sw_lc_walkthrough_rma (egret)</a><br><a href="03_test_report.md#chip_sw_lc_walkthrough_testunlocks-egret">chip_sw_lc_walkthrough_testunlocks (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## jtag_access

This test checks jtag debug interface in lc_ctrl.
This test will use both JTAG TAP and TLUL to access the CSR space.
All above CSR sequences should be accessible via both interfaces.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#lc_ctrl_jtag_access">lc_ctrl_jtag_access</a><br><a href="03_test_report.md#lc_ctrl_jtag_alert_test">lc_ctrl_jtag_alert_test</a><br><a href="03_test_report.md#lc_ctrl_jtag_csr_aliasing">lc_ctrl_jtag_csr_aliasing</a><br><a href="03_test_report.md#lc_ctrl_jtag_csr_bit_bash">lc_ctrl_jtag_csr_bit_bash</a><br><a href="03_test_report.md#lc_ctrl_jtag_csr_hw_reset">lc_ctrl_jtag_csr_hw_reset</a><br><a href="03_test_report.md#lc_ctrl_jtag_csr_mem_rw_with_rand_reset">lc_ctrl_jtag_csr_mem_rw_with_rand_reset</a><br><a href="03_test_report.md#lc_ctrl_jtag_csr_rw">lc_ctrl_jtag_csr_rw</a><br><a href="03_test_report.md#lc_ctrl_jtag_errors">lc_ctrl_jtag_errors</a><br><a href="03_test_report.md#lc_ctrl_jtag_prog_failure">lc_ctrl_jtag_prog_failure</a><br><a href="03_test_report.md#lc_ctrl_jtag_regwen_during_op">lc_ctrl_jtag_regwen_during_op</a><br><a href="03_test_report.md#lc_ctrl_jtag_same_csr_outstanding">lc_ctrl_jtag_same_csr_outstanding</a><br><a href="03_test_report.md#lc_ctrl_jtag_smoke">lc_ctrl_jtag_smoke</a><br><a href="03_test_report.md#lc_ctrl_jtag_state_post_trans">lc_ctrl_jtag_state_post_trans</a></td>
  <td><a href="01_feature_report.md#lc_ctrlaccessjtag">LC_CTRL.ACCESS.JTAG</a></td>
</tr>
  </tbody>
</table>

## jtag_priority

This test covers a corner case in JTAG and TLUL interfaces.

**Stimulus**:

- Issue mux_claim operation from TLUL and JTAG interfaces at the same time.

**Checks**:

- Ensure TAP interface has the priority.
- Ensure right after the mux_claim operation, the non-prioritized interface returns 0
  from the CSR readings. This checking ensures there is no token leakage between
  interfaces.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#lc_ctrl_jtag_priority">lc_ctrl_jtag_priority</a></td>
  <td><a href="01_feature_report.md#lc_ctrlaccessjtag">LC_CTRL.ACCESS.JTAG</a></td>
</tr>
  </tbody>
</table>

## lc_ctrl_volatile_unlock

This test covers lc_ctrl volatile_raw_unlock functionality.

**Stimulus**:

- Claim the mutex.
- Set volatile_raw_unlock to 1.
- Trigger a lc_transition.
- Trigger a second lc_transition without reset.

**Checks if the feature is enabled in HW**:

- If the current state is RawState, and transition state is TestUnlocked0, and if the
  input token is correct, expect the transition to be successful.
- Check status and volatile_raw_unlock output.
- If the raw unlock transition is successful, check the second lc_transition can be
  performed without any error.

**Checks if the feature is disabled in HW**:

- Check that the volatile_raw_unlock CSR stays at 0
- Check that the transition command fails with a token error
  (a real unlock transition expects the unhashed token instead of the hashed one).


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#lc_ctrl_volatile_unlock_smoke">lc_ctrl_volatile_unlock_smoke</a></td>
  <td><a href="01_feature_report.md#lc_ctrlaccessjtag">LC_CTRL.ACCESS.JTAG</a><br><a href="01_feature_report.md#lc_ctrlauthenticated_transitions">LC_CTRL.AUTHENTICATED_TRANSITIONS</a><br><a href="01_feature_report.md#lc_ctrlstateraw">LC_CTRL.STATE.RAW</a><br><a href="01_feature_report.md#lc_ctrlstatetest_unlocked">LC_CTRL.STATE.TEST_UNLOCKED</a></td>
</tr>
  </tbody>
</table>

## lc_errors

This test randomly executes the error scenarios:

- otp_ctrl input lc_trans_cnt reaches 16
- lc_ctrl state transition request is invalid
- input LC token does not match the output from otp_ctrl
- flash rma responses to lc_ctrl request with error
- lc_ctrl clock bypass responses with error
- input otp_lc_data's error bit is set to 1

Note that all the above scenarios except the last one requires a reset to recover.

**Checks**:

- Check if status register reflects the correct error bit.
- Check if lc_state moves to correct exit state.
- Check if lc_trans_cnt is incremented.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#lc_ctrl_errors">lc_ctrl_errors</a></td>
  <td><a href="01_feature_report.md#lc_ctrlauthenticated_transitions">LC_CTRL.AUTHENTICATED_TRANSITIONS</a></td>
</tr>
  </tbody>
</table>

## lc_prog_failure

This test checks lc_program failure by setting the error bit after otp program request.

**Checks**:

- Check if status register reflects the correct error bit.
- Check if lc_program_failure alert is triggered.
- Check if lc_state moves to escalation state.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#lc_ctrl_prog_failure">lc_ctrl_prog_failure</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## lc_state_failure

This test checks lc_state failure by:

- Driving invalid data to lc_ctrl input `otp_lc_data_i` fields `lc_state` and `lc_cnt`.
- Backdoor changing lc_ctrl FSM's to invalid value.

For invalid value, the testbench will test using random value and valid `A/B/C/D`
values with different orders.

**Checks**:

- Check if status register reflects the correct error bit.
- Check if lc_state_failure alert is triggered.
- Check if lc_state moves to escalation state.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#lc_ctrl_state_failure">lc_ctrl_state_failure</a></td>
  <td><a href="01_feature_report.md#lc_ctrllogical_scrap">LC_CTRL.LOGICAL_SCRAP</a></td>
</tr>
  </tbody>
</table>

## rand_wr_claim_transition_if

`claim_transition_if` only accept `Mubi8True` or 0 value.
This test will write random value to this register.
**Checks**:

- When write value `Mubi8True` to `claim_transition_if` register, the
  `transition_regwen` is set to 1.
- When write any other value to `claim_transition_if` register, the `transition_regwen`
  register remains value 0.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#lc_ctrl_claim_transition_if">lc_ctrl_claim_transition_if</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## regwen_during_op

`Transition_regwen` is RO register and it gates bunch of write access of other
registers.

**Checks**:

- Check `transition_regwen` register is set to 1 during lc_state transition request.
- Check that accessing its locked CSRs is gated during the transition operation.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#lc_ctrl_regwen_during_op">lc_ctrl_regwen_during_op</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## security_escalation

This test checks two security escalation responses:

- wipe secrets: permanently asserts lc_escalate_en signal
- scrap state: lc_ctrl moves to escalation state, check the state will be cleared up
  upon next power cycle


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#lc_ctrl_errors">lc_ctrl_errors</a><br><a href="03_test_report.md#lc_ctrl_jtag_errors">lc_ctrl_jtag_errors</a><br><a href="03_test_report.md#lc_ctrl_jtag_prog_failure">lc_ctrl_jtag_prog_failure</a><br><a href="03_test_report.md#lc_ctrl_jtag_state_failure">lc_ctrl_jtag_state_failure</a><br><a href="03_test_report.md#lc_ctrl_prog_failure">lc_ctrl_prog_failure</a><br><a href="03_test_report.md#lc_ctrl_security_escalation">lc_ctrl_security_escalation</a><br><a href="03_test_report.md#lc_ctrl_state_failure">lc_ctrl_state_failure</a></td>
  <td><a href="01_feature_report.md#lc_ctrllogical_scrap">LC_CTRL.LOGICAL_SCRAP</a></td>
</tr>
  </tbody>
</table>

## smoke

Smoke test accessing lc_ctrl state transition datapath.

**Stimulus**:

- Initialize lc_ctrl by sending pwrmgr req and otp_ctrl valid random data.
- Request a valid next LC state by writing CSRs: `transition_target`,
  `transition_token*`, and `transition_cmd`.

**Checks**:

- After lc_ctrl initialization finishes, check lc_ctrl broadcast outputs, check
  the value of lc_state and lc_transition_cnt CSRs, and check device_id and id_state
  CSRs.
- After lc_ctrl state transition request, check status to ensure the transition is
  valid and successful.
- Check token matching for both conditional and unconditional requests.
- Once the transition is successful, check lc_ctrl broadcast outputs are all turned
  off.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#lc_ctrl_smoke">lc_ctrl_smoke</a></td>
  <td><a href="01_feature_report.md#lc_ctrlauthenticated_transitions">LC_CTRL.AUTHENTICATED_TRANSITIONS</a><br><a href="01_feature_report.md#lc_ctrlstateraw">LC_CTRL.STATE.RAW</a><br><a href="01_feature_report.md#lc_ctrlstatetest_unlocked">LC_CTRL.STATE.TEST_UNLOCKED</a></td>
</tr>
  </tbody>
</table>

## state_post_trans

This test is based on smoke test.
After smoke sequence, this test adds additional lc_state transition request before
issuing reset. This should happen regardless if the transition is successful.
Use scoreboard to ensure lc_ctrl ignores this additional lc_state transition request
and check state count.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#lc_ctrl_state_post_trans">lc_ctrl_state_post_trans</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## stress_all


- Combine above sequences in one test to run sequentially, except csr sequence.
- Random selection of Tilelink or JTAG CSR for each sequence
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
  <td><a href="03_test_report.md#lc_ctrl_stress_all">lc_ctrl_stress_all</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>
