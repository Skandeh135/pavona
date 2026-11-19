# i2c Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="i2cmodeackcontrol">
      <td>I2C.MODE.ACKCONTROL</td>
      <td>The I2C Target module can be configured to support N-byte ACK Control Mode.With ACK Control Mode off, software provides no protocol-level control of deciding whether to ACK or NACK bytes.With ACK Control Mode on, software may choose whether to ACK Write data bytes.Software may program the Target module to ACK up to N bytes without software intervention.The configuration resets to 0 for the next transfer.</td>
    </tr>
    <tr id="i2cmodehost">
      <td>I2C.MODE.HOST</td>
      <td>The I2C block can be configured in host mode.</td>
    </tr>
    <tr id="i2cmodetarget">
      <td>I2C.MODE.TARGET</td>
      <td>The I2C block can be configured in target mode.</td>
    </tr>
    <tr id="i2coperationread">
      <td>I2C.OPERATION.READ</td>
      <td>Hosts can read from targets.</td>
    </tr>
    <tr id="i2coperationwrite">
      <td>I2C.OPERATION.WRITE</td>
      <td>Hosts can write to targets.</td>
    </tr>
    <tr id="i2coverride">
      <td>I2C.OVERRIDE</td>
      <td>Software can override the values of SCL and SDA.</td>
    </tr>
    <tr id="i2cprotocolclockstretching">
      <td>I2C.PROTOCOL.CLOCKSTRETCHING</td>
      <td>Clock stretching is a way for a target to buy time.There are three scenarios when clock stretching occurs:- After an address read.- During a write.- During a read.</td>
    </tr>
    <tr id="i2cprotocolnack">
      <td>I2C.PROTOCOL.NACK</td>
      <td>Whenever a byte is sent, it must be accompanied by an acknowledgement (ack), unless NAKOK is high.When no ack is received, this is a nack.</td>
    </tr>
    <tr id="i2cprotocolrepeatedstart">
      <td>I2C.PROTOCOL.REPEATEDSTART</td>
      <td>Instead of doing a stop and then a start to start the next transaction, a host can choose to perform a repeated start to begin a new transaction without stopping the previous one.</td>
    </tr>
    <tr id="i2cspeedfast">
      <td>I2C.SPEED.FAST</td>
      <td>Fast-mode of 400 kbaud is supported.</td>
    </tr>
    <tr id="i2cspeedfastplus">
      <td>I2C.SPEED.FASTPLUS</td>
      <td>Fast-mode Plus of 1 Mbaud is supported.</td>
    </tr>
    <tr id="i2cspeedstandard">
      <td>I2C.SPEED.STANDARD</td>
      <td>Standard-mode of 100 kbaud is supported.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>I2C.MODE.HOST</th>
    <th>I2C.MODE.TARGET</th>
    <th>I2C.MODE.ACKCONTROL</th>
    <th>I2C.SPEED.STANDARD</th>
    <th>I2C.SPEED.FAST</th>
    <th>I2C.SPEED.FASTPLUS</th>
    <th>I2C.OVERRIDE</th>
    <th>I2C.OPERATION.READ</th>
    <th>I2C.OPERATION.WRITE</th>
    <th>I2C.PROTOCOL.CLOCKSTRETCHING</th>
    <th>I2C.PROTOCOL.NACK</th>
    <th>I2C.PROTOCOL.REPEATEDSTART</th>
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
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#block-diagram">Block Diagram</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#functional-description">Functional Description</a></th>
    <td><a href="../theory_of_operation.md#functional-description">X</a></td>
    <td><a href="../theory_of_operation.md#functional-description">X</a></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#bus-monitor">Bus Monitor</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#controller-module">Controller Module</a></th>
    <td><a href="../theory_of_operation.md#controller-module">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#controller-nack-handling">Controller NACK Handling</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#controller-nack-handling">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#bus-arbitration">Bus Arbitration</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#target-module">Target Module</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#target-module">X</a></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#target-address-registers">Target Address Registers</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#target-transfers">Target Transfers</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#target-transfers">X</a></td>
    <td><a href="../theory_of_operation.md#target-transfers">X</a></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#target-transfers">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#target-clock-stretching">Target Clock Stretching</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#target-clock-stretching">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#stretching-after-address-read">Stretching after address read</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#stretching-after-address-read">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#stretching-during-write">Stretching during write</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#stretching-during-write">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#stretching-during-read">Stretching during read</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#stretching-during-read">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#target-nacks">Target NACKs</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#target-nacks">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#target-ack-control-mode">Target ACK Control Mode</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#target-ack-control-mode">X</a></td>
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
    <th><a href="../theory_of_operation.md#timing-control-registers">Timing Control Registers</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#timing-control-registers">X</a></td>
    <td><a href="../theory_of_operation.md#timing-control-registers">X</a></td>
    <td><a href="../theory_of_operation.md#timing-control-registers">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#timeout-controls">Timeout Controls</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#bus-timeout-or-stretch-timeout">Bus Timeout or Stretch Timeout</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#scl-idle-timeout">SCL Idle Timeout</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#target-module-stretch-timeout">Target Module Stretch Timeout</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#interrupts">Interrupts</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#controller-interrupts">Controller Interrupts</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#target-interrupts">Target Interrupts</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#implementation-details-format-flag-parsing">Implementation Details: Format Flag Parsing</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#application-notes">Application Notes</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#virtual-open-drain">Virtual Open Drain</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#glitch-filter">Glitch Filter</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#override-mode-for-direct-pin-access">Override Mode for Direct Pin Access</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#override-mode-for-direct-pin-access">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#fsm-control-of-scl-and-sda">FSM control of SCL and SDA</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th>I2C.MODE.HOST</th>
    <th>I2C.MODE.TARGET</th>
    <th>I2C.MODE.ACKCONTROL</th>
    <th>I2C.SPEED.STANDARD</th>
    <th>I2C.SPEED.FAST</th>
    <th>I2C.SPEED.FASTPLUS</th>
    <th>I2C.OVERRIDE</th>
    <th>I2C.OPERATION.READ</th>
    <th>I2C.OPERATION.WRITE</th>
    <th>I2C.PROTOCOL.CLOCKSTRETCHING</th>
    <th>I2C.PROTOCOL.NACK</th>
    <th>I2C.PROTOCOL.REPEATEDSTART</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#host_smoke">host_smoke</a></th>
    <td><a href="02_testpoint_report.md#host_smoke">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#host_smoke">X</a></td>
    <td><a href="02_testpoint_report.md#host_smoke">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#host_smoke">X</a></td>
    <td><a href="02_testpoint_report.md#host_smoke">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#host_error_intr">host_error_intr</a></th>
    <td><a href="02_testpoint_report.md#host_error_intr">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#host_stress_all">host_stress_all</a></th>
    <td><a href="02_testpoint_report.md#host_stress_all">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#host_stress_all_with_rand_reset">host_stress_all_with_rand_reset</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#host_maxperf">host_maxperf</a></th>
    <td><a href="02_testpoint_report.md#host_maxperf">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#host_override">host_override</a></th>
    <td><a href="02_testpoint_report.md#host_override">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#host_override">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#host_fifo_watermark">host_fifo_watermark</a></th>
    <td><a href="02_testpoint_report.md#host_fifo_watermark">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#host_fifo_overflow">host_fifo_overflow</a></th>
    <td><a href="02_testpoint_report.md#host_fifo_overflow">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#host_fifo_reset">host_fifo_reset</a></th>
    <td><a href="02_testpoint_report.md#host_fifo_reset">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#host_fifo_full">host_fifo_full</a></th>
    <td><a href="02_testpoint_report.md#host_fifo_full">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#host_timeout">host_timeout</a></th>
    <td><a href="02_testpoint_report.md#host_timeout">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#host_rx_oversample">host_rx_oversample</a></th>
    <td><a href="02_testpoint_report.md#host_rx_oversample">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#i2c_host_mode_toggle">i2c_host_mode_toggle</a></th>
    <td><a href="02_testpoint_report.md#i2c_host_mode_toggle">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#i2c_host_mode_toggle">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#target_smoke">target_smoke</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#target_smoke">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#target_smoke">X</a></td>
    <td><a href="02_testpoint_report.md#target_smoke">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#target_smoke">X</a></td>
    <td><a href="02_testpoint_report.md#target_smoke">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#target_error_intr">target_error_intr</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#target_error_intr">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#target_glitch">target_glitch</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#target_glitch">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#target_stress_all">target_stress_all</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#target_stress_all">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#target_stress_all_with_rand_reset">target_stress_all_with_rand_reset</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#target_stress_all_with_rand_reset">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#target_maxperf">target_maxperf</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#target_maxperf">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#target_maxperf">X</a></td>
    <td><a href="02_testpoint_report.md#target_maxperf">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#target_fifo_empty">target_fifo_empty</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#target_fifo_empty">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#target_fifo_reset">target_fifo_reset</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#target_fifo_reset">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#target_fifo_full">target_fifo_full</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#target_fifo_full">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#target_timeout">target_timeout</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#target_timeout">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#target_clock_stretch">target_clock_stretch</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#target_clock_stretch">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#target_clock_stretch">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#target_loopback">target_loopback</a></th>
    <td><a href="02_testpoint_report.md#target_loopback">X</a></td>
    <td><a href="02_testpoint_report.md#target_loopback">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#bad_address">bad_address</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#bad_address">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#target_mode_glitch">target_mode_glitch</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#target_mode_glitch">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#target_fifo_watermark">target_fifo_watermark</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#target_fifo_watermark">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#host_mode_config_perf">host_mode_config_perf</a></th>
    <td><a href="02_testpoint_report.md#host_mode_config_perf">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#host_mode_clock_stretching">host_mode_clock_stretching</a></th>
    <td><a href="02_testpoint_report.md#host_mode_clock_stretching">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#host_mode_clock_stretching">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#target_mode_tx_stretch_ctrl">target_mode_tx_stretch_ctrl</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#target_mode_tx_stretch_ctrl">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#target_mode_tx_stretch_ctrl">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#target_mode_nack_generation">target_mode_nack_generation</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#target_mode_nack_generation">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#target_mode_nack_generation">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#host_mode_halt_on_nak">host_mode_halt_on_nak</a></th>
    <td><a href="02_testpoint_report.md#host_mode_halt_on_nak">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#host_mode_halt_on_nak">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#target_mode_n_byte_ack_control">target_mode_n_byte_ack_control</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#target_mode_n_byte_ack_control">X</a></td>
    <td><a href="02_testpoint_report.md#target_mode_n_byte_ack_control">X</a></td>
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
    <th><a href="02_testpoint_report.md#target_mode_bus_timeout">target_mode_bus_timeout</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#target_mode_bus_timeout">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#controller_mode_bus_timeout">controller_mode_bus_timeout</a></th>
    <td><a href="02_testpoint_report.md#controller_mode_bus_timeout">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#controller_mode_bus_idle_delay">controller_mode_bus_idle_delay</a></th>
    <td><a href="02_testpoint_report.md#controller_mode_bus_idle_delay">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#loopback_test">loopback_test</a></th>
    <td><a href="02_testpoint_report.md#loopback_test">X</a></td>
    <td><a href="02_testpoint_report.md#loopback_test">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#multi_controller_clock_synchronization">multi_controller_clock_synchronization</a></th>
    <td><a href="02_testpoint_report.md#multi_controller_clock_synchronization">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#multi_controller_arbitration_lost_interference">multi_controller_arbitration_lost_interference</a></th>
    <td><a href="02_testpoint_report.md#multi_controller_arbitration_lost_interference">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#multi_controller_arbitration_lost">multi_controller_arbitration_lost</a></th>
    <td><a href="02_testpoint_report.md#multi_controller_arbitration_lost">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#target_mode_arbitration_lost_interference">target_mode_arbitration_lost_interference</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#target_mode_arbitration_lost_interference">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#target_mode_arbitration_lost">target_mode_arbitration_lost</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#target_mode_arbitration_lost">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#target_mode_smbus_maxlen">target_mode_smbus_maxlen</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#target_mode_smbus_maxlen">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_i2c_host_tx_rx-dragonfly">chip_sw_i2c_host_tx_rx (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_host_tx_rx-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_host_tx_rx-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_host_tx_rx-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_i2c_device_tx_rx-dragonfly">chip_sw_i2c_device_tx_rx (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_device_tx_rx-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_device_tx_rx-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_device_tx_rx-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_i2c_speed-dragonfly">chip_sw_i2c_speed (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_speed-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_speed-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_speed-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_speed-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_speed-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_i2c_override-dragonfly">chip_sw_i2c_override (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_override-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_override-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_i2c_clockstretching-dragonfly">chip_sw_i2c_clockstretching (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_clockstretching-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_clockstretching-dragonfly">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_i2c_nack-dragonfly">chip_sw_i2c_nack (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_nack-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_nack-dragonfly">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_i2c_repeatedstart-dragonfly">chip_sw_i2c_repeatedstart (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_repeatedstart-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_repeatedstart-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_i2c_host_tx_rx-egret">chip_sw_i2c_host_tx_rx (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_host_tx_rx-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_host_tx_rx-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_host_tx_rx-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_i2c_device_tx_rx-egret">chip_sw_i2c_device_tx_rx (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_device_tx_rx-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_device_tx_rx-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_device_tx_rx-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_i2c_speed-egret">chip_sw_i2c_speed (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_speed-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_speed-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_speed-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_speed-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_speed-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_i2c_override-egret">chip_sw_i2c_override (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_override-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_override-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_i2c_clockstretching-egret">chip_sw_i2c_clockstretching (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_clockstretching-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_clockstretching-egret">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_i2c_nack-egret">chip_sw_i2c_nack (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_nack-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_nack-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_i2c_repeatedstart-egret">chip_sw_i2c_repeatedstart (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_repeatedstart-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_i2c_repeatedstart-egret">X</a></td>
  </tr>
</table>
</div>
</div>
