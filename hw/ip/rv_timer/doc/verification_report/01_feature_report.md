# rv_timer Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="rv_timercompare">
      <td>RV_TIMER.COMPARE</td>
      <td>The timer has a 64-bit compare register that triggers an interrupt when it matches the counter.</td>
    </tr>
    <tr id="rv_timerconfig">
      <td>RV_TIMER.CONFIG</td>
      <td>Configures the tick period.</td>
    </tr>
    <tr id="rv_timercounter">
      <td>RV_TIMER.COUNTER</td>
      <td>The timer has a 64-bit counter that wraps.</td>
    </tr>
    <tr id="rv_timerdisable">
      <td>RV_TIMER.DISABLE</td>
      <td>Disable timer with CTRL CSR.</td>
    </tr>
    <tr id="rv_timerenable">
      <td>RV_TIMER.ENABLE</td>
      <td>Enable timer with CTRL CSR.</td>
    </tr>
    <tr id="rv_timerinterrupt">
      <td>RV_TIMER.INTERRUPT</td>
      <td>The timer triggers interrupts when the counter register matches the compare register.</td>
    </tr>
    <tr id="rv_timerriscv_csrs_integration">
      <td>RV_TIMER.RISCV_CSRS_INTEGRATION</td>
      <td>The RV_TIMER block is integrated with the RISC-V CSRs `mtime` and `mtimecmp`.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
IP rv_timer currently contains no **Feature → Specification** mapping

## Feature -> Testpoint Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Testpoints↓ : Features→</th>
    <th>RV_TIMER.RISCV_CSRS_INTEGRATION</th>
    <th>RV_TIMER.ENABLE</th>
    <th>RV_TIMER.DISABLE</th>
    <th>RV_TIMER.INTERRUPT</th>
    <th>RV_TIMER.CONFIG</th>
    <th>RV_TIMER.COUNTER</th>
    <th>RV_TIMER.COMPARE</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#random">random</a></th>
    <td><a href="02_testpoint_report.md#random">X</a></td>
    <td><a href="02_testpoint_report.md#random">X</a></td>
    <td><a href="02_testpoint_report.md#random">X</a></td>
    <td><a href="02_testpoint_report.md#random">X</a></td>
    <td><a href="02_testpoint_report.md#random">X</a></td>
    <td><a href="02_testpoint_report.md#random">X</a></td>
    <td><a href="02_testpoint_report.md#random">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#random_reset">random_reset</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#disabled">disabled</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#disabled">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#cfg_update_on_fly">cfg_update_on_fly</a></th>
    <td><a href="02_testpoint_report.md#cfg_update_on_fly">X</a></td>
    <td><a href="02_testpoint_report.md#cfg_update_on_fly">X</a></td>
    <td><a href="02_testpoint_report.md#cfg_update_on_fly">X</a></td>
    <td><a href="02_testpoint_report.md#cfg_update_on_fly">X</a></td>
    <td><a href="02_testpoint_report.md#cfg_update_on_fly">X</a></td>
    <td><a href="02_testpoint_report.md#cfg_update_on_fly">X</a></td>
    <td><a href="02_testpoint_report.md#cfg_update_on_fly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#no_interrupt_test">no_interrupt_test</a></th>
    <td><a href="02_testpoint_report.md#no_interrupt_test">X</a></td>
    <td><a href="02_testpoint_report.md#no_interrupt_test">X</a></td>
    <td><a href="02_testpoint_report.md#no_interrupt_test">X</a></td>
    <td><a href="02_testpoint_report.md#no_interrupt_test">X</a></td>
    <td><a href="02_testpoint_report.md#no_interrupt_test">X</a></td>
    <td><a href="02_testpoint_report.md#no_interrupt_test">X</a></td>
    <td><a href="02_testpoint_report.md#no_interrupt_test">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#min_value">min_value</a></th>
    <td><a href="02_testpoint_report.md#min_value">X</a></td>
    <td><a href="02_testpoint_report.md#min_value">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#min_value">X</a></td>
    <td><a href="02_testpoint_report.md#min_value">X</a></td>
    <td><a href="02_testpoint_report.md#min_value">X</a></td>
    <td><a href="02_testpoint_report.md#min_value">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#max_value">max_value</a></th>
    <td><a href="02_testpoint_report.md#max_value">X</a></td>
    <td><a href="02_testpoint_report.md#max_value">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#max_value">X</a></td>
    <td><a href="02_testpoint_report.md#max_value">X</a></td>
    <td><a href="02_testpoint_report.md#max_value">X</a></td>
    <td><a href="02_testpoint_report.md#max_value">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#stress">stress</a></th>
    <td><a href="02_testpoint_report.md#stress">X</a></td>
    <td><a href="02_testpoint_report.md#stress">X</a></td>
    <td><a href="02_testpoint_report.md#stress">X</a></td>
    <td><a href="02_testpoint_report.md#stress">X</a></td>
    <td><a href="02_testpoint_report.md#stress">X</a></td>
    <td><a href="02_testpoint_report.md#stress">X</a></td>
    <td><a href="02_testpoint_report.md#stress">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_timer-dragonfly">chip_sw_timer (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_timer-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_timer-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_timer-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_timer-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_timer-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_timer-egret">chip_sw_timer (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_timer-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_timer-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_timer-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_timer-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_timer-egret">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#tick_configuration-egret">tick_configuration (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#tick_configuration-egret">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#tick_configuration-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#tick_configuration-egret">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#counter_wrap-egret">counter_wrap (egret)</a></th>
    <td><a href="02_testpoint_report.md#counter_wrap-egret">X</a></td>
    <td><a href="02_testpoint_report.md#counter_wrap-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#counter_wrap-egret">X</a></td>
    <td><a href="02_testpoint_report.md#counter_wrap-egret">X</a></td>
    <td><a href="02_testpoint_report.md#counter_wrap-egret">X</a></td>
    <td><a href="02_testpoint_report.md#counter_wrap-egret">X</a></td>
  </tr>
</table>
</div>
</div>
