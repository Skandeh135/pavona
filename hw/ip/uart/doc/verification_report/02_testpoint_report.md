# uart Testpoint Report

## base_random_seq


- This is the basic sequence that is extended by most of random sequence.
- TX and RX have 2 independent threads respectively.
  - TX: keep programming csr wdata with random delay when fifo isn't full
  - RX: 2 processes. One is to send item through uart interface when fifo isn't full
    and the other is to read csr rdata when fifo isn't empty


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#uart_tx_rx">uart_tx_rx</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_uart_baud_rate (dragonfly)
Verify UART transmission of data at various speeds.

Test data transfer in both directions for each UART instance configured for each of
these baud rates: 9600Bd, 115200Bd, 230400Bd, 128kBd, 256kBd, 1MBd, 1.5MBd.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_uart_rand_baudrate-dragonfly">chip_sw_uart_rand_baudrate (dragonfly)</a></td>
  <td><a href="01_feature_report.md#uartbaud_rate_control">UART.BAUD_RATE_CONTROL</a></td>
</tr>
  </tbody>
</table>

## chip_sw_uart_baud_rate (egret)
Verify UART transmission of data at various speeds.

Test data transfer in both directions for each UART instance configured for each of
these baud rates: 9600Bd, 115200Bd, 230400Bd, 128kBd, 256kBd, 1MBd, 1.5MBd.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_uart_rand_baudrate-egret">chip_sw_uart_rand_baudrate (egret)</a></td>
  <td><a href="01_feature_report.md#uartbaud_rate_control">UART.BAUD_RATE_CONTROL</a></td>
</tr>
  </tbody>
</table>

## chip_sw_uart_line_break (dragonfly)
Check that the UART can detect line breaks.

Enable RX and configure the line break threshold. On the host side, send data but hold
the signal low for enough characters that this should be detected as a line break. Check
that the rx_break_err interrupt was asserted.

Repeat with parity enabled and with different line break thresholds (controlled by
CTRL.RXBLVL).


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
  <td><a href="01_feature_report.md#uartline_break">UART.LINE_BREAK</a></td>
</tr>
  </tbody>
</table>

## chip_sw_uart_line_break (egret)
Check that the UART can detect line breaks.

Enable RX and configure the line break threshold. On the host side, send data but hold
the signal low for enough characters that this should be detected as a line break. Check
that the rx_break_err interrupt was asserted.

Repeat with parity enabled and with different line break thresholds (controlled by
CTRL.RXBLVL).


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
  <td><a href="01_feature_report.md#uartline_break">UART.LINE_BREAK</a></td>
</tr>
  </tbody>
</table>

## chip_sw_uart_line_loopback (dragonfly)
Verify UART line loopback feature.

Configure the UART to enable RX, TX and line loopback. Send it some data and check that
the bits appear on its TX side.


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
  <td><a href="01_feature_report.md#uartline_loopback">UART.LINE_LOOPBACK</a></td>
</tr>
  </tbody>
</table>

## chip_sw_uart_line_loopback (egret)
Verify UART line loopback feature.

Configure the UART to enable RX, TX and line loopback. Send it some data and check that
the bits appear on its TX side.


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
  <td><a href="01_feature_report.md#uartline_loopback">UART.LINE_LOOPBACK</a></td>
</tr>
  </tbody>
</table>

## chip_sw_uart_parity (dragonfly)
Verify transmission of data in both directions with parity enabled.

This is very similar to chip_sw_uart_tx_rx except that parity (generation and checking)
should be enabled. Control expected word parity by configuring CTRL.PARITY_ODD register.

Test the rx_parity_err interrupt by sending a word with incorrect parity.


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
  <td><a href="01_feature_report.md#uartparity">UART.PARITY</a></td>
</tr>
  </tbody>
</table>

## chip_sw_uart_parity (egret)
Verify transmission of data in both directions with parity enabled.

This is very similar to chip_sw_uart_tx_rx except that parity (generation and checking)
should be enabled. Control expected word parity by configuring CTRL.PARITY_ODD register.

Test the rx_parity_err interrupt by sending a word with incorrect parity.


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
  <td><a href="01_feature_report.md#uartparity">UART.PARITY</a></td>
</tr>
  </tbody>
</table>

## chip_sw_uart_rx_overflow (dragonfly)
Verify the RX overflow interrupt.

The testbench sends a random payload of size greater than the RX fifo size (32). The SW
ignores the received the data to allow the RX overflow interrupt to assert.

Verify each UART instance at the chip level independently. Verify there is no aliasing
on all UART ports across the instances.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_uart_tx_rx-dragonfly">chip_sw_uart_tx_rx (dragonfly)</a><br><a href="03_test_report.md#chip_sw_uart_tx_rx_idx1-dragonfly">chip_sw_uart_tx_rx_idx1 (dragonfly)</a><br><a href="03_test_report.md#chip_sw_uart_tx_rx_idx2-dragonfly">chip_sw_uart_tx_rx_idx2 (dragonfly)</a><br><a href="03_test_report.md#chip_sw_uart_tx_rx_idx3-dragonfly">chip_sw_uart_tx_rx_idx3 (dragonfly)</a></td>
  <td><a href="01_feature_report.md#uartfifo_interrupts">UART.FIFO_INTERRUPTS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_uart_rx_overflow (egret)
Verify the RX overflow interrupt.

The testbench sends a random payload of size greater than the RX fifo size (32). The SW
ignores the received the data to allow the RX overflow interrupt to assert.

Verify each UART instance at the chip level independently. Verify there is no aliasing
on all UART ports across the instances.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_uart_tx_rx-egret">chip_sw_uart_tx_rx (egret)</a><br><a href="03_test_report.md#chip_sw_uart_tx_rx_idx1-egret">chip_sw_uart_tx_rx_idx1 (egret)</a><br><a href="03_test_report.md#chip_sw_uart_tx_rx_idx2-egret">chip_sw_uart_tx_rx_idx2 (egret)</a><br><a href="03_test_report.md#chip_sw_uart_tx_rx_idx3-egret">chip_sw_uart_tx_rx_idx3 (egret)</a></td>
  <td><a href="01_feature_report.md#uartfifo_interrupts">UART.FIFO_INTERRUPTS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_uart_system_loopback (dragonfly)
Verify UART system loopback feature.

Configure the UART to enable RX, TX and system loopback. Transmit some data and check
that the data that was transmitted also appears on the RX side.


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
  <td><a href="01_feature_report.md#uartsystem_loopback">UART.SYSTEM_LOOPBACK</a></td>
</tr>
  </tbody>
</table>

## chip_sw_uart_system_loopback (egret)
Verify UART system loopback feature.

Configure the UART to enable RX, TX and system loopback. Transmit some data and check
that the data that was transmitted also appears on the RX side.


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
  <td><a href="01_feature_report.md#uartsystem_loopback">UART.SYSTEM_LOOPBACK</a></td>
</tr>
  </tbody>
</table>

## chip_sw_uart_tx_rx (dragonfly)
Verify transmission of data over the TX and RX port.

SW test sends a known payload over the TX port. The testbench, at the same time
sends a known payload over RX. On reception, both payloads are checked for integrity.
SW validates the reception of TX watermark, RX watermark, and the TX empty interrupts.
Choosing the max supported baud rate for the UART is sufficient.

Verify each UART instance at the chip level independently. Verify there is no aliasing
on all UART ports across the instances.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_uart_tx_rx-dragonfly">chip_sw_uart_tx_rx (dragonfly)</a></td>
  <td><a href="01_feature_report.md#uartfifo_interrupts">UART.FIFO_INTERRUPTS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_uart_tx_rx (egret)
Verify transmission of data over the TX and RX port.

SW test sends a known payload over the TX port. The testbench, at the same time
sends a known payload over RX. On reception, both payloads are checked for integrity.
SW validates the reception of TX watermark, RX watermark, and the TX empty interrupts.
Choosing the max supported baud rate for the UART is sufficient.

Verify each UART instance at the chip level independently. Verify there is no aliasing
on all UART ports across the instances.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_uart_tx_rx-egret">chip_sw_uart_tx_rx (egret)</a></td>
  <td><a href="01_feature_report.md#uartfifo_interrupts">UART.FIFO_INTERRUPTS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_uart_tx_rx_alt_clk_freq (dragonfly)
Verify the transmission of UART via using external clock as uart core clock.

Extend from chip_sw_uart_rand_baudrate with following added settings.

- Configure LC to RMA state, so that it allows clkmgr to use external clock.
- Configure clkmgr to select external clock.
- Randomize `HI_SPEED_SEL`, so that uart core clock frequency can be either
  ext_clk_freq / 4 or ext_clk_freq / 2.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_uart_tx_rx_alt_clk_freq-dragonfly">chip_sw_uart_tx_rx_alt_clk_freq (dragonfly)</a></td>
  <td><a href="01_feature_report.md#uartbaud_rate_control">UART.BAUD_RATE_CONTROL</a></td>
</tr>
  </tbody>
</table>

## chip_sw_uart_tx_rx_alt_clk_freq (egret)
Verify the transmission of UART via using external clock as uart core clock.

Extend from chip_sw_uart_rand_baudrate with following added settings.

- Configure LC to RMA state, so that it allows clkmgr to use external clock.
- Configure clkmgr to select external clock.
- Randomize `HI_SPEED_SEL`, so that uart core clock frequency can be either
  ext_clk_freq / 4 or ext_clk_freq / 2.

Notes for silicon targets:

- This testpoint currently has an empty list of associated features, because the choice
  of clock is really a clkmgr/chip-level feature, rather than a feature of the UART
  block.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_uart_tx_rx_alt_clk_freq-egret">chip_sw_uart_tx_rx_alt_clk_freq (egret)</a><br><a href="03_test_report.md#chip_sw_uart_tx_rx_alt_clk_freq_low_speed-egret">chip_sw_uart_tx_rx_alt_clk_freq_low_speed (egret)</a></td>
  <td><a href="01_feature_report.md#uartbaud_rate_control">UART.BAUD_RATE_CONTROL</a></td>
</tr>
  </tbody>
</table>

## chip_sw_uart_watermarks (dragonfly)
Observe UART watermark interrupts.

Transmit data from the host and receive it on the OT side by servicing the rx_watermark
interrupt. Check that the data matches the sequence that the host was expected to send.

Send the data back from OT to the host, refilling the TX FIFO on reception of the
tx_watermark interrupt. On the host side, check that the data that came back matches the
sequence that was sent in the first place.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_uart_tx_rx-dragonfly">chip_sw_uart_tx_rx (dragonfly)</a></td>
  <td><a href="01_feature_report.md#uartfifo_interrupts">UART.FIFO_INTERRUPTS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_uart_watermarks (egret)
Observe UART watermark interrupts.

Transmit data from the host and receive it on the OT side by servicing the rx_watermark
interrupt. Check that the data matches the sequence that the host was expected to send.

Send the data back from OT to the host, refilling the TX FIFO on reception of the
tx_watermark interrupt. On the host side, check that the data that came back matches the
sequence that was sent in the first place.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_uart_tx_rx-egret">chip_sw_uart_tx_rx (egret)</a></td>
  <td><a href="01_feature_report.md#uartfifo_interrupts">UART.FIFO_INTERRUPTS</a></td>
</tr>
  </tbody>
</table>

## fifo_full
Send over 32 bytes of data but stop when fifo is full


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#uart_fifo_full">uart_fifo_full</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## fifo_overflow


- Keep sending over 32 bytes of data over tx/rx fifo
- Ensure excess data bytes are dropped and check overflow interrupt
- This uart_fifo_overflow_vseq is extent from uart_fifo_full_vseq and override the
  constraint to be able to send data over fifo size


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#uart_fifo_overflow">uart_fifo_overflow</a></td>
  <td><a href="01_feature_report.md#uartfifo_interrupts">UART.FIFO_INTERRUPTS</a></td>
</tr>
  </tbody>
</table>

## fifo_reset


- Fill up the tx/rx fifo. After a random number of bytes shows up on fifo, reset
  the fifo and ensure that the remaining data bytes do not show up
- this sequence is extent from uart_fifo_overflow_vseq, so it can also reset when fifo
  is at any level, including full or overflow


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#uart_fifo_reset">uart_fifo_reset</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## line_loopback


- Enable line loopback and drive uart_rx with random data and random delay
- Check uart_tx has same value as uart_rx. There is not synchronizer register between
  uart_rx and uart_tx during line loopback


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#uart_loopback">uart_loopback</a></td>
  <td><a href="01_feature_report.md#uartline_loopback">UART.LINE_LOOPBACK</a></td>
</tr>
  </tbody>
</table>

## long_b2b_transfer


- Reduce delay to fill TX fifo and read RX fifo to ensure back2back transfers
- Use long back2back transfer to ensure clock difference won't be accumulated across transactions
- Uart monitor checks the clock offset between sender and receiver is never over 1/4 of the period


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#uart_long_xfer_wo_dly">uart_long_xfer_wo_dly</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## parity
Send / receive bytes with parity and odd parity enabled randomly.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#uart_smoke">uart_smoke</a><br><a href="03_test_report.md#uart_tx_rx">uart_tx_rx</a></td>
  <td><a href="01_feature_report.md#uartparity">UART.PARITY</a></td>
</tr>
  </tbody>
</table>

## parity_error


- Enable parity and randomly set even/odd parity
- Inject parity error randomly on data sent from rx and ensure the interrupt is
  raised


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#uart_intr">uart_intr</a><br><a href="03_test_report.md#uart_rx_parity_err">uart_rx_parity_err</a></td>
  <td><a href="01_feature_report.md#uartfifo_interrupts">UART.FIFO_INTERRUPTS</a><br><a href="01_feature_report.md#uartparity">UART.PARITY</a></td>
</tr>
  </tbody>
</table>

## perf
Run fifo_full_vseq with very small delays


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#uart_perf">uart_perf</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## rx_break_err


- Program random number of break detection characters
- create a frame error scenario and send random number of 0 bytes
- If that random number exceeds the programmed break characters
- Ensure that the break_err interrupt is asserted


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#uart_intr">uart_intr</a></td>
  <td><a href="01_feature_report.md#uartfifo_interrupts">UART.FIFO_INTERRUPTS</a></td>
</tr>
  </tbody>
</table>

## rx_frame_err


- Inject frame error in parity and non-parity cases by not setting stop bit = 1
- Ensure the interrupt gets asserted


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#uart_intr">uart_intr</a></td>
  <td><a href="01_feature_report.md#uartfifo_interrupts">UART.FIFO_INTERRUPTS</a></td>
</tr>
  </tbody>
</table>

## rx_noise_filter


- Use 16x fast clk to sample it, data on uart_rx need to be stable for 3 clocks,
  otherwise, data change won't be taken
- Enable noise filter and drive many glitches. Each glitch doesn't lasts less than
  3 clocks
- Ensure the noise will be filtered out and it doesn't affect next normal
  transaction


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#uart_noise_filter">uart_noise_filter</a></td>
  <td><a href="01_feature_report.md#uartrx_filtering">UART.RX_FILTERING</a></td>
</tr>
  </tbody>
</table>

## rx_oversample


- Use 16x baud clock to sample uart rx
- Drive uart rx with 16 bits value, using 16x baud clock
- Read RX oversampled value and ensure it's same as driven value


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#uart_rx_oversample">uart_rx_oversample</a></td>
  <td><a href="01_feature_report.md#uartrx_filtering">UART.RX_FILTERING</a></td>
</tr>
  </tbody>
</table>

## rx_start_bit_filter


- Start bit should last for at least half baud clock, otherwise, it will be dropped
- It's always enabled. Drive start bit for less than half cycle.
- Ensure the start bit will be dropped


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#uart_rx_start_bit_filter">uart_rx_start_bit_filter</a></td>
  <td><a href="01_feature_report.md#uartrx_filtering">UART.RX_FILTERING</a></td>
</tr>
  </tbody>
</table>

## rx_timeout


- Program timeout_ctrl register to randomize the timeout. Send random number of
  data over rx
- Wait until it's about to timeout, then check timeout interrupt doesn't fire. Wait
  for timeout and check timeout interrupt fires
- Wait until it's about to timeout, then use either read csr rdata or send RX item
  through uart interface to reset timeout timer in order to ensure timeout never
  fires


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#uart_intr">uart_intr</a></td>
  <td><a href="01_feature_report.md#uartfifo_interrupts">UART.FIFO_INTERRUPTS</a></td>
</tr>
  </tbody>
</table>

## smoke


- UART smoke test with few bytes transmitted and received asynchronously and
  in parallel with scoreboard checks
- TX and RX have 2 independent threads respectively.
  - program one Tx item in register and wait for it to complete at uart interface,
    before send another one
  - sequentially send one Rx byte, then immediately read from register and check it


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#uart_smoke">uart_smoke</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## stress_all


- Combine above sequences in one test to run sequentially, except csr sequence and
  uart_rx_oversample_vseq (requires zero_delays)
- Randomly add reset between each sequence


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#uart_stress_all">uart_stress_all</a></td>
  <td><a href="01_feature_report.md#uartfifo_interrupts">UART.FIFO_INTERRUPTS</a><br><a href="01_feature_report.md#uartline_loopback">UART.LINE_LOOPBACK</a><br><a href="01_feature_report.md#uartparity">UART.PARITY</a><br><a href="01_feature_report.md#uartrx_filtering">UART.RX_FILTERING</a><br><a href="01_feature_report.md#uartsystem_loopback">UART.SYSTEM_LOOPBACK</a><br><a href="01_feature_report.md#uarttx_override">UART.TX_OVERRIDE</a></td>
</tr>
  </tbody>
</table>

## sys_loopback


- Enable system loopback, then drive uart TX and data will be loopbacked through RX
- After loopback is done, uart.RDATA will be equal to the data programmed to
  uart.WDATA


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#uart_loopback">uart_loopback</a></td>
  <td><a href="01_feature_report.md#uartsystem_loopback">UART.SYSTEM_LOOPBACK</a></td>
</tr>
  </tbody>
</table>

## tx_overide
Enable override control and use register programming to drive uart output
directly.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#uart_tx_ovrd">uart_tx_ovrd</a></td>
  <td><a href="01_feature_report.md#uarttx_override">UART.TX_OVERRIDE</a></td>
</tr>
  </tbody>
</table>

## watermark


- Program random tx/rx fifo watermark level and keep sending random tx/rx data
  to fifo.
- As the number of pending data entries in the tx/rx fifo reaches the programmed
  watermark level (fifo size >= watermark level), ensure that the watermark interrupt
  is asserted
- Ensure interrupt stays asserted until cleared as well as fifo level dropped.
  The tx/rx watermark interrupt is sticky


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#uart_intr">uart_intr</a><br><a href="03_test_report.md#uart_tx_rx">uart_tx_rx</a></td>
  <td><a href="01_feature_report.md#uartfifo_interrupts">UART.FIFO_INTERRUPTS</a></td>
</tr>
  </tbody>
</table>
