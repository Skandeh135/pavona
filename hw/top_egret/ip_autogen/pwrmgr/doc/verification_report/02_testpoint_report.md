# pwrmgr Testpoint Report

## aborted_low_power

Test aborted low power transitions.

Low power transitions can be aborted in two cases:

- The processor gets an interrupt soon after a low power entry is
  triggered.
- OTP, LC, or FLASH are not idle.

This test aborts low power transitions, and disables any wakeups,
so the test would timeout if low power was entered.

**Stimulus**:

- Bring pwrmgr to low power.
- Either disable `pwr_cpu.core_sleeping` or keep some of `lc_idle`,
  `otp_idle`, or `flash_idle` inputs off.
- Disable all wakeup enables.
- Randomly set `wakeup_info_capture_dis` CSR.

**Checks**:

- The `ctrl_cfg_regwen` CSR reads as 1 on the first attempt.
- Checks the output `pwr_rst_req.reset_cause` doesn't change for
  a bounded amount of time.
- Check that the `wakeup_info` CSR flags either `fall_through` or
  `abort` events when capture is enabled.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwrmgr_aborted_low_power">pwrmgr_aborted_low_power</a><br><a href="03_test_report.md#pwrmgr_lowpower_invalid">pwrmgr_lowpower_invalid</a></td>
  <td><a href="01_feature_report.md#pwrmgrlow_powerentry">PWRMGR.LOW_POWER.ENTRY</a><br><a href="01_feature_report.md#pwrmgrlow_powerwake_info">PWRMGR.LOW_POWER.WAKE_INFO</a></td>
</tr>
  </tbody>
</table>

## chip_sw_all_resets (egret)
Verify resets by relevant reset sources when active.

- POR (HW PAD) reset, SW POR, sysrst, wdog timer reset, esc rst.
- rstmgr sw reset is in rstmgr testplan.
- ndm reset is in rv_dm testplan.

This test is like the pwrmgr_*_sleep_all_reset_reqs tests, except the CPU will
just spin_wait for a reset, so the pwrmgr will be in active state.
SiVal: The CPU must be enabled to configure the test.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_all_reset_reqs-egret">chip_sw_pwrmgr_all_reset_reqs (egret)</a></td>
  <td><a href="01_feature_report.md#pwrmgrresetescalation_request">PWRMGR.RESET.ESCALATION_REQUEST</a><br><a href="01_feature_report.md#pwrmgrresetpor_request">PWRMGR.RESET.POR_REQUEST</a><br><a href="01_feature_report.md#pwrmgrresetrequest">PWRMGR.RESET.REQUEST</a><br><a href="01_feature_report.md#pwrmgrresetsw_rst_request">PWRMGR.RESET.SW_RST_REQUEST</a></td>
</tr>
  </tbody>
</table>

## chip_sw_pwrmgr_aon_power_glitch_reset (egret)
Verify the cold boot sequence through an AON power glitch.


Pulsing the AST vcaon_supp_i input causes an AON power glitch which becomes a POR.
This ensures that both FSMs are properly reset on the POR signal. The check is that
the processor ends up running. Also verify, the rstmgr recorded POR in `reset_info` CSR
by checking retention SRAM for reset_reason.
SiVal: AON power glitch cannot be triggered at will.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_full_aon_reset-egret">chip_sw_pwrmgr_full_aon_reset (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_pwrmgr_b2b_sleep_reset_req (egret)
Verify that the pwrmgr sequences sleep_req and reset req coming in almost at the same
time, one after the other. Use POR_N PAD to trigger reset.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_b2b_sleep_reset_req-egret">chip_sw_pwrmgr_b2b_sleep_reset_req (egret)</a></td>
  <td><a href="01_feature_report.md#pwrmgrlow_powerdisable_power">PWRMGR.LOW_POWER.DISABLE_POWER</a><br><a href="01_feature_report.md#pwrmgrlow_powerentry">PWRMGR.LOW_POWER.ENTRY</a><br><a href="01_feature_report.md#pwrmgrlow_powerwakeup">PWRMGR.LOW_POWER.WAKEUP</a><br><a href="01_feature_report.md#pwrmgrresetpor_request">PWRMGR.RESET.POR_REQUEST</a></td>
</tr>
  </tbody>
</table>

## chip_sw_pwrmgr_deep_sleep_all_reset_reqs (egret)
Verify resets by relevant reset sources in deep sleep mode.

- 4 resets are generated with deep sleep mode
- sysrst, wdog timer reset, rstmgr sw reset, and escalation reset

Notice rstmgr sw reset cannot be triggered in sleep mode.
Esc reset is triggered by pwrmgr ALERT_TEST.FATAL_FAULT CSR, configuring the
alert handler so that the reset triggers after setting sleep mode.
This verifies ALL programmable or external reset sources. This also verifies
that the pwrmgr sequencing is working correctly as expected. X-ref'ed with
all individual IP tests. For each reset source, enable the source and bring
the chip to low power, issue a reset, and verify the rstmgr's `reset_info`
indicates the expected reset.
SiVal: The CPU must be enabled to enter sleep mode.
No need to run this, run chip_sw_pwrmgr_random_sleep_all_reset_reqs instead.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_aon_timer_wdog_bite_reset-egret">chip_sw_aon_timer_wdog_bite_reset (egret)</a><br><a href="03_test_report.md#chip_sw_pwrmgr_deep_sleep_all_reset_reqs-egret">chip_sw_pwrmgr_deep_sleep_all_reset_reqs (egret)</a></td>
  <td><a href="01_feature_report.md#pwrmgrlow_powerdisable_power">PWRMGR.LOW_POWER.DISABLE_POWER</a><br><a href="01_feature_report.md#pwrmgrlow_powerentry">PWRMGR.LOW_POWER.ENTRY</a><br><a href="01_feature_report.md#pwrmgrresetescalation_request">PWRMGR.RESET.ESCALATION_REQUEST</a><br><a href="01_feature_report.md#pwrmgrresetrequest">PWRMGR.RESET.REQUEST</a><br><a href="01_feature_report.md#pwrmgrresetsw_rst_request">PWRMGR.RESET.SW_RST_REQUEST</a></td>
</tr>
  </tbody>
</table>

## chip_sw_pwrmgr_deep_sleep_all_wake_ups (egret)
Verify that the chip can go into deep sleep state and be woken up by ALL wake up
sources.

This verifies ALL wake up sources. This also verifies that the pwrmgr sequencing is
working correctly as expected. X-ref'ed with all individual IP tests. Similar to
chip_pwrmgr_sleep_all_wake_ups, except `control.main_pd_n` is set to 0.
SiVal: No need to run this, run chip_sw_pwrmgr_random_sleep_all_wake_ups instead.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_deep_sleep_all_wake_ups-egret">chip_sw_pwrmgr_deep_sleep_all_wake_ups (egret)</a></td>
  <td><a href="01_feature_report.md#pwrmgrlow_powerentry">PWRMGR.LOW_POWER.ENTRY</a><br><a href="01_feature_report.md#pwrmgrlow_powerwakeup">PWRMGR.LOW_POWER.WAKEUP</a><br><a href="01_feature_report.md#pwrmgrlow_powerwake_info">PWRMGR.LOW_POWER.WAKE_INFO</a></td>
</tr>
  </tbody>
</table>

## chip_sw_pwrmgr_deep_sleep_por_reset (egret)
Verify POR in deep sleep mode.

This verifies that the pwrmgr can handle POR in deep sleep. The chip is placed
in deep sleep, a POR is sent, and the wakeup cause is checked to be POR. This
test is broken out of the all_reset_reqs tests since the retention sram is wiped
on POR, so there is no state indicating the two PORs are any different.
SiVal: The CPU must be running to configure lop power entry.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_deep_sleep_por_reset-egret">chip_sw_pwrmgr_deep_sleep_por_reset (egret)</a></td>
  <td><a href="01_feature_report.md#pwrmgrlow_powerdisable_power">PWRMGR.LOW_POWER.DISABLE_POWER</a><br><a href="01_feature_report.md#pwrmgrlow_powerentry">PWRMGR.LOW_POWER.ENTRY</a><br><a href="01_feature_report.md#pwrmgrresetpor_request">PWRMGR.RESET.POR_REQUEST</a></td>
</tr>
  </tbody>
</table>

## chip_sw_pwrmgr_deep_sleep_power_glitch_reset (egret)
Verify the effect of a glitch in main power rail in deep sleep.

The vcmain_supp_i AST input is forced to drop right after putting the chip in deep
sleep. This triggers a MainPwr reset request, which is checked by reading retention
SRAM's reset_reason to show that the reset_info CSR's POR bit is not set when the test
restarts.

Note: the glitch has to be sent in a very narrow window:

- If sent too early the chip won't have started to process deep sleep.
- If too late the hardware won't monitor main power okay so the glitch will have no
  effect, and the test will timeout.

SiVal: Main power glitch cannot be triggered at will.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_deep_sleep_power_glitch_reset-egret">chip_sw_pwrmgr_deep_sleep_power_glitch_reset (egret)</a></td>
  <td><a href="01_feature_report.md#pwrmgrlow_powerdisable_power">PWRMGR.LOW_POWER.DISABLE_POWER</a><br><a href="01_feature_report.md#pwrmgrlow_powerentry">PWRMGR.LOW_POWER.ENTRY</a><br><a href="01_feature_report.md#pwrmgrresetmain_power_glitch_reset">PWRMGR.RESET.MAIN_POWER_GLITCH_RESET</a></td>
</tr>
  </tbody>
</table>

## chip_sw_pwrmgr_escalation_reset (egret)
Verify the power manager resets to a clean state after an escalation reset.

Trigger an internal fatal fault for the regfile onehot checker and let it escalate to
reset. Upon alert escalation reset, the internal status should be clear and pwrmgr
should not attempt to send out more alerts.
SiVal: This is not suitable for sival, and the various reset tests that work in sival
platforms cover escalation resets via writing to the alert_test, and setting the
alert_handler to immediately trip escalation reset.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_all_escalation_resets-egret">chip_sw_all_escalation_resets (egret)</a></td>
  <td><a href="01_feature_report.md#pwrmgrresetescalation_request">PWRMGR.RESET.ESCALATION_REQUEST</a></td>
</tr>
  </tbody>
</table>

## chip_sw_pwrmgr_external_full_reset (egret)
Verify the cold boot sequence by wiggling of chip's `POR_N`.

This ensures that both FSMs are properly reset on the POR signal. The check is that
the processor ends up running. Also verify, the rstmgr recorded POR in `reset_info` CSR
by checking retention SRAM for reset_reason.
SiVal: This will be exercised without any special test, since all tests trigger POR
when they start.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_full_aon_reset-egret">chip_sw_pwrmgr_full_aon_reset (egret)</a></td>
  <td><a href="01_feature_report.md#pwrmgrresetpor_request">PWRMGR.RESET.POR_REQUEST</a></td>
</tr>
  </tbody>
</table>

## chip_sw_pwrmgr_main_power_glitch_reset (egret)
Verify the effect of a glitch in main power rail.

The vcmain_supp_i AST input is forced to drop once the test is running. This triggers
a MainPwr reset request, which is checked by reading retention SRAM's reset_reason to
see that the reset_info CSR's POR bit is not set when the test restarts.
SiVal: Main power glitch cannot be triggered at will.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_main_power_glitch_reset-egret">chip_sw_pwrmgr_main_power_glitch_reset (egret)</a></td>
  <td><a href="01_feature_report.md#pwrmgrresetmain_power_glitch_reset">PWRMGR.RESET.MAIN_POWER_GLITCH_RESET</a></td>
</tr>
  </tbody>
</table>

## chip_sw_pwrmgr_normal_sleep_all_reset_reqs (egret)
Verify that the chip can go into normal sleep state and be reset up by ALL reset req
sources.

This verifies ALL reset sources.

- 7 resets are generated randomly with normal sleeps
- POR (HW PAD) reset, SW POR, sysrst, wdog timer reset, esc rst, SW req
- esc reset is followed by normal mode and cleared by reset because it does not work
  with sleep mode

SiVal: No need to run this, run chip_sw_pwrmgr_random_sleep_all_reset_reqs instead.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_normal_sleep_all_reset_reqs-egret">chip_sw_pwrmgr_normal_sleep_all_reset_reqs (egret)</a></td>
  <td><a href="01_feature_report.md#pwrmgrlow_powerentry">PWRMGR.LOW_POWER.ENTRY</a><br><a href="01_feature_report.md#pwrmgrresetescalation_request">PWRMGR.RESET.ESCALATION_REQUEST</a><br><a href="01_feature_report.md#pwrmgrresetrequest">PWRMGR.RESET.REQUEST</a><br><a href="01_feature_report.md#pwrmgrresetsw_rst_request">PWRMGR.RESET.SW_RST_REQUEST</a></td>
</tr>
  </tbody>
</table>

## chip_sw_pwrmgr_normal_sleep_all_wake_ups (egret)
Verify that the chip can go into normal sleep state and be woken up by ALL wake up
sources.

This verifies ALL wake up sources. This also verifies that the pwrmgr sequencing is
working correctly as expected. X-ref'ed with all individual IP tests. For each wakeup
source clear and enable `wake_info` CSR, enable the wakeup from that source with the
`wakeup_en` CSR, bring the chip to normal sleep, optionally disabling the source's
clock, have the source issue a wakeup event and verify `wake_info` indicates the
expected wakeup.
SiVal: No need to run this, run chip_sw_pwrmgr_random_sleep_all_wake_ups instead.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_normal_sleep_all_wake_ups-egret">chip_sw_pwrmgr_normal_sleep_all_wake_ups (egret)</a></td>
  <td><a href="01_feature_report.md#pwrmgrlow_powerwakeup">PWRMGR.LOW_POWER.WAKEUP</a><br><a href="01_feature_report.md#pwrmgrlow_powerwake_info">PWRMGR.LOW_POWER.WAKE_INFO</a></td>
</tr>
  </tbody>
</table>

## chip_sw_pwrmgr_normal_sleep_por_reset (egret)
Verify POR in normal sleep mode.

This verifies that the pwrmgr can handle POR in normal sleep. The chip is placed
in normal sleep, a POR is sent, and the wakeup cause is checked to be POR. This
test is broken out of the all_reset_reqs tests since the retention sram is wiped
on POR, so there is no state indicating the two PORs are any different.
SiVal: The CPU must be running to configure lop power entry.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_normal_sleep_por_reset-egret">chip_sw_pwrmgr_normal_sleep_por_reset (egret)</a></td>
  <td><a href="01_feature_report.md#pwrmgrlow_powerentry">PWRMGR.LOW_POWER.ENTRY</a><br><a href="01_feature_report.md#pwrmgrresetpor_request">PWRMGR.RESET.POR_REQUEST</a></td>
</tr>
  </tbody>
</table>

## chip_sw_pwrmgr_random_sleep_all_reset_reqs (egret)
Verify resets by relevant reset sources in sleep modes.

- 4 resets are generated with normal and deep sleep mode each
- sysrst, wdog timer reset, rstmgr sw reset, and escalation reset

Notice rstmgr sw reset cannot be triggered in sleep mode.
Esc reset is triggered by pwrmgr ALERT_TEST.FATAL_FAULT CSR, configuring the
alert handler so that the reset triggers after setting sleep mode.
This verifies ALL programmable or external reset sources. This also verifies
that the pwrmgr sequencing is working correctly as expected. X-ref'ed with
all individual IP tests. For each reset source, enable the source and bring
the chip to low power, issue a reset, and verify the rstmgr's `reset_info`
indicates the expected reset.
SiVal: The CPU must be enabled to enter sleep mode.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_random_sleep_all_reset_reqs-egret">chip_sw_pwrmgr_random_sleep_all_reset_reqs (egret)</a></td>
  <td><a href="01_feature_report.md#pwrmgrlow_powerdisable_power">PWRMGR.LOW_POWER.DISABLE_POWER</a><br><a href="01_feature_report.md#pwrmgrlow_powerentry">PWRMGR.LOW_POWER.ENTRY</a><br><a href="01_feature_report.md#pwrmgrresetescalation_request">PWRMGR.RESET.ESCALATION_REQUEST</a><br><a href="01_feature_report.md#pwrmgrresetrequest">PWRMGR.RESET.REQUEST</a><br><a href="01_feature_report.md#pwrmgrresetsw_rst_request">PWRMGR.RESET.SW_RST_REQUEST</a></td>
</tr>
  </tbody>
</table>

## chip_sw_pwrmgr_random_sleep_all_wake_ups (egret)
Verify that the chip can go into random low power states and be woken up by ALL wake
up sources.

This verifies ALL wake up sources. This also verifies that the pwrmgr sequencing is
working correctly as expected. X-ref'ed with all individual IP tests. For each wakeup
source clear and enable `wake_info` CSR, enable the wakeup from that source with the
`wakeup_en` CSR, bring the chip to both normal and low power sleep, optionally
disabling the source's clock, have the source issue a wakeup event and verify
`wake_info` indicates the expected wakeup.

Each test should perform a minimum of 2 low power transitions to ensure there are no
state dependent corner cases with wakeup interactions.
SiVal: This test can do controllable variants of wakeup testing, provided we run
enough cycles with suitable randomization. This can run in any lifecycle state
with the corresponding OTP.
This test will need the host side to trigger wakeups that use external pins.
Note:

- The sensor_ctrl wakeup is not necessarily controllable, or the ones that are
  will not trigger in sleep mode.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_random_sleep_all_wake_ups-egret">chip_sw_pwrmgr_random_sleep_all_wake_ups (egret)</a></td>
  <td><a href="01_feature_report.md#pwrmgrlow_powerentry">PWRMGR.LOW_POWER.ENTRY</a><br><a href="01_feature_report.md#pwrmgrlow_powerwakeup">PWRMGR.LOW_POWER.WAKEUP</a><br><a href="01_feature_report.md#pwrmgrlow_powerwake_info">PWRMGR.LOW_POWER.WAKE_INFO</a></td>
</tr>
  </tbody>
</table>

## chip_sw_pwrmgr_random_sleep_power_glitch_reset (egret)
Verify the effect of a glitch in main power rail in random sleep states.

The vcmain_supp_i AST input is forced to drop right after putting the chip in a random
sleep state. This triggers a MainPwr reset request, which is checked by reading
retention SRAM's reset_reason to show that the reset_info CSR's POR bit is not set when
the test restarts.

Note: the glitch has to be sent in a very narrow window:

- If sent too early the chip won't have started to process deep sleep.
- If too late the hardware won't monitor main power okay so the glitch will have no
  effect, and the test will timeout.

Each test should perform a minimum of 2 low power transitions to ensure there are no
state dependent corner cases with power glitch handling.
SiVal: Main power glitch cannot be triggered at will.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_random_sleep_power_glitch_reset-egret">chip_sw_pwrmgr_random_sleep_power_glitch_reset (egret)</a></td>
  <td><a href="01_feature_report.md#pwrmgrlow_powerentry">PWRMGR.LOW_POWER.ENTRY</a><br><a href="01_feature_report.md#pwrmgrresetmain_power_glitch_reset">PWRMGR.RESET.MAIN_POWER_GLITCH_RESET</a></td>
</tr>
  </tbody>
</table>

## chip_sw_pwrmgr_sleep_disabled (egret)
Verify that the chip does not go to sleep on WFI when low power hint is 0.

This calls WFI with low_power_hint disabled and pwrmgr interrupts enabled,
and fails if the pwrmgr ISR is called.

SiVal: CPU must be enabled, but no other OTP or lifecycle dependencies.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_sleep_disabled-egret">chip_sw_pwrmgr_sleep_disabled (egret)</a></td>
  <td><a href="01_feature_report.md#pwrmgrlow_powerentry">PWRMGR.LOW_POWER.ENTRY</a></td>
</tr>
  </tbody>
</table>

## chip_sw_pwrmgr_sleep_power_glitch_reset (egret)
Verify the effect of a glitch in main power rail in shallow sleep.

The vcmain_supp_i AST input is forced to drop after putting the chip in shallow sleep.
This triggers a MainPwr reset request, which is checked by reading the retention SRAM's
reset_reason shows that the reset_info CSR's POR bit is not set when the
test restarts.
SiVal: Main power glitch cannot be triggered at will.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_sleep_power_glitch_reset-egret">chip_sw_pwrmgr_sleep_power_glitch_reset (egret)</a></td>
  <td><a href="01_feature_report.md#pwrmgrlow_powerentry">PWRMGR.LOW_POWER.ENTRY</a><br><a href="01_feature_report.md#pwrmgrresetmain_power_glitch_reset">PWRMGR.RESET.MAIN_POWER_GLITCH_RESET</a></td>
</tr>
  </tbody>
</table>

## chip_sw_pwrmgr_sysrst_ctrl_reset (egret)
Verify sysrst_ctrl and watchdog reset.

- Read the reset cause register in rstmgr to confirm that the SW is in the POR reset
  phase.
- Generate sysrst by driving input PAD.
- After reset read the rstmgr reset_info CSR to confirm it indicates a sysrst reset.
- Program the AON timer wdog to 'bark' after some time.
- Let the bark escalate to bite, which should cause a reset.
- After reset, read the rstmgr reset_info CSR to confirm it indicates a watchdog reset.

SiVal: The pin that causes sysrst to reset needs to be pulsed from the host side.
The chip_sw_all_resets is a superset of this testpoint.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_all_reset_reqs-egret">chip_sw_pwrmgr_all_reset_reqs (egret)</a><br><a href="03_test_report.md#chip_sw_pwrmgr_sysrst_ctrl_reset-egret">chip_sw_pwrmgr_sysrst_ctrl_reset (egret)</a></td>
  <td><a href="01_feature_report.md#pwrmgrresetrequest">PWRMGR.RESET.REQUEST</a></td>
</tr>
  </tbody>
</table>

## chip_sw_pwrmgr_usb_clk_disabled_when_active (egret)
Verify that the USB stops responding when its clock is disabled in active state.

Configure the pwrmgr CONTROL CSR with USB_CLK_EN_ACTIVE off, and issue a CSR read
to the USB.  This CSR read should cause the CPU to hung.  Prior to this read,
configure the watchdog to bite, and the test passes if there is a watchdog reset.

SiVal: CPU must be enabled, but no other OTP or lifecycle dependencies.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_usb_clk_disabled_when_active-egret">chip_sw_pwrmgr_usb_clk_disabled_when_active (egret)</a></td>
  <td><a href="01_feature_report.md#pwrmgrclock_controlusb_when_active">PWRMGR.CLOCK_CONTROL.USB_WHEN_ACTIVE</a><br><a href="01_feature_report.md#pwrmgrresetrequest">PWRMGR.RESET.REQUEST</a></td>
</tr>
  </tbody>
</table>

## chip_sw_pwrmgr_wdog_reset (egret)
Verify that the chip can be reset by watchdog timer reset source.

This verifies watchdog timer reset source. This also verifies that the pwrmgr sequencing
is working correctly as expected. X-ref'ed with all individual IP tests. Similar to
chip_pwrmgr_sleep_all_reset_reqs, except the chip is not put in low power mode.

SiVal: CPU must be enabled, but no other OTP or lifecycle dependencies.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_wdog_reset-egret">chip_sw_pwrmgr_wdog_reset (egret)</a></td>
  <td><a href="01_feature_report.md#pwrmgrresetrequest">PWRMGR.RESET.REQUEST</a></td>
</tr>
  </tbody>
</table>

## chip_sw_sensor_ctrl_deep_sleep_wake_up (egret)
Verify that the chip will wake up from deep sleep by sensor_ctrl.

This forces the sensor_ctrl alert input from AST to trigger wake up.
It does this while the chip is in deep sleep, so clocks are off.
SiVal: This test can only run in sim_dv.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_sensor_ctrl_deep_sleep_wake_up-egret">chip_sw_pwrmgr_sensor_ctrl_deep_sleep_wake_up (egret)</a></td>
  <td><a href="01_feature_report.md#pwrmgrlow_powerentry">PWRMGR.LOW_POWER.ENTRY</a><br><a href="01_feature_report.md#pwrmgrlow_powerwakeup">PWRMGR.LOW_POWER.WAKEUP</a><br><a href="01_feature_report.md#pwrmgrlow_powerwake_info">PWRMGR.LOW_POWER.WAKE_INFO</a></td>
</tr>
  </tbody>
</table>

## control_clks

Test CSR control of peripheral clocks during low power.

The peripheral clocks can be configured to remain on or be turned
off during low power with bits in the `control` CSR register.
The usb clock can also be configured off in active mode.
**Stimulus**:

- Sets these control bits at random.
- Cause a low power transition and wakeup.

**Checks**:

- The clock enable outputs to the AST clocks during a low
  power transition match the control bits.
- The usb clock is also checked during active mode against
  the control register.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwrmgr_wakeup">pwrmgr_wakeup</a></td>
  <td><a href="01_feature_report.md#pwrmgrclock_controlio_in_low_power">PWRMGR.CLOCK_CONTROL.IO_IN_LOW_POWER</a><br><a href="01_feature_report.md#pwrmgrclock_controlmain_in_low_power">PWRMGR.CLOCK_CONTROL.MAIN_IN_LOW_POWER</a><br><a href="01_feature_report.md#pwrmgrclock_controlusb_in_low_power">PWRMGR.CLOCK_CONTROL.USB_IN_LOW_POWER</a><br><a href="01_feature_report.md#pwrmgrclock_controlusb_when_active">PWRMGR.CLOCK_CONTROL.USB_WHEN_ACTIVE</a><br><a href="01_feature_report.md#pwrmgrlow_powerentry">PWRMGR.LOW_POWER.ENTRY</a><br><a href="01_feature_report.md#pwrmgrlow_powerwakeup">PWRMGR.LOW_POWER.WAKEUP</a><br><a href="01_feature_report.md#pwrmgrlow_powerwake_info">PWRMGR.LOW_POWER.WAKE_INFO</a></td>
</tr>
  </tbody>
</table>

## disable_rom_integrity_check

Test rom integrity check is disabled under life cycle test states.

While running a series of reset event, at FastPwrStateRomCheck
state,

- Drive lc_hw_debug_en_i and lc_dft_en_i to random value
  excluding {lc_ctrl_pkg::On, lc_ctrl_pkg::On} for both ports.
- Set rom_ctrl_i.good = Mubi4False.
- Wait for a while to make sure fsm state check is not FastPwrStateActive.

Then,

- Drive lc_hw_debug_en_i and lc_dft_en_i to {lc_ctrl_pkg::On, lc_ctrl_pkg::On}
- Check test finish gracefully.

Try these steps with different lc_ctrl inputs.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwrmgr_disable_rom_integrity_check">pwrmgr_disable_rom_integrity_check</a></td>
  <td><a href="01_feature_report.md#pwrmgrresetcheck_rom_integrity">PWRMGR.RESET.CHECK_ROM_INTEGRITY</a></td>
</tr>
  </tbody>
</table>

## escalation_timeout
This tests the escalation timeout feature.

If the escalation network doesn't respond to an outgoing "health"
requests within 128 cycles pwrmgr should issue an escalation reset
request.

**Stimulus**:

- Cause the external escalation network to stop responding, either
  disabling the clock or jamming the differential pairs.

**Check**:

- After 128 cycles of inactivity an escalation reset should be
  triggered.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwrmgr_escalation_timeout">pwrmgr_escalation_timeout</a></td>
  <td><a href="01_feature_report.md#pwrmgrresetescalation_timeout">PWRMGR.RESET.ESCALATION_TIMEOUT</a></td>
</tr>
  </tbody>
</table>

## lowpower_wakeup_race

Test wakeups coming close to lowpower entry.

If low power entry and a wakeup are closely aligned the hardware
could get confused. Notice this is very unlikely, since wakeup is
only sensed when the slow fsm is in LowPower state.

**Stimulus**:

- Trigger low power entry as described for other testpoints.
- Have all wakeups enabled.
- Assert wakeups_i in the temporal neighborhood of low power
  entry.

**Check**:

- No timeout occurs.
- Either pwrmgr remains active or a full low power cycle occurs.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwrmgr_lowpower_wakeup_race">pwrmgr_lowpower_wakeup_race</a></td>
  <td><a href="01_feature_report.md#pwrmgrlow_powerentry">PWRMGR.LOW_POWER.ENTRY</a><br><a href="01_feature_report.md#pwrmgrlow_powerwakeup">PWRMGR.LOW_POWER.WAKEUP</a></td>
</tr>
  </tbody>
</table>

## main_power_glitch_reset

Test reset due to a glitch in main power.

A power glitch causes an unconditional reset.

**Stimulus**:

- Set the rst_main_ni input low indicating a main power glitch.

**Checks**:

- The fast fsm becomes active when `fetch_en_o` output rises.
- Checks the `reset_status` CSRs.
- Checks `ip_clk_en` output has a low transition.
- Checks the output `pwr_rst_req.reset_cause` matches HwReq.
- Checks the output `pwr_rst_req.rstreqs` matches power glitch.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwrmgr_reset">pwrmgr_reset</a></td>
  <td><a href="01_feature_report.md#pwrmgrresetmain_power_glitch_reset">PWRMGR.RESET.MAIN_POWER_GLITCH_RESET</a></td>
</tr>
  </tbody>
</table>

## reset

Test random reset and reset_en.

Conditional reset inputs can be disabled via bits in the `reset_en`
CSR, while escalation and main power are unconditional. Resets can
be triggered either in active or low power state.

**Stimulus**:

- Sets `reset_en` randomly.
- Randomly choose whether to put the unit in low power mode.
- Generate resets randomly in value and time:
  - Conditionals via rstreqs_i,
  - Main power glitch via rst_main_ni.
  - Escalation via `esc_rst_tx_i`.
  - Sw reset from rstmgr via `sw_rst_req_i`.

**Checks**:

- The fast fsm becomes active when `fetch_en_o` output rises.
- Checks the `reset_status` CSRs.
- Checks `ip_clk_en` output has a low transition.
- SVA that when `pwr_rst_req.reset_cause` is HwReq, and the output
  `pwr_rst_req.rstreqs` matches the unconditional and enabled
  conditional resets inputs.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwrmgr_reset">pwrmgr_reset</a><br><a href="03_test_report.md#pwrmgr_reset_invalid">pwrmgr_reset_invalid</a></td>
  <td><a href="01_feature_report.md#pwrmgrresetescalation_request">PWRMGR.RESET.ESCALATION_REQUEST</a><br><a href="01_feature_report.md#pwrmgrresetmain_power_glitch_reset">PWRMGR.RESET.MAIN_POWER_GLITCH_RESET</a><br><a href="01_feature_report.md#pwrmgrresetrequest">PWRMGR.RESET.REQUEST</a><br><a href="01_feature_report.md#pwrmgrresetsw_rst_request">PWRMGR.RESET.SW_RST_REQUEST</a></td>
</tr>
  </tbody>
</table>

## reset_wakeup_race

Test wakeup from low power and reset request almost coinciding.

If a wakeup from low power and a reset occur at nearly the same time
the system handles them one at a time.

**Stimulus**:

- Trigger reset and wakeup from low power as described for other
  testpoints.
- Issue reset and wakeup a random number of cycles after the slow
  state machine is in LowPower state.
  - This also checks them coinciding.

**Check**:

- Similar tests as for the wakeup and reset testpoints, except
  making sure they happen per the triggering order.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwrmgr_wakeup_reset">pwrmgr_wakeup_reset</a></td>
  <td><a href="01_feature_report.md#pwrmgrlow_powerwakeup">PWRMGR.LOW_POWER.WAKEUP</a><br><a href="01_feature_report.md#pwrmgrlow_powerwake_info">PWRMGR.LOW_POWER.WAKE_INFO</a><br><a href="01_feature_report.md#pwrmgrresetrequest">PWRMGR.RESET.REQUEST</a></td>
</tr>
  </tbody>
</table>

## smoke

Smoke test exercising the pwrmgr state transitions.

- Brings pwrmgr out of POR.
- Enables wakeup.
- Triggers SW initiated low power transition with reset settings
  in `control` CSR.
- Triggers wakeup.
- Enables and triggers a reset.
- Waits for pwrmgr to be out of reset.

**Stimulus**:

- CSR writes to `wakeup_en`, `reset_en`, and `low_power_hint`.
- Needs many input pins to line up correctly in order to prevent the
  pwrmgr from waiting forever. Most of these are set in response
  to outputs, and are checked by SVA.

**Checks**:

- The fast fsm becomes active when `fetch_en_o` output rises.
- The wakeup and reset causes are as expected reading CSRs
  `wake_status` and `reset_status`.
- The output `pwr_rst_req.reset_cause` matches a low power or
  reset cause.
- The output `pwr_rst_req.rstreqs` matches the enabled resets.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwrmgr_smoke">pwrmgr_smoke</a></td>
  <td><a href="01_feature_report.md#pwrmgrlow_powerentry">PWRMGR.LOW_POWER.ENTRY</a><br><a href="01_feature_report.md#pwrmgrlow_powerwakeup">PWRMGR.LOW_POWER.WAKEUP</a><br><a href="01_feature_report.md#pwrmgrlow_powerwake_info">PWRMGR.LOW_POWER.WAKE_INFO</a><br><a href="01_feature_report.md#pwrmgrresetrequest">PWRMGR.RESET.REQUEST</a></td>
</tr>
  </tbody>
</table>

## stress_all
This runs random sequences in succession.

Randomly chooses from the following sequences:

- pwrmgr_aborted_low_power_vseq
- pwrmgr_lowpower_wakeup_race_vseq
- pwrmgr_reset_vseq
- pwrmgr_smoke_vseq
- pwrmgr_wakeup_reset_vseq
- pwrmgr_wakeup_vseq


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwrmgr_stress_all">pwrmgr_stress_all</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## wakeup

Test random wakeup, wakeup_en, wake_info_capture_dis, and
interrupt.

The different wakeup inputs can be disabled via bits in the
`wakeup_en` CSR. Update of `wakeup_info` can be disabled
via the `wake_info_capture_dis` CSR. Any wakeup causes an
interrupt unless interrupts are disabled.

**Stimulus**:

- Sets `wakeup_en` randomly but don't set it to zero, or the
  test will timeout.
- Set `wake_info_capture_dis` randomly on and off.
- Bring pwrmgr to low power.
- Set `wakeups_i` inputs randomly.
- Set `intr_enable` randomly.

**Checks**:

- The fast fsm becomes active when `fetch_en_o` output rises.
- Depending on `wakeups_i`:
  - If all wakeups are disabled, wait some time checking the
    state remains inactive.
  - Set `wakeups_i` so at least one is enabled.
- Checks `wakeup_status` CSR during transition to active state
  since the reset involved will clear the wakeups_i input.
- Checks the `wake_info` CSR.
- Checks the output `pwr_rst_req.reset_cause` is `LowPwrEntry`.
- Check that `intr_wakeup_o` is set according to `intr_enable` CSR.
- Coverage collected by `wakeup_cg` and `wakeup_intr_cg`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pwrmgr_wakeup">pwrmgr_wakeup</a></td>
  <td><a href="01_feature_report.md#pwrmgrlow_powerentry">PWRMGR.LOW_POWER.ENTRY</a><br><a href="01_feature_report.md#pwrmgrlow_powerwakeup">PWRMGR.LOW_POWER.WAKEUP</a><br><a href="01_feature_report.md#pwrmgrlow_powerwake_info">PWRMGR.LOW_POWER.WAKE_INFO</a></td>
</tr>
  </tbody>
</table>
