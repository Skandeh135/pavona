# adc_ctrl Testpoint Report

## chip_sw_adc_ctrl_debug_cable_irq (egret)
Verify that the ADC correctly detects the voltage level programmed for each channel.

- Program both ADC channels to detect mutually exclusive range of voltages. Setting only
  one filter CSR is sufficient.
- Program the ADC intr ctrl CSR to detect the selected filter on both channels.
  Enable the debug cable interrupt at ADC ctrl as well as PLIC.
- Enable the ADC ctrl to run with defaults in normal mode (depending on simulation
  runtime).
- Verify through assertion checks, the ADC with AST stays powered down periodically in
  slow scan mode.
- After some time, force the ADC output of AST to be a value within the programmed range
  for each channel. Glitch it out of range for some time before stabilizing to ensure
  that debounce logic works.
- Service the debug cable irq. Read the intr status register to verify that the selected
  filter caused the interrupt to fire. Read the ADC channel value register to verify the
  correctness of the detected value that was forced in the AST for each channel.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_adc_ctrl_sleep_debug_cable_wakeup-egret">chip_sw_adc_ctrl_sleep_debug_cable_wakeup (egret)</a></td>
  <td><a href="01_feature_report.md#adc_ctrlmodelow_power">ADC_CTRL.MODE.LOW_POWER</a></td>
</tr>
  </tbody>
</table>

## chip_sw_adc_ctrl_normal (egret)
Verify that ADC can sample from channel 0 and 1 in normal mode.


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
  <td><a href="01_feature_report.md#adc_ctrlmodenormal">ADC_CTRL.MODE.NORMAL</a></td>
</tr>
  </tbody>
</table>

## chip_sw_adc_ctrl_oneshot (egret)
Verify that ADC can sample from channel 0 and 1 in normal mode with oneshot filter config.


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
  <td><a href="01_feature_report.md#adc_ctrlmodenormal">ADC_CTRL.MODE.NORMAL</a><br><a href="01_feature_report.md#adc_ctrloneshot">ADC_CTRL.ONESHOT</a></td>
</tr>
  </tbody>
</table>

## chip_sw_adc_ctrl_sleep_debug_cable_wakeup (egret)
Verify that in deep sleep, ADC ctrl can signal the ADC within the AST to power down.

- Read the reset cause register in rstmgr to confirm we are in POR reset phase.
- Follow the same steps as chip_adc_ctrl_debug_cable_irq, but instead of programming the
  selected filter to interrupt, program it to wake up the chip from sleep.
- Program the pwrmgr to put the chip in deep sleep state and wake up on debug cable
  detection.
- Issue a WFI to bring the chip in low power state.
- After some time, force the ADC output of AST to be a value within the programmed
  filter range. That should cause the pwrmgr to wake up.
- Read the reset cause register to confirm wake up from low power exit phase.
- Read the pwrmgr wake up status register to confirm wake up was due to debug cable
  detection.
- Read the ADC channel value register to verify the correctness of the detected value
  that was forced in the AST.
- Repeat for both ADC channels.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_adc_ctrl_sleep_debug_cable_wakeup-egret">chip_sw_adc_ctrl_sleep_debug_cable_wakeup (egret)</a></td>
  <td><a href="01_feature_report.md#adc_ctrlmodelow_power">ADC_CTRL.MODE.LOW_POWER</a></td>
</tr>
  </tbody>
</table>

## clock_gating

Verify filter wakeup and interrupts function correctly when fast clock is
turned off as would occur in the system.

**Stimulus**:

For a number of iterations:

- Configure DUT with randomized filter parameters, filters,
  interrupt and wakeup enabled, low power sampling mode.
- Turn off fast clock.
- Generate ADC data stream.
- When wakeup occurs after a further random period turn fast clock back on.

**Checks**:

- From monitored ADC data predict when filters should be triggered.
- Confirm this by reading the filter status register and interrupt status register.
- Check wakeup signal operates as expected.
- Check interrupt signal operates as expected.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#adc_ctrl_clock_gating">adc_ctrl_clock_gating</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## filters_both

Verify filter wakeup and interrupt function correctly together.

**Stimulus**:

For a number of iterations:

- Configure DUT with randomized filter parameters, filters,
  interrupt and wakeup enabled, randomized low/high power sampling mode.
- Generate ADC data stream.

**Checks**:

- From monitored ADC data predict when filters should be triggered.
- Confirm this by reading the filter status register and interrupt status register.
- Check wakeup signal operates as expected.
- Check interrupt signal operates as expected.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#adc_ctrl_filters_both">adc_ctrl_filters_both</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## filters_interrupt

Verify filter interrupt functionality.

**Stimulus**:

For a number of iterations:

- Configure DUT with randomized filter parameters, filters and interrupts enabled.
- Generate ADC data stream.


**Checks**:

- From monitored ADC data predict when filters should be triggered.
- Confirm this by reading the filter status register and interrupt status register.
- Confirm correct interrupt sample value has been captured in ADC sample registers(s).
- Check interrupt signal operates as expected.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#adc_ctrl_filters_interrupt">adc_ctrl_filters_interrupt</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## filters_interrupt_fixed

As filters_interrupt but with filter parameters fixed during the test.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#adc_ctrl_filters_interrupt_fixed">adc_ctrl_filters_interrupt_fixed</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## filters_polled

Verify filter functionality by polling filter status register.

**Stimulus**:

For a number of iterations:

- Configure DUT with randomized filter parameters, filters enabled
  but no interrupts or wake events.
- Generate ADC data stream.

**Checks**:

- From monitored ADC data predict when filters should be triggered.
- Confirm this by reading the filter status register.
- Ensure that only one ADC channel is selected at a time.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#adc_ctrl_filters_polled">adc_ctrl_filters_polled</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## filters_polled_fixed

As filters_polled but with filter parameters fixed during the test.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#adc_ctrl_filters_polled_fixed">adc_ctrl_filters_polled_fixed</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## filters_wakeup

Verify filter wakeup functionality.

**Stimulus**:
For a number of iterations:

- Configure DUT with randomized filter parameters,
  filters and wakeup enabled, low power sampling mode.
- Generate ADC data stream.

**Checks**:

- From monitored ADC data predict when filters should be triggered.
- Confirm this by reading the filter status register.
- Check wakeup signal operates as expected.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#adc_ctrl_filters_wakeup">adc_ctrl_filters_wakeup</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## filters_wakeup_fixed

As filters_wakeup but with filter parameters fixed during the test.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#adc_ctrl_filters_wakeup_fixed">adc_ctrl_filters_wakeup_fixed</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## fsm_reset

Verify ADC controller FSM software reset.

**Stimulus**:

For a number of iterations:

- Configure DUT with a random low power sample count.
- Enable ADC randomly in low or high power mode.
- Generate ADC data stream.
- Trigger a software reset by writing to adc_fsm_rst register.

**Checks**:

- Ensure ADC controller FSM and counters are reset.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#adc_ctrl_fsm_reset">adc_ctrl_fsm_reset</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## lowpower_counter

Verify ADC low power counter.

**Stimulus**:

For a number of iterations:

- Configure DUT with a random low power sample count.
- Enable ADC in low power mode.
- Generate ADC data stream.

**Checks**:

- Confirm return to fast sampling happens as expected.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#adc_ctrl_lowpower_counter">adc_ctrl_lowpower_counter</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## poweron_counter

Verify ADC power on counter.

**Stimulus**:

For a number of iterations:

- Configure DUT with a random ADC power on count.
- Enable ADC.
- Generate ADC data stream.

**Checks**:

- Confirm timing of power down and channel select signals to ADC.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#adc_ctrl_poweron_counter">adc_ctrl_poweron_counter</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## smoke

Verify datapath between AST ADC interface and ADC sample registers.

**Stimulus**:

For a number of iterations:

- Configure DUT no filters or events.
- Generate ADC data.
- Sample into capture registers using oneshot mode.

**Checks:**

- From monitored ADC data predict the value of the ADC sample register.
- Compare sample registers against expected.
- Check oneshot bit of interrupt status register works as expected.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#adc_ctrl_smoke">adc_ctrl_smoke</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## stress_all

Combine above sequences in one test then randomly select for running.

Stimulus:

  - Start sequences and randomly add reset between each sequence.

Checking:

  - All sequences should be finished and checked by the scoreboard.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#adc_ctrl_stress_all">adc_ctrl_stress_all</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>
