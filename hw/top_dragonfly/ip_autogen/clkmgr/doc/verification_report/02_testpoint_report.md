# clkmgr Testpoint Report

## chip_sw_clkmgr_alert_handler_clock_enables (dragonfly)
Verify the clock manager sends the correct information to the alert handler
regarding individual clocks being active so it can ignore missing ping responses
from them and avoid triggering spurious escalation. This scenario is caused by
peripheral and transactional clocks being disabled among others. The check is
that spurious escalation is not triggered.
SiVal: CPU must be enabled, but no other OTP or lifecycle dependencies.
This tests already run in CW310.


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
  <td><a href="01_feature_report.md#clkmgralert_handlerclock_status">CLKMGR.ALERT_HANDLER.CLOCK_STATUS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_clkmgr_deep_sleep_frequency (dragonfly)
Verify the frequency measurement through deep sleep.

Enable clock cycle counts. Put the chip in deep sleep. Upon wakeup reset the
clock measurements should be off, but the recoverable fault status should not
be cleared.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_ast_clk_outputs-dragonfly">chip_sw_ast_clk_outputs (dragonfly)</a></td>
  <td><a href="01_feature_report.md#clkmgrmeas_ctrlrecov_err">CLKMGR.MEAS_CTRL.RECOV_ERR</a><br><a href="01_feature_report.md#clkmgrmeas_ctrlregwen">CLKMGR.MEAS_CTRL.REGWEN</a><br><a href="01_feature_report.md#clkmgrmeas_ctrlrg_src">CLKMGR.MEAS_CTRL.RG_SRC</a></td>
</tr>
  </tbody>
</table>

## chip_sw_clkmgr_div (dragonfly)
Verify clk division logic is working correctly.

The IP level checks the divided clocks via SVA, and these are also bound at chip level.
Connectivity tests check peripherals are connected to the clock they expect.
Use the clkmgr count measurement feature to verify clock division.

SiVal: These tests should be run after clock calibration is completed.
Any LC cycle stage after calibration is done.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_ast_clk_outputs-dragonfly">chip_sw_ast_clk_outputs (dragonfly)</a><br><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_sw_fast_dev-dragonfly">chip_sw_clkmgr_external_clk_src_for_sw_fast_dev (dragonfly)</a><br><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_sw_fast_rma-dragonfly">chip_sw_clkmgr_external_clk_src_for_sw_fast_rma (dragonfly)</a><br><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_sw_fast_test_unlocked0-dragonfly">chip_sw_clkmgr_external_clk_src_for_sw_fast_test_unlocked0 (dragonfly)</a><br><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_sw_slow_dev-dragonfly">chip_sw_clkmgr_external_clk_src_for_sw_slow_dev (dragonfly)</a><br><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_sw_slow_rma-dragonfly">chip_sw_clkmgr_external_clk_src_for_sw_slow_rma (dragonfly)</a><br><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_sw_slow_test_unlocked0-dragonfly">chip_sw_clkmgr_external_clk_src_for_sw_slow_test_unlocked0 (dragonfly)</a></td>
  <td><a href="01_feature_report.md#clkmgrmeas_ctrlregwen">CLKMGR.MEAS_CTRL.REGWEN</a><br><a href="01_feature_report.md#clkmgrmeas_ctrlrg_src">CLKMGR.MEAS_CTRL.RG_SRC</a></td>
</tr>
  </tbody>
</table>

## chip_sw_clkmgr_escalation_reset (dragonfly)
Verify the clock manager resets to a clean state after an escalation reset.

Trigger an internal fatal fault for the regfile onehot checker and let it escalate to
reset. Upon alert escalation reset, the internal status should be clear and clkmgr
should not attempt to send out more alerts.
SiVal: This is tested by other unit's escalation tests. They will need to
add extra checks for specific units having been reset.


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

## chip_sw_clkmgr_extended_range (dragonfly)
Verify that the system can run at a reduced, calibrated clock frequency.

This test should check that the system can run at a reduced, calibrated clock frequency
(70MHz) with jitter enabled (which can lower the frequency down to ~55 MHz
momentarily). This option is intended as a fall-back in case there are issues running
the system with at 100MHz (calibrated).

This testpoint can be covered by extending the DV environment to support the extended
range clock option via a flag, and running several existing chip-level tests with that
option.

Test the following functionalities with reduced clock:

- flash_ctrl initialization
- flash_ctrl program, read and erase operations
- AES, HMAC, KMAC and ACC operations
- Keymgr key derivation
- Scramble-enabled access from the main SRAM
- Csrng edn concurrency

SiVal: This can be executed if we detect problems running at nominal frequencies.
It may be implemented as the system running specific tests with an external cLock.
No specific work may be needed other than configuring external clocks.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_acc_ecdsa_op_irq_jitter_en_reduced_freq-dragonfly">chip_sw_acc_ecdsa_op_irq_jitter_en_reduced_freq (dragonfly)</a><br><a href="03_test_report.md#chip_sw_aes_enc_jitter_en_reduced_freq-dragonfly">chip_sw_aes_enc_jitter_en_reduced_freq (dragonfly)</a><br><a href="03_test_report.md#chip_sw_clkmgr_jitter_reduced_freq-dragonfly">chip_sw_clkmgr_jitter_reduced_freq (dragonfly)</a><br><a href="03_test_report.md#chip_sw_csrng_edn_concurrency_reduced_freq-dragonfly">chip_sw_csrng_edn_concurrency_reduced_freq (dragonfly)</a><br><a href="03_test_report.md#chip_sw_flash_ctrl_access_jitter_en_reduced_freq-dragonfly">chip_sw_flash_ctrl_access_jitter_en_reduced_freq (dragonfly)</a><br><a href="03_test_report.md#chip_sw_flash_ctrl_ops_jitter_en_reduced_freq-dragonfly">chip_sw_flash_ctrl_ops_jitter_en_reduced_freq (dragonfly)</a><br><a href="03_test_report.md#chip_sw_flash_init_reduced_freq-dragonfly">chip_sw_flash_init_reduced_freq (dragonfly)</a><br><a href="03_test_report.md#chip_sw_hmac_enc_jitter_en_reduced_freq-dragonfly">chip_sw_hmac_enc_jitter_en_reduced_freq (dragonfly)</a><br><a href="03_test_report.md#chip_sw_keymgr_key_derivation_jitter_en_reduced_freq-dragonfly">chip_sw_keymgr_key_derivation_jitter_en_reduced_freq (dragonfly)</a><br><a href="03_test_report.md#chip_sw_kmac_mode_kmac_jitter_en_reduced_freq-dragonfly">chip_sw_kmac_mode_kmac_jitter_en_reduced_freq (dragonfly)</a><br><a href="03_test_report.md#chip_sw_sram_ctrl_scrambled_access_jitter_en_reduced_freq-dragonfly">chip_sw_sram_ctrl_scrambled_access_jitter_en_reduced_freq (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_clkmgr_external_clk_src_for_lc (dragonfly)
Verify the clkmgr requests ext clk src during certain LC states.

On POR lc asserts lc_clk_byp_req on some LC states, and de-asserts
it when lc_program completes. This also triggers divided clocks to step down. It may be
best to verify this via SVA, unless we implement clock cycle counters.
SiVal: This is implicitly tested by the success of OTP updates for calibration.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_lc-dragonfly">chip_sw_clkmgr_external_clk_src_for_lc (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_clkmgr_external_clk_src_for_sw (dragonfly)
Verify SW causes the clkmgr requests ext clk src during certain LC states.

In DEV, TEST_UNLOCKED, and RMA lc states the external clock is enabled in response to
`extclk_ctrl.sel` CSR writes. In addition `extclk_ctrl.hi_speed_sel` CSR causes the
divided clocks to step down. Verify this via SVA bound to clkmgr, and clock cycle
counters.

Disable external clock source and verify the AST reliably falls back to the internal
clock. Ensure the chip operates normally.
X-ref with chip_sw_uart_tx_rx_alt_clk_freq, which needs to deal with this as well.
SiVal: The only necessary test is that the internal clocks are running
with the right frequency after calibration. There are a few such tests already.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_sw_fast_dev-dragonfly">chip_sw_clkmgr_external_clk_src_for_sw_fast_dev (dragonfly)</a><br><a href="03_test_report.md#chip_sw_clkmgr_external_clk_src_for_sw_slow_dev-dragonfly">chip_sw_clkmgr_external_clk_src_for_sw_slow_dev (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_clkmgr_idle_trans (dragonfly)
Verify the ability to turn off the transactional clock via SW.

Ensure that the clock to transactional units will be turned off after any activity
completes in the transactional IP.  Verify it is off via spinwait in hints_status CSR.
Verify that turning off this clock does not affect the other derived clocks.

SiVal: CPU must be enabled, but no other OTP or lifecycle dependencies.
This tests already run in CW310.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_acc_randomness-dragonfly">chip_sw_acc_randomness (dragonfly)</a><br><a href="03_test_report.md#chip_sw_aes_idle-dragonfly">chip_sw_aes_idle (dragonfly)</a><br><a href="03_test_report.md#chip_sw_hmac_enc_idle-dragonfly">chip_sw_hmac_enc_idle (dragonfly)</a><br><a href="03_test_report.md#chip_sw_kmac_idle-dragonfly">chip_sw_kmac_idle (dragonfly)</a></td>
  <td><a href="01_feature_report.md#clkmgrhinttrans_clk">CLKMGR.HINT.TRANS_CLK</a></td>
</tr>
  </tbody>
</table>

## chip_sw_clkmgr_jitter (dragonfly)
Verify the clock jitter functionality.

Enable clock jitter setting the clkmgr `jitter_enable` CSR high. This causes the
jitter_o clkmgr output to toggle. Verify this output is connected to AST's
clk_src_sys_jen_i input using formal.

If jitter_regwen is enabled check that jitter_enable can be toggled.
If jitter_regwen is disabled check that jitter_enable cannot be changed.
X-ref with various specific jitter enable tests.
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
  <td><a href="03_test_report.md#chip_sw_acc_ecdsa_op_irq_jitter_en-dragonfly">chip_sw_acc_ecdsa_op_irq_jitter_en (dragonfly)</a><br><a href="03_test_report.md#chip_sw_aes_enc_jitter_en-dragonfly">chip_sw_aes_enc_jitter_en (dragonfly)</a><br><a href="03_test_report.md#chip_sw_clkmgr_jitter-dragonfly">chip_sw_clkmgr_jitter (dragonfly)</a><br><a href="03_test_report.md#chip_sw_edn_entropy_reqs_jitter-dragonfly">chip_sw_edn_entropy_reqs_jitter (dragonfly)</a><br><a href="03_test_report.md#chip_sw_flash_ctrl_access_jitter_en-dragonfly">chip_sw_flash_ctrl_access_jitter_en (dragonfly)</a><br><a href="03_test_report.md#chip_sw_flash_ctrl_ops_jitter_en-dragonfly">chip_sw_flash_ctrl_ops_jitter_en (dragonfly)</a><br><a href="03_test_report.md#chip_sw_hmac_enc_jitter_en-dragonfly">chip_sw_hmac_enc_jitter_en (dragonfly)</a><br><a href="03_test_report.md#chip_sw_keymgr_key_derivation_jitter_en-dragonfly">chip_sw_keymgr_key_derivation_jitter_en (dragonfly)</a><br><a href="03_test_report.md#chip_sw_kmac_mode_kmac_jitter_en-dragonfly">chip_sw_kmac_mode_kmac_jitter_en (dragonfly)</a><br><a href="03_test_report.md#chip_sw_sram_ctrl_scrambled_access_jitter_en-dragonfly">chip_sw_sram_ctrl_scrambled_access_jitter_en (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_clkmgr_jitter_cycle_measurements (dragonfly)
Verify jitter via clock cycle measurements after calibration.
The clock count thresholds for main clk need to be set wider than when jitter is disabled.

Check when jitter is enabled:

- using jitter thresholds no errors are detected
- using normal thresholds results in recoverable errors
- don't test normal thresholds for FPGAs since they don't support jitter and no errors will occur

Check when jitter is disabled:

- using either sets of thresholds result in no errors

The test flow should depend on jitter enable lock:

- if it is locked only tests for the given jitter configuration
- if it is unlocked test for both jitter enabled and disabled

SiVal: This is only useful on real silicon since FPGAs don't support jitter.
Should be done after clock calibration.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_clkmgr_jitter_frequency-dragonfly">chip_sw_clkmgr_jitter_frequency (dragonfly)</a></td>
  <td><a href="01_feature_report.md#clkmgrjitterenable">CLKMGR.JITTER.ENABLE</a><br><a href="01_feature_report.md#clkmgrjitterregwen">CLKMGR.JITTER.REGWEN</a><br><a href="01_feature_report.md#clkmgrmeas_ctrlregwen">CLKMGR.MEAS_CTRL.REGWEN</a><br><a href="01_feature_report.md#clkmgrmeas_ctrlrg_src">CLKMGR.MEAS_CTRL.RG_SRC</a></td>
</tr>
  </tbody>
</table>

## chip_sw_clkmgr_off_peri (dragonfly)
Verify the ability to turn off the peripheral clock via SW.

 Verify CSR accesses do not complete in peripherals that are off.  Using the watchdog
 timers, turn off a peripheral's clock, issue a CSR access to that peripheral, verify a
 watchdog event results, and verify the rstmgr crash dump info records the CSR address,
and the execution pc is close enough to the address that performs the hung access.

 SiVal: CPU must be enabled, but no other OTP or lifecycle dependencies.
 This tests already run in CW310.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_clkmgr_off_peri-dragonfly">chip_sw_clkmgr_off_peri (dragonfly)</a></td>
  <td><a href="01_feature_report.md#clkmgrenableperiph_clk">CLKMGR.ENABLE.PERIPH_CLK</a></td>
</tr>
  </tbody>
</table>

## chip_sw_clkmgr_off_trans (dragonfly)
Verify the turned off transactional units.

Verify CSR accesses do not complete in units that are off.  Using the watchdog timers,
turn off a transactional unit's clock, issue a CSR access to that unit, verify a
watchdog event results, verify the rstmgr crash dump info records the CSR address,
and the execution pc is close enough to the address that performs the hung access.

SiVal: CPU must be enabled, but no other OTP or lifecycle dependencies.
This tests already run in CW310.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_clkmgr_off_acc_trans-dragonfly">chip_sw_clkmgr_off_acc_trans (dragonfly)</a><br><a href="03_test_report.md#chip_sw_clkmgr_off_aes_trans-dragonfly">chip_sw_clkmgr_off_aes_trans (dragonfly)</a><br><a href="03_test_report.md#chip_sw_clkmgr_off_hmac_trans-dragonfly">chip_sw_clkmgr_off_hmac_trans (dragonfly)</a><br><a href="03_test_report.md#chip_sw_clkmgr_off_kmac_trans-dragonfly">chip_sw_clkmgr_off_kmac_trans (dragonfly)</a></td>
  <td><a href="01_feature_report.md#clkmgrhinttrans_clk">CLKMGR.HINT.TRANS_CLK</a></td>
</tr>
  </tbody>
</table>

## chip_sw_clkmgr_reset_frequency (dragonfly)
Verify the frequency measurement through reset.

Enable clock cycle counts, configured to cause errors. Trigger a chip reset via SW.
After reset the clock measurements should be off and the recoverable fault status
should be cleared.
SiVal: CPU must be enabled and clocks must be calibrated, but no other OTP or
lifecycle dependencies. This tests already run in CW310.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_clkmgr_reset_frequency-dragonfly">chip_sw_clkmgr_reset_frequency (dragonfly)</a></td>
  <td><a href="01_feature_report.md#clkmgrmeas_ctrlrecov_err">CLKMGR.MEAS_CTRL.RECOV_ERR</a><br><a href="01_feature_report.md#clkmgrmeas_ctrlregwen">CLKMGR.MEAS_CTRL.REGWEN</a><br><a href="01_feature_report.md#clkmgrmeas_ctrlrg_src">CLKMGR.MEAS_CTRL.RG_SRC</a></td>
</tr>
  </tbody>
</table>

## chip_sw_clkmgr_sleep_frequency (dragonfly)
Verify the frequency measurement through shallow sleep.

Enable clock cycle counts. Put the chip in shallow sleep with pwrmgr's CONTROL CSR
keeping some clocks disabled. Upon wakeup the clock measurements should be on, and the
recoverable fault status should show no errors for the disabled clocks.
SiVal: CPU must be enabled, but no other OTP or lifecycle dependencies.
This tests already run in CW310.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_clkmgr_sleep_frequency-dragonfly">chip_sw_clkmgr_sleep_frequency (dragonfly)</a></td>
  <td><a href="01_feature_report.md#clkmgrmeas_ctrlrecov_err">CLKMGR.MEAS_CTRL.RECOV_ERR</a><br><a href="01_feature_report.md#clkmgrmeas_ctrlregwen">CLKMGR.MEAS_CTRL.REGWEN</a><br><a href="01_feature_report.md#clkmgrmeas_ctrlrg_src">CLKMGR.MEAS_CTRL.RG_SRC</a></td>
</tr>
  </tbody>
</table>

## clk_status

This tests the three `pwr_o.*_status` output ports, for the
`io`, `main`, and `usb` clocks.

The `pwr_o.*_status` output must track the corresponding
`pwr_i.*_ip_clk_en` input.

**Stimulus**:

- Randomize the `pwr_i.*_ip_clk_en` setting for each clock.

**Check**:

- The checks are done in SVA at `clkmgr_pwrmgr_sva_if.sv`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#clkmgr_clk_status">clkmgr_clk_status</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## frequency
This tests the frequency counters measured count functionality.

These counters compute the number of cycles of each clock relative
to the aon timer, and compares it to the corresponding
thresholds written into the `*_meas_ctrl_shadowed` CSR. Measurements
beyond these thresholds trigger a recoverable alert and set a bit
in the `recov_err_code` CSR. Also, if the counters reach their
maximum value they don't wrap around.

If clock calibration is lost, indicated by the `calib_rdy_i` input
being `prim_mubi_pkg::MuBi4False`, the measurements stop, no
error is triggered, and `measure_ctrl_regwen` is set to 1.

**Stimulus**:

- Randomly set slow, correct, and fast interval for each counter
  and test.
- Randomly set the `calib_rdy_i` input.
- Randomly trigger a clock saturation by forcing its cycle count
  to be near its maximum value while counting.

**Check**:

- Slow and fast intervals should cause a recoverable alert.
- Coverage collected per clock.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#clkmgr_frequency">clkmgr_frequency</a></td>
  <td><a href="01_feature_report.md#clkmgrmeas_ctrlrecov_err">CLKMGR.MEAS_CTRL.RECOV_ERR</a><br><a href="01_feature_report.md#clkmgrmeas_ctrlregwen">CLKMGR.MEAS_CTRL.REGWEN</a><br><a href="01_feature_report.md#clkmgrmeas_ctrlrg_src">CLKMGR.MEAS_CTRL.RG_SRC</a></td>
</tr>
  </tbody>
</table>

## frequency_overflow
This tests the overflow feature in prim_clock_meas.

This needs to modify the state of the counter to trigger the
feature.

**Stimulus**:

- Program the counter. Whenever it hits the value of 1, set it to
  the range - 2.

**Check**:

- The internal cnt_ovfl flop is set.
- The fast_o output should be set.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#clkmgr_frequency">clkmgr_frequency</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## frequency_timeout
This tests the frequency counters timeout functionality.

These counters compute the number of cycles of some clock relative
to the aon timer. It should trigger a recoverable alert when there
is no valid measurement when enabled, leading to a timeout. This is
separate from the `frequently` testpoint to simplify the test checks.

**Stimulus**:

- Randomly stop measured clocks to trigger a timeout.

**Check**:

- Timeout should cause a recoverable alert.
- Coverage collected per clock.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#clkmgr_frequency_timeout">clkmgr_frequency_timeout</a></td>
  <td><a href="01_feature_report.md#clkmgrmeas_ctrlrecov_err">CLKMGR.MEAS_CTRL.RECOV_ERR</a><br><a href="01_feature_report.md#clkmgrmeas_ctrlregwen">CLKMGR.MEAS_CTRL.REGWEN</a><br><a href="01_feature_report.md#clkmgrmeas_ctrlrg_src">CLKMGR.MEAS_CTRL.RG_SRC</a></td>
</tr>
  </tbody>
</table>

## jitter

This tests the jitter functionality.

The jitter functionality is implemented by the AST block, but
controlled by the `jitter_enable` CSR in this block. This CSR
directly drives the `jitter_en_o` output pin.

**Stimulus**:

- CSR write to `jitter_enable`.

**Check**:

- The `jitter_en_o` output pin reflects the `jitter_enable` CSR.
  Test is implemented in the scoreboard, and is always running.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#clkmgr_smoke">clkmgr_smoke</a></td>
  <td><a href="01_feature_report.md#clkmgrjitterenable">CLKMGR.JITTER.ENABLE</a><br><a href="01_feature_report.md#clkmgrjitterregwen">CLKMGR.JITTER.REGWEN</a></td>
</tr>
  </tbody>
</table>

## peri_enables

Peripheral clocks are disabled if its `clk_enables` bit is off,
or the corresponding `pwr_i.*_ip_clk_en` is off, and `scanmode_i`
is not `lc_ctrl_pkg::On`.

This test runs multiple rounds which do the following:

- Randomize `pwr_i.usb_ip_clk_en` and `scanmode_i`, and the initial
  setting of `clk_enables`.
- Send a CSR write to `clk_enables` with its initial value.
- Send a CSR write to `clk_enables` that flips all bits.

It makes no sense to have `pwr_i.io_ip_clk_en` set to zero since
that would prevent the CPU from running and sending CSR updates.

**Checks**:

- SVA assertions for peripheral clocks enable and disable
  properties.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#clkmgr_peri">clkmgr_peri</a></td>
  <td><a href="01_feature_report.md#clkmgrenableperiph_clk">CLKMGR.ENABLE.PERIPH_CLK</a></td>
</tr>
  </tbody>
</table>

## regwen
This tests the behavior of the regwen CSRs.

When a regwen is clear, any write to CSRs it locks are ignored.
Once a regwen is cleared, it will only be set again after a full
reset.

**Stimulus**:

- Clear each regwen.
- Write to the corresponding locked CSRs.

**Check**:

- The locked CSR value is not updated.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#clkmgr_regwen">clkmgr_regwen</a></td>
  <td><a href="01_feature_report.md#clkmgrmeas_ctrlregwen">CLKMGR.MEAS_CTRL.REGWEN</a></td>
</tr>
  </tbody>
</table>

## smoke

Smoke test disabling peripheral and transactional clocks.

- Disables all peripheral clocks from their enabled reset state.
- Transactional clocks gating depends on whether they are idle.
- Initializes all units as busy (not idle).
- Clears each unit's `clk_hints` bit, which has no effect until
  the unit becomes idle.
- Sets the unit's `idle_i` bit, which should disable the clock.
- Writes both values of the `jitter_enable` CSR.

**Stimulus**:

- CSR writes to `clk_enables` and `clk_hints`.
- Setting `idle_i` clkmgr input.

**Checks**:

- SVA assertions for peripheral clocks enable and disable
  properties.
- Transactional clocks check SVA properties as follows:
  - If the hint enables it, the clock becomes active.
  - If the hint disables it but the unit is busy, the clock remains
    active.
  - If the hint disables it and the unit is idle, the clock stops.
- For transactional units the CSR `clk_hints_status` is checked
  to correspond to `clk_hints` once the units are idle.
- Check in scoreboard the `jitter_en_o` output tracks updates of the
  `jitter_enable` CSR.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#clkmgr_smoke">clkmgr_smoke</a></td>
  <td><a href="01_feature_report.md#clkmgrenableperiph_clk">CLKMGR.ENABLE.PERIPH_CLK</a><br><a href="01_feature_report.md#clkmgrhinttrans_clk">CLKMGR.HINT.TRANS_CLK</a><br><a href="01_feature_report.md#clkmgrjitterenable">CLKMGR.JITTER.ENABLE</a><br><a href="01_feature_report.md#clkmgrjitterregwen">CLKMGR.JITTER.REGWEN</a></td>
</tr>
  </tbody>
</table>

## stress_all
This runs random sequences in succession.

Randomly chooses from the following sequences:

- clkmgr_frequency_timeout_vseq,
- clkmgr_frequency_vseq,
- clkmgr_peri_vseq,
- clkmgr_smoke_vseq,
- clkmgr_trans_vseq


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#clkmgr_stress_all">clkmgr_stress_all</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## trans_enables

Transactional unit clocks are disabled if they are idle and
their CSR `clk_hints` bit is off, or `pwr_i.main_ip_clk_en` is off,
and `scanmode_i` is not `lc_ctrl_pkg::On`.
This test randomizes the initial setting of `idle_i` and the
desired value of `clk_hints`. Each round performs this sequence:

- Writes the desired value to CSR `clk_hints` and checks that the
  CSR `clk_hints_status` reflects CSR `clk_hints` except for the
  units not-idle.
- Marks all units as idle, and checks that `csr_hints_status`
  matches `clk_hints`.
- Writes `clk_hints` to all ones and checks that `csr_hints_status`
  is all ones.
- Writes `clk_hints` with its reset value.

**Checks**:

- SVA assertions for transactional unit clocks described in
  clkmgr_smoke.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#clkmgr_trans">clkmgr_trans</a></td>
  <td><a href="01_feature_report.md#clkmgrhinttrans_clk">CLKMGR.HINT.TRANS_CLK</a></td>
</tr>
  </tbody>
</table>
