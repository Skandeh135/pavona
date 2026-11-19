# uart Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="uartbaud_rate_control">
      <td>UART.BAUD_RATE_CONTROL</td>
      <td>The UART baud rate can be configured.</td>
    </tr>
    <tr id="uartfifo_interrupts">
      <td>UART.FIFO_INTERRUPTS</td>
      <td>The UART can be configured to send an "watermark" interrupt when RX or TX FIFO is nearly full/empty, respectively.It sends an rx_overflow interrupt if it sees an extra character when the RX FIFO is full.</td>
    </tr>
    <tr id="uartline_break">
      <td>UART.LINE_BREAK</td>
      <td>The UART can detect line breaks (defined as the RX pin being continuously low for several bit-times).The threshold for number of low bits to signal a line break is configurable.</td>
    </tr>
    <tr id="uartline_loopback">
      <td>UART.LINE_LOOPBACK</td>
      <td>The UART can be configured so that incoming bits are sent on the TX side.</td>
    </tr>
    <tr id="uartparity">
      <td>UART.PARITY</td>
      <td>The UART can be configured to so that it sends (or expects) a parity bit after each 8 data bits.In receive mode, the UART sends the rx_parity_err interrupt if it receives a parity bit of the wrong polarity.The parity mode is configurable (ensuring words are even or odd).</td>
    </tr>
    <tr id="uartrx_filtering">
      <td>UART.RX_FILTERING</td>
      <td>The RX line is oversampled at 16x the baud rate, which is used both to reject glitches andto expose the raw oversampled values. A start bit is only accepted if the line is still lowhalf a bit-time after the falling edge, and an optional noise filter passes the RX linethrough a 3-tap repetition code so that noise lasting a single clock period is ignored.</td>
    </tr>
    <tr id="uartsystem_loopback">
      <td>UART.SYSTEM_LOOPBACK</td>
      <td>The UART can be configured so that outgoing bits are registered as having been received on the RX side.</td>
    </tr>
    <tr id="uarttx_override">
      <td>UART.TX_OVERRIDE</td>
      <td>Software can take direct control of the TX pin, driving its level from a register insteadof from the transmit FIFO.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>UART.PARITY</th>
    <th>UART.LINE_LOOPBACK</th>
    <th>UART.SYSTEM_LOOPBACK</th>
    <th>UART.BAUD_RATE_CONTROL</th>
    <th>UART.LINE_BREAK</th>
    <th>UART.FIFO_INTERRUPTS</th>
    <th>UART.RX_FILTERING</th>
    <th>UART.TX_OVERRIDE</th>
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
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#serial-interface-both-directions">Serial interface (both directions)</a></th>
    <td><a href="../theory_of_operation.md#serial-interface-both-directions">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#transmission">Transmission</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#transmission">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#tx-pin-override">TX pin override</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#tx-pin-override">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#reception">Reception</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#reception">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#reception">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#setting-the-baud-rate">Setting the baud rate</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#setting-the-baud-rate">X</a></td>
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
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#tx_watermark--tx_empty--rx_watermark">tx_watermark / tx_empty / rx_watermark</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#tx_watermark--tx_empty--rx_watermark">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#tx_done">tx_done</a></th>
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
    <th><a href="../theory_of_operation.md#rx_overflow">rx_overflow</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#rx_overflow">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#rx_break_err">rx_break_err</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#rx_break_err">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#rx_frame_err">rx_frame_err</a></th>
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
    <th><a href="../theory_of_operation.md#rx_timeout">rx_timeout</a></th>
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
    <th><a href="../theory_of_operation.md#rx_parity_err">rx_parity_err</a></th>
    <td><a href="../theory_of_operation.md#rx_parity_err">X</a></td>
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
    <th>UART.PARITY</th>
    <th>UART.LINE_LOOPBACK</th>
    <th>UART.SYSTEM_LOOPBACK</th>
    <th>UART.BAUD_RATE_CONTROL</th>
    <th>UART.LINE_BREAK</th>
    <th>UART.FIFO_INTERRUPTS</th>
    <th>UART.RX_FILTERING</th>
    <th>UART.TX_OVERRIDE</th>
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
    <th><a href="02_testpoint_report.md#base_random_seq">base_random_seq</a></th>
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
    <th><a href="02_testpoint_report.md#parity">parity</a></th>
    <td><a href="02_testpoint_report.md#parity">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#parity_error">parity_error</a></th>
    <td><a href="02_testpoint_report.md#parity_error">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#parity_error">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#watermark">watermark</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#watermark">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#fifo_full">fifo_full</a></th>
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
    <th><a href="02_testpoint_report.md#fifo_overflow">fifo_overflow</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#fifo_overflow">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#fifo_reset">fifo_reset</a></th>
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
    <th><a href="02_testpoint_report.md#rx_frame_err">rx_frame_err</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#rx_frame_err">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#rx_break_err">rx_break_err</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#rx_break_err">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#rx_timeout">rx_timeout</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#rx_timeout">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#perf">perf</a></th>
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
    <th><a href="02_testpoint_report.md#sys_loopback">sys_loopback</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#sys_loopback">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#line_loopback">line_loopback</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#line_loopback">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#rx_noise_filter">rx_noise_filter</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#rx_noise_filter">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#rx_start_bit_filter">rx_start_bit_filter</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#rx_start_bit_filter">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#tx_overide">tx_overide</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#tx_overide">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#rx_oversample">rx_oversample</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#rx_oversample">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#long_b2b_transfer">long_b2b_transfer</a></th>
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
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_uart_tx_rx-dragonfly">chip_sw_uart_tx_rx (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_uart_tx_rx-dragonfly">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_uart_rx_overflow-dragonfly">chip_sw_uart_rx_overflow (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_uart_rx_overflow-dragonfly">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_uart_baud_rate-dragonfly">chip_sw_uart_baud_rate (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_uart_baud_rate-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_uart_tx_rx_alt_clk_freq-dragonfly">chip_sw_uart_tx_rx_alt_clk_freq (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_uart_tx_rx_alt_clk_freq-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_uart_parity-dragonfly">chip_sw_uart_parity (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_uart_parity-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_uart_line_loopback-dragonfly">chip_sw_uart_line_loopback (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_uart_line_loopback-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_uart_system_loopback-dragonfly">chip_sw_uart_system_loopback (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_uart_system_loopback-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_uart_line_break-dragonfly">chip_sw_uart_line_break (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_uart_line_break-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_uart_watermarks-dragonfly">chip_sw_uart_watermarks (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_uart_watermarks-dragonfly">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_uart_tx_rx-egret">chip_sw_uart_tx_rx (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_uart_tx_rx-egret">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_uart_rx_overflow-egret">chip_sw_uart_rx_overflow (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_uart_rx_overflow-egret">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_uart_baud_rate-egret">chip_sw_uart_baud_rate (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_uart_baud_rate-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_uart_tx_rx_alt_clk_freq-egret">chip_sw_uart_tx_rx_alt_clk_freq (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_uart_tx_rx_alt_clk_freq-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_uart_parity-egret">chip_sw_uart_parity (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_uart_parity-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_uart_line_loopback-egret">chip_sw_uart_line_loopback (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_uart_line_loopback-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_uart_system_loopback-egret">chip_sw_uart_system_loopback (egret)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_uart_system_loopback-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_uart_line_break-egret">chip_sw_uart_line_break (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_uart_line_break-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_uart_watermarks-egret">chip_sw_uart_watermarks (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_uart_watermarks-egret">X</a></td>
    <td></td>
    <td></td>
  </tr>
</table>
</div>
</div>
