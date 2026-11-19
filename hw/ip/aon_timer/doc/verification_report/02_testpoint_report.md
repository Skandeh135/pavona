# aon_timer Testpoint Report

## alternating_on_off

Run aon_timer_alternating_enable_on_off_vseq, which alternates each counter enable
between ON/OFF as well as intr_test writes in order to ensure the TB can cope with non
SW-like stimulus.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aon_timer_alternating_enable_on_off">aon_timer_alternating_enable_on_off</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_aon_timer_sleep_wakeup (dragonfly)
Verify that AON timer can wake up the chip from a deep sleep state.

- Read the reset cause register in rstmgr to confirm that the SW is in the POR reset
  phase.
- Program the pwrmgr to go to deep sleep state (clocks off, power off).
- Program the AON timer to wake up the chip in a reasonable amount of time.
- Have the CPU issue WFI to signal the pwrmgr to go into sleep state.
- Verify via assertion checks, the wake up request occurs after the timeout has elapsed.
- After reset followed by AON timer wake up, read the reset cause register to confirm
  the AON timer wake up phase.
- After the test sequence is complete, read the wake up threshold register - it should
  not be reset.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_smoketest-dragonfly">chip_sw_pwrmgr_smoketest (dragonfly)</a></td>
  <td><a href="01_feature_report.md#aon_timerwakeupwakeup_config">AON_TIMER.WAKEUP.WAKEUP_CONFIG</a><br><a href="01_feature_report.md#aon_timerwakeupwakeup_request">AON_TIMER.WAKEUP.WAKEUP_REQUEST</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aon_timer_sleep_wakeup (egret)
Verify that AON timer can wake up the chip from a deep sleep state.

- Read the reset cause register in rstmgr to confirm that the SW is in the POR reset
  phase.
- Program the pwrmgr to go to deep sleep state (clocks off, power off).
- Program the AON timer to wake up the chip in a reasonable amount of time.
- Have the CPU issue WFI to signal the pwrmgr to go into sleep state.
- Verify via assertion checks, the wake up request occurs after the timeout has elapsed.
- After reset followed by AON timer wake up, read the reset cause register to confirm
  the AON timer wake up phase.
- After the test sequence is complete, read the wake up threshold register - it should
  not be reset.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_smoketest-egret">chip_sw_pwrmgr_smoketest (egret)</a></td>
  <td><a href="01_feature_report.md#aon_timerwakeupwakeup_config">AON_TIMER.WAKEUP.WAKEUP_CONFIG</a><br><a href="01_feature_report.md#aon_timerwakeupwakeup_request">AON_TIMER.WAKEUP.WAKEUP_REQUEST</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aon_timer_sleep_wdog_bite_reset (dragonfly)
Verify the watchdog bite causing reset in sleep state.

- Repeat the steps in chip_aon_timer_wdog_bite_reset test, but with following changes:
- Program the pwrmgr to go to deep sleep state (clocks off, power off).
- Issue a WFI after programming the wdog, so that the reset request due to bite occurs
  during deep sleep state.
- After reset, read the reset cause register in rstmgr to confirm that the SW is now in
  the wdog reset phase.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_aon_timer_wdog_bite_reset-dragonfly">chip_sw_aon_timer_wdog_bite_reset (dragonfly)</a></td>
  <td><a href="01_feature_report.md#aon_timerwatchdogbark">AON_TIMER.WATCHDOG.BARK</a><br><a href="01_feature_report.md#aon_timerwatchdogbite">AON_TIMER.WATCHDOG.BITE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aon_timer_sleep_wdog_bite_reset (egret)
Verify the watchdog bite causing reset in sleep state.

- Repeat the steps in chip_aon_timer_wdog_bite_reset test, but with following changes:
- Program the pwrmgr to go to deep sleep state (clocks off, power off).
- Issue a WFI after programming the wdog, so that the reset request due to bite occurs
  during deep sleep state.
- After reset, read the reset cause register in rstmgr to confirm that the SW is now in
  the wdog reset phase.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_aon_timer_wdog_bite_reset-egret">chip_sw_aon_timer_wdog_bite_reset (egret)</a></td>
  <td><a href="01_feature_report.md#aon_timerwatchdogbark">AON_TIMER.WATCHDOG.BARK</a><br><a href="01_feature_report.md#aon_timerwatchdogbite">AON_TIMER.WATCHDOG.BITE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aon_timer_sleep_wdog_sleep_pause (dragonfly)
Verify that the wdog can be paused in sleep state.

- Repeat the steps in chip_aon_timer_sleep_wakeup test, but with following changes:
- Program the wdog to 'bite' a little sooner than the AON timer wake up.
- Also, program the wdog to pause during sleep.
- Issue a WFI after programming the wdog, so that the reset request occurs during deep
  sleep state.
- After reset followed by AON timer wake up, read the reset cause register to confirm
  that the AON timer woke up the chip, not the wdog reset.
- Un-pause the wdog and service the bark interrupt.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_aon_timer_sleep_wdog_sleep_pause-dragonfly">chip_sw_aon_timer_sleep_wdog_sleep_pause (dragonfly)</a></td>
  <td><a href="01_feature_report.md#aon_timerwatchdogbite">AON_TIMER.WATCHDOG.BITE</a><br><a href="01_feature_report.md#aon_timerwatchdogpause">AON_TIMER.WATCHDOG.PAUSE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aon_timer_sleep_wdog_sleep_pause (egret)
Verify that the wdog can be paused in sleep state.

- Repeat the steps in chip_aon_timer_sleep_wakeup test, but with following changes:
- Program the wdog to 'bite' a little sooner than the AON timer wake up.
- Also, program the wdog to pause during sleep.
- Issue a WFI after programming the wdog, so that the reset request occurs during deep
  sleep state.
- After reset followed by AON timer wake up, read the reset cause register to confirm
  that the AON timer woke up the chip, not the wdog reset.
- Un-pause the wdog and service the bark interrupt.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_aon_timer_sleep_wdog_sleep_pause-egret">chip_sw_aon_timer_sleep_wdog_sleep_pause (egret)</a></td>
  <td><a href="01_feature_report.md#aon_timerwatchdogbite">AON_TIMER.WATCHDOG.BITE</a><br><a href="01_feature_report.md#aon_timerwatchdogpause">AON_TIMER.WATCHDOG.PAUSE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aon_timer_wakeup_irq (dragonfly)
Verify the AON timer wake up interrupt in normal operating state.

- Program the PLIC to let the AON timer wake up interrupt the CPU.
- Program the AON timer to generate the wake up timeout interrupt after some time.
- Issue a WFI to wait for the interrupt to trigger.
- Service the interrupt when it triggers; verify that it came from AON timer.
- Verify that the interrupt triggered only after the timeout elapsed.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_aon_timer_irq-dragonfly">chip_sw_aon_timer_irq (dragonfly)</a></td>
  <td><a href="01_feature_report.md#aon_timerwakeupinterrupt">AON_TIMER.WAKEUP.INTERRUPT</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aon_timer_wakeup_irq (egret)
Verify the AON timer wake up interrupt in normal operating state.

- Program the PLIC to let the AON timer wake up interrupt the CPU.
- Program the AON timer to generate the wake up timeout interrupt after some time.
- Issue a WFI to wait for the interrupt to trigger.
- Service the interrupt when it triggers; verify that it came from AON timer.
- Verify that the interrupt triggered only after the timeout elapsed.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_aon_timer_irq-egret">chip_sw_aon_timer_irq (egret)</a></td>
  <td><a href="01_feature_report.md#aon_timerwakeupinterrupt">AON_TIMER.WAKEUP.INTERRUPT</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aon_timer_wdog_bark_irq (dragonfly)
Verify the watchdog bark reception in normal state.

- Program the PLIC to let the wdog bark signal interrupt the CPU.
- Program the AON timer wdog to 'bark' after some time and enable the bark interrupt.
- Service the bark interrupt upon reception.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_aon_timer_irq-dragonfly">chip_sw_aon_timer_irq (dragonfly)</a></td>
  <td><a href="01_feature_report.md#aon_timerwatchdoginterrupt">AON_TIMER.WATCHDOG.INTERRUPT</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aon_timer_wdog_bark_irq (egret)
Verify the watchdog bark reception in normal state.

- Program the PLIC to let the wdog bark signal interrupt the CPU.
- Program the AON timer wdog to 'bark' after some time and enable the bark interrupt.
- Service the bark interrupt upon reception.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_aon_timer_irq-egret">chip_sw_aon_timer_irq (egret)</a></td>
  <td><a href="01_feature_report.md#aon_timerwatchdoginterrupt">AON_TIMER.WATCHDOG.INTERRUPT</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aon_timer_wdog_bite_reset (dragonfly)
Verify the watchdog bite causing reset in the normal state.

- Read the reset cause register in rstmgr to confirm that the SW is in the POR reset
  phase.
- Program the AON timer wdog to 'bark' after some time.
- Let the bark escalate to bite, which should result in a reset request.
- After reset, read the reset cause register in rstmgr to confirm that the SW is now in
  the wdog reset phase.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_aon_timer_wdog_bite_reset-dragonfly">chip_sw_aon_timer_wdog_bite_reset (dragonfly)</a></td>
  <td><a href="01_feature_report.md#aon_timerwatchdogbark">AON_TIMER.WATCHDOG.BARK</a><br><a href="01_feature_report.md#aon_timerwatchdogbite">AON_TIMER.WATCHDOG.BITE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aon_timer_wdog_bite_reset (egret)
Verify the watchdog bite causing reset in the normal state.

- Read the reset cause register in rstmgr to confirm that the SW is in the POR reset
  phase.
- Program the AON timer wdog to 'bark' after some time.
- Let the bark escalate to bite, which should result in a reset request.
- After reset, read the reset cause register in rstmgr to confirm that the SW is now in
  the wdog reset phase.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_aon_timer_wdog_bite_reset-egret">chip_sw_aon_timer_wdog_bite_reset (egret)</a></td>
  <td><a href="01_feature_report.md#aon_timerwatchdogbark">AON_TIMER.WATCHDOG.BARK</a><br><a href="01_feature_report.md#aon_timerwatchdogbite">AON_TIMER.WATCHDOG.BITE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aon_timer_wdog_lc_escalate (dragonfly)
Verify that the LC escalation signal disables the AON timer wdog.

- Program the AON timer wdog to 'bark' after some time and enable the bark interrupt.
- Start the escalation process and fail the test in the interrupt handler in case the
  bark interrupt is fired.
- Program the alert handler to escalate on alerts upto phase 2 (i.e. reset) but the
  phase 1 (i.e. wipe secrets) should occur and last during the time the wdog is
  programed to bark and bite.
- Trigger an alert to cause an escalation condition before the bark signal asserts.
- After the reset ensure that the reset cause was due to the escalation to prove that
  the wdog was disabled.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_aon_timer_wdog_lc_escalate-dragonfly">chip_sw_aon_timer_wdog_lc_escalate (dragonfly)</a></td>
  <td><a href="01_feature_report.md#aon_timerwatchdogdisable_by_lc_ctrl">AON_TIMER.WATCHDOG.DISABLE_BY_LC_CTRL</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aon_timer_wdog_lc_escalate (egret)
Verify that the LC escalation signal disables the AON timer wdog.

- Program the AON timer wdog to 'bark' after some time and enable the bark interrupt.
- Start the escalation process and fail the test in the interrupt handler in case the
  bark interrupt is fired.
- Program the alert handler to escalate on alerts upto phase 2 (i.e. reset) but the
  phase 1 (i.e. wipe secrets) should occur and last during the time the wdog is
  programed to bark and bite.
- Trigger an alert to cause an escalation condition before the bark signal asserts.
- After the reset ensure that the reset cause was due to the escalation to prove that
  the wdog was disabled.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_aon_timer_wdog_lc_escalate-egret">chip_sw_aon_timer_wdog_lc_escalate (egret)</a></td>
  <td><a href="01_feature_report.md#aon_timerwatchdogdisable_by_lc_ctrl">AON_TIMER.WATCHDOG.DISABLE_BY_LC_CTRL</a></td>
</tr>
  </tbody>
</table>

## custom_intr

Run aon_timer_custom_intr_vseq, which drives random wdog/wkup control enables
as well as intr_test writes in order to help close intr_test_cg covergroup.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aon_timer_custom_intr">aon_timer_custom_intr</a></td>
  <td><a href="01_feature_report.md#aon_timerwakeupinterrupt">AON_TIMER.WAKEUP.INTERRUPT</a><br><a href="01_feature_report.md#aon_timerwakeupwakeup_config">AON_TIMER.WAKEUP.WAKEUP_CONFIG</a><br><a href="01_feature_report.md#aon_timerwakeupwakeup_request">AON_TIMER.WAKEUP.WAKEUP_REQUEST</a><br><a href="01_feature_report.md#aon_timerwatchdogbark">AON_TIMER.WATCHDOG.BARK</a><br><a href="01_feature_report.md#aon_timerwatchdogbite">AON_TIMER.WATCHDOG.BITE</a><br><a href="01_feature_report.md#aon_timerwatchdoginterrupt">AON_TIMER.WATCHDOG.INTERRUPT</a></td>
</tr>
  </tbody>
</table>

## jump

Change threshold values and prescaler value on random times without locking
configuration registers of watchdog timer.

**Stimulus**:

- Register writes to WDOG_BARK_THOLD, WDOG_BITE_THOLD, WKUP_THOLD, WKUP_CTRL

**Checks**:

- If we are changing WDOG_BARK_THOLD to be lower than the current WDOG_COUNT
  watchdog timer should raise the interrupt `wdog_timer_bark`.
- If we are changing WDOG_BITE_THOLD to be lower than the current WDOG_COUNT
  watchdog timer should trigger a reset request.
- If we are changing WKUP_THOLD to be lower than the current WKUP_COUNT
  wakeup timer should raise the interrupt `wkup_timer_expired`.
- WKUP_COUNT should reflect expected passing of real time regardless of
  prescaler value.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aon_timer_jump">aon_timer_jump</a></td>
  <td><a href="01_feature_report.md#aon_timerwakeupinterrupt">AON_TIMER.WAKEUP.INTERRUPT</a><br><a href="01_feature_report.md#aon_timerwakeupwakeup_config">AON_TIMER.WAKEUP.WAKEUP_CONFIG</a><br><a href="01_feature_report.md#aon_timerwakeupwakeup_request">AON_TIMER.WAKEUP.WAKEUP_REQUEST</a><br><a href="01_feature_report.md#aon_timerwatchdogbark">AON_TIMER.WATCHDOG.BARK</a><br><a href="01_feature_report.md#aon_timerwatchdogbite">AON_TIMER.WATCHDOG.BITE</a><br><a href="01_feature_report.md#aon_timerwatchdoginterrupt">AON_TIMER.WATCHDOG.INTERRUPT</a></td>
</tr>
  </tbody>
</table>

## max_threshold

Run the basic smoke sequence, but constrained to set max thresholds. This helps
close coverage.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aon_timer_smoke_max_thold">aon_timer_smoke_max_thold</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## min_threshold

Run the basic smoke sequence, but constrained to set min thresholds. This helps
close coverage.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aon_timer_smoke_min_thold">aon_timer_smoke_min_thold</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## prescaler

Switch prescaler value at random times without locking configuration registers
of watchdog timer.

**Stimulus**:

- Register writes to WKUP_CTRL while running.

**Checks**:

- WKUP_COUNT should reflect expected -and changed- passing of real time
  regardless of its changing prescaler value.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aon_timer_prescaler">aon_timer_prescaler</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## smoke

Smoke test initializes and starts AON Timer according to
the programmers guide.

**Stimulus**:

- Register writes to Watchdog/Wakeup COUNT, CTRL, and THOLD registers.

**Checks**:

- If we are changing WDOG_BARK_THOLD to be lower than the current WDOG_COUNT
  watchdog timer should raise the interrupt `wdog_timer_bark`.
- If we are changing WDOG_BITE_THOLD to be lower than the current WDOG_COUNT
  watchdog timer should trigger a reset request.
- If we are changing WKUP_THOLD to be lower than the current WKUP_COUNT
  wakeup timer should raise the interrupt `wkup_timer_expired`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aon_timer_smoke">aon_timer_smoke</a></td>
  <td><a href="01_feature_report.md#aon_timerwakeupinterrupt">AON_TIMER.WAKEUP.INTERRUPT</a><br><a href="01_feature_report.md#aon_timerwakeupwakeup_config">AON_TIMER.WAKEUP.WAKEUP_CONFIG</a><br><a href="01_feature_report.md#aon_timerwakeupwakeup_request">AON_TIMER.WAKEUP.WAKEUP_REQUEST</a><br><a href="01_feature_report.md#aon_timerwatchdogbark">AON_TIMER.WATCHDOG.BARK</a><br><a href="01_feature_report.md#aon_timerwatchdogbite">AON_TIMER.WATCHDOG.BITE</a><br><a href="01_feature_report.md#aon_timerwatchdoginterrupt">AON_TIMER.WATCHDOG.INTERRUPT</a></td>
</tr>
  </tbody>
</table>

## stress_all

This runs random sequences in succession.

Randomly chooses from the following sequences:

- aon_timer_intr_test
- aon_timer_jump
- aon_timer_prescaler
- aon_timer_smoke


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aon_timer_stress_all">aon_timer_stress_all</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## wkup_count_hi_cdc

Run aon_timer_wkup_count_cdc_hi_vseq which maximises the chances to hit
conditional and branch coverage in wkup_count_hi_cdc (prim_reg_cdc and
prim_reg_cdc_arb).


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aon_timer_wkup_count_cdc_hi">aon_timer_wkup_count_cdc_hi</a></td>
  <td><a href="01_feature_report.md#aon_timerwakeupinterrupt">AON_TIMER.WAKEUP.INTERRUPT</a><br><a href="01_feature_report.md#aon_timerwakeupwakeup_config">AON_TIMER.WAKEUP.WAKEUP_CONFIG</a><br><a href="01_feature_report.md#aon_timerwakeupwakeup_request">AON_TIMER.WAKEUP.WAKEUP_REQUEST</a></td>
</tr>
  </tbody>
</table>
