# pwm Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="pwmblink">
      <td>PWM.BLINK</td>
      <td>Duty cycle switches between one programmable value and another.    </td>
    </tr>
    <tr id="pwmclockdivider">
      <td>PWM.CLOCKDIVIDER</td>
      <td>The duty cycles are set with counters, and a clock divider can be set to adjust the clock for all of these counters.    </td>
    </tr>
    <tr id="pwmdutycycle">
      <td>PWM.DUTYCYCLE</td>
      <td>The duty cycle of the generated pulse can be changed.    </td>
    </tr>
    <tr id="pwmheartbeat">
      <td>PWM.HEARTBEAT</td>
      <td>Duty cycle linearly increases from one programmable value to another.    </td>
    </tr>
    <tr id="pwmphasedelay">
      <td>PWM.PHASEDELAY</td>
      <td>Different PWM signals can be offset in phase.    </td>
    </tr>
    <tr id="pwmpolarity">
      <td>PWM.POLARITY</td>
      <td>PWM is active high by default, but this can be changed.    </td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
IP pwm currently contains no **Feature → Specification** mapping

## Feature -> Testpoint Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Testpoints↓ : Features→</th>
    <th>PWM.DUTYCYCLE</th>
    <th>PWM.BLINK</th>
    <th>PWM.HEARTBEAT</th>
    <th>PWM.POLARITY</th>
    <th>PWM.CLOCKDIVIDER</th>
    <th>PWM.PHASEDELAY</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dutycycle">dutycycle</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#pulse">pulse</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#blink">blink</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#heartbeat">heartbeat</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#resolution">resolution</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#multi_channel">multi_channel</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#polarity">polarity</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#phase">phase</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#lowpower">lowpower</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#heartbeat_wrap">heartbeat_wrap</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#perf">perf</a></th>
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
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_pwm_smoketest-egret">chip_sw_pwm_smoketest (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_pwm_smoketest-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_pwm_smoketest-egret">X</a></td>
    <td></td>
  </tr>
</table>
</div>
</div>
