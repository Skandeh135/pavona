# alert_handler Testpoint Report

## alert_handler_alert_accum_saturation

This sequence forces all four alert classes' accumulate counters to a large value that
is close to the max saturation value.
Then the sequence triggers alerts until the count saturates.

Checks:

- Check `accum_cnt` register does not overflow, but stays at the max value.
- Check the correct interrupt fires if even the count saturates.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#alert_handler_alert_accum_saturation">alert_handler_alert_accum_saturation</a></td>
  <td><a href="01_feature_report.md#alert_handleralertescalate">ALERT_HANDLER.ALERT.ESCALATE</a><br><a href="01_feature_report.md#alert_handleralertinterrupt">ALERT_HANDLER.ALERT.INTERRUPT</a><br><a href="01_feature_report.md#alert_handlerescalationcount">ALERT_HANDLER.ESCALATION.COUNT</a></td>
</tr>
  </tbody>
</table>

## alert_handler_entropy_stress_test

Stress the alert_handler's entropy request and make sure there is no spurious alert.

Stimulus:

- Randomly force the `wait_cyc_mask_i` to a legal value to stress the ping requests.
- Wait for all alerts at least being pinged for a few times.

Checks:

- Check alert_cause and loc_alert_cause registers to make sure there is no spurious
  alert being fired.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#alert_handler_entropy_stress">alert_handler_entropy_stress</a></td>
  <td><a href="01_feature_report.md#alert_handlerping_timer">ALERT_HANDLER.PING_TIMER</a></td>
</tr>
  </tbody>
</table>

## chip_sw_alert_handler_alerts (dragonfly)
Verify all alerts coming into the alert_handler.

An automated SW test, which does the following (applies to all alerts in all IPs):

- Program the alert_test CSR in each block to trigger each alert one by one.
- Ensure that all alerts are properly connected to the alert handler and cause the
  escalation paths to trigger.

Note for silicon validation:

- Ensure this test makes no alterations to OTP (use NMI escalation path).


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_alert_test-dragonfly">chip_sw_alert_test (dragonfly)</a></td>
  <td><a href="01_feature_report.md#alert_handleralertescalate">ALERT_HANDLER.ALERT.ESCALATE</a><br><a href="01_feature_report.md#alert_handleralertobserve">ALERT_HANDLER.ALERT.OBSERVE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_alert_handler_crashdump (dragonfly)
Verify the alert handler crashdump signal.

When the chip resets due to alert escalating to cause the chip to reset, verify the
reset cause to verify the alert crashdump.

Xref'ed with chip_sw_rstmgr_alert_info.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rstmgr_alert_info-dragonfly">chip_sw_rstmgr_alert_info (dragonfly)</a></td>
  <td><a href="01_feature_report.md#alert_handlercrash_dump">ALERT_HANDLER.CRASH_DUMP</a></td>
</tr>
  </tbody>
</table>

## chip_sw_alert_handler_entropy (dragonfly)
Verify the alert handler entropy input to ensure pseudo-random ping timer.

- Force `alert_handler_ping_timer` input signal `wait_cyc_mask_i` to `8'h07` to
  shorten the simulation time.
- Verify that the alert_handler can request EDN to provide entropy.
- Ensure that the alert ping handshake to all alert sources and escalation receivers
  complete without errors.

SiVal: This test is not necessary:

- We cannot explicitly detect an EDN request.
- There are plenty of tests checking ping behavior.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_alert_handler_entropy-dragonfly">chip_sw_alert_handler_entropy (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_alert_handler_escalation_methods (dragonfly)
Verify the different escalation trigger methods

For each escalation class, verify the escalation occurs (just the first stage, NMI
escalation) with all of the possible trigger methods.

- Escalation triggered when the number of alerts seen in the class is greater than the
  threshold
- Escalation triggered when initial interrupt isn't acknowledged within the timeout


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
  <td><a href="01_feature_report.md#alert_handlerescalationcount">ALERT_HANDLER.ESCALATION.COUNT</a><br><a href="01_feature_report.md#alert_handlerescalationtimeout">ALERT_HANDLER.ESCALATION.TIMEOUT</a></td>
</tr>
  </tbody>
</table>

## chip_sw_alert_handler_escalation_nmi_reset (dragonfly)
Verify NMI and reset alert escalation paths.

- Program the alert classes to only use escalation signals 0 and 3 (NMI interrupt and
  chip reset)
- Verify the first escalation of an alert results in NMI interrupt serviced by the CPU.
- Verify the second escalation of an alert results in a chip reset.
- It is critical this test does not trigger escalation signals 1 and 2 as these result
  in an OTP mutate that puts the chips in an unrecoverable SCRAP state.
- Verify any timer interrupts are disabled by escalation.
- Verify after the escalation reset all faults are cleared, and that the alert
  info captured the correct alert.
- Check that no additional resets occur.


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
  <td><a href="01_feature_report.md#alert_handleralertescalate">ALERT_HANDLER.ALERT.ESCALATE</a><br><a href="01_feature_report.md#alert_handlerescalationphases">ALERT_HANDLER.ESCALATION.PHASES</a></td>
</tr>
  </tbody>
</table>

## chip_sw_alert_handler_escalations (dragonfly)
Verify all alert escalation paths.

Verify all escalation paths triggered by an alert.

- Verify the first escalation results in NMI interrupt serviced by the CPU.
- Verify the second results in device being put in scrap state, via the LC JTAG TAP.
- Verify the third results in chip reset.
- Ensure that all escalation handshakes complete without errors.
  - This cannot be checked in sival as the handshake signals cannot
    be directly observed.


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
  <td><a href="01_feature_report.md#alert_handleralertescalate">ALERT_HANDLER.ALERT.ESCALATE</a><br><a href="01_feature_report.md#alert_handlerescalationphases">ALERT_HANDLER.ESCALATION.PHASES</a></td>
</tr>
  </tbody>
</table>

## chip_sw_alert_handler_irqs (dragonfly)
Verify all classes of alert handler interrupts to the CPU.

X-ref'ed with the automated PLIC test.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_plic_all_irqs_0-dragonfly">chip_plic_all_irqs_0 (dragonfly)</a><br><a href="03_test_report.md#chip_plic_all_irqs_10-dragonfly">chip_plic_all_irqs_10 (dragonfly)</a><br><a href="03_test_report.md#chip_plic_all_irqs_20-dragonfly">chip_plic_all_irqs_20 (dragonfly)</a></td>
  <td><a href="01_feature_report.md#alert_handleralertinterrupt">ALERT_HANDLER.ALERT.INTERRUPT</a></td>
</tr>
  </tbody>
</table>

## chip_sw_alert_handler_lpg_clock_off (dragonfly)
Verify alert_handler's works correctly when sender clock is turned off.

- Configure clkmgr to randomly turn off one of the IP's clock and check alert_handler
  won't trigger a ping timeout error on that block.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_alert_handler_lpg_clkoff-dragonfly">chip_sw_alert_handler_lpg_clkoff (dragonfly)</a></td>
  <td><a href="01_feature_report.md#alert_handlerping_timer">ALERT_HANDLER.PING_TIMER</a></td>
</tr>
  </tbody>
</table>

## chip_sw_alert_handler_lpg_reset_toggle (dragonfly)
Verify alert_handler's works correctly when sender reset is toggled.

- Configure rstmgr to randomly toggle one IP block's SW reset and check alert_handler
  won't trigger a ping timeout error on that block.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_alert_handler_lpg_reset_toggle-dragonfly">chip_sw_alert_handler_lpg_reset_toggle (dragonfly)</a></td>
  <td><a href="01_feature_report.md#alert_handlerping_timer">ALERT_HANDLER.PING_TIMER</a></td>
</tr>
  </tbody>
</table>

## chip_sw_alert_handler_lpg_sleep_mode_alerts (dragonfly)
Verify alert_handler can preserve alerts during low_power mode.

- Trigger fatal alerts for all IPs but configure alert_handler so it won't trigger
  reset.
- Randomly enter normal or deep sleep mode.
- Wait random cycles then wake up from the sleep mode.
- After wake up from normal sleep mode, clear all alert cause registers and check that
  all alerts are still firing after waking up.
- Repeat the previous steps for random number of iterations.
- Fatal alerts from flash_ctrl, otp_ctrl, sram_ctrl, and lc_ctrl are omitted because
  they disable the CPU and require a reset for the system to continue to function.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_alert_handler_lpg_sleep_mode_alerts-dragonfly">chip_sw_alert_handler_lpg_sleep_mode_alerts (dragonfly)</a></td>
  <td><a href="01_feature_report.md#alert_handlerping_timer">ALERT_HANDLER.PING_TIMER</a></td>
</tr>
  </tbody>
</table>

## chip_sw_alert_handler_lpg_sleep_mode_pings (dragonfly)
Verify alert_handler's ping mechanism works correctly during sleep and wake up.

There are two scenarios to check:

- Configure alert_handler's ping timeout register to a reasonable value that won't
  cause ping timeout in normal cases.
  Then randomly enter and exit normal or deep sleep modes.
  Check that no local alerts triggered in alert_handler.
  This scenario ensures that ping mechanism won't send out spurious failure.
- Configure alert_handler's ping timeout register to a small value that will always
  causes ping timeout.
  Then randomly enter and exit normal or deep sleep modes.
  Clear local alert cause register and check that alert ping timeout continue to fire
  after wake up.
  This scenario ensures the ping mechanism will continue to send out pings after waking
  up from sleep modes.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_alert_handler_lpg_sleep_mode_pings-dragonfly">chip_sw_alert_handler_lpg_sleep_mode_pings (dragonfly)</a></td>
  <td><a href="01_feature_report.md#alert_handlerping_timer">ALERT_HANDLER.PING_TIMER</a></td>
</tr>
  </tbody>
</table>

## chip_sw_alert_handler_ping_ok (dragonfly)
Verify alert ping mechanism doesn't trigger spurious alerts.

Check that the alert handler ping mechanism doesn't trigger any unexpected NMI
interrupts once enabled.

**Ping timeout calculation**
See timeout calculations described in the
`chip_sw_alert_handler_reverse_ping_in_deep_sleep` test.

**Procedure**

- On POR reset:
  - Enable an alert and assign it to to ClassA.
  - Set escalation configuration to trigger before test wake up time.
  - Set ping timeout to 0x100
  - Lock alert configuration and enable ping mechanism.
  - Wait for polling counters to cycle through by busy polling on Ibex for
    5 milliseconds.
  - Check there are no alert_handler NMI interrupts triggered.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_alert_handler_ping_ok-dragonfly">chip_sw_alert_handler_ping_ok (dragonfly)</a></td>
  <td><a href="01_feature_report.md#alert_handlerping_timer">ALERT_HANDLER.PING_TIMER</a></td>
</tr>
  </tbody>
</table>

## chip_sw_alert_handler_ping_timeout (dragonfly)
Verify the alert senders' ping timeout.

Set alert_handler's ping timeout cycle to 2 and enable alert_senders. Verify that
alert_handler detects the ping timeout and reflects it on the `loc_alert_cause`
register.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_alert_handler_ping_timeout-dragonfly">chip_sw_alert_handler_ping_timeout (dragonfly)</a></td>
  <td><a href="01_feature_report.md#alert_handlerping_timer">ALERT_HANDLER.PING_TIMER</a></td>
</tr>
  </tbody>
</table>

## chip_sw_alert_handler_reverse_ping_in_deep_sleep (dragonfly)
Verify escalation reverse ping timer disabled in sleep mode.

Check that escalation receivers located inside always-on blocks do not auto-escalate
due to the reverse ping feature while the system is in deep sleep.

**Reverse ping timeout calculation**

The reverse ping timeout calculation is done using the following formula available in
`prim_esc_receiver`:

```
4  * N_ESC_SEV * (2 * 2 * 2^PING_CNT_DW)
```

`pwrmgr` is the only block consuming the `N_ESC_SEV` and `PING_CNT_DW` compile time
parameters:

```
alert_handler_reg_pkg::N_ESC_SEV = 4
alert_handler_reg_pkg::PING_CNT_DW = 16
```

The alert escalation responder inside `pwrmgr` is connected to the `io_div4` clock,
yielding a target 24MHz frequency. The result expected timeout based on the above
parameters is thus:

```
reverse_ping_timeout = 0.175s = (4 * 4 ( 2 * 2 * 2^16)) / 24e6
```

**Procedure**

- On POR reset:
  - Enable all alerts assigning them to ClassA.
  - Enable all local alerts and assign to ClassB.
  - Set escalation configuration to trigger before test wake up time.
  - Set ping timeout to a time less than wake up time.
  - Lock alert configuration and enable ping mechanism.
  - Wait for polling counters to cycle through by busy polling on Ibex for
    `reverse_ping_timeout >> 2` usec.
  - Configure AON to wake up device at a later time, making sure it is greater than the
    `reverse_ping_timeout` calculated in the previous section.
  - Enter deep sleep.
- On wake up from sleep:
  - Ensure reset status is low power exit. A `kDifRstmgrResetInfoEscalation` signals
    that there was a local escalation and should result in test failure.
  - Disable AON timer.
  - Check there are no flagged local alerts.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_alert_handler_reverse_ping_in_deep_sleep-dragonfly">chip_sw_alert_handler_reverse_ping_in_deep_sleep (dragonfly)</a></td>
  <td><a href="01_feature_report.md#alert_handlerping_timer">ALERT_HANDLER.PING_TIMER</a></td>
</tr>
  </tbody>
</table>

## chip_sw_all_escalation_resets (dragonfly)
Verify escalation from all unit integrity errors.

Inject integrity errors in any unit that has a one-hot checker for CSR register
writes, and verify escalation is triggered. Allow escalation to go through reset.
Use the rstmgr alert info and the unit's fault CSRs to check the alert cause is right.
Each run of the test randomly chooses some one-hot checker for the error to be injected.
Keep state across resets in flash to check the expected interrupts and the right number
of resets occur.

- Verify the integrity error results in a regular interrupt.
- Verify the first escalation results in NMI serviced by the CPU.
- Verify the alert id in both these interrupts.
- Verify the unit's fault CSR correctly captured the fault kind.
- Verify any timer interrupts are disabled by escalation.
- Verify after the escalation reset all faults are cleared, and that the alert
  info captured the correct alert.
- Check that no additional resets occur.

SiVal: It is not possible to trigger internal integrity errors.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_all_escalation_resets-dragonfly">chip_sw_all_escalation_resets (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## clk_skew

This test will randomly inject clock skew within the differential pairs. Then check no
alert is raised.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#alert_handler_smoke">alert_handler_smoke</a></td>
  <td><a href="01_feature_report.md#alert_handleralertobserve">ALERT_HANDLER.ALERT.OBSERVE</a></td>
</tr>
  </tbody>
</table>

## entropy

Based on the smoke test, this test enables ping testing, and check if the ping feature
correctly pings all devices within certain period of time.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#alert_handler_entropy">alert_handler_entropy</a></td>
  <td><a href="01_feature_report.md#alert_handlerping_timer">ALERT_HANDLER.PING_TIMER</a></td>
</tr>
  </tbody>
</table>

## esc_accum

Based on the smoke test, this test will focus on testing the escalation accumulation
feature. So all the escalations in the test will be triggered by alert accumulation.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#alert_handler_esc_alert_accum">alert_handler_esc_alert_accum</a></td>
  <td><a href="01_feature_report.md#alert_handleralertescalate">ALERT_HANDLER.ALERT.ESCALATE</a><br><a href="01_feature_report.md#alert_handlerescalationcount">ALERT_HANDLER.ESCALATION.COUNT</a></td>
</tr>
  </tbody>
</table>

## esc_timeout

Based on the smoke test, this test will focus on testing the escalation timeout
feature. So all the escalations in the test will be triggered by interrupt timeout.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#alert_handler_esc_intr_timeout">alert_handler_esc_intr_timeout</a></td>
  <td><a href="01_feature_report.md#alert_handleralertescalate">ALERT_HANDLER.ALERT.ESCALATE</a><br><a href="01_feature_report.md#alert_handleralertinterrupt">ALERT_HANDLER.ALERT.INTERRUPT</a><br><a href="01_feature_report.md#alert_handlerescalationtimeout">ALERT_HANDLER.ESCALATION.TIMEOUT</a></td>
</tr>
  </tbody>
</table>

## lpg

Test alert_handler low_power_group(lpg) request.

Stimulus:

- Randomly enabled alert_receivers' `alert_en` but disable their ping response.
- Turn on their low-power control by either set `lpg_cg_en_i` or `lpg_rst_en_i`.
  Or pause the alert_handler's clk input for a random period of time.
- Enable alert ping timeout local alert.
- Run alert_handler_entropy_vseq.

Checks:

- Expect no ping timeout error because the alert_receivers are disabled via low-power
  group, or because alert_handler's clk input is paused due to sleep mode.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#alert_handler_lpg">alert_handler_lpg</a><br><a href="03_test_report.md#alert_handler_lpg_stub_clk">alert_handler_lpg_stub_clk</a></td>
  <td><a href="01_feature_report.md#alert_handlerping_timer">ALERT_HANDLER.PING_TIMER</a></td>
</tr>
  </tbody>
</table>

## ping_timeout

Based on entropy test, this test request alert_sender and esc_receiver drivers to
randomly create ping requests timeout stimulus.

Checks:

- Verify interrupt pin and states.
- Verify alert and local alert causes.
- Verify escalation states and counts.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#alert_handler_ping_timeout">alert_handler_ping_timeout</a></td>
  <td><a href="01_feature_report.md#alert_handleralertescalate">ALERT_HANDLER.ALERT.ESCALATE</a><br><a href="01_feature_report.md#alert_handleralertinterrupt">ALERT_HANDLER.ALERT.INTERRUPT</a><br><a href="01_feature_report.md#alert_handlerescalationcount">ALERT_HANDLER.ESCALATION.COUNT</a><br><a href="01_feature_report.md#alert_handlerping_timer">ALERT_HANDLER.PING_TIMER</a></td>
</tr>
  </tbody>
</table>

## random_alerts
Input random alerts and randomly write phase cycles.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#alert_handler_random_alerts">alert_handler_random_alerts</a></td>
  <td><a href="01_feature_report.md#alert_handleralertobserve">ALERT_HANDLER.ALERT.OBSERVE</a><br><a href="01_feature_report.md#alert_handlerescalationphases">ALERT_HANDLER.ESCALATION.PHASES</a></td>
</tr>
  </tbody>
</table>

## random_classes
Based on random_alerts test, this test will also randomly enable interrupt classes.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#alert_handler_random_classes">alert_handler_random_classes</a></td>
  <td><a href="01_feature_report.md#alert_handleralertinterrupt">ALERT_HANDLER.ALERT.INTERRUPT</a></td>
</tr>
  </tbody>
</table>

## sig_int_fail

This test will randomly inject differential pair failures on alert tx/rx pairs and the
escalator tx/rx pairs. Then check if integrity failure alert is triggered and
escalated.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#alert_handler_sig_int_fail">alert_handler_sig_int_fail</a></td>
  <td><a href="01_feature_report.md#alert_handleralertescalate">ALERT_HANDLER.ALERT.ESCALATE</a></td>
</tr>
  </tbody>
</table>

## smoke


- Alert_handler smoke test with one class configured that escalates through all
  phases after one alert has been triggered
- Check interrupt pins, alert cause CSR values, escalation pings, and crashdump_o
  output values
- Support both synchronous and asynchronous settings


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#alert_handler_smoke">alert_handler_smoke</a></td>
  <td><a href="01_feature_report.md#alert_handleralertescalate">ALERT_HANDLER.ALERT.ESCALATE</a><br><a href="01_feature_report.md#alert_handleralertinterrupt">ALERT_HANDLER.ALERT.INTERRUPT</a><br><a href="01_feature_report.md#alert_handleralertobserve">ALERT_HANDLER.ALERT.OBSERVE</a><br><a href="01_feature_report.md#alert_handlercrash_dump">ALERT_HANDLER.CRASH_DUMP</a><br><a href="01_feature_report.md#alert_handlerescalationphases">ALERT_HANDLER.ESCALATION.PHASES</a><br><a href="01_feature_report.md#alert_handlerping_timer">ALERT_HANDLER.PING_TIMER</a></td>
</tr>
  </tbody>
</table>

## stress_all

Combine above sequences in one test to run sequentially with the following exclusions:

- CSR sequences: scoreboard disabled
- Ping_corner_cases sequence: included reset in the sequence


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#alert_handler_stress_all">alert_handler_stress_all</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>
