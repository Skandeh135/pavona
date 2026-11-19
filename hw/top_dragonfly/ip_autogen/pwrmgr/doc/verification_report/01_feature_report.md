# pwrmgr Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="pwrmgrclock_controlio_in_low_power">
      <td>PWRMGR.CLOCK_CONTROL.IO_IN_LOW_POWER</td>
      <td>Controls whether the IO clock remains active inlow power mode.</td>
    </tr>
    <tr id="pwrmgrclock_controlmain_in_low_power">
      <td>PWRMGR.CLOCK_CONTROL.MAIN_IN_LOW_POWER</td>
      <td>Controls whether the MAIN clock remains active inlow power mode.</td>
    </tr>
    <tr id="pwrmgrlow_powerdisable_power">
      <td>PWRMGR.LOW_POWER.DISABLE_POWER</td>
      <td>Controls whether power is turned off for non-AON domains whenin low power.</td>
    </tr>
    <tr id="pwrmgrlow_powerentry">
      <td>PWRMGR.LOW_POWER.ENTRY</td>
      <td>Controls of low power entry, and cases when low power isnot entered due to interrupts or specific units getting busy.</td>
    </tr>
    <tr id="pwrmgrlow_powerwakeup">
      <td>PWRMGR.LOW_POWER.WAKEUP</td>
      <td>Power manager can enable/disable wakeup requests from various modulesin low power mode.</td>
    </tr>
    <tr id="pwrmgrlow_powerwake_info">
      <td>PWRMGR.LOW_POWER.WAKE_INFO</td>
      <td>Record what caused the chip to wakeup from low power.</td>
    </tr>
    <tr id="pwrmgrresetcheck_rom_integrity">
      <td>PWRMGR.RESET.CHECK_ROM_INTEGRITY</td>
      <td>Wait for successful completion of ROM integrity checks.</td>
    </tr>
    <tr id="pwrmgrresetescalation_request">
      <td>PWRMGR.RESET.ESCALATION_REQUEST</td>
      <td>Trigger reset in response to incoming escalation requests.</td>
    </tr>
    <tr id="pwrmgrresetescalation_timeout">
      <td>PWRMGR.RESET.ESCALATION_TIMEOUT</td>
      <td>Trigger reset in response to non-responsive escalation network.</td>
    </tr>
    <tr id="pwrmgrresetmain_power_glitch_reset">
      <td>PWRMGR.RESET.MAIN_POWER_GLITCH_RESET</td>
      <td>Trigger reset in response to glitch in main power.</td>
    </tr>
    <tr id="pwrmgrresetndm_reset_request">
      <td>PWRMGR.RESET.NDM_RESET_REQUEST</td>
      <td>Trigger reset in response to RV_DM ndm reset.</td>
    </tr>
    <tr id="pwrmgrresetpor_request">
      <td>PWRMGR.RESET.POR_REQUEST</td>
      <td>Trigger reset in response to POR_N pin.</td>
    </tr>
    <tr id="pwrmgrresetrequest">
      <td>PWRMGR.RESET.REQUEST</td>
      <td>Power manager can enable/disable reset requests from various modules</td>
    </tr>
    <tr id="pwrmgrresetsw_rst_request">
      <td>PWRMGR.RESET.SW_RST_REQUEST</td>
      <td>Trigger reset in response to rstmgr's sw reset request.</td>
    </tr>
    <tr id="pwrmgrstartuplife_cycle_initialization">
      <td>PWRMGR.STARTUP.LIFE_CYCLE_INITIALIZATION</td>
      <td>Wait completion of Life Cycle initialization.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>PWRMGR.STARTUP.LIFE_CYCLE_INITIALIZATION</th>
    <th>PWRMGR.CLOCK_CONTROL.IO_IN_LOW_POWER</th>
    <th>PWRMGR.CLOCK_CONTROL.MAIN_IN_LOW_POWER</th>
    <th>PWRMGR.LOW_POWER.ENTRY</th>
    <th>PWRMGR.LOW_POWER.DISABLE_POWER</th>
    <th>PWRMGR.LOW_POWER.WAKEUP</th>
    <th>PWRMGR.LOW_POWER.WAKE_INFO</th>
    <th>PWRMGR.RESET.CHECK_ROM_INTEGRITY</th>
    <th>PWRMGR.RESET.REQUEST</th>
    <th>PWRMGR.RESET.ESCALATION_REQUEST</th>
    <th>PWRMGR.RESET.ESCALATION_TIMEOUT</th>
    <th>PWRMGR.RESET.SW_RST_REQUEST</th>
    <th>PWRMGR.RESET.MAIN_POWER_GLITCH_RESET</th>
    <th>PWRMGR.RESET.NDM_RESET_REQUEST</th>
    <th>PWRMGR.RESET.POR_REQUEST</th>
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
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#overall-sequencing">Overall Sequencing</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#slow-clock-domain-fsm">Slow Clock Domain FSM</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#slow-clock-domain-fsm">X</a></td>
    <td><a href="../theory_of_operation.md#slow-clock-domain-fsm">X</a></td>
    <td></td>
    <td><a href="../theory_of_operation.md#slow-clock-domain-fsm">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#slow-clock-domain-fsm">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#slow-sparse-fsm">Slow Sparse FSM</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#fast-clock-domain-fsm">Fast Clock Domain FSM</a></th>
    <td><a href="../theory_of_operation.md#fast-clock-domain-fsm">X</a></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#fast-clock-domain-fsm">X</a></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#fast-sparse-fsm">Fast Sparse FSM</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#rom-integrity-checks">ROM Integrity Checks</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#rom-integrity-checks">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#fall-through-handling">Fall Through Handling</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#fall-through-handling">X</a></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#abort-handling">Abort Handling</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#abort-handling">X</a></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#reset-request-handling">Reset Request Handling</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#reset-request-handling">X</a></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#reset-request-handling">X</a></td>
    <td></td>
    <td><a href="../theory_of_operation.md#reset-request-handling">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#power-manager-internal-reset-requests">Power Manager Internal Reset Requests</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#power-manager-internal-reset-requests">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#escalation-reset-request">Escalation Reset Request</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#escalation-reset-request">X</a></td>
    <td><a href="../theory_of_operation.md#escalation-reset-request">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#escalation-clock-timeout">Escalation Clock Timeout</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#escalation-clock-timeout">X</a></td>
    <td><a href="../theory_of_operation.md#escalation-clock-timeout">X</a></td>
    <td><a href="../theory_of_operation.md#escalation-clock-timeout">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#main-power-unstable-reset-requests">Main Power Unstable Reset Requests</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#main-power-unstable-reset-requests">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#main-power-unstable-reset-requests">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#reset-requests-received-during-other-states">Reset Requests Received During Other States</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#reset-requests-received-during-other-states">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#reset-recording">Reset Recording</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#reset-recording">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#wakeup-recording">Wakeup Recording</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#wakeup-recording">X</a></td>
    <td><a href="../theory_of_operation.md#wakeup-recording">X</a></td>
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
    <th><a href="../theory_of_operation.md#flash-handling">Flash Handling</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#power-up-handling">Power-Up Handling</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#power-down-handling">Power-Down Handling</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#flash-brownout-handling">Flash Brownout Handling</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#supported-low-power-modes">Supported Low Power Modes</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#deep-sleep-or-standby">Deep Sleep or Standby</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#deep-sleep-or-standby">X</a></td>
    <td><a href="../theory_of_operation.md#deep-sleep-or-standby">X</a></td>
    <td></td>
    <td><a href="../theory_of_operation.md#deep-sleep-or-standby">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#normal-sleep">Normal Sleep</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#normal-sleep">X</a></td>
    <td><a href="../theory_of_operation.md#normal-sleep">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#debug">Debug</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th>PWRMGR.STARTUP.LIFE_CYCLE_INITIALIZATION</th>
    <th>PWRMGR.CLOCK_CONTROL.IO_IN_LOW_POWER</th>
    <th>PWRMGR.CLOCK_CONTROL.MAIN_IN_LOW_POWER</th>
    <th>PWRMGR.LOW_POWER.ENTRY</th>
    <th>PWRMGR.LOW_POWER.DISABLE_POWER</th>
    <th>PWRMGR.LOW_POWER.WAKEUP</th>
    <th>PWRMGR.LOW_POWER.WAKE_INFO</th>
    <th>PWRMGR.RESET.CHECK_ROM_INTEGRITY</th>
    <th>PWRMGR.RESET.REQUEST</th>
    <th>PWRMGR.RESET.ESCALATION_REQUEST</th>
    <th>PWRMGR.RESET.ESCALATION_TIMEOUT</th>
    <th>PWRMGR.RESET.SW_RST_REQUEST</th>
    <th>PWRMGR.RESET.MAIN_POWER_GLITCH_RESET</th>
    <th>PWRMGR.RESET.NDM_RESET_REQUEST</th>
    <th>PWRMGR.RESET.POR_REQUEST</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#wakeup">wakeup</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#wakeup">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#wakeup">X</a></td>
    <td><a href="02_testpoint_report.md#wakeup">X</a></td>
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
    <th><a href="02_testpoint_report.md#control_clks">control_clks</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#control_clks">X</a></td>
    <td><a href="02_testpoint_report.md#control_clks">X</a></td>
    <td><a href="02_testpoint_report.md#control_clks">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#control_clks">X</a></td>
    <td><a href="02_testpoint_report.md#control_clks">X</a></td>
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
    <th><a href="02_testpoint_report.md#aborted_low_power">aborted_low_power</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#aborted_low_power">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#aborted_low_power">X</a></td>
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
    <th><a href="02_testpoint_report.md#reset">reset</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#reset">X</a></td>
    <td><a href="02_testpoint_report.md#reset">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#reset">X</a></td>
    <td><a href="02_testpoint_report.md#reset">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#main_power_glitch_reset">main_power_glitch_reset</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#main_power_glitch_reset">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#reset_wakeup_race">reset_wakeup_race</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#reset_wakeup_race">X</a></td>
    <td><a href="02_testpoint_report.md#reset_wakeup_race">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#reset_wakeup_race">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#lowpower_wakeup_race">lowpower_wakeup_race</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#lowpower_wakeup_race">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#lowpower_wakeup_race">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#disable_rom_integrity_check">disable_rom_integrity_check</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#disable_rom_integrity_check">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#escalation_timeout">escalation_timeout</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#escalation_timeout">X</a></td>
    <td></td>
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
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_pwrmgr_external_full_reset-dragonfly">chip_sw_pwrmgr_external_full_reset (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_external_full_reset-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_pwrmgr_random_sleep_all_wake_ups-dragonfly">chip_sw_pwrmgr_random_sleep_all_wake_ups (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_random_sleep_all_wake_ups-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_random_sleep_all_wake_ups-dragonfly">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_pwrmgr_normal_sleep_all_wake_ups-dragonfly">chip_sw_pwrmgr_normal_sleep_all_wake_ups (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_pwrmgr_deep_sleep_por_reset-dragonfly">chip_sw_pwrmgr_deep_sleep_por_reset (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_deep_sleep_por_reset-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_deep_sleep_por_reset-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_deep_sleep_por_reset-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_pwrmgr_normal_sleep_por_reset-dragonfly">chip_sw_pwrmgr_normal_sleep_por_reset (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_normal_sleep_por_reset-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_normal_sleep_por_reset-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_pwrmgr_deep_sleep_all_wake_ups-dragonfly">chip_sw_pwrmgr_deep_sleep_all_wake_ups (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_pwrmgr_deep_sleep_all_reset_reqs-dragonfly">chip_sw_pwrmgr_deep_sleep_all_reset_reqs (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_deep_sleep_all_reset_reqs-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_deep_sleep_all_reset_reqs-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_deep_sleep_all_reset_reqs-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_deep_sleep_all_reset_reqs-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_deep_sleep_all_reset_reqs-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_sensor_ctrl_deep_sleep_wake_up-dragonfly">chip_sw_sensor_ctrl_deep_sleep_wake_up (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_sensor_ctrl_deep_sleep_wake_up-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_sensor_ctrl_deep_sleep_wake_up-dragonfly">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_pwrmgr_normal_sleep_all_reset_reqs-dragonfly">chip_sw_pwrmgr_normal_sleep_all_reset_reqs (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_normal_sleep_all_reset_reqs-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_normal_sleep_all_reset_reqs-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_normal_sleep_all_reset_reqs-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_normal_sleep_all_reset_reqs-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_pwrmgr_wdog_reset-dragonfly">chip_sw_pwrmgr_wdog_reset (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_wdog_reset-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_pwrmgr_aon_power_glitch_reset-dragonfly">chip_sw_pwrmgr_aon_power_glitch_reset (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_pwrmgr_main_power_glitch_reset-dragonfly">chip_sw_pwrmgr_main_power_glitch_reset (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_pwrmgr_random_sleep_power_glitch_reset-dragonfly">chip_sw_pwrmgr_random_sleep_power_glitch_reset (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_pwrmgr_deep_sleep_power_glitch_reset-dragonfly">chip_sw_pwrmgr_deep_sleep_power_glitch_reset (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_pwrmgr_sleep_power_glitch_reset-dragonfly">chip_sw_pwrmgr_sleep_power_glitch_reset (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_pwrmgr_random_sleep_all_reset_reqs-dragonfly">chip_sw_pwrmgr_random_sleep_all_reset_reqs (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_random_sleep_all_reset_reqs-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_random_sleep_all_reset_reqs-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_random_sleep_all_reset_reqs-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_random_sleep_all_reset_reqs-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_random_sleep_all_reset_reqs-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_pwrmgr_sysrst_ctrl_reset-dragonfly">chip_sw_pwrmgr_sysrst_ctrl_reset (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_pwrmgr_b2b_sleep_reset_req-dragonfly">chip_sw_pwrmgr_b2b_sleep_reset_req (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_pwrmgr_sleep_disabled-dragonfly">chip_sw_pwrmgr_sleep_disabled (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_sleep_disabled-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_all_resets-dragonfly">chip_sw_all_resets (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_all_resets-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_all_resets-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_all_resets-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_all_resets-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_pwrmgr_escalation_reset-dragonfly">chip_sw_pwrmgr_escalation_reset (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwrmgr_escalation_reset-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>
</div>
</div>
