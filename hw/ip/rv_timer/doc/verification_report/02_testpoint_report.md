# rv_timer Testpoint Report

## cfg_update_on_fly
This test will verify update timer configuration on running timer.

- Program timer.Active to zero
- Program random values in interrupt enable, prescaler, step, mtime and mtime cmp
- After some clocks update timer config values
- Check for interrupt as per new config set


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_timer_rst_safe_cfg_update_on_fly">rv_timer_rst_safe_cfg_update_on_fly</a></td>
  <td><a href="01_feature_report.md#rv_timercompare">RV_TIMER.COMPARE</a><br><a href="01_feature_report.md#rv_timerconfig">RV_TIMER.CONFIG</a><br><a href="01_feature_report.md#rv_timercounter">RV_TIMER.COUNTER</a><br><a href="01_feature_report.md#rv_timerdisable">RV_TIMER.DISABLE</a><br><a href="01_feature_report.md#rv_timerenable">RV_TIMER.ENABLE</a><br><a href="01_feature_report.md#rv_timerinterrupt">RV_TIMER.INTERRUPT</a><br><a href="01_feature_report.md#rv_timerriscv_csrs_integration">RV_TIMER.RISCV_CSRS_INTEGRATION</a></td>
</tr>
  </tbody>
</table>

## chip_sw_timer (dragonfly)
Verify the timeout interrupt assertion.

- Configure RV_TIMER to generate an interrupt after a set timeout.
- Issue a WFI to wait for the interrupt to trigger.
- Service the interrupt when it triggers; verify that it came from rv_timer.
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
  <td><a href="03_test_report.md#chip_sw_rv_timer_irq-dragonfly">chip_sw_rv_timer_irq (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rv_timercompare">RV_TIMER.COMPARE</a><br><a href="01_feature_report.md#rv_timerconfig">RV_TIMER.CONFIG</a><br><a href="01_feature_report.md#rv_timercounter">RV_TIMER.COUNTER</a><br><a href="01_feature_report.md#rv_timerenable">RV_TIMER.ENABLE</a><br><a href="01_feature_report.md#rv_timerinterrupt">RV_TIMER.INTERRUPT</a></td>
</tr>
  </tbody>
</table>

## chip_sw_timer (egret)
Verify the timeout interrupt assertion.

- Configure RV_TIMER to generate an interrupt after a set timeout.
- Issue a WFI to wait for the interrupt to trigger.
- Service the interrupt when it triggers; verify that it came from rv_timer.
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
  <td><a href="03_test_report.md#chip_sw_rv_timer_irq-egret">chip_sw_rv_timer_irq (egret)</a></td>
  <td><a href="01_feature_report.md#rv_timercompare">RV_TIMER.COMPARE</a><br><a href="01_feature_report.md#rv_timerconfig">RV_TIMER.CONFIG</a><br><a href="01_feature_report.md#rv_timercounter">RV_TIMER.COUNTER</a><br><a href="01_feature_report.md#rv_timerenable">RV_TIMER.ENABLE</a><br><a href="01_feature_report.md#rv_timerinterrupt">RV_TIMER.INTERRUPT</a></td>
</tr>
  </tbody>
</table>

## counter_wrap (egret)
Verify that the timer counter will wrap to zero when the limit is reached.

- Enable interrupts.
- Set the counter to `UINT64_MAX - 5 milliseconds`.
- Set the compare register to UINT64_MAX.
- Enable the timer.
- Start a busy loop of 5 milliseconds based on the `mcycleh` CSR.
- Verify that the counter has wrapped around by reading `mtime`.
- Verify that the interrupt has fired.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rv_timer_systick_test-egret">chip_sw_rv_timer_systick_test (egret)</a></td>
  <td><a href="01_feature_report.md#rv_timercompare">RV_TIMER.COMPARE</a><br><a href="01_feature_report.md#rv_timerconfig">RV_TIMER.CONFIG</a><br><a href="01_feature_report.md#rv_timercounter">RV_TIMER.COUNTER</a><br><a href="01_feature_report.md#rv_timerenable">RV_TIMER.ENABLE</a><br><a href="01_feature_report.md#rv_timerinterrupt">RV_TIMER.INTERRUPT</a><br><a href="01_feature_report.md#rv_timerriscv_csrs_integration">RV_TIMER.RISCV_CSRS_INTEGRATION</a></td>
</tr>
  </tbody>
</table>

## disabled
This test to verify no activity in mTime, Interrupt Status, Interrupt signal,
When all timers are deactivated (ctrl.active = 0).

- Program 1 in interrupt enable and 0 in control register and random value for
  rest of the registers
- Scoreboard check for no activity and no interrupt whatever is setting


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_timer_rst_safe_disabled">rv_timer_rst_safe_disabled</a></td>
  <td><a href="01_feature_report.md#rv_timerdisable">RV_TIMER.DISABLE</a></td>
</tr>
  </tbody>
</table>

## max_value
This test configures the prescaler, step and mtimecm to the maximum value.
The counter is randomized to be up to 5 units lower than the timecmp.
By doing this, some seeds trigger an interrupt directly on configuration if timecmp=mtime.
While others force mtime to increase.
This test helps close functional coverage by hitting the maximum values for step, prescaler, mtime and mtimecmp


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_timer_rst_safe_max">rv_timer_rst_safe_max</a></td>
  <td><a href="01_feature_report.md#rv_timercompare">RV_TIMER.COMPARE</a><br><a href="01_feature_report.md#rv_timerconfig">RV_TIMER.CONFIG</a><br><a href="01_feature_report.md#rv_timercounter">RV_TIMER.COUNTER</a><br><a href="01_feature_report.md#rv_timerenable">RV_TIMER.ENABLE</a><br><a href="01_feature_report.md#rv_timerinterrupt">RV_TIMER.INTERRUPT</a><br><a href="01_feature_report.md#rv_timerriscv_csrs_integration">RV_TIMER.RISCV_CSRS_INTEGRATION</a></td>
</tr>
  </tbody>
</table>

## min_value
This test configures the prescaler and mtime to 0.
The step is randomized between 0 and 1 to allow the counter to increase sometimes.
The register timecmp is randomized to be set up to 5, so some seeds trigger an interrupt directly on configuration if timecmp=0.
While others force mtime to increase.
This test helps close functional coverage by hitting the minimum values for step, prescaler, mtime and mtimecmp


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_timer_rst_safe_min">rv_timer_rst_safe_min</a></td>
  <td><a href="01_feature_report.md#rv_timercompare">RV_TIMER.COMPARE</a><br><a href="01_feature_report.md#rv_timerconfig">RV_TIMER.CONFIG</a><br><a href="01_feature_report.md#rv_timercounter">RV_TIMER.COUNTER</a><br><a href="01_feature_report.md#rv_timerenable">RV_TIMER.ENABLE</a><br><a href="01_feature_report.md#rv_timerinterrupt">RV_TIMER.INTERRUPT</a><br><a href="01_feature_report.md#rv_timerriscv_csrs_integration">RV_TIMER.RISCV_CSRS_INTEGRATION</a></td>
</tr>
  </tbody>
</table>

## no_interrupt_test
This test will update timer value and compare value just before timer is going to
expire (multiple times) and verify no interrupt is asserted

- Program timer.Active to zero
- Program random values in interrupt enable, prescaler, step, mtime and mtime cmp
- Update timer config values just before timer is about to expire
- Check for no interrupt set


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_timer_rst_safe_cfg_update_on_fly">rv_timer_rst_safe_cfg_update_on_fly</a></td>
  <td><a href="01_feature_report.md#rv_timercompare">RV_TIMER.COMPARE</a><br><a href="01_feature_report.md#rv_timerconfig">RV_TIMER.CONFIG</a><br><a href="01_feature_report.md#rv_timercounter">RV_TIMER.COUNTER</a><br><a href="01_feature_report.md#rv_timerdisable">RV_TIMER.DISABLE</a><br><a href="01_feature_report.md#rv_timerenable">RV_TIMER.ENABLE</a><br><a href="01_feature_report.md#rv_timerinterrupt">RV_TIMER.INTERRUPT</a><br><a href="01_feature_report.md#rv_timerriscv_csrs_integration">RV_TIMER.RISCV_CSRS_INTEGRATION</a></td>
</tr>
  </tbody>
</table>

## random
RV_TIMER random test performs following steps for number of iterations

- Program zero to CTRL.active* Register(deactivate timer)
- Program random legal values in CFG*, TIMER_V_*, COMPARE_*, INTR_ENABLE*
- Program one to CTRL.active* (activate timer)
- Wait for number of cycles to have mTime>= mTimeCmp
- Check Interrupt state register and Interrupt signal (scoreboard logic)


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_timer_rst_safe_smoke">rv_timer_rst_safe_smoke</a></td>
  <td><a href="01_feature_report.md#rv_timercompare">RV_TIMER.COMPARE</a><br><a href="01_feature_report.md#rv_timerconfig">RV_TIMER.CONFIG</a><br><a href="01_feature_report.md#rv_timercounter">RV_TIMER.COUNTER</a><br><a href="01_feature_report.md#rv_timerdisable">RV_TIMER.DISABLE</a><br><a href="01_feature_report.md#rv_timerenable">RV_TIMER.ENABLE</a><br><a href="01_feature_report.md#rv_timerinterrupt">RV_TIMER.INTERRUPT</a><br><a href="01_feature_report.md#rv_timerriscv_csrs_integration">RV_TIMER.RISCV_CSRS_INTEGRATION</a></td>
</tr>
  </tbody>
</table>

## random_reset
This test is to exercise on the fly reset(timer is active)

- Assert reset randomly in the middle of random test steps
- Scoreboard check for all register go back to reset value


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_timer_rst_safe_smoke_with_rand_reset">rv_timer_rst_safe_smoke_with_rand_reset</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## stress
Do combinations of multiple of above scenarios to get multiple interrupts
asserted at the same time. Scoreboard should be robust enough to deal with all
scenarios.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_timer_stress_all">rv_timer_stress_all</a></td>
  <td><a href="01_feature_report.md#rv_timercompare">RV_TIMER.COMPARE</a><br><a href="01_feature_report.md#rv_timerconfig">RV_TIMER.CONFIG</a><br><a href="01_feature_report.md#rv_timercounter">RV_TIMER.COUNTER</a><br><a href="01_feature_report.md#rv_timerdisable">RV_TIMER.DISABLE</a><br><a href="01_feature_report.md#rv_timerenable">RV_TIMER.ENABLE</a><br><a href="01_feature_report.md#rv_timerinterrupt">RV_TIMER.INTERRUPT</a><br><a href="01_feature_report.md#rv_timerriscv_csrs_integration">RV_TIMER.RISCV_CSRS_INTEGRATION</a></td>
</tr>
  </tbody>
</table>

## tick_configuration (egret)
Verify that the timer can be configured to generate a system tick.

- Configure the timer to generate a tick of `T` microseconds long.
- Enable the timer.
- Start a busy loop of 5 milliseconds based on the `mcycleh` CSR.
- Read the number of ticks `n`.
- Verify that `n * T ~= 5 milliseconds` within 3% of tolerance.
- Repeat for T in:
  [1, 5, 25, 100, 125]


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rv_timer_systick_test-egret">chip_sw_rv_timer_systick_test (egret)</a></td>
  <td><a href="01_feature_report.md#rv_timercompare">RV_TIMER.COMPARE</a><br><a href="01_feature_report.md#rv_timerconfig">RV_TIMER.CONFIG</a><br><a href="01_feature_report.md#rv_timerenable">RV_TIMER.ENABLE</a></td>
</tr>
  </tbody>
</table>
