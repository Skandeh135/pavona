# rstmgr Testpoint Report

## alert_info
Test the alert_info recording.

The `alert_info` CSR register(s) can capture the contents of the
`alert_dump_i` input when resets happen and it is enabled.

**Stimulus**:

- Regularly modify the `alert_dump_i` input.
- With `alert_regwen` on, randomly set `alert_info_ctrl.en` to
  control whether the dump should be captured.
- Generate reset(s) as in `smoke` testpoint.

**Checks**:

- Verify the `alert_info` is only captured when enabled.
- Verify the `alert_info` contents at each `alert_info_ctrl.index`
  matches the expected value.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rstmgr_reset">rstmgr_reset</a></td>
  <td><a href="01_feature_report.md#rstmgralert_infocapture">RSTMGR.ALERT_INFO.CAPTURE</a><br><a href="01_feature_report.md#rstmgralert_infoenable">RSTMGR.ALERT_INFO.ENABLE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rstmgr_alert_handler_reset_enables (dragonfly)
Verify the reset manager sends the correct information to the alert handler
regarding individual resets being active so it can ignore missing ping responses
from them and avoid triggering spurious escalation. This scenario is caused by
software induced peripheral resets among others. The check is that spurious
escalation is not triggered.

SiVal: CPU must be enabled, but no other OTP or lifecycle dependencies.
This test already runs in CW310.


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
  <td><a href="01_feature_report.md#rstmgralert_handlerreset_status">RSTMGR.ALERT_HANDLER.RESET_STATUS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rstmgr_alert_info (dragonfly)
Verify the expected values from the `alert_info` CSR on reset.

Various alerts can be created, for example, timeouts, and integrity errors, and at
least part of the `alert_info` CSR can be predicted. To cause some of these to
cause a reset, mask the relevant processor interrupts. Trigger these resets and
verify the `alert_info` register contents when reset is handled. Disable
capture for some cases and make sure the alert info remains unchanged.
Refer to `chip_sw_rstmgr_*sys_reset_info`.

SiVal: CPU must be enabled, but no other OTP or lifecycle dependencies.
This can be an important diagnostic tool, so setting it to SV1.


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
  <td><a href="01_feature_report.md#rstmgralert_infocapture">RSTMGR.ALERT_INFO.CAPTURE</a><br><a href="01_feature_report.md#rstmgralert_infoenable">RSTMGR.ALERT_INFO.ENABLE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rstmgr_cpu_info (dragonfly)
Verify the expected values from the `cpu_info` CSR on reset.

For some software induced resets we can predict the expected contents of `cpu_info`;
reads of writes to unmapped addresses for example. Generate these resets and verify
the `cpu_info` register contents when reset is handled.
Refer to `chip_sw_rstmgr_*sys_reset_info`.

SiVal: CPU must be enabled, but no other OTP or lifecycle dependencies.
This can be an important diagnostic tool, so setting it to SV1.
This test already runs in CW310.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rstmgr_cpu_info-dragonfly">chip_sw_rstmgr_cpu_info (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rstmgrcpu_infocapture">RSTMGR.CPU_INFO.CAPTURE</a><br><a href="01_feature_report.md#rstmgrcpu_infoenable">RSTMGR.CPU_INFO.ENABLE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rstmgr_escalation_reset (dragonfly)
Verify the reset manager resets to a clean state after an escalation reset.

Trigger an internal fatal fault for the regfile onehot checker and let it escalate to
reset. Upon alert escalation reset, the internal status should be clear and rstmgr
should not attempt to send out more alerts. In addition, set some CSR to its
non-reset value and check it returns to its reset value after reset.

SiVal: Rather than relying on injecting fatal faults, escalation reset can be
triggered by not responding to software induced alerts interrupts, and properly
configuring the alert handler. CPU must be enabled, but no other OTP or lifecycle
dependencies.


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
  <td><a href="01_feature_report.md#rstmgralert_infocapture">RSTMGR.ALERT_INFO.CAPTURE</a><br><a href="01_feature_report.md#rstmgrreset_infocapture">RSTMGR.RESET_INFO.CAPTURE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rstmgr_non_sys_reset_info (dragonfly)
Verify the `reset_info` CSR register for lc or higher resets.

Generate the 5 types of reset at `lc` level or higher, and check the retention SRAM's
reset_reason to show that `reset_info` CSR is as expected. This and other rstmgr
testpoints that require different resets cross-reference the individual IP tests that
generate those resets, and this testpoint merely adds reset checks in them. Those IP
blocks are `pwrmgr`, `alert_handler`, `aon_timer`, and `sysrst_ctrl`.

This should also check the reset's destination IP to make sure some reset side-effect
is present. Setting some `intr_enable` CSR bit when the test starts and checking it
after reset seems suitable. The `spi_host` IPs receive multiple resets so they will
need special consideration.

SiVal: This testpoint is exercised by a large number of existing reset cases, yet
it would be best to develop a single test that issues all resets realizable by
software, not on error injection. The requirement for this testpoint is to check
the reset info is checked. CPU must be enabled, but no other OTP or lifecycle
dependencies.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_all_reset_reqs-dragonfly">chip_sw_pwrmgr_all_reset_reqs (dragonfly)</a><br><a href="03_test_report.md#chip_sw_pwrmgr_random_sleep_all_reset_reqs-dragonfly">chip_sw_pwrmgr_random_sleep_all_reset_reqs (dragonfly)</a><br><a href="03_test_report.md#chip_sw_pwrmgr_smoketest-dragonfly">chip_sw_pwrmgr_smoketest (dragonfly)</a><br><a href="03_test_report.md#chip_sw_pwrmgr_wdog_reset-dragonfly">chip_sw_pwrmgr_wdog_reset (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rstmgrreset_infocapture">RSTMGR.RESET_INFO.CAPTURE</a><br><a href="01_feature_report.md#rstmgrreset_infoclear">RSTMGR.RESET_INFO.CLEAR</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rstmgr_sw_req_reset (dragonfly)
Verify software requested device reset.

Generate a reset request by directly writing the `reset_req` CSR.
The reset created should be identical to those caused by hardware sources.
After reset, the retention SRAM's reset_reason should show that the `reset_info` CSR
reflects that a software request was the reset cause.

SiVal: CPU must be enabled, but no other OTP or lifecycle dependencies.
For early SiV we could rely on the external reset, so this seems SV3.
This test already runs in CW310.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rstmgr_sw_req-dragonfly">chip_sw_rstmgr_sw_req (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rstmgrsw_rstchip_reset">RSTMGR.SW_RST.CHIP_RESET</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rstmgr_sw_rst (dragonfly)
Verify `sw_rst_ctrl_n` CSR resets individual peripherals.

- Pick a rw type CSR in each peripheral and program arbitrary value
  that does not cause any adverse side-effects.
- Pulse the reset to the peripheral via software.
- Read the resister after reset and verify it returns the reset value.
- Repeat these steps for each of these software resettable peripherals:
  `spi_device`, `spi_host0`, `spi_host1`, `usb`, `i2c0`, `i2c1`, `i2c2`.

Notice the two `spi_host` IPs receive two different resets, `spi_host*`.

SiVal: CPU must be enabled, but no other OTP or lifecycle dependencies.
This test already runs in CW310.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rstmgr_sw_rst-dragonfly">chip_sw_rstmgr_sw_rst (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rstmgrsw_rstrequest">RSTMGR.SW_RST.REQUEST</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rstmgr_sys_reset_info (dragonfly)
Verify the `reset_info` CSR register for sys reset.

Generate reset triggered by `rv_dm`, which results in a sys level reset, and check the
retention SRAM's reset_reason to show that the `reset_info` CSR is as expected. This
testpoint cross-reference the `rv_dm` tests that generate this reset, and this
testpoint merely adds reset checks in them.

This should also check the reset's destination IP to make sure some reset side-effect
is present. Setting some `intr_enable` CSR bit when the test starts and checking it
after reset seems suitable. The `spi_host` IPs receive multiple resets so they will
need special consideration.

SiVal: CPU and debug must be enabled, so it only works in TEST_UNLOCKED, DEV, and RMA.
The rv_dm is an important tool for SiVal, so the stage is set to SV2.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_rv_dm_ndm_reset_req-dragonfly">chip_rv_dm_ndm_reset_req (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rstmgrreset_infocapture">RSTMGR.RESET_INFO.CAPTURE</a><br><a href="01_feature_report.md#rstmgrreset_infoclear">RSTMGR.RESET_INFO.CLEAR</a></td>
</tr>
  </tbody>
</table>

## cpu_info
Test the cpu_info recording.

The `cpu_info` CSR register(s) can capture the contents of the
`cpu_dump_i` input when resets happen and it is enabled.

**Stimulus**:

- Regularly modify the `cpu_dump_i` input.
- With `cpu_regwen` on, randomly set `cpu_info_ctrl.en` to control
  whether the dump should be captured.
- Generate reset(s) as in `smoke` testpoint.

**Checks**:

- Verify the `cpu_info` is only captured when enabled.
- Verify the `cpu_info` contents at each `cpu_info_ctrl.index`
  matches the expected value.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rstmgr_reset">rstmgr_reset</a></td>
  <td><a href="01_feature_report.md#rstmgrcpu_infocapture">RSTMGR.CPU_INFO.CAPTURE</a><br><a href="01_feature_report.md#rstmgrcpu_infoenable">RSTMGR.CPU_INFO.ENABLE</a></td>
</tr>
  </tbody>
</table>

## reset_info
Test the reporting of reset reason.

**Stimulus**:

- Generate the different resets recorded in `reset_info` CSR.
- Randomly clear `reset_info` (it is rw1c).

**Checks**:

- The resulting setting of `reset_info` is as expected.
- Each bit was set at least once.
- Each bit was cleared at least once.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rstmgr_reset">rstmgr_reset</a></td>
  <td><a href="01_feature_report.md#rstmgrreset_infocapture">RSTMGR.RESET_INFO.CAPTURE</a><br><a href="01_feature_report.md#rstmgrreset_infoclear">RSTMGR.RESET_INFO.CLEAR</a></td>
</tr>
  </tbody>
</table>

## reset_info_capture
Test the capture blocking effect of rst_cpu_n input.

After an AON reset reset capture is blocked until the input
rst_cpu_n goes inactive.

**Stimulus**:

- Wait for a random number of resets before setting rst_cpu_n
  inactive.

**Checks**:

- Non-AON resets prior to this event don't capture.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rstmgr_reset">rstmgr_reset</a></td>
  <td><a href="01_feature_report.md#rstmgrreset_infocapture">RSTMGR.RESET_INFO.CAPTURE</a></td>
</tr>
  </tbody>
</table>

## reset_stretcher
Test the POR reset signal must be stable for multiple cycles.

The POR reset signal must remain active for at least 32 consecutive
cycles before going inactive for the rest of the reset tree to go
inactive.

**Stimulus**:

- Activate POR, and de-activate it at a random width less than 32
  cycles between de-activations for N de-activations.

**Checks**:

- With SVA check the output reset is only set if the input reset
  has had at least 32 cycles of steady input reset active.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rstmgr_por_stretcher">rstmgr_por_stretcher</a></td>
  <td><a href="01_feature_report.md#rstmgrporstretcher">RSTMGR.POR.STRETCHER</a></td>
</tr>
  </tbody>
</table>

## rstmgr_cnsty_chk
This is a dedicated test environment for consistency checks.

This checks are performed by the rstmgr_cnsty_chk module, which
contains logic to check whether conditions allow for a reset to
be asserted. For example, if a child reset asserts, either its
parent reset or a software control must have asserted; otherwise
it is considered a fatal error.

The environment is very simple, and consists of a testbench that
instantiates a rstmgr_cnsty_chk module and classes to generate
stimulus for it.

This testbench generates combinations of parent resets, software
reset requests, and child resets. It verifies ilegitimate child
resets are detected and flag an error. It can also can be used
to determine the actual delay between the parent or software
reset and the child reset they trigger.

It uses a combination of randomized variables and exhaustive
delays over a certain range to trigger the various resets
mentioned above.

The dedicated environment is under dv/rstmgr_cnsty_chk relative
to rstmgr.


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
  <td><a href="01_feature_report.md#rstmgrreset_consistency_checks">RSTMGR.RESET_CONSISTENCY_CHECKS</a></td>
</tr>
  </tbody>
</table>

## smoke

Smoke test accessing a major datapath within the rstmgr.

Checks the behavior of rstmgr when receiving various reset requests.

**Stimulus**:

- Send a scan reset.
- Send a low power entry reset.
- Send a peripheral reset request.
- Send a debug reset.
- Configure a software request for peripheral reset.
- Set alert and cpu dump inputs to random values.

**Checks**:

- Checks the reset_info matches expected values.
- Checks the `alert_info` CSR correctly captures the input info.
- Checks the `cpu_info` CSR correctly captures the input info.
- Checks the output reset pins corresponding to sw resettable
  units match `sw_rst_ctrl_n` CSR.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rstmgr_smoke">rstmgr_smoke</a></td>
  <td><a href="01_feature_report.md#rstmgralert_infocapture">RSTMGR.ALERT_INFO.CAPTURE</a><br><a href="01_feature_report.md#rstmgrcpu_infocapture">RSTMGR.CPU_INFO.CAPTURE</a><br><a href="01_feature_report.md#rstmgrreset_infocapture">RSTMGR.RESET_INFO.CAPTURE</a><br><a href="01_feature_report.md#rstmgrsw_rstrequest">RSTMGR.SW_RST.REQUEST</a></td>
</tr>
  </tbody>
</table>

## stress_all
This runs random tests sequentially.

Stress with the following sequences:

- rstmgr_reset_vseq
- rstmgr_smoke_vseq
- rstmgr_sw_rst_vseq


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rstmgr_stress_all">rstmgr_stress_all</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## sw_rst
Test the sw_rst functionality.

The `sw_rst_regwen` and `sw_rst_ctrl_n` CSRs control the specific
reset outputs to peripherals in the following sequence:

- Test all `sw_rst_ctrl_n` bits when `sw_rst_regwen` is all 1's.
- Clear each `sw_rst_regwen` bit to verify the corresponding resets
  are masked.

**Stimulus**:

- Write `sw_rst_ctrl_n` CSR with random values when regwen is all 1's.
- Clear each `sw_rst_regwen` bit and write `sw_rst_ctrl_n` CSR with
  all 0's.
- After each regwen bit check set `sw_rst_ctrl_n` to all 1's.

**Checks**:

- Check that the zero bits in `sw_rst_ctrl_n` enabled by
  `sw_rst_regwen` cause the respective resets to become active.
- Check that the zero bits in `sw_rst_ctrl_n` disabled by
  `sw_rst_regwen` have no effect on resets.
- Check the `reset_info`, `cpu_info`, and `alert_info` CSRs are not modified.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rstmgr_sw_rst">rstmgr_sw_rst</a></td>
  <td><a href="01_feature_report.md#rstmgrsw_rstrequest">RSTMGR.SW_RST.REQUEST</a></td>
</tr>
  </tbody>
</table>

## sw_rst_reset_race
Test sw_rst and reset close in time.

Sends sw_rst and regular resets in close temporal proximity.

**Stimulus**:

- Write `sw_rst_ctrl_n` CSR with random values when regwen is all 1's.
- Send a hardware reset.
- Release resets.

**Checks**:

- Check the `reset_info` CSR.
- Reset behavior is checked by SVA.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rstmgr_sw_rst_reset_race">rstmgr_sw_rst_reset_race</a></td>
  <td><a href="01_feature_report.md#rstmgrreset_infocapture">RSTMGR.RESET_INFO.CAPTURE</a><br><a href="01_feature_report.md#rstmgrsw_rstrequest">RSTMGR.SW_RST.REQUEST</a></td>
</tr>
  </tbody>
</table>
