# clkmgr Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="clkmgralert_handlerclock_status">
      <td>CLKMGR.ALERT_HANDLER.CLOCK_STATUS</td>
      <td>Inform alert handler about clock enable status for each clock.</td>
    </tr>
    <tr id="clkmgrenableperiph_clk">
      <td>CLKMGR.ENABLE.PERIPH_CLK</td>
      <td>Clock manager supports the gating of clocks to peripheral devices</td>
    </tr>
    <tr id="clkmgrhinttrans_clk">
      <td>CLKMGR.HINT.TRANS_CLK</td>
      <td>Clock manager is able to suggest (hint) that transactional   modules (such as hmac or aes) manipulate their clocks. This   suggestion is carried forwards when the module in question   completes any ongoing transactional tasks</td>
    </tr>
    <tr id="clkmgrjitterenable">
      <td>CLKMGR.JITTER.ENABLE</td>
      <td>Enable clock jitter.</td>
    </tr>
    <tr id="clkmgrjitterregwen">
      <td>CLKMGR.JITTER.REGWEN</td>
      <td>Control modification of clock jitter enable.</td>
    </tr>
    <tr id="clkmgrmeas_ctrlrecov_err">
      <td>CLKMGR.MEAS_CTRL.RECOV_ERR</td>
      <td>Clock manager's frequency and timeout measurementscan flag recoverable errors.</td>
    </tr>
    <tr id="clkmgrmeas_ctrlregwen">
      <td>CLKMGR.MEAS_CTRL.REGWEN</td>
      <td>All of clock manager's frequency and timeout measurements can bemodified via the `MEASURE_CTRL_REGWEN` control register.</td>
    </tr>
    <tr id="clkmgrmeas_ctrlrg_src">
      <td>CLKMGR.MEAS_CTRL.RG_SRC</td>
      <td>Clock manager supports frequency and timeout measurementsof root-gated clock sources</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>CLKMGR.ENABLE.PERIPH_CLK</th>
    <th>CLKMGR.HINT.TRANS_CLK</th>
    <th>CLKMGR.MEAS_CTRL.REGWEN</th>
    <th>CLKMGR.MEAS_CTRL.RG_SRC</th>
    <th>CLKMGR.MEAS_CTRL.RECOV_ERR</th>
    <th>CLKMGR.JITTER.REGWEN</th>
    <th>CLKMGR.JITTER.ENABLE</th>
    <th>CLKMGR.ALERT_HANDLER.CLOCK_STATUS</th>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#theory-of-operation">Theory of Operation</a></th>
    <td><a href="../theory_of_operation.md#theory-of-operation">X</a></td>
    <td><a href="../theory_of_operation.md#theory-of-operation">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#power-up-clock-group">Power-up Clock Group</a></th>
    <td><a href="../theory_of_operation.md#power-up-clock-group">X</a></td>
    <td><a href="../theory_of_operation.md#power-up-clock-group">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#transactional-clock-group">Transactional Clock Group</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#transactional-clock-group">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#infrastructure-clock-group">Infrastructure Clock Group</a></th>
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
    <th><a href="../theory_of_operation.md#security-clock-group">Security Clock Group</a></th>
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
    <th><a href="../theory_of_operation.md#timer-clock-group">Timer Clock Group</a></th>
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
    <th><a href="../theory_of_operation.md#peripheral-clock-group">Peripheral Clock Group</a></th>
    <td><a href="../theory_of_operation.md#peripheral-clock-group">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#wait-for-interrupt-wfi-gating">Wait-for-Interrupt (`wfi`) Gating</a></th>
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
    <th><a href="../theory_of_operation.md#transactional-clock-group-wfi-gating">Transactional Clock Group `wfi` Gating</a></th>
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
    <th><a href="../theory_of_operation.md#peripheral-clock-group-wfi-gating">Peripheral Clock Group `wfi` Gating</a></th>
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
    <th><a href="../theory_of_operation.md#infrastructural-clock-group-wfi-gating">Infrastructural Clock Group `wfi` Gating</a></th>
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
    <th><a href="../theory_of_operation.md#clock-jitter">Clock Jitter</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#clock-jitter">X</a></td>
    <td><a href="../theory_of_operation.md#clock-jitter">X</a></td>
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
    <th><a href="../theory_of_operation.md#reset-domains">Reset Domains</a></th>
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
    <th><a href="../theory_of_operation.md#clock-gated-indications-for-alert-handler">Clock Gated Indications for Alert Handler</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#clock-gated-indications-for-alert-handler">X</a></td>
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
    <th><a href="../theory_of_operation.md#root-clock-gating-and-interface-with-power-manager">Root Clock Gating and Interface with Power Manager</a></th>
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
    <th><a href="../theory_of_operation.md#clock-division">Clock Division</a></th>
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
    <th><a href="../theory_of_operation.md#wait-for-interrupt-support">Wait-for-Interrupt Support</a></th>
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
    <th><a href="../theory_of_operation.md#external-clock-switch-support">External Clock Switch Support</a></th>
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
    <th><a href="../theory_of_operation.md#clock-frequency-measurements">Clock Frequency Measurements</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#clock-frequency-measurements">X</a></td>
    <td><a href="../theory_of_operation.md#clock-frequency-measurements">X</a></td>
    <td><a href="../theory_of_operation.md#clock-frequency-measurements">X</a></td>
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
    <th>CLKMGR.ENABLE.PERIPH_CLK</th>
    <th>CLKMGR.HINT.TRANS_CLK</th>
    <th>CLKMGR.MEAS_CTRL.REGWEN</th>
    <th>CLKMGR.MEAS_CTRL.RG_SRC</th>
    <th>CLKMGR.MEAS_CTRL.RECOV_ERR</th>
    <th>CLKMGR.JITTER.REGWEN</th>
    <th>CLKMGR.JITTER.ENABLE</th>
    <th>CLKMGR.ALERT_HANDLER.CLOCK_STATUS</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#peri_enables">peri_enables</a></th>
    <td><a href="02_testpoint_report.md#peri_enables">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#trans_enables">trans_enables</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#trans_enables">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#clk_status">clk_status</a></th>
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
    <th><a href="02_testpoint_report.md#jitter">jitter</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#jitter">X</a></td>
    <td><a href="02_testpoint_report.md#jitter">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#frequency">frequency</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#frequency">X</a></td>
    <td><a href="02_testpoint_report.md#frequency">X</a></td>
    <td><a href="02_testpoint_report.md#frequency">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#frequency_timeout">frequency_timeout</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#frequency_timeout">X</a></td>
    <td><a href="02_testpoint_report.md#frequency_timeout">X</a></td>
    <td><a href="02_testpoint_report.md#frequency_timeout">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#frequency_overflow">frequency_overflow</a></th>
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
    <th><a href="02_testpoint_report.md#regwen">regwen</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#regwen">X</a></td>
    <td></td>
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
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_clkmgr_idle_trans-dragonfly">chip_sw_clkmgr_idle_trans (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_clkmgr_idle_trans-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_clkmgr_off_trans-dragonfly">chip_sw_clkmgr_off_trans (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_clkmgr_off_trans-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_clkmgr_off_peri-dragonfly">chip_sw_clkmgr_off_peri (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_clkmgr_off_peri-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_clkmgr_div-dragonfly">chip_sw_clkmgr_div (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_clkmgr_div-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_clkmgr_div-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_clkmgr_external_clk_src_for_lc-dragonfly">chip_sw_clkmgr_external_clk_src_for_lc (dragonfly)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_clkmgr_external_clk_src_for_sw-dragonfly">chip_sw_clkmgr_external_clk_src_for_sw (dragonfly)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_clkmgr_jitter-dragonfly">chip_sw_clkmgr_jitter (dragonfly)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_clkmgr_jitter_cycle_measurements-dragonfly">chip_sw_clkmgr_jitter_cycle_measurements (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_clkmgr_jitter_cycle_measurements-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_clkmgr_jitter_cycle_measurements-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_clkmgr_jitter_cycle_measurements-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_clkmgr_jitter_cycle_measurements-dragonfly">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_clkmgr_extended_range-dragonfly">chip_sw_clkmgr_extended_range (dragonfly)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_clkmgr_deep_sleep_frequency-dragonfly">chip_sw_clkmgr_deep_sleep_frequency (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_clkmgr_deep_sleep_frequency-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_clkmgr_deep_sleep_frequency-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_clkmgr_deep_sleep_frequency-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_clkmgr_sleep_frequency-dragonfly">chip_sw_clkmgr_sleep_frequency (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_clkmgr_sleep_frequency-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_clkmgr_sleep_frequency-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_clkmgr_sleep_frequency-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_clkmgr_reset_frequency-dragonfly">chip_sw_clkmgr_reset_frequency (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_clkmgr_reset_frequency-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_clkmgr_reset_frequency-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_clkmgr_reset_frequency-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_clkmgr_escalation_reset-dragonfly">chip_sw_clkmgr_escalation_reset (dragonfly)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_clkmgr_alert_handler_clock_enables-dragonfly">chip_sw_clkmgr_alert_handler_clock_enables (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_clkmgr_alert_handler_clock_enables-dragonfly">X</a></td>
  </tr>
</table>
</div>
</div>
