# pinmux Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="pinmuxdioattrs">
      <td>PINMUX.DIO.ATTRS</td>
      <td>Pinmux keeps track of implementation-specific DIO pad attributes.</td>
    </tr>
    <tr id="pinmuxdioconnected">
      <td>PINMUX.DIO.CONNECTED</td>
      <td>DIO ports are directly connected to a given peripheral port. Communication betweenperipheral and DIO is disabled when in sleep mode.</td>
    </tr>
    <tr id="pinmuxdioen">
      <td>PINMUX.DIO.EN</td>
      <td>Signals from peripherals to DIO can be accompanied by an output-enable signal. Theoutput-enable is appropriately low or high depending on whether in sleep mode anddepending on the output-enable signal coming from the peripheral.</td>
    </tr>
    <tr id="pinmuxjtagdft">
      <td>PINMUX.JTAG.DFT</td>
      <td>Configuration allows selection of JTAG design-for-test TAP strap group. JTAGcommunication takes precedence over peripheral-MIO communication.</td>
    </tr>
    <tr id="pinmuxjtaglc">
      <td>PINMUX.JTAG.LC</td>
      <td>Configuration allows selection of JTAG life cycle TAP strap group. JTAG communicationtakes precedence over peripheral-MIO communication.</td>
    </tr>
    <tr id="pinmuxjtagrv">
      <td>PINMUX.JTAG.RV</td>
      <td>Configuration allows selection of JTAG RISC-V TAP strap group. JTAG communicationtakes precedence over peripheral-MIO communication.</td>
    </tr>
    <tr id="pinmuxjtagscanmode">
      <td>PINMUX.JTAG.SCANMODE</td>
      <td>If scanmode is enabled, JTAG `trst_ni` comes from internal reset signal; else, JTAGreset matches `trst_ni` from MIO.</td>
    </tr>
    <tr id="pinmuxmioattrs">
      <td>PINMUX.MIO.ATTRS</td>
      <td>Pinmux keeps track of impementation-specific MIO pad attributes. Attributes areconfigured differently when JTAG is used because JTAG uses MIO pads.</td>
    </tr>
    <tr id="pinmuxmioen">
      <td>PINMUX.MIO.EN</td>
      <td>Outputs to MIO can be accopanied by an output-enable signal, which is appropriatelyhigh or low based on the output value. Output-enable is appropriately high or lowdepending on whether or not in sleep mode or JTAG, depending on the output-enable signalcoming from the peripheral, and depending on if output should be high-Z.</td>
    </tr>
    <tr id="pinmuxmioinsel">
      <td>PINMUX.MIO.INSEL</td>
      <td>Signals sent to peripherals can be configurably tied to any MIO port or to a constantvalue (0 or 1). If the selected MIO port index is invalid, the output value should be 0.MIO-to-peripheral communication is disabled if JTAG is enabled or in sleep mode.</td>
    </tr>
    <tr id="pinmuxmiomux">
      <td>PINMUX.MIO.MUX</td>
      <td>Signals are correctly routed between any MIO port and any peripheral.</td>
    </tr>
    <tr id="pinmuxmiooutsel">
      <td>PINMUX.MIO.OUTSEL</td>
      <td>Signals sent to MIO can be configurably tied to any peripheral with availableconnections, to a constant value (0 or 1), or to high impedance. If the selectedperipheral index is invalid, the output value should be 0. Peripheral-to-MIOcommunication is disabled if JTAG is enabled or in sleep mode.</td>
    </tr>
    <tr id="pinmuxsleepmode">
      <td>PINMUX.SLEEP.MODE</td>
      <td>All MIO/DIO outputs are held at proper values during sleep mode. Sleep mode can beconfigured to drive pads to 0, 1, high-Z, or stable.</td>
    </tr>
    <tr id="pinmuxsleepstable">
      <td>PINMUX.SLEEP.STABLE</td>
      <td>All sleep mode values are held until sleep mode is cleared with a write from TL-UL.</td>
    </tr>
    <tr id="pinmuxusb_connection">
      <td>PINMUX.USB_CONNECTION</td>
      <td>Pinmux suports connectivity with USB module.</td>
    </tr>
    <tr id="pinmuxwkupcause">
      <td>PINMUX.WKUP.CAUSE</td>
      <td>Wakeup may be triggered by any one of the configured debounced-signal patterns.</td>
    </tr>
    <tr id="pinmuxwkupmode">
      <td>PINMUX.WKUP.MODE</td>
      <td>Wakeup detector can be configured to trigger on rising edge, falling edge, positivepulse cycles, or negative pulse cycles.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>PINMUX.MIO.INSEL</th>
    <th>PINMUX.MIO.OUTSEL</th>
    <th>PINMUX.MIO.EN</th>
    <th>PINMUX.MIO.ATTRS</th>
    <th>PINMUX.MIO.MUX</th>
    <th>PINMUX.DIO.EN</th>
    <th>PINMUX.DIO.ATTRS</th>
    <th>PINMUX.DIO.CONNECTED</th>
    <th>PINMUX.JTAG.LC</th>
    <th>PINMUX.JTAG.RV</th>
    <th>PINMUX.JTAG.DFT</th>
    <th>PINMUX.JTAG.SCANMODE</th>
    <th>PINMUX.WKUP.MODE</th>
    <th>PINMUX.WKUP.CAUSE</th>
    <th>PINMUX.SLEEP.MODE</th>
    <th>PINMUX.SLEEP.STABLE</th>
    <th>PINMUX.USB_CONNECTION</th>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#theory-of-operation">Theory of Operation</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#block-diagram-and-overview">Block Diagram and Overview</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#block-diagram-and-overview">X</a></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#block-diagram-and-overview">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#mio-and-dio-signal-categories">MIO and DIO Signal Categories</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#mio-and-dio-signal-categories">X</a></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#retention-and-wakeup-features">Retention and Wakeup Features</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#retention-and-wakeup-features">X</a></td>
    <td><a href="../theory_of_operation.md#retention-and-wakeup-features">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#pad-attributes">Pad Attributes</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#pad-attributes">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#muxing-matrix">Muxing Matrix</a></th>
    <td><a href="../theory_of_operation.md#muxing-matrix">X</a></td>
    <td><a href="../theory_of_operation.md#muxing-matrix">X</a></td>
    <td><a href="../theory_of_operation.md#muxing-matrix">X</a></td>
    <td></td>
    <td><a href="../theory_of_operation.md#muxing-matrix">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#retention-logic">Retention Logic</a></th>
    <td><a href="../theory_of_operation.md#retention-logic">X</a></td>
    <td><a href="../theory_of_operation.md#retention-logic">X</a></td>
    <td><a href="../theory_of_operation.md#retention-logic">X</a></td>
    <td></td>
    <td><a href="../theory_of_operation.md#retention-logic">X</a></td>
    <td><a href="../theory_of_operation.md#retention-logic">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#retention-logic">X</a></td>
    <td><a href="../theory_of_operation.md#retention-logic">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#wakeup-detectors">Wakeup Detectors</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#wakeup-detectors">X</a></td>
    <td><a href="../theory_of_operation.md#wakeup-detectors">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#strap-sampling-and-tap-isolation">Strap Sampling and TAP Isolation</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#strap-sampling-and-tap-isolation">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#strap-sampling-and-tap-isolation">X</a></td>
    <td><a href="../theory_of_operation.md#strap-sampling-and-tap-isolation">X</a></td>
    <td><a href="../theory_of_operation.md#strap-sampling-and-tap-isolation">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#generic-pad-wrapper">Generic Pad Wrapper</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#generic-pad-wrapper">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>
</div>
</div>


## Feature -> Testpoint Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Testpoints↓ : Features→</th>
    <th>PINMUX.MIO.INSEL</th>
    <th>PINMUX.MIO.OUTSEL</th>
    <th>PINMUX.MIO.EN</th>
    <th>PINMUX.MIO.ATTRS</th>
    <th>PINMUX.MIO.MUX</th>
    <th>PINMUX.DIO.EN</th>
    <th>PINMUX.DIO.ATTRS</th>
    <th>PINMUX.DIO.CONNECTED</th>
    <th>PINMUX.JTAG.LC</th>
    <th>PINMUX.JTAG.RV</th>
    <th>PINMUX.JTAG.DFT</th>
    <th>PINMUX.JTAG.SCANMODE</th>
    <th>PINMUX.WKUP.MODE</th>
    <th>PINMUX.WKUP.CAUSE</th>
    <th>PINMUX.SLEEP.MODE</th>
    <th>PINMUX.SLEEP.STABLE</th>
    <th>PINMUX.USB_CONNECTION</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#insel0_a">InSel0_A</a></th>
    <td><a href="02_testpoint_report.md#insel0_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#insel1_a">InSel1_A</a></th>
    <td><a href="02_testpoint_report.md#insel1_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#inseln_a">InSelN_A</a></th>
    <td><a href="02_testpoint_report.md#inseln_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#inseln_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#inseloob_a">InSelOOB_A</a></th>
    <td><a href="02_testpoint_report.md#inseloob_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#miotoperiph0backward_a">MioToPeriph0Backward_A</a></th>
    <td><a href="02_testpoint_report.md#miotoperiph0backward_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#miotoperiph0backward_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#miotoperiph1backward_a">MioToPeriph1Backward_A</a></th>
    <td><a href="02_testpoint_report.md#miotoperiph1backward_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#miotoperiph1backward_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#dioinseln_a">DioInSelN_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dioinseln_a">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#outsel0_a">OutSel0_A</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#outsel0_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#outsel1_a">OutSel1_A</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#outsel1_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#outsel2_a">OutSel2_A</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#outsel2_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#outseln_a">OutSelN_A</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#outseln_a">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#outseln_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#outseloob_a">OutSelOOB_A</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#outseloob_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#mioout0backward_a">MioOut0Backward_A</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#mioout0backward_a">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#mioout0backward_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#mioout0backward_a">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#mioout1backward_a">MioOut1Backward_A</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#mioout1backward_a">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#mioout1backward_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#mioout1backward_a">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#outseloe0_a">OutSelOe0_A</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#outseloe0_a">X</a></td>
    <td><a href="02_testpoint_report.md#outseloe0_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#outseloe1_a">OutSelOe1_A</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#outseloe1_a">X</a></td>
    <td><a href="02_testpoint_report.md#outseloe1_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#outseloe2_a">OutSelOe2_A</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#outseloe2_a">X</a></td>
    <td><a href="02_testpoint_report.md#outseloe2_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#outseloen_a">OutSelOeN_A</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#outseloen_a">X</a></td>
    <td><a href="02_testpoint_report.md#outseloen_a">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#outseloen_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#outseloeoob_a">OutSelOeOOB_A</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#outseloeoob_a">X</a></td>
    <td><a href="02_testpoint_report.md#outseloeoob_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#miooe0backward_a">MioOe0Backward_A</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#miooe0backward_a">X</a></td>
    <td><a href="02_testpoint_report.md#miooe0backward_a">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#miooe0backward_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#miooe0backward_a">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#miooe1backward_a">MioOe1Backward_A</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#miooe1backward_a">X</a></td>
    <td><a href="02_testpoint_report.md#miooe1backward_a">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#miooe1backward_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#miooe1backward_a">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#miosleepmode0_a">MioSleepMode0_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#miosleepmode0_a">X</a></td>
    <td><a href="02_testpoint_report.md#miosleepmode0_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#miosleepmode1_a">MioSleepMode1_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#miosleepmode1_a">X</a></td>
    <td><a href="02_testpoint_report.md#miosleepmode1_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#miosleepmode2_a">MioSleepMode2_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#miosleepmode2_a">X</a></td>
    <td><a href="02_testpoint_report.md#miosleepmode2_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#miosleepmode3_a">MioSleepMode3_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#miosleepmode3_a">X</a></td>
    <td><a href="02_testpoint_report.md#miosleepmode3_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#miosleepstable_a">MioSleepStable_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#miosleepstable_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#miooesleepmode0_a">MioOeSleepMode0_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#miooesleepmode0_a">X</a></td>
    <td><a href="02_testpoint_report.md#miooesleepmode0_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#miooesleepmode1_a">MioOeSleepMode1_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#miooesleepmode1_a">X</a></td>
    <td><a href="02_testpoint_report.md#miooesleepmode1_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#miooesleepmode2_a">MioOeSleepMode2_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#miooesleepmode2_a">X</a></td>
    <td><a href="02_testpoint_report.md#miooesleepmode2_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#miooesleepmode3_a">MioOeSleepMode3_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#miooesleepmode3_a">X</a></td>
    <td><a href="02_testpoint_report.md#miooesleepmode3_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#miooesleepstable_a">MioOeSleepStable_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#miooesleepstable_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#miosleep0backward_a">MioSleep0Backward_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#miosleep0backward_a">X</a></td>
    <td><a href="02_testpoint_report.md#miosleep0backward_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#miosleep1backward_a">MioSleep1Backward_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#miosleep1backward_a">X</a></td>
    <td><a href="02_testpoint_report.md#miosleep1backward_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#miooesleep0backward_a">MioOeSleep0Backward_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#miooesleep0backward_a">X</a></td>
    <td><a href="02_testpoint_report.md#miooesleep0backward_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#miooesleep1backward_a">MioOeSleep1Backward_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#miooesleep1backward_a">X</a></td>
    <td><a href="02_testpoint_report.md#miooesleep1backward_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#doutseln_a">DOutSelN_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#doutseln_a">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#doutseloen_a">DOutSelOeN_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#doutseloen_a">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#doutseloen_a">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#diosleepmode0_a">DioSleepMode0_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#diosleepmode0_a">X</a></td>
    <td><a href="02_testpoint_report.md#diosleepmode0_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#diosleepmode1_a">DioSleepMode1_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#diosleepmode1_a">X</a></td>
    <td><a href="02_testpoint_report.md#diosleepmode1_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#diosleepmode2_a">DioSleepMode2_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#diosleepmode2_a">X</a></td>
    <td><a href="02_testpoint_report.md#diosleepmode2_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#diosleepmode3_a">DioSleepMode3_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#diosleepmode3_a">X</a></td>
    <td><a href="02_testpoint_report.md#diosleepmode3_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#diosleepstable_a">DioSleepStable_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#diosleepstable_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#diooesleepmode0_a">DioOeSleepMode0_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#diooesleepmode0_a">X</a></td>
    <td><a href="02_testpoint_report.md#diooesleepmode0_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#diooesleepmode1_a">DioOeSleepMode1_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#diooesleepmode1_a">X</a></td>
    <td><a href="02_testpoint_report.md#diooesleepmode1_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#diooesleepmode2_a">DioOeSleepMode2_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#diooesleepmode2_a">X</a></td>
    <td><a href="02_testpoint_report.md#diooesleepmode2_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#diooesleepmode3_a">DioOeSleepMode3_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#diooesleepmode3_a">X</a></td>
    <td><a href="02_testpoint_report.md#diooesleepmode3_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#diooesleepstable_a">DioOeSleepStable_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#diooesleepstable_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dio0backward_a">Dio0Backward_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dio0backward_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dio0backward_a">X</a></td>
    <td><a href="02_testpoint_report.md#dio0backward_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dio1backward_a">Dio1Backward_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dio1backward_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dio1backward_a">X</a></td>
    <td><a href="02_testpoint_report.md#dio1backward_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#diooe0backward_a">DioOe0Backward_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#diooe0backward_a">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#diooe0backward_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#diooe0backward_a">X</a></td>
    <td><a href="02_testpoint_report.md#diooe0backward_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#diooe1backward_a">DioOe1Backward_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#diooe1backward_a">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#diooe1backward_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#diooe1backward_a">X</a></td>
    <td><a href="02_testpoint_report.md#diooe1backward_a">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#mioattro_a">MioAttrO_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#mioattro_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#miojtagattro_a">MioJtagAttrO_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#miojtagattro_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#dioattro_a">DioAttrO_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dioattro_a">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#wkupposedge_a">WkupPosedge_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#wkupposedge_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#wkupnegedge_a">WkupNegedge_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#wkupnegedge_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#wkupedge_a">WkupEdge_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#wkupedge_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#wkuptimedhigh_a">WkupTimedHigh_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#wkuptimedhigh_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#wkuptimedlow_a">WkupTimedLow_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#wkuptimedlow_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#wkupcauseq_a">WkupCauseQ_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#wkupcauseq_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#aonwkupo_a">AonWkupO_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#aonwkupo_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#wkupcause0_a">WkupCause0_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#wkupcause0_a">X</a></td>
    <td><a href="02_testpoint_report.md#wkupcause0_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#wkupcause1_a">WkupCause1_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#wkupcause1_a">X</a></td>
    <td><a href="02_testpoint_report.md#wkupcause1_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#lcjtagwoscanmode_a">LcJtagWoScanmode_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#lcjtagwoscanmode_a">X</a></td>
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
    <th><a href="02_testpoint_report.md#lcjtagwscanmode_a">LcJtagWScanmode_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#lcjtagwscanmode_a">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#lcjtagwscanmode_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#lcjtagodefault_a">LcJtagODefault_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#lcjtagobackward_a">LcJtagOBackward_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#lcjtagobackward_a">X</a></td>
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
    <th><a href="02_testpoint_report.md#rvjtagwoscanmode_a">RvJtagWoScanmode_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#rvjtagwoscanmode_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#rvjtagwscanmode_a">RvJtagWScanmode_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#rvjtagwscanmode_a">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#rvjtagwscanmode_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#rvjtagodefault_a">RvJtagODefault_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#rvjtagobackward_a">RvJtagOBackward_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#rvjtagobackward_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dftjtagwoscanmode_a">DftJtagWoScanmode_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dftjtagwoscanmode_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dftjtagwscanmode_a">DftJtagWScanmode_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dftjtagwscanmode_a">X</a></td>
    <td><a href="02_testpoint_report.md#dftjtagwscanmode_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dftjtagodefault_a">DftJtagODefault_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#dftjtagobackward_a">DftJtagOBackward_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dftjtagobackward_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dftjtago1backward_a">DftJtagO1Backward_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dftjtago1backward_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#tapstrap_a">TapStrap_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#tapstrap0_a">TapStrap0_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#lcjtagi_a">LcJtagI_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#lcjtagi_a">X</a></td>
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
    <th><a href="02_testpoint_report.md#rvjtagi_a">RvJtagI_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#rvjtagi_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dftjtagi_a">DftJtagI_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dftjtagi_a">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dftstraptesto_a">DftStrapTestO_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#dftstraptestovalidstable_a">DftStrapTestOValidStable_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#dftstraptestostrapstable_a">DftStrapTestOStrapStable_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#usbsleepeni_a">UsbSleepEnI_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#usbsleepeni_a">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#usbdppullupenupwri_a">UsbDppullupEnUpwrI_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#usbdppullupenupwri_a">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#usbdnpullupenupwri_a">UsbDnpullupEnUpwrI_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#usbdnpullupenupwri_a">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#usbdppullupeno_a">UsbDppullupEnO_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#usbdppullupeno_a">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#usbdnpullupeno_a">UsbDnpullupEnO_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#usbdnpullupeno_a">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#usboutofrsti_a">UsbOutOfRstI_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#usboutofrsti_a">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#usbaonwakeenupwri_a">UsbAonWakeEnUpwrI_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#usbaonwakeenupwri_a">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#usbaonwakeackupwri_a">UsbAonWakeAckUpwrI_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#usbaonwakeackupwri_a">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#usbsuspendi_a">UsbSuspendI_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#usbsuspendi_a">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#usbwkupreqo_a">UsbWkupReqO_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#usbwkupreqo_a">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#usbbusreseto_a">UsbBusResetO_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#usbbusreseto_a">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#usbsenselosto_a">UsbSenseLostO_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#usbsenselosto_a">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#usbstatedebugo_a">UsbStateDebugO_A</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#usbstatedebugo_a">X</a></td>
  </tr>
</table>
</div>
</div>
