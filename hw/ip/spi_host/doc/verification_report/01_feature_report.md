# spi_host Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="spihostconfigclockdiv">
      <td>SPIHOST.CONFIG.CLOCKDIV</td>
      <td>The clock divider in the SPI host can be configured.</td>
    </tr>
    <tr id="spihostconfigcpol">
      <td>SPIHOST.CONFIG.CPOL</td>
      <td>The polarity of the SPI can be configured.</td>
    </tr>
    <tr id="spihosteventempty">
      <td>SPIHOST.EVENT.EMPTY</td>
      <td>The block can be configured to raise an event when the transmit queue is empty.</td>
    </tr>
    <tr id="spihosteventfull">
      <td>SPIHOST.EVENT.FULL</td>
      <td>The block can be configured to raise an event when the receive queue is full.</td>
    </tr>
    <tr id="spihosteventwatermark">
      <td>SPIHOST.EVENT.WATERMARK</td>
      <td>The block can be configured to raise an event on watermarks for transmit and receive queues.</td>
    </tr>
    <tr id="spihostratedual">
      <td>SPIHOST.RATE.DUAL</td>
      <td>Host can operate in dual SPI data rate.</td>
    </tr>
    <tr id="spihostratequad">
      <td>SPIHOST.RATE.QUAD</td>
      <td>Host can operate in quad SPI data rate.</td>
    </tr>
    <tr id="spihostratestandard">
      <td>SPIHOST.RATE.STANDARD</td>
      <td>Host can operate in standard SPI data rate.</td>
    </tr>
    <tr id="spihostusecasepassthrough">
      <td>SPIHOST.USECASE.PASSTHROUGH</td>
      <td>The SPI host block can work together with a device to create a pass through.</td>
    </tr>
    <tr id="spihostusecaseserialnorflash">
      <td>SPIHOST.USECASE.SERIALNORFLASH</td>
      <td>The SPI host block can talk to serial NOR flash devices.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>SPIHOST.USECASE.SERIALNORFLASH</th>
    <th>SPIHOST.USECASE.PASSTHROUGH</th>
    <th>SPIHOST.RATE.STANDARD</th>
    <th>SPIHOST.RATE.DUAL</th>
    <th>SPIHOST.RATE.QUAD</th>
    <th>SPIHOST.CONFIG.CPOL</th>
    <th>SPIHOST.CONFIG.CLOCKDIV</th>
    <th>SPIHOST.EVENT.WATERMARK</th>
    <th>SPIHOST.EVENT.FULL</th>
    <th>SPIHOST.EVENT.EMPTY</th>
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
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#spi-protocol-basics">SPI Protocol Basics</a></th>
    <td><a href="../theory_of_operation.md#spi-protocol-basics">X</a></td>
    <td></td>
    <td><a href="../theory_of_operation.md#spi-protocol-basics">X</a></td>
    <td><a href="../theory_of_operation.md#spi-protocol-basics">X</a></td>
    <td><a href="../theory_of_operation.md#spi-protocol-basics">X</a></td>
    <td><a href="../theory_of_operation.md#spi-protocol-basics">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#api-details">API Details</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#command-interface">Command Interface</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#creating-a-spi-command-from-multiple-segments">Creating a SPI Command from multiple segments</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#about-command-segments">About Command Segments</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#csid-register">CSID Register</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#configuration-options">Configuration Options</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#clock-rate-selection">Clock rate selection</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#clock-rate-selection">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#chip-select-timing-control">Chip-select Timing Control</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#clock-phase-and-polarity">Clock Phase and Polarity</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#clock-phase-and-polarity">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#full-cycle-sampling">Full-Cycle Sampling</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#idle-time-delays-when-changing-configurations">Idle Time Delays When Changing Configurations</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#special-command-fields">Special Command Fields</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#chip-select-masks">Chip Select Masks</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#back-to-back-segments">Back-to-back Segments</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#data-formatting">Data Formatting</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#input-and-output-byte-ordering">Input and Output Byte Ordering</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#command-length-and-alignment-in-data">Command Length and Alignment in DATA</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#pass-through-mode">Pass-through Mode</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#pass-through-mode">X</a></td>
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
    <th><a href="../theory_of_operation.md#interrupt-aggregation">Interrupt Aggregation</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#spi-events-and-event-interrupts">SPI Events and Event Interrupts</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#spi-events-and-event-interrupts">X</a></td>
    <td><a href="../theory_of_operation.md#spi-events-and-event-interrupts">X</a></td>
    <td><a href="../theory_of_operation.md#spi-events-and-event-interrupts">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#stall-conditions">Stall Conditions</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#error-interrupt-conditions">Error Interrupt Conditions</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#status-indicators">Status Indicators</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#other-registers">Other Registers</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#spi_host-enable">SPI_HOST Enable</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#spi_host-output-enable">SPI_HOST Output Enable</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#component-reset">Component reset</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#design-details">Design Details</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#block-diagrams">Block Diagrams</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#component-overview">Component Overview</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#rx-and-tx-fifos">RX and TX FIFOs</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#byte-select">Byte Select</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#byte-merge">Byte Merge</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#shift-register">Shift Register</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#bubbles-in-the-data-pipeline">Bubbles in the Data Pipeline</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#spi_host-finite-state-machine-fsm">SPI_HOST Finite State Machine (FSM)</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#clock-divider">Clock Divider</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#clock-divider">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#other-internal-counters">Other Internal Counters</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#basic-operation">Basic Operation</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#milestone-signals-serial-data-lines--shift-register-control">Milestone Signals, Serial Data Lines & Shift Register Control</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#milestone-signals-and-control-of-the-bit-and-byte-counters">Milestone Signals and Control of the Bit and Byte Counters</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#implementation-of-configuration-change-delays">Implementation of Configuration Change Delays</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#csaat-support">CSAAT Support</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#skipped-idle-states">Skipped idle states</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#stall">Stall</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#appendices">Appendices</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#analysis-of-transient-datapath-stalls">Analysis of Transient Datapath Stalls</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#transient-stalls-in-the-tx-direction">Transient Stalls in the TX direction</a></th>
    <td></td>
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
    <th><a href="../theory_of_operation.md#transient-stalls-in-the-rx-direction">Transient Stalls in the RX direction</a></th>
    <td></td>
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
</table>
</div>
</div>


## Feature -> Testpoint Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Testpoints↓ : Features→</th>
    <th>SPIHOST.USECASE.SERIALNORFLASH</th>
    <th>SPIHOST.USECASE.PASSTHROUGH</th>
    <th>SPIHOST.RATE.STANDARD</th>
    <th>SPIHOST.RATE.DUAL</th>
    <th>SPIHOST.RATE.QUAD</th>
    <th>SPIHOST.CONFIG.CPOL</th>
    <th>SPIHOST.CONFIG.CLOCKDIV</th>
    <th>SPIHOST.EVENT.WATERMARK</th>
    <th>SPIHOST.EVENT.FULL</th>
    <th>SPIHOST.EVENT.EMPTY</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#performance">performance</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#performance">X</a></td>
    <td><a href="02_testpoint_report.md#performance">X</a></td>
    <td><a href="02_testpoint_report.md#performance">X</a></td>
    <td><a href="02_testpoint_report.md#performance">X</a></td>
    <td><a href="02_testpoint_report.md#performance">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#error_event_intr">error_event_intr</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#error_event_intr">X</a></td>
    <td><a href="02_testpoint_report.md#error_event_intr">X</a></td>
    <td><a href="02_testpoint_report.md#error_event_intr">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#clock_rate">clock_rate</a></th>
    <td></td>
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
    <th><a href="02_testpoint_report.md#speed">speed</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#speed">X</a></td>
    <td><a href="02_testpoint_report.md#speed">X</a></td>
    <td><a href="02_testpoint_report.md#speed">X</a></td>
    <td><a href="02_testpoint_report.md#speed">X</a></td>
    <td><a href="02_testpoint_report.md#speed">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_select_timing">chip_select_timing</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_select_timing">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#sw_reset">sw_reset</a></th>
    <td></td>
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
    <th><a href="02_testpoint_report.md#passthrough_mode">passthrough_mode</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#passthrough_mode">X</a></td>
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
    <th><a href="02_testpoint_report.md#cpol_cpha">cpol_cpha</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cpol_cpha">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#full_cycle">full_cycle</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#full_cycle">X</a></td>
    <td><a href="02_testpoint_report.md#full_cycle">X</a></td>
    <td><a href="02_testpoint_report.md#full_cycle">X</a></td>
    <td><a href="02_testpoint_report.md#full_cycle">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#duplex">duplex</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#duplex">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#tx_rx_only">tx_rx_only</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#tx_rx_only">X</a></td>
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
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#spien">spien</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#spien">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#stall">stall</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#stall">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#stall">X</a></td>
    <td><a href="02_testpoint_report.md#stall">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#idlecsbactive">Idlecsbactive</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#idlecsbactive">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#data_fifo_status">data_fifo_status</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#data_fifo_status">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#data_fifo_status">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#winbond">winbond</a></th>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_spi_host_tx_rx-dragonfly">chip_sw_spi_host_tx_rx (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_host_tx_rx-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_host_tx_rx-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_host_tx_rx-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_spi_host_pass_through-dragonfly">chip_sw_spi_host_pass_through (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_spi_host_pass_through-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_host_pass_through-dragonfly">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_spi_host_configuration-dragonfly">chip_sw_spi_host_configuration (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_host_configuration-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_host_configuration-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_spi_host_events-dragonfly">chip_sw_spi_host_events (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_host_events-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_host_events-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_host_events-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_spi_host_tx_rx-egret">chip_sw_spi_host_tx_rx (egret)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_host_tx_rx-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_host_tx_rx-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_host_tx_rx-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_spi_host_pass_through-egret">chip_sw_spi_host_pass_through (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_spi_host_pass_through-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_host_pass_through-egret">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_spi_host_configuration-egret">chip_sw_spi_host_configuration (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_host_configuration-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_host_configuration-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_spi_host_events-egret">chip_sw_spi_host_events (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_host_events-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_host_events-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_host_events-egret">X</a></td>
  </tr>
</table>
</div>
</div>
