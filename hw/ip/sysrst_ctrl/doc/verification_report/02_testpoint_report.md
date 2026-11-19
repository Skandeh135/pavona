# sysrst_ctrl Testpoint Report

## auto_block_key_outputs

Verify the auto block key output feature.

* Trigger the input keys combo.
* Set the debounce timer value in AUTO_BLOCK_DEBOUNCE_CTL register.
* Select the output override value by configuring AUTO_BLOCK_OUT_CTL register.
* Check whether the input keys stays low for the selected debounce time.
* Read the AUTO_BLOCK_OUT_CTL register to check if the output key is overridden.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#sysrst_ctrl_auto_blk_key_output">sysrst_ctrl_auto_blk_key_output</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_sysrst_ctrl_ec_rst_l (egret)
Verify that the ec_rst_l stays asserted on power-on-reset until SW can control it.

- Verify that ec_rst_l stays asserted as the chip is brought out of reset.
- Verify that the pin continues to remain low until SW is alive.
- Have the SW write to pin_allowed|out_ctrl CSRs to control the ec_rst_l value and
  verify the value at the chip output.
- Optionally, also verify ec_rst_l pulse stretching by setting the ec_rst_ctl register
  with a suitable pulse width.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_sysrst_ctrl_ec_rst_l-egret">chip_sw_sysrst_ctrl_ec_rst_l (egret)</a></td>
  <td><a href="01_feature_report.md#sysrst_ctrlhardware_reset_stretch">SYSRST_CTRL.HARDWARE_RESET_STRETCH</a></td>
</tr>
  </tbody>
</table>

## chip_sw_sysrst_ctrl_flash_wp_l (egret)
Verify that the flash_wp_l stays asserted on power-on-reset until SW can control it.

- Exactly the same as chip_sysrst_ctrl_ec_rst_l, but covers the flash_wp_l pin.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_sysrst_ctrl_ec_rst_l-egret">chip_sw_sysrst_ctrl_ec_rst_l (egret)</a></td>
  <td><a href="01_feature_report.md#sysrst_ctrlflash_write_protect">SYSRST_CTRL.FLASH_WRITE_PROTECT</a></td>
</tr>
  </tbody>
</table>

## chip_sw_sysrst_ctrl_in_irq (egret)
Verify the SYSRST ctrl can detect an input combination to signal an interrupt.

- Program a specific combination of transitions on pwrb, key*, ac_present and ec_reset_l
  pins to trigger an interrupt by writing to key_intr_ctl register.
- Program the key_intr_debounce_ctl register to debounce an appropriate time.
- Enable the interrupt at SYSRST ctrl as well as at the PLIC.
- Create glitches only for some time less than detection time and check that there is no
- interrupt triggered.
- Glitch the inputs at the chip IOs before stabilizing on the programmed transitions.
- SW services the interrupt when triggered, verifies the pin input value and
  key_intr_status for correctness and clears the interrupt status.
- Verify separately, each key combination successfully generates an interrupt.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_sysrst_ctrl_in_irq-egret">chip_sw_sysrst_ctrl_in_irq (egret)</a></td>
  <td><a href="01_feature_report.md#sysrst_ctrlinput_triggered_interrupt">SYSRST_CTRL.INPUT_TRIGGERED_INTERRUPT</a></td>
</tr>
  </tbody>
</table>

## chip_sw_sysrst_ctrl_inputs (egret)
Verify that the SYSRST ctrl input pin values can be read.

- Drive a known value on ac_reset, ec_rst_l, flash_wp_l, pwrb, lid_open and key* pins at
  the chip inputs.
- Read the pin_in_value CSR to check for correctness.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_sysrst_ctrl_inputs-egret">chip_sw_sysrst_ctrl_inputs (egret)</a></td>
  <td><a href="01_feature_report.md#sysrst_ctrlpin_input_value_access">SYSRST_CTRL.PIN_INPUT_VALUE_ACCESS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_sysrst_ctrl_outputs (egret)
Verify that the SYSRST ctrl output pin values can be set.

- Drive a known value on ac_reset, ec_rst_l, flash_wp_l, pwrb, lid_open and key* pins
  at the chip inputs.
- Verify that SYSRST ctrl correctly loops them back to the chip outputs.
- Write the pin_allowed_ctl register to allow some of the pins to be overridden with
  either 0 or 1 or both.
- Write the pin_out_ctl register to enable the override on some of the pins.
- Write the pin_out_value register to set known values on those pins.
- Verify that at the chip outputs, pins on which override should be active is
  reflecting the overridden values. All others should reflect the values driven on chip
  inputs.
- Via assertion checks (or equivalent) verify that the transitions at the inputs
  immediately reflect at the outputs, if not intercepted / debounced by sysrst_ctrl.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_sysrst_ctrl_outputs-egret">chip_sw_sysrst_ctrl_outputs (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_sysrst_ctrl_reset (egret)
Verify the SYSRST ctrl can reset the chip from normal state.

- Read the reset cause register in rstmgr to confirm we are in POR reset phase.
- Program one of the com_sel_ctl_* CSRs to choose a set of inputs to be detected as
  the chip reset signal.
- Program the associated detection timer.
- Program the detection outcome CSR's (com_out_ctl) chip reset bit to 1.
- After some time, set the SYSRST ctrl inputs at the chip IOs to the programmed
  combination for the duration of the detection timer.
- The pwrmgr will power cycle the chip once it receives the chip reset input.
- Check that ec_rst_l and flash_wp_l (on pads IOR8 and IOR9) are asserted right after
  the pwrmgr has power cycled the system.
- Read the reset cause register after boot up to confirm peripheral reset phase.
- Read the pwrmgr reset status register to confirm chip reset.
- Read the com_sel_ctl_* CSR in SYSRST ctrl we programmed earlier - it should have been
  reset.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_pwrmgr_sysrst_ctrl_reset-egret">chip_sw_pwrmgr_sysrst_ctrl_reset (egret)</a><br><a href="03_test_report.md#chip_sw_sysrst_ctrl_reset-egret">chip_sw_sysrst_ctrl_reset (egret)</a></td>
  <td><a href="01_feature_report.md#sysrst_ctrlcombo_detect">SYSRST_CTRL.COMBO_DETECT</a></td>
</tr>
  </tbody>
</table>

## chip_sw_sysrst_ctrl_sleep_reset (egret)
Verify the SYSRST ctrl can reset the chip from deep sleep.

- Read the reset cause register in rstmgr to confirm we are in POR reset phase.
- Program one of the com_sel_ctl_* CSRs to choose a set of inputs to be detected as
  the chip reset signal.
- Program the associated detection timer.
- Program the detection outcome CSR's (com_out_ctl) chip reset bit to 1.
- Program the pwrmgr to put the chip in deep sleep state and allow it to be reset by the
  chip reset bit.
- Issue a WFI to bring the chip in low power state.
- After the chip has entered low power mode, set the SYSRST ctrl inputs at the chip IOs
  to the programmed combination for the duration of the detection timer.
- The pwrmgr will power cycle the chip from the deep sleep state once it receives the
  chip reset input.
- Read the reset cause register after boot up to confirm peripheral reset phase.
- Read the pwrmgr reset status register to confirm chip reset.
- Read the com_sel_ctl_* CSR in SYSRST ctrl we programmed earlier - it should have been
  reset.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_sysrst_ctrl_reset-egret">chip_sw_sysrst_ctrl_reset (egret)</a></td>
  <td><a href="01_feature_report.md#sysrst_ctrlcombo_detect">SYSRST_CTRL.COMBO_DETECT</a><br><a href="01_feature_report.md#sysrst_ctrlultra_low_power_wakeup">SYSRST_CTRL.ULTRA_LOW_POWER_WAKEUP</a></td>
</tr>
  </tbody>
</table>

## chip_sw_sysrst_ctrl_sleep_wakeup (egret)
Verify the SYSRST ctrl can wake up the chip from deep sleep.

- Read the reset cause register in rstmgr to confirm we are in POR reset phase.
- Program one of the com_sel_ctl_* CSRs to choose a set of inputs to be detected as
  a low power wakeup signal for the pwrmgr.
- Program the associated detection timer.
- Program the detection outcome CSR's (com_out_ctl) interrupt bit to 1.
- Program the pwrmgr to put the chip in deep sleep state and wake up on chip wake up
  event.
- Issue a WFI to bring the chip in low power state.
- After the chip has entered low power mode, set the SYSRST ctrl inputs at the chip IOs
  to the programmed combination for the duration of the detection timer.
- Read the reset cause register to confirm wake up from low power exit phase.
- Read the pwrmgr wake up status register to confirm chip wake up.
- Read the pin input value and the combo_intr_status CSRs to verify the correct
  combination on inputs woke up the chip from sleep.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_sysrst_ctrl_reset-egret">chip_sw_sysrst_ctrl_reset (egret)</a></td>
  <td><a href="01_feature_report.md#sysrst_ctrlultra_low_power_wakeup">SYSRST_CTRL.ULTRA_LOW_POWER_WAKEUP</a></td>
</tr>
  </tbody>
</table>

## chip_sw_sysrst_ctrl_ulp_z3_wakeup (egret)
Verify the z3_wakeup signaling.

- Start off with ac_present = 0, lid_open = 0 and pwrb = 0 at the chip inputs.
- Program the ulp_ac|lid|pwrb_debounce_ctl registers to debounce these inputs for an
  appropriate time.
- Enable the ULP wakeup feature by writing to the ulp_ctl register.
- Read the ulp_wakeup register and verify that no wakeup event is detected, after some
  amount of delay.
- Glitch the lid_open input at the chip IOs before stabilizing on value 1.
- Read the ulp_wakeup register to verify that the wakeup event is detected this time.
- Verify that the z3_wakeup output at the chip IOs is reflecting the value of 1.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_adc_ctrl_sleep_debug_cable_wakeup-egret">chip_sw_adc_ctrl_sleep_debug_cable_wakeup (egret)</a><br><a href="03_test_report.md#chip_sw_sysrst_ctrl_ulp_z3_wakeup-egret">chip_sw_sysrst_ctrl_ulp_z3_wakeup (egret)</a></td>
  <td><a href="01_feature_report.md#sysrst_ctrlultra_low_power_wakeup">SYSRST_CTRL.ULTRA_LOW_POWER_WAKEUP</a></td>
</tr>
  </tbody>
</table>

## combo_detect

Verify the combo detection with random action.

* Randomly set the input keys by configuring COM_SEL_CTL_0-3 register.
* Set the random combo duration via the COM_DET_CTL_0-3 register.
* Randomly select the action to be taken by configuring COM_OUT_CTL_0-3 register.
* Set the pulse width via EC_RST_CTL register.
* Read the COMBO_INTR_STATUS register to check whether an interrupt is correctly raised for all the combinations.
  Clear the interrupt in case it was raised.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#sysrst_ctrl_combo_detect">sysrst_ctrl_combo_detect</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## combo_detect_ec_rst

Verify the combo detection with ec_rst action.

* Set the input keys by configuring COM_SEL_CTL_0 register.
* Set the combo duration via the COM_DET_CTL_0 register.
* Select the action to be taken by configuring COM_OUT_CTL_0 register.
* Set the pulse width via EC_RST_CTL register only to raise ec_rst action.
* Drive the input with a randomized delay.
* Read the COMBO_INTR_STATUS register.
  In case the input was driven for longer than the debounce delay, check if the interrupt is raised and clear the interrupt.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#sysrst_ctrl_combo_detect_ec_rst">sysrst_ctrl_combo_detect_ec_rst</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## combo_detect_ec_rst_with_pre_cond

Verify the pre-condition for combo detection.

* Define `pwrb_in == 0` as a pre-condition by writing the COM_PRE_SEL_CTL_0 register
  with value 'h8.
* Set the pre-condition duration time via the `COM_PRE_DET_CTL` register.
* Wait for the pre-condition to be satisfied.
* Trigger the combo_detect_ec_rst sequence.
* NOTE: This is a directed test with no random values for V1 stage,
  further this test will be randomized.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#sysrst_ctrl_combo_detect_ec_rst_with_pre_cond">sysrst_ctrl_combo_detect_ec_rst_with_pre_cond</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## combo_detect_with_pre_cond

Verify the combo detection with random action and precondition.

* Randomly set the input keys combination as precondition by configuring COM_PRE_SEL_CTL_0-3 register.
* Randomly set the input keys combination for combo detection by configuring COM_SEL_CTL_0-3 register.
* Set the random combo precondition duration via the COM_PRE_DET_CTL_0-3 register.
* Set the random combo duration via the COM_DET_CTL_0-3 register.
* Randomly select the action to be taken by configuring COM_OUT_CTL_0-3 register.
* Set the pulse width via EC_RST_CTL register.
* Randomly set the input keys, such that precondition and subsequent combo detection logic are activated randomly.
* Read the COMBO_INTR_STATUS register to check whether an interrupt is correctly raised for all the combinations.
  Clear the interrupt in case it was raised.
* Check for bat_disable, rst_req or wake_up_o assertion depending on COM_OUT_CTL_0-3 register


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#sysrst_ctrl_combo_detect_with_pre_cond">sysrst_ctrl_combo_detect_with_pre_cond</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## ec_power_on_reset

Verify the EC and power on reset.

* Disable EC reset override.
* Set EC reset timer to stretch reset.
* Make sure ec_rst_out_l is asserted even after OpenTitan reset is released.
* Set PIN_OUT_CTL.EC_RST_L to 0 to release the ec_rst_out_l reset.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#sysrst_ctrl_ec_pwr_on_rst">sysrst_ctrl_ec_pwr_on_rst</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## flash_write_protect_output

Verify the flash write protect.

* Make sure flash_wp_out_l signal is asserted low by reading PIN_OUT_CTL.flash_wp_l.
* Enable the override function by setting PIN_OUT_CTL.FLASH_WP_L to value 1.
* Randomize the corresponding flash_wp_l_i input pin.
* Check flash_wp_l_i does not have a bypass path to flash_wp_l_o.
* Check if flash_wp_l_o is released only by the override function.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#sysrst_ctrl_flash_wr_prot_out">sysrst_ctrl_flash_wr_prot_out</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## input_output_inverted

Verify end to end data transfer with inverted input and inverted output.

* Write a random data to the input keys.
* Randomly configure KEY_INVERT_CTL to invert or not invert inputs and outputs.
* In case of no inversions or inverting both check that input matches output.
* In case where the input is inverted but not the output or the other way around check that input does not match output.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#sysrst_ctrl_in_out_inverted">sysrst_ctrl_in_out_inverted</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## keyboard_input_triggered_interrupt

Verify the keyboard and input triggered interrupt feature by detecting the edge
transitions on input pins.

* Set the input signals and edge transition by configuring KEY_INTR_CTL register.
* Set the debounce timer value via KEY_INTR_DEBOUNCE_CTL register.
* Read the KEY_INTR_STATUS register to check if the interrupt caused and clear the interrupt.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#sysrst_ctrl_edge_detect">sysrst_ctrl_edge_detect</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## pin_input_value_accessibility

Verify the pin input value accessibility.

* Trigger the key[0,1,2], ac_present_in, pwrb_in, ec_rst_in_l input pins with random values.
* Read the PIN_IN_VALUE register and check if the read value is same as input value.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#sysrst_ctrl_pin_access_test">sysrst_ctrl_pin_access_test</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## pin_output_keyboard_inversion_control

Verify the keyboard inversion feature by override logic.

* Select the output signals to override via PIN_OUT_CTL register.
* Allow the output signals to override the value via PIN_ALLOWED_CTL register.
* Set the override value to the output signal via PIN_OUT_VALUE register.
* Check whether the override happens correctly.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#sysrst_ctrl_pin_override_test">sysrst_ctrl_pin_override_test</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## smoke

Verify end to end data transfer in normal operation mode.

* Write a random data to the input keys.
* Read the data at the output pins and compare it with the input data.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#sysrst_ctrl_smoke">sysrst_ctrl_smoke</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## stress_all

Test all the sequences randomly in one sequence.

* Combine above sequences in one test then randomly select for running.
* All sequences should be finished and checked by the scoreboard.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#sysrst_ctrl_stress_all">sysrst_ctrl_stress_all</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## sysrst_ctrl_feature_disable

Verify the feature disable and debounce to idle state transitions

* Configure COM_DET_CTL, COM_PRE_DET_CTL, ULP_*_DEBOUNCE_CTL
* Assert input signals to trigger debounce timer and deassert before debounce timer expires
* Check for output and interrupts to make sure design doesn't detected the transitions


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#sysrst_ctrl_feature_disable">sysrst_ctrl_feature_disable</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## ultra_low_power_test

Verify the ultra low power feature.

* Configure ULP_AC_DEBOUNCE_CTL, ULP_LID_DEBOUNCE_CTL and ULP_PWRB_DEBOUNCE_CTL register to set the debounce timer value.
* Disable the bus clock to check detection logic works in sleep mode.
* Trigger the ac_present_i, lid_open_in and ec_rst_l_i input keys.
* Turn on the bus clock to read the status register.
* Read the WKUP_STATUS register to check if the event has occurred.
* Read the ULP_STATUS register and check if the ultra low power wakeup event is detected.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#sysrst_ctrl_ultra_low_pwr">sysrst_ctrl_ultra_low_pwr</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>
