# sysrst_ctrl Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="sysrst_ctrlauto_block_key_output">
      <td>SYSRST_CTRL.AUTO_BLOCK_KEY_OUTPUT</td>
      <td>sysrst_ctrl block can be configured to override the output value of specific passthrough signals,depending on whether certain input signals are asserted or not</td>
    </tr>
    <tr id="sysrst_ctrlcombo_detect">
      <td>SYSRST_CTRL.COMBO_DETECT</td>
      <td>sys_rst_ctrl block can be configured to detect input key combinationswith optional precondition</td>
    </tr>
    <tr id="sysrst_ctrlflash_write_protect">
      <td>SYSRST_CTRL.FLASH_WRITE_PROTECT</td>
      <td>Upon reset, the flash_wp_l_o signal will be asserted active low.The software can release flash_wp_l_o explicitly by setting PIN_OUT_CTL.FLASH_WP_L to 0 when needed.</td>
    </tr>
    <tr id="sysrst_ctrlhardware_reset_stretch">
      <td>SYSRST_CTRL.HARDWARE_RESET_STRETCH</td>
      <td>When the top-level system is in reset, ec_rst_l_o will be asserted (active low).The power-on-reset value of PIN_ALLOWED_CTL.EC_RST_L_1 and PIN_OUT_CTL.EC_RST_L willguarantee that ec_rst_l_o remains asserted after system reset is released.</td>
    </tr>
    <tr id="sysrst_ctrlinput_triggered_interrupt">
      <td>SYSRST_CTRL.INPUT_TRIGGERED_INTERRUPT</td>
      <td>sysrst_ctrl block can be configured to assert interrupt based on a combination of input signal transitions</td>
    </tr>
    <tr id="sysrst_ctrlpinout_key_inversion_control">
      <td>SYSRST_CTRL.PINOUT_KEY_INVERSION_CONTROL</td>
      <td>sysrst_ctrl block can be programmed to override all output signals, and change the signal polarityof some of the input and output signals</td>
    </tr>
    <tr id="sysrst_ctrlpin_input_value_access">
      <td>SYSRST_CTRL.PIN_INPUT_VALUE_ACCESS</td>
      <td>sysrst_ctrl allows the software to read the raw input pin values via the PIN_IN_VALUE register like GPIOs.</td>
    </tr>
    <tr id="sysrst_ctrlultra_low_power_wakeup">
      <td>SYSRST_CTRL.ULTRA_LOW_POWER_WAKEUP</td>
      <td>sysrst_ctrl block can be programmed to detect certain specific signal transitions on theac_present_i, pwrb_in_i and lid_open_i inputs. After this transition is held for a programmed time,sysrst_ctrl block triggers z3_wakeup signal</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
IP sysrst_ctrl currently contains no **Feature → Specification** mapping

## Feature -> Testpoint Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Testpoints↓ : Features→</th>
    <th>SYSRST_CTRL.COMBO_DETECT</th>
    <th>SYSRST_CTRL.AUTO_BLOCK_KEY_OUTPUT</th>
    <th>SYSRST_CTRL.INPUT_TRIGGERED_INTERRUPT</th>
    <th>SYSRST_CTRL.ULTRA_LOW_POWER_WAKEUP</th>
    <th>SYSRST_CTRL.PINOUT_KEY_INVERSION_CONTROL</th>
    <th>SYSRST_CTRL.HARDWARE_RESET_STRETCH</th>
    <th>SYSRST_CTRL.FLASH_WRITE_PROTECT</th>
    <th>SYSRST_CTRL.PIN_INPUT_VALUE_ACCESS</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#input_output_inverted">input_output_inverted</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#combo_detect_ec_rst">combo_detect_ec_rst</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#combo_detect_ec_rst_with_pre_cond">combo_detect_ec_rst_with_pre_cond</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#combo_detect">combo_detect</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#combo_detect_with_pre_cond">combo_detect_with_pre_cond</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#auto_block_key_outputs">auto_block_key_outputs</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#keyboard_input_triggered_interrupt">keyboard_input_triggered_interrupt</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#pin_output_keyboard_inversion_control">pin_output_keyboard_inversion_control</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#pin_input_value_accessibility">pin_input_value_accessibility</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#ec_power_on_reset">ec_power_on_reset</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#flash_write_protect_output">flash_write_protect_output</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#ultra_low_power_test">ultra_low_power_test</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#sysrst_ctrl_feature_disable">sysrst_ctrl_feature_disable</a></th>
    <td></td>
    <td></td>
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
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_sysrst_ctrl_reset-egret">chip_sw_sysrst_ctrl_reset (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_sysrst_ctrl_reset-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_sysrst_ctrl_inputs-egret">chip_sw_sysrst_ctrl_inputs (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_sysrst_ctrl_inputs-egret">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_sysrst_ctrl_outputs-egret">chip_sw_sysrst_ctrl_outputs (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_sysrst_ctrl_in_irq-egret">chip_sw_sysrst_ctrl_in_irq (egret)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_sysrst_ctrl_in_irq-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_sysrst_ctrl_sleep_wakeup-egret">chip_sw_sysrst_ctrl_sleep_wakeup (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_sysrst_ctrl_sleep_wakeup-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_sysrst_ctrl_sleep_reset-egret">chip_sw_sysrst_ctrl_sleep_reset (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_sysrst_ctrl_sleep_reset-egret">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_sysrst_ctrl_sleep_reset-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_sysrst_ctrl_ec_rst_l-egret">chip_sw_sysrst_ctrl_ec_rst_l (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_sysrst_ctrl_ec_rst_l-egret">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_sysrst_ctrl_flash_wp_l-egret">chip_sw_sysrst_ctrl_flash_wp_l (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_sysrst_ctrl_flash_wp_l-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_sysrst_ctrl_ulp_z3_wakeup-egret">chip_sw_sysrst_ctrl_ulp_z3_wakeup (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_sysrst_ctrl_ulp_z3_wakeup-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>
</div>
</div>
