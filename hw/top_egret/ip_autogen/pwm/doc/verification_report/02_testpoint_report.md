# pwm Testpoint Report

## blink

Verify the blink mode of the PWM
by asserting the blink_en field in the PWM_PARAM register


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwm_rand_output">pwm_rand_output</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_pwm_smoketest (egret)
Verify that the PWM outputs correct wave.

- Program the PWM to output waves of 24hz, 48, 98hz.
- Program the duty cycle to 11%, 36%, 50%, 71%, and 91%.
- The test harness should check that the frequency and duty cycle is correct within a tolerance of 2%.


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
  <td><a href="01_feature_report.md#pwmclockdivider">PWM.CLOCKDIVIDER</a><br><a href="01_feature_report.md#pwmdutycycle">PWM.DUTYCYCLE</a></td>
</tr>
  </tbody>
</table>

## dutycycle

Verify different duty cycle settings in Pulse, Blink and Heart Beat mode.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwm_rand_output">pwm_rand_output</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## heartbeat

Verify the Heart Beat mode of the PWM
by asserting the blink_en and HTBT field in the PWM_PARAM register


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwm_rand_output">pwm_rand_output</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## heartbeat_wrap

Observe wrapping behaviour when doing heartbeat operation.

This will exercise saturation of the duty cycle value
(dc_htbt_q), which is clamped to [0, ffff].


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwm_heartbeat_wrap">pwm_heartbeat_wrap</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## lowpower

Verify the PWM can continue when the chip is in low power mode.
Stimulus:

  - start PWM on one or more channels
  - stop the TL UL clock

Checks:

  - Ensure pulses are still generated when in LP mode


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwm_rand_output">pwm_rand_output</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## multi_channel

Verifies that PWM correctly generates pulses on multiple channels concurrently


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwm_rand_output">pwm_rand_output</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## perf

Checking ip operation at min/max bandwidth

Stimulus:

  - Program timing registers (CLK_DIV, DC_RESN) to high/low values (slow/fast data rate)
  - Program other required registers for pwm operation
  - Start pwm channels

Checks:

  - Ensure the output pulses are correctly modulated for all channels


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwm_perf">pwm_perf</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## phase

Check that the relative phase between pulses matches the setting in the phase_delay field in the PWM_PARAM register.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwm_phase">pwm_phase</a><br><a href="03_test_report.md#pwm_rand_output">pwm_rand_output</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## polarity

Verify that the polarity of the pulse can be inverted by setting the invert channel bit in the invert register


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwm_rand_output">pwm_rand_output</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## pulse

Verify the pulse mode of the PWM
by de-asserting blink_en field in the PWM_PARAM register


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwm_rand_output">pwm_rand_output</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## regwen

Set the DUT operating with a configuration that produces clear variation on all of the PWM outputs.
Lock the configuration using REGWEN and then attempt to change the configuration.
The DUT, monitors and scoreboard should continue unaffected until the DUT is reset.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwm_regwen">pwm_regwen</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## resolution

Verify the PWM generates correct duty cycle for different resolution settings


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwm_rand_output">pwm_rand_output</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## smoke

pwm_smoke tests pulse and blink mode for a single channel

Stimulus:

  - configure the envionment for one PWM channel
  - program the duty cycle a and b values
  - configure  the ClkDiv and Resn

Checking:

  - ensure pulses are generated correctly in pulse or blink mode


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwm_smoke">pwm_smoke</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## stress_all

Combine above sequences in one test then randomly select for running

Stimulus:

  - Start sequences and randomly add reset between each sequence

Checking:

  - All sequences should be finished and checked by the scoreboard


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwm_stress_all">pwm_stress_all</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>
