# adc_ctrl Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="adc_ctrlmodelow_power">
      <td>ADC_CTRL.MODE.LOW_POWER</td>
      <td>During low-power mode, the ADC controller is intermittently activated to capture samples.When the number of samples acquired and processed by the filter matches the predefined value set in adc_ctrl.ADC_LP_SAMPLE_CTL, the controller switches to normal operation mode.</td>
    </tr>
    <tr id="adc_ctrlmodenormal">
      <td>ADC_CTRL.MODE.NORMAL</td>
      <td>In this mode, the ADC will always be enabled and consuming power.Use when fast sampling is required.</td>
    </tr>
    <tr id="adc_ctrloneshot">
      <td>ADC_CTRL.ONESHOT</td>
      <td>When the controller is set to oneshot mode, it waits for a high value (1) from both channel 0 and channel 1, sequentially.Once it detects these high values from both channels, it proceeds to set adc_ctrl.ADC_INTR_STATUS.ONESHOT and returns to a powered-off state, without evaluating the filters.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
IP adc_ctrl currently contains no **Feature → Specification** mapping

## Feature -> Testpoint Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Testpoints↓ : Features→</th>
    <th>ADC_CTRL.MODE.NORMAL</th>
    <th>ADC_CTRL.MODE.LOW_POWER</th>
    <th>ADC_CTRL.ONESHOT</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#filters_polled">filters_polled</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#filters_polled_fixed">filters_polled_fixed</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#filters_interrupt">filters_interrupt</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#filters_interrupt_fixed">filters_interrupt_fixed</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#filters_wakeup">filters_wakeup</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#filters_wakeup_fixed">filters_wakeup_fixed</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#filters_both">filters_both</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#clock_gating">clock_gating</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#poweron_counter">poweron_counter</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#lowpower_counter">lowpower_counter</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#fsm_reset">fsm_reset</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#stress_all">stress_all</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_adc_ctrl_debug_cable_irq-egret">chip_sw_adc_ctrl_debug_cable_irq (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_adc_ctrl_debug_cable_irq-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_adc_ctrl_sleep_debug_cable_wakeup-egret">chip_sw_adc_ctrl_sleep_debug_cable_wakeup (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_adc_ctrl_sleep_debug_cable_wakeup-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_adc_ctrl_normal-egret">chip_sw_adc_ctrl_normal (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_adc_ctrl_normal-egret">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_adc_ctrl_oneshot-egret">chip_sw_adc_ctrl_oneshot (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_adc_ctrl_oneshot-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_adc_ctrl_oneshot-egret">X</a></td>
  </tr>
</table>
</div>
</div>
