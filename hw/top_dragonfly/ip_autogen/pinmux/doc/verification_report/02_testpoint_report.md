# pinmux Testpoint Report

## AonWkupO_A
When register `wkup_cause` is 1, `pin_wkup_req_o` should also be 1.
`pin_wkup_req_o` is 0 only when all `wkup_cause` registers are 0.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxwkupcause">PINMUX.WKUP.CAUSE</a></td>
</tr>
  </tbody>
</table>

## DOutSelN_A
`dio_out_o` is connected to `periph_to_dio_i` if not in sleep mode.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxdioconnected">PINMUX.DIO.CONNECTED</a></td>
</tr>
  </tbody>
</table>

## DOutSelOeN_A
`dio_oe_o` is connected to `periph_to_dio_oe_i` if not in sleep mode.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxdioconnected">PINMUX.DIO.CONNECTED</a><br><a href="01_feature_report.md#pinmuxdioen">PINMUX.DIO.EN</a></td>
</tr>
  </tbody>
</table>

## DftJtagI_A
When Dft tap is selected and `lc_dft_en_i` is On for the past two clock cycles
due to the synchronizer, the corresponding `mio_out_o` and `mio_out_oe` should be equal
to `dft_jtag_i`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxjtagdft">PINMUX.JTAG.DFT</a></td>
</tr>
  </tbody>
</table>

## DftJtagO1Backward_A
`dft_jtag_o` pins are ones if one of the following conditions are met:

- Dft Jtag is enabled and the corresponding pins are 1.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxjtagdft">PINMUX.JTAG.DFT</a></td>
</tr>
  </tbody>
</table>

## DftJtagOBackward_A
`dft_jtag_o` pins are equal to the corresponding `mio_in_i` inputs if one of the
following conditions are met:

- Dft Jtag is disabled and the corresponding pins are 0.
- Dft Jtag is enabled.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxjtagdft">PINMUX.JTAG.DFT</a></td>
</tr>
  </tbody>
</table>

## DftJtagODefault_A
`dft_jtag_o` should stay 0 if tap_strap did not select DFT_tap or the `lc_dft_en_i`
input is Off for the past two clock cycles due to the synchronizer.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## DftJtagWScanmode_A
In scanmode, when tap_strap select DFT_tap and `lc_dft_en_i` is On for the past
two clock cycles due to the synchronizer, `lc_jtag_o` must be equal to the
corresponding `mio_in_i` pins based on the `TargetCfg` configuration except the
`jtag_trst` pin, which must be equal to `rst_ni`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxjtagdft">PINMUX.JTAG.DFT</a><br><a href="01_feature_report.md#pinmuxjtagscanmode">PINMUX.JTAG.SCANMODE</a></td>
</tr>
  </tbody>
</table>

## DftJtagWoScanmode_A
Not in scanmode, when tap_strap select DFT_tap and `lc_dft_en_i` is On for the past
two clock cycles due to the synchronizer, `lc_jtag_o` must be equal to the
corresponding `mio_in_i` pins based on the `TargetCfg` configuration.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxjtagdft">PINMUX.JTAG.DFT</a></td>
</tr>
  </tbody>
</table>

## DftStrapTestOStrapStable_A
`dft_strap_test_o.valid` once set, `dft_strap_test_o.straps` should stay stable.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## DftStrapTestOValidStable_A
`dft_strap_test_o.valid` once set to 1 will stay high until reset.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## DftStrapTestO_A
When `lc_dft_en_i` is On for the past two clock cycles due to the synchronizer,
`dft_strap_test_o.valid` must be 1, and `dft_strap_test_o.straps` should be equal to
the corresponding `mio_in_i` index.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## Dio0Backward_A
`dio_out_o` should output 0 only if one of the following conditions meets:

- The corresponding `periph_to_dio_i` is 0.
- In sleep mode, register `dio_pad_sleep_mode` is set to 0 or 2.
- In sleep mode, previous `dio_out_o` is 0 and `dio_pad_sleep_mode` is set to 3.
- In sleep mode, previous `dio_out_o` is 0 and input `sleep_en_i` is not at posedge.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxdioconnected">PINMUX.DIO.CONNECTED</a><br><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## Dio1Backward_A
`dio_out_o` should output 1 only if one of the following conditions meets:

- The corresponding `periph_to_dio_i` is 1.
- In sleep mode, register `dio_pad_sleep_mode` is set to 1.
- In sleep mode, previous `dio_out_o` is 1 and `dio_pad_sleep_mode` is set to 3.
- In sleep mode, previous `dio_out_o` is 1 and input `sleep_en_i` is not at posedge.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxdioconnected">PINMUX.DIO.CONNECTED</a><br><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## DioAttrO_A
`dio_attr_o` should be equal to corresponding `dio_pad_attr` register value and
TargetCfg's dio_pad_type configuration.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxdioattrs">PINMUX.DIO.ATTRS</a></td>
</tr>
  </tbody>
</table>

## DioInSelN_A
This assertion checks that `dio_to_periph_o` is directly connected to `dio_in_i`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxdioconnected">PINMUX.DIO.CONNECTED</a></td>
</tr>
  </tbody>
</table>

## DioOe0Backward_A
`dio_oe_o` should output 0 only if one of the following conditions meets:

- The corresponding `periph_to_dio_i` is 0.
- In sleep mode, register `dio_pad_sleep_mode` is set to 2.
- In sleep mode, previous `dio_oe_o` is 0 and `dio_pad_sleep_mode` is set to 3.
- In sleep mode, previous `dio_oe_o` is 0 and input `sleep_en_i` is not at posedge.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxdioconnected">PINMUX.DIO.CONNECTED</a><br><a href="01_feature_report.md#pinmuxdioen">PINMUX.DIO.EN</a><br><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## DioOe1Backward_A
`dio_oe_o` should output 1 only if one of the following conditions meets:

- The corresponding `periph_to_dio_i` is 1.
- In sleep mode, register `dio_pad_sleep_mode` is set to 0 or 1.
- In sleep mode, previous `dio_oe_o` is 1 and `dio_pad_sleep_mode` is set to 3.
- In sleep mode, previous `dio_oe_o` is 1 and input `sleep_en_i` is not at posedge.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxdioconnected">PINMUX.DIO.CONNECTED</a><br><a href="01_feature_report.md#pinmuxdioen">PINMUX.DIO.EN</a><br><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## DioOeSleepMode0_A
At posedge of `sleep_en_i`, if register `dio_pad_sleep_en` is 1 and
`dio_pad_sleep_mode` is 0, which means the pad is driven zero in deep sleep mode.
In the meantime, if register `dio_pad_sleep_status` is not written via TLUL interface
to clear the sleep status, the corresponding `dio_oe_o` must be 1.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## DioOeSleepMode1_A
At posedge of `sleep_en_i`, if register `dio_pad_sleep_en` is 1 and
`dio_pad_sleep_mode` is 1, which means the pad is driven one in deep sleep mode.
In the meantime, if register `dio_pad_sleep_status` is not written via TLUL interface
to clear the sleep status, the corresponding `dio_oe_o` must be 1.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## DioOeSleepMode2_A
At posedge of `sleep_en_i`, if register `dio_pad_sleep_en` is 1 and
`dio_pad_sleep_mode` is 2, which means the pad is driven high-Z in deep sleep mode.
In the meantime, if register `dio_pad_sleep_status` is not written via TLUL interface
to clear the sleep status, the corresponding `dio_oe_o` must be 0.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## DioOeSleepMode3_A
At posedge of `sleep_en_i`, if register `dio_pad_sleep_en` is 1 and
`dio_pad_sleep_mode` is 3, which means the pad keeps last driven value in deep sleep
mode.
In the meantime, if register `dio_pad_sleep_status` is not written via TLUL interface
to clear the sleep status, the corresponding `dio_oe_o` should be stable.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## DioOeSleepStable_A
If not at posedge of `sleep_en_i`, and in the meantime, if register
`dio_pad_sleep_status` is not written via TLUL interface to clear the sleep status, the
corresponding `dio_oe_o` should be stable.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## DioSleepMode0_A
At posedge of `sleep_en_i`, if register `dio_pad_sleep_en` is 1 and
`dio_pad_sleep_mode` is 0, which means the pad is driven zero in deep sleep mode.
In the meantime, if register `dio_pad_sleep_status` is not written via TLUL interface
to clear the sleep status, the corresponding `dio_out_o` must be 0.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## DioSleepMode1_A
At posedge of `sleep_en_i`, if register `dio_pad_sleep_en` is 1 and
`dio_pad_sleep_mode` is 1, which means the pad is driven one in deep sleep mode.
In the meantime, if register `dio_pad_sleep_status` is not written via TLUL interface
to clear the sleep status, the corresponding `dio_out_o` must be 1.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## DioSleepMode2_A
At posedge of `sleep_en_i`, if register `dio_pad_sleep_en` is 1 and
`dio_pad_sleep_mode` is 2, which means the pad is driven high-Z in deep sleep mode.
In the meantime, if register `dio_pad_sleep_status` is not written via TLUL interface
to clear the sleep status, the corresponding `dio_out_o` must be 0.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## DioSleepMode3_A
At posedge of `sleep_en_i`, if register `dio_pad_sleep_en` is 1 and
`dio_pad_sleep_mode` is 3, which means the pad keeps last driven value in deep sleep
mode.
In the meantime, if register `dio_pad_sleep_status` is not written via TLUL interface
to clear the sleep status, the corresponding `dio_out_o` should be stable.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## DioSleepStable_A
If not at posedge of `sleep_en_i`, and in the meantime, if register
`dio_pad_sleep_status` is not written via TLUL interface to clear the sleep status, the
corresponding `dio_out_o` should be stable.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## InSel0_A
When register `periph_insel` is set to 0, which means the selected input is constant
zero, the corresponding `mio_to_periph_o` must be 0.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmioinsel">PINMUX.MIO.INSEL</a></td>
</tr>
  </tbody>
</table>

## InSel1_A
When register `periph_insel` is set to 1, which means the selected input is constant
one, the corresponding `mio_to_periph_o` must be 1.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmioinsel">PINMUX.MIO.INSEL</a></td>
</tr>
  </tbody>
</table>

## InSelN_A
When register `periph_insel` is set to any value between 2 and
(2 + number of MioPads) and the select index is not jtag, the corresponding
`mio_to_periph_o` must be equal to the related `mio_in_i` value.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmioinsel">PINMUX.MIO.INSEL</a><br><a href="01_feature_report.md#pinmuxmiomux">PINMUX.MIO.MUX</a></td>
</tr>
  </tbody>
</table>

## InSelOOB_A
When register `periph_insel` is set to any value larger than
(2 + number of MioPads), the corresponding `mio_to_periph_o` must be 0.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmioinsel">PINMUX.MIO.INSEL</a></td>
</tr>
  </tbody>
</table>

## LcJtagI_A
When Lc tap is selected, the corresponding `mio_out_o` and `mio_out_oe` should be
equal to `lc_jtag_i`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxjtaglc">PINMUX.JTAG.LC</a></td>
</tr>
  </tbody>
</table>

## LcJtagOBackward_A
`lc_jtag_o` pins are equal to the corresponding `mio_in_i` inputs if one of the
following conditions are met:

- Lc Jtag is disabled and the corresponding pins are 0.
- Lc Jtag is enabled.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxjtaglc">PINMUX.JTAG.LC</a></td>
</tr>
  </tbody>
</table>

## LcJtagODefault_A
`lc_jtag_o` should stay 0 if tap_strap did not select LC_tap.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## LcJtagWScanmode_A
In scanmode, when tap_strap select LC_tap, `lc_jtag_o` must be equal to the
corresponding `mio_in_i` pins based on the `TargetCfg` configuration except the
`jtag_trst` pin, which must be equal to `rst_ni`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxjtaglc">PINMUX.JTAG.LC</a><br><a href="01_feature_report.md#pinmuxjtagscanmode">PINMUX.JTAG.SCANMODE</a></td>
</tr>
  </tbody>
</table>

## LcJtagWoScanmode_A
Not in scanmode, when tap_strap select LC_tap, `lc_jtag_o` must be equal to the
corresponding `mio_in_i` pins based on the `TargetCfg` configuration.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxjtaglc">PINMUX.JTAG.LC</a></td>
</tr>
  </tbody>
</table>

## MioAttrO_A
`mio_attr_o` should be equal to corresponding `mio_pad_attr` register value and
TargetCfg's mio_pad_type configuration.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmioattrs">PINMUX.MIO.ATTRS</a></td>
</tr>
  </tbody>
</table>

## MioJtagAttrO_A
If JTAG is enabled, each padring attribute should be clamped to zero, except that
Schmitt triggering should be enabled for the tck and trst pads.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmioattrs">PINMUX.MIO.ATTRS</a></td>
</tr>
  </tbody>
</table>

## MioOe0Backward_A
`mio_oe_o` should output 0 only if one of the following conditions meets:

- Register `mio_insel` is set to 2.
- The corresponding `periph_to_mio_oe_i` is 0.
- Sleep mode is enabled.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmioen">PINMUX.MIO.EN</a><br><a href="01_feature_report.md#pinmuxmiomux">PINMUX.MIO.MUX</a><br><a href="01_feature_report.md#pinmuxmiooutsel">PINMUX.MIO.OUTSEL</a><br><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a></td>
</tr>
  </tbody>
</table>

## MioOe1Backward_A
`mio_oe_o` should output 1 only if one of the following conditions meets:

- Register `mio_insel` is set to 0 or 1.
- The corresponding `periph_to_mio_oe_i` is 1.
- Sleep mode is enabled.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmioen">PINMUX.MIO.EN</a><br><a href="01_feature_report.md#pinmuxmiomux">PINMUX.MIO.MUX</a><br><a href="01_feature_report.md#pinmuxmiooutsel">PINMUX.MIO.OUTSEL</a><br><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a></td>
</tr>
  </tbody>
</table>

## MioOeSleep0Backward_A
`mio_oe_o` should output 0 only if one of the following conditions meets:

- In sleep mode, register `mio_pad_sleep_mode` is set to 2.
- In sleep mode, previous `mio_oe_o` is 0 and `mio_pad_sleep_mode` is set to 3.
- In sleep mode, previous `mio_oe_o` is 0 and input `sleep_en_i` is not at posedge.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## MioOeSleep1Backward_A
`mio_oe_o` should output 1 only if one of the following conditions meets:

- In sleep mode, register `mio_pad_sleep_mode` is set to 0 or 1.
- In sleep mode, previous `mio_oe_o` is 1 and `mio_pad_sleep_mode` is set to 3.
- In sleep mode, previous `mio_oe_o` is 1 and input `sleep_en_i` is not at posedge.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## MioOeSleepMode0_A
At posedge of `sleep_en_i`, if register `mio_pad_sleep_en` is 1 and
`mio_pad_sleep_mode` is 0, which means the pad is driven zero in deep sleep mode.
In the meantime, if register `mio_pad_sleep_status` is not written via TLUL interface
to clear the sleep status, the corresponding `mio_oe_o` must be 1.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## MioOeSleepMode1_A
At posedge of `sleep_en_i`, if register `mio_pad_sleep_en` is 1 and
`mio_pad_sleep_mode` is 1, which means the pad is driven one in deep sleep mode.
In the meantime, if register `mio_pad_sleep_status` is not written via TLUL interface
to clear the sleep status, the corresponding `mio_oe_o` must be 1.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## MioOeSleepMode2_A
At posedge of `sleep_en_i`, if register `mio_pad_sleep_en` is 1 and
`mio_pad_sleep_mode` is 2, which means the pad is driven high-Z in deep sleep mode.
In the meantime, if register `mio_pad_sleep_status` is not written via TLUL interface
to clear the sleep status, the corresponding `mio_oe_o` must be 0.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## MioOeSleepMode3_A
At posedge of `sleep_en_i`, if register `mio_pad_sleep_en` is 1 and
`mio_pad_sleep_mode` is 3, which means the pad keeps last driven value in deep sleep
mode.
In the meantime, if register `mio_pad_sleep_status` is not written via TLUL interface
to clear the sleep status, the corresponding `mio_oe_o` should be stable.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## MioOeSleepStable_A
If not at posedge of `sleep_en_i`, and in the meantime, if register
`mio_pad_sleep_status` is not written via TLUL interface to clear the sleep status, the
corresponding `mio_oe_o` should be stable.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## MioOut0Backward_A
`mio_out_o` should output 0 only if one of the following conditions meets:

- Register `mio_outsel` is set to 0 or 2.
- The corresponding `periph_to_mio_i` is 0.
- Sleep mode is enabled.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmiomux">PINMUX.MIO.MUX</a><br><a href="01_feature_report.md#pinmuxmiooutsel">PINMUX.MIO.OUTSEL</a><br><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a></td>
</tr>
  </tbody>
</table>

## MioOut1Backward_A
`mio_out_o` should output 1 only if one of the following conditions meets:

- Register `mio_outsel` is set to 1.
- The corresponding `periph_to_mio_i` is 1.
- Sleep mode is enabled.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmiomux">PINMUX.MIO.MUX</a><br><a href="01_feature_report.md#pinmuxmiooutsel">PINMUX.MIO.OUTSEL</a><br><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a></td>
</tr>
  </tbody>
</table>

## MioSleep0Backward_A
`mio_out_o` should output 0 only if one of the following conditions meets:

- In sleep mode, register `mio_pad_sleep_mode` is set to 0 or 2.
- In sleep mode, previous `mio_out_o` is 0 and `mio_pad_sleep_mode` is set to 3.
- In sleep mode, previous `mio_out_o` is 0 and input `sleep_en_i` is not at posedge.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## MioSleep1Backward_A
`mio_out_o` should output 1 only if one of the following conditions meets:

- In sleep mode, register `mio_pad_sleep_mode` is set to 1.
- In sleep mode, previous `mio_out_o` is 1 and `mio_pad_sleep_mode` is set to 3.
- In sleep mode, previous `mio_out_o` is 1 and input `sleep_en_i` is not at posedge.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## MioSleepMode0_A
At posedge of `sleep_en_i`, if register `mio_pad_sleep_en` is 1 and
`mio_pad_sleep_mode` is 0, which means the pad is driven zero in deep sleep mode.
If, in the meantime, register `mio_pad_sleep_status` is not written via TLUL interface
to clear the sleep status, the corresponding `mio_out_o` must be 0.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## MioSleepMode1_A
At posedge of `sleep_en_i`, if register `mio_pad_sleep_en` is 1 and
`mio_pad_sleep_mode` is 1, which means the pad is driven one in deep sleep mode.
In the meantime, if register `mio_pad_sleep_status` is not written via TLUL interface
to clear the sleep status, the corresponding `mio_out_o` must be 1.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## MioSleepMode2_A
At posedge of `sleep_en_i`, if register `mio_pad_sleep_en` is 1 and
`mio_pad_sleep_mode` is 2, which means the pad is driven high-Z in deep sleep mode.
In the meantime, if register `mio_pad_sleep_status` is not written via TLUL interface
to clear the sleep status, the corresponding `mio_out_o` must be 0.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## MioSleepMode3_A
At posedge of `sleep_en_i`, if register `mio_pad_sleep_en` is 1 and
`mio_pad_sleep_mode` is 3, which means the pad keeps last driven value in deep sleep
mode.
In the meantime, if register `mio_pad_sleep_status` is not written via TLUL interface
to clear the sleep status, the corresponding `mio_out_o` should be stable.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepmode">PINMUX.SLEEP.MODE</a><br><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## MioSleepStable_A
If not at posedge of `sleep_en_i`, and in the meantime register
`mio_pad_sleep_status` is not written via TLUL interface to clear the sleep status, the
corresponding `mio_out_o` should be stable.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxsleepstable">PINMUX.SLEEP.STABLE</a></td>
</tr>
  </tbody>
</table>

## MioToPeriph0Backward_A
`mio_to_periph_o` should output 0 only if one of the following conditions meets:

- Register `periph_insel` is set to 0.
- The corresponding `mio_in_i` is 0.
- Jtag is enabled.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmioinsel">PINMUX.MIO.INSEL</a><br><a href="01_feature_report.md#pinmuxmiomux">PINMUX.MIO.MUX</a></td>
</tr>
  </tbody>
</table>

## MioToPeriph1Backward_A
`mio_to_periph_o` should output 1 only if one of the following conditions meets:

- Register `periph_insel` is set to 1.
- The corresponding `mio_in_i` is 1.
- Jtag is enabled.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmioinsel">PINMUX.MIO.INSEL</a><br><a href="01_feature_report.md#pinmuxmiomux">PINMUX.MIO.MUX</a></td>
</tr>
  </tbody>
</table>

## OutSel0_A
When register `mio_outsel` is set to 0 and is not in sleep mode or jtag, which means
the selected output is constant zero, the corresponding `mio_out_o` must be 0.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmiooutsel">PINMUX.MIO.OUTSEL</a></td>
</tr>
  </tbody>
</table>

## OutSel1_A
When register `mio_outsel` is set to 1 and is not in sleep mode or jtag, which means
the selected output is constant one, the corresponding `mio_out_o` must be 1.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmiooutsel">PINMUX.MIO.OUTSEL</a></td>
</tr>
  </tbody>
</table>

## OutSel2_A
When register `mio_outsel` is set to 2 and is not in sleep mode or jtag, which means
the selected output is driving high-Z, the corresponding `mio_out_o` must be 0.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmiooutsel">PINMUX.MIO.OUTSEL</a></td>
</tr>
  </tbody>
</table>

## OutSelN_A
When register `mio_outsel` is set to any value between 3 and
(3 + Number of periph out) and is not in sleep mode or jtag, the corresponding
`mio_out_o` must be equal to the related `periph_to_mio_i` value.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmiomux">PINMUX.MIO.MUX</a><br><a href="01_feature_report.md#pinmuxmiooutsel">PINMUX.MIO.OUTSEL</a></td>
</tr>
  </tbody>
</table>

## OutSelOOB_A
When register `mio_outsel` is set to any value larger than
(3 + Number of periph out) and is not in sleep mode, the corresponding `mio_out_o` must
be 0.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmiooutsel">PINMUX.MIO.OUTSEL</a></td>
</tr>
  </tbody>
</table>

## OutSelOe0_A
When register `mio_outsel` is set to 0 and is not in sleep mode or jtag, the
corresponding `mio_oe_o` must be 1.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmioen">PINMUX.MIO.EN</a><br><a href="01_feature_report.md#pinmuxmiooutsel">PINMUX.MIO.OUTSEL</a></td>
</tr>
  </tbody>
</table>

## OutSelOe1_A
When register `mio_outsel` is set to 1 and is not in sleep mode or jtag, the
corresponding `mio_oe_o` must be 1.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmioen">PINMUX.MIO.EN</a><br><a href="01_feature_report.md#pinmuxmiooutsel">PINMUX.MIO.OUTSEL</a></td>
</tr>
  </tbody>
</table>

## OutSelOe2_A
When register `mio_outsel` is set to 2 and is not in sleep mode or jtag, which
indicates driving high-Z to the selected output, the corresponding `mio_oe_o` must
be 0.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmioen">PINMUX.MIO.EN</a><br><a href="01_feature_report.md#pinmuxmiooutsel">PINMUX.MIO.OUTSEL</a></td>
</tr>
  </tbody>
</table>

## OutSelOeN_A
When register `mio_outsel` is set to any value between 3 and
(3 + Number of periph out) and is not in sleep mode or jtag, the corresponding
`mio_oe_o` must be equal to the related `periph_to_mio_oe_i` value.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmioen">PINMUX.MIO.EN</a><br><a href="01_feature_report.md#pinmuxmiomux">PINMUX.MIO.MUX</a><br><a href="01_feature_report.md#pinmuxmiooutsel">PINMUX.MIO.OUTSEL</a></td>
</tr>
  </tbody>
</table>

## OutSelOeOOB_A
When register `mio_outsel` is set to any value larger than
(3 + Number of periph out) and is not in sleep mode, the corresponding `mio_oe_o` must
be 0.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxmioen">PINMUX.MIO.EN</a><br><a href="01_feature_report.md#pinmuxmiooutsel">PINMUX.MIO.OUTSEL</a></td>
</tr>
  </tbody>
</table>

## RvJtagI_A
When Rv tap is selected and `lc_hw_debug_en_i` is On for the past two clock cycles
due to the synchronizer, the corresponding `mio_out_o` and `mio_out_oe` should be equal
to `rv_jtag_i`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxjtagrv">PINMUX.JTAG.RV</a></td>
</tr>
  </tbody>
</table>

## RvJtagOBackward_A
`rv_jtag_o` pins are equal to the corresponding `mio_in_i` inputs if one of the
following conditions are met:

- Rv Jtag is disabled and the corresponding pins are 0.
- Rv Jtag is enabled.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxjtagrv">PINMUX.JTAG.RV</a></td>
</tr>
  </tbody>
</table>

## RvJtagODefault_A
`rv_jtag_o` should stay 0 if tap_strap did not select RV_tap or `lc_hw_debug_en_i`
input is Off for the past two clock cycles due to the synchronizer.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## RvJtagWScanmode_A
In scanmode, When tap_strap select RV_tap and `lc_hw_debug_en_i` is On for the past
two clock cycles due to the synchronizer, then `rv_jtag_o` must be equal to the
corresponding `mio_in_i` pins based on the `TargetCfg` configuration except the
`jtag_trst` pin, which must be equal to `rst_ni`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxjtagrv">PINMUX.JTAG.RV</a><br><a href="01_feature_report.md#pinmuxjtagscanmode">PINMUX.JTAG.SCANMODE</a></td>
</tr>
  </tbody>
</table>

## RvJtagWoScanmode_A
Not in scanmode, when tap_strap select RV_tap and `lc_hw_debug_en_i` input is On for
the past two clock cycles due to the synchronizer, then `rv_jtag_o` must be equal to
the corresponding `mio_in_i` pins based on the `TargetCfg` configuration.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxjtagrv">PINMUX.JTAG.RV</a></td>
</tr>
  </tbody>
</table>

## TapStrap0_A
If `dft_hold_tap_sel_i` is 0 and `lc_dft_en_i` is On for the past two clock cycles
due to the synchronizer, or `strap_en_i` is 1.
Then tap_strap[0] must be equal to the past value of corresponding `mio_in_i`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## TapStrap_A
If `dft_hold_tap_sel_i` is 0 and `lc_dft_en_i` is On for the past two clock cycles
due to the synchronizer, or `strap_en_i` is 1.
And in the meantime, if `lc_hw_debug_en_i` is On for the past two clock cycles due to
the synchronizer, then tap_strap must be equal to the past value of corresponding
`mio_in_i`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## UsbAonWakeAckUpwrI_A
`usb_aon_wake_ack_i` should be connected directly to usbdev's
`usb_aon_woken_upwr_i`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxusb_connection">PINMUX.USB_CONNECTION</a></td>
</tr>
  </tbody>
</table>

## UsbAonWakeEnUpwrI_A
`usb_aon_wake_en_i` should be connected directly to usbdev's
`usb_aon_wake_en_upwr_i`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxusb_connection">PINMUX.USB_CONNECTION</a></td>
</tr>
  </tbody>
</table>

## UsbBusResetO_A
`usb_bus_reset_o` should be connected directly to usbdev's `bus_reset_alw_o`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxusb_connection">PINMUX.USB_CONNECTION</a></td>
</tr>
  </tbody>
</table>

## UsbDnpullupEnO_A
`usb_dnpullup_en_o` should be connected directly to usbdev's
`usb_dnpullup_en_o`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxusb_connection">PINMUX.USB_CONNECTION</a></td>
</tr>
  </tbody>
</table>

## UsbDnpullupEnUpwrI_A
`usb_dnpullup_en_upwr_i` should be connected directly to usbdev's
`usb_dnpullup_en_upwr_i`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxusb_connection">PINMUX.USB_CONNECTION</a></td>
</tr>
  </tbody>
</table>

## UsbDppullupEnO_A
`usb_dppullup_en_o` should be connected directly to usbdev's
`usb_dppullup_en_o`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxusb_connection">PINMUX.USB_CONNECTION</a></td>
</tr>
  </tbody>
</table>

## UsbDppullupEnUpwrI_A
`usb_dppullup_en_upwr_i` should be connected directly to usbdev's
`usb_dppullup_en_upwr_i`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxusb_connection">PINMUX.USB_CONNECTION</a></td>
</tr>
  </tbody>
</table>

## UsbOutOfRstI_A
`usb_out_of_rst_i` should be connected directly to usbdev's `usb_out_of_rst_upwr_i`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxusb_connection">PINMUX.USB_CONNECTION</a></td>
</tr>
  </tbody>
</table>

## UsbSenseLostO_A
`usb_sense_lost_o` should be connected directly to usbdev's `bus_lost_alw_o`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxusb_connection">PINMUX.USB_CONNECTION</a></td>
</tr>
  </tbody>
</table>

## UsbSleepEnI_A
`sleep_en_i` should be connected directly to usbdev's `low_power_alw_i`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxusb_connection">PINMUX.USB_CONNECTION</a></td>
</tr>
  </tbody>
</table>

## UsbStateDebugO_A
`usb_state_debug_o` should be connected directly to usbdev's `bus_debug_o`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxusb_connection">PINMUX.USB_CONNECTION</a></td>
</tr>
  </tbody>
</table>

## UsbSuspendI_A
`usb_suspend_i` should be connected directly to usbdev's `usb_suspended_upwr_i`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxusb_connection">PINMUX.USB_CONNECTION</a></td>
</tr>
  </tbody>
</table>

## UsbWkupReqO_A
`usb_wkup_req_o` should be connected directly to usbdev's `wake_rep_alw_o`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxusb_connection">PINMUX.USB_CONNECTION</a></td>
</tr>
  </tbody>
</table>

## WkupCause0_A
Register `wkup_cause` is 0 only when none of the above wakeup conditions is met.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxwkupcause">PINMUX.WKUP.CAUSE</a><br><a href="01_feature_report.md#pinmuxwkupmode">PINMUX.WKUP.MODE</a></td>
</tr>
  </tbody>
</table>

## WkupCause1_A
Register `wkup_cause` is 1 when at least one of the above wakeup conditions is met.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxwkupcause">PINMUX.WKUP.CAUSE</a><br><a href="01_feature_report.md#pinmuxwkupmode">PINMUX.WKUP.MODE</a></td>
</tr>
  </tbody>
</table>

## WkupCauseQ_A
When `wkup_cause` register's `de` attribute is set to 1 and user is not writing to
`wkup_cause` at the same cycle, then `wkup_cause.q` should be set to 1.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxwkupcause">PINMUX.WKUP.CAUSE</a></td>
</tr>
  </tbody>
</table>

## WkupEdge_A
When register `wkup_detector_en` is set to 1 and `wkup_detector.mode` is set to 2,
which means either rising or falling edge is used to detect wakeup. If variable
`final_pin_val` is at posedge or negedge, then `wkup_cause` register's `de` attribute
should be set to 1.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxwkupmode">PINMUX.WKUP.MODE</a></td>
</tr>
  </tbody>
</table>

## WkupNegedge_A
When register `wkup_detector_en` is set to 1 and `wkup_detector.mode` is set to 1,
which means falling edge is used to detect wakeup. If variable `final_pin_val` is at
negedge, then `wkup_cause` register's `de` attribute should be set to 1.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxwkupmode">PINMUX.WKUP.MODE</a></td>
</tr>
  </tbody>
</table>

## WkupPosedge_A
When register `wkup_detector_en` is set to 1 and `wkup_detector.mode` is set to 0,
which means rising edge is used to detect wakeup. If variable `final_pin_val` is at
posedge then `wkup_cause` register's `de` attribute should be set to 1.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxwkupmode">PINMUX.WKUP.MODE</a></td>
</tr>
  </tbody>
</table>

## WkupTimedHigh_A
When register `wkup_detector_en` is set to 1 and `wkup_detector.mode` is set to 3,
which means postive pulse cycles are used to detect wakeup. If variable `final_pin_val`
stays high longer than the threshold, then `wkup_cause` register's `de` attribute
should be set to 1.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxwkupmode">PINMUX.WKUP.MODE</a></td>
</tr>
  </tbody>
</table>

## WkupTimedLow_A
When register `wkup_detector_en` is set to 1 and `wkup_detector.mode` is set to 4,
which means negative pulse cycles are used to detect wakeup. If variable `final_pin_val`
stays low longer than the threshold, then `wkup_cause` register's `de` attribute should
be set to 1.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pinmux_assert">pinmux_assert</a></td>
  <td><a href="01_feature_report.md#pinmuxwkupmode">PINMUX.WKUP.MODE</a></td>
</tr>
  </tbody>
</table>
