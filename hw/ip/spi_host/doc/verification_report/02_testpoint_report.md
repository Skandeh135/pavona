# spi_host Testpoint Report

## Idlecsbactive

Stimulus:

  - Pause next segment availability and idly wait for next command

Checking:

  - Ensure transactions goes through even with a segment pause and idle wait
    in the state IdleCsbActive


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_host_idlecsbactive">spi_host_idlecsbactive</a></td>
  <td><a href="01_feature_report.md#spihostratestandard">SPIHOST.RATE.STANDARD</a></td>
</tr>
  </tbody>
</table>

## chip_select_timing

Stimulus:

  - Randomly select a setting for the 16bit clock divider

Checking:

  - Check that the DUT operates correctly under different SPI clock speeds


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_host_speed">spi_host_speed</a></td>
  <td><a href="01_feature_report.md#spihostconfigclockdiv">SPIHOST.CONFIG.CLOCKDIV</a></td>
</tr>
  </tbody>
</table>

## chip_sw_spi_host_configuration (dragonfly)
 Verifiy that the polarity configurations work appropriately.

1. Send four packets from the host to the device, each one with a different configuration for cpol and cpha.
2. The device should receive the packets and be able to decode them with the appropriated configuration.


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
  <td><a href="01_feature_report.md#spihostconfigclockdiv">SPIHOST.CONFIG.CLOCKDIV</a><br><a href="01_feature_report.md#spihostconfigcpol">SPIHOST.CONFIG.CPOL</a></td>
</tr>
  </tbody>
</table>

## chip_sw_spi_host_configuration (egret)
 Verifiy that the polarity configurations work appropriately.

1. Send four packets from the host to the device, each one with a different configuration for cpol and cpha.
2. The device should receive the packets and be able to decode them with the appropriated configuration.


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
  <td><a href="01_feature_report.md#spihostconfigclockdiv">SPIHOST.CONFIG.CLOCKDIV</a><br><a href="01_feature_report.md#spihostconfigcpol">SPIHOST.CONFIG.CPOL</a></td>
</tr>
  </tbody>
</table>

## chip_sw_spi_host_events (dragonfly)
 Verify that various events are correctly triggered by the SPI host.

- For the transmit empty and watermark events:
  - Fill the transmit queue on the Ibex side.
  - Clear and enable the respective interrupt.
  - Testbench should check that it receives the same data as Ibex has sent.
  - Ibex should check whether it has received the transmit empty or watermark interrupt within a reasonable amount of time.
- For the receive full and watermark events:
  - Empty the receive queue.
  - Clear and enable the respective interrupt.
  - Testbench sends as much data as the receive queue can hold for the full interrupt or the amount necessary to hit the watermark.
  - Ibex checks that the receive full or watermark interrupt is raised.


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
  <td><a href="01_feature_report.md#spihosteventempty">SPIHOST.EVENT.EMPTY</a><br><a href="01_feature_report.md#spihosteventfull">SPIHOST.EVENT.FULL</a><br><a href="01_feature_report.md#spihosteventwatermark">SPIHOST.EVENT.WATERMARK</a></td>
</tr>
  </tbody>
</table>

## chip_sw_spi_host_events (egret)
 Verify that various events are correctly triggered by the SPI host.

- For the transmit empty and watermark events:
  - Fill the transmit queue on the Ibex side.
  - Clear and enable the respective interrupt.
  - Testbench should check that it receives the same data as Ibex has sent.
  - Ibex should check whether it has received the transmit empty or watermark interrupt within a reasonable amount of time.
- For the receive full and watermark events:
  - Empty the receive queue.
  - Clear and enable the respective interrupt.
  - Testbench sends as much data as the receive queue can hold for the full interrupt or the amount necessary to hit the watermark.
  - Ibex checks that the receive full or watermark interrupt is raised.


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
  <td><a href="01_feature_report.md#spihosteventempty">SPIHOST.EVENT.EMPTY</a><br><a href="01_feature_report.md#spihosteventfull">SPIHOST.EVENT.FULL</a><br><a href="01_feature_report.md#spihosteventwatermark">SPIHOST.EVENT.WATERMARK</a></td>
</tr>
  </tbody>
</table>

## chip_sw_spi_host_pass_through (dragonfly)
Verify that the SPI host can be configured in pass through mode.
Essentially the configuration is as follows: (real) host -> OT -> flash device

- Connect one of the OpenTitan SPI hosts to a SPI device on a serial NOR flash.
- Configure an OpenTitan SPI device and the above mentioned OpenTitan SPI host in pass through mode.
- Use the testbench's (external) SPI host to write a word to the flash through the passthrough SPI host and device in OpenTitan.
- Let the testbench read that word back, again through the pass through of the SPI host and device on OpenTitan.
- The testbench should check that the word read back is the same as the one written.


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
  <td><a href="01_feature_report.md#spihostusecasepassthrough">SPIHOST.USECASE.PASSTHROUGH</a><br><a href="01_feature_report.md#spihostusecaseserialnorflash">SPIHOST.USECASE.SERIALNORFLASH</a></td>
</tr>
  </tbody>
</table>

## chip_sw_spi_host_pass_through (egret)
Verify that the SPI host can be configured in pass through mode.
Essentially the configuration is as follows: (real) host -> OT -> flash device

- Connect one of the OpenTitan SPI hosts to a SPI device on a serial NOR flash.
- Configure an OpenTitan SPI device and the above mentioned OpenTitan SPI host in pass through mode.
- Use the testbench's (external) SPI host to write a word to the flash through the passthrough SPI host and device in OpenTitan.
- Let the testbench read that word back, again through the pass through of the SPI host and device on OpenTitan.
- The testbench should check that the word read back is the same as the one written.


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
  <td><a href="01_feature_report.md#spihostusecasepassthrough">SPIHOST.USECASE.PASSTHROUGH</a><br><a href="01_feature_report.md#spihostusecaseserialnorflash">SPIHOST.USECASE.SERIALNORFLASH</a></td>
</tr>
  </tbody>
</table>

## chip_sw_spi_host_tx_rx (dragonfly)
Verify the transmission of data on the chip's SPI host port.

- Program the SPI host to send a known payload out of the chip on the SPI host ports.
- The testbench receives the payload and plays it back to the SPI host interface.
- The SW verifies the sent payload matches the read response and services SPI event
  interrupts.
- Run with min and max SPI clk frequencies and with single, dual and quad SPI modes.

Verify all SPI host instances in the chip.

Notes for silicon targets:

- The testbench that mimics a physical SPI device should measure the clock to verify that the frequencies for each speed mode is correct.
  This can be done by checking timing of the beginning and the end of the packet.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_spi_host_tx_rx-dragonfly">chip_sw_spi_host_tx_rx (dragonfly)</a></td>
  <td><a href="01_feature_report.md#spihostratedual">SPIHOST.RATE.DUAL</a><br><a href="01_feature_report.md#spihostratequad">SPIHOST.RATE.QUAD</a><br><a href="01_feature_report.md#spihostratestandard">SPIHOST.RATE.STANDARD</a></td>
</tr>
  </tbody>
</table>

## chip_sw_spi_host_tx_rx (egret)
Verify the transmission of data on the chip's SPI host port.

- Program the SPI host to send a known payload out of the chip on the SPI host ports.
- The testbench receives the payload and plays it back to the SPI host interface.
- The SW verifies the sent payload matches the read response and services SPI event
  interrupts.
- Run with min and max SPI clk frequencies and with single, dual and quad SPI modes.

Verify all SPI host instances in the chip.

Notes for silicon targets:

- The testbench that mimics a physical SPI device should measure the clock to verify that the frequencies for each speed mode is correct.
  This can be done by checking timing of the beginning and the end of the packet.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_spi_host_tx_rx-egret">chip_sw_spi_host_tx_rx (egret)</a></td>
  <td><a href="01_feature_report.md#spihostratedual">SPIHOST.RATE.DUAL</a><br><a href="01_feature_report.md#spihostratequad">SPIHOST.RATE.QUAD</a><br><a href="01_feature_report.md#spihostratestandard">SPIHOST.RATE.STANDARD</a></td>
</tr>
  </tbody>
</table>

## clock_rate

Stimulus:

  - select different settings for:
    - CONFIGOPTS_0.CSNIDLE_0
    - CONFIGOPTS_0.CSNLEAD_0
    - CONFIGOPTS_0.CSNTRAIL_0

Checking:

  - verify that merging of commands work correctly
  - verify that the DUT can handle different sck -> cs_n timings


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_host_speed">spi_host_speed</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## cpol_cpha

Stimulus:

  - Randomly chip select for different polarity / phase

Checking:

  - Check that the DUT operates correctly under different cs_n settings


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_host_speed">spi_host_speed</a></td>
  <td><a href="01_feature_report.md#spihostconfigcpol">SPIHOST.CONFIG.CPOL</a></td>
</tr>
  </tbody>
</table>

## data_fifo_status

Ensure we are modelling the Fifo depths, to ensure we can compare against predictions
of their state, particularly current depth.

- TXDATA
  Push on CSR writes, Pop on submitting new word to ByteSel/SR
- RXDATA
  Push on new word from SR/ByteMerge, Pop on CSR read

Stimulus:

  - Create transactions that Pop/Push to the data FIFOs
  - Readback the queue depths at various points during active and after completed
    transactions.

Checking:

  - Ensure rx/tx_qd and rx/tx_full/empty match predictions.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_host_overflow_underflow">spi_host_overflow_underflow</a></td>
  <td><a href="01_feature_report.md#spihostconfigclockdiv">SPIHOST.CONFIG.CLOCKDIV</a><br><a href="01_feature_report.md#spihostratestandard">SPIHOST.RATE.STANDARD</a></td>
</tr>
  </tbody>
</table>

## duplex

Stimulus:

  - in standard mode set the DUT to run full duplex

Checking:

  - verify that the DUT support both half and full duplex in standard mode.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_host_smoke">spi_host_smoke</a></td>
  <td><a href="01_feature_report.md#spihostratestandard">SPIHOST.RATE.STANDARD</a></td>
</tr>
  </tbody>
</table>

## error_event_intr

This test includes multi tasks which verify error/event interrupt assertion
(except TX OVERFLOW error interrupt is verified in separate test)

Stimulus:

  - Program ERROR_ENABLE/EVENT_ENABLE register to enable
    corresponding error/event interrupt assertion
  - Program transaction with proper constraints to assert error/event interrupts

Checking:

  - Ensure transactions are transmitted/received correctly
  - Ensure the matching between the bit-field values of ERROR_STATUS
    and ERROR_ENABLE respectively once the error interrupt pin is asserted
  - Ensure the matching between the bit-field values of ERROR_ENABLE
    once the event interrupt pin is asserted


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_host_error_cmd">spi_host_error_cmd</a><br><a href="03_test_report.md#spi_host_event">spi_host_event</a><br><a href="03_test_report.md#spi_host_overflow_underflow">spi_host_overflow_underflow</a></td>
  <td><a href="01_feature_report.md#spihosteventempty">SPIHOST.EVENT.EMPTY</a><br><a href="01_feature_report.md#spihosteventfull">SPIHOST.EVENT.FULL</a><br><a href="01_feature_report.md#spihosteventwatermark">SPIHOST.EVENT.WATERMARK</a></td>
</tr>
  </tbody>
</table>

## full_cycle

Stimulus:

  - randomly select FULLCYC to be set

Checking:

  - Check that the data can be read one full cycle after the data was asserted


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_host_speed">spi_host_speed</a></td>
  <td><a href="01_feature_report.md#spihostconfigcpol">SPIHOST.CONFIG.CPOL</a><br><a href="01_feature_report.md#spihostratedual">SPIHOST.RATE.DUAL</a><br><a href="01_feature_report.md#spihostratequad">SPIHOST.RATE.QUAD</a><br><a href="01_feature_report.md#spihostratestandard">SPIHOST.RATE.STANDARD</a></td>
</tr>
  </tbody>
</table>

## passthrough_mode


- Verify the function of spi_host in passthrough_mode

Stimulus:

  - Enable Passthrough Mode

Checking:

  - Ensure Host to Device and Device to Host paths are switched to Passthrough ports


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_host_passthrough_mode">spi_host_passthrough_mode</a></td>
  <td><a href="01_feature_report.md#spihostusecasepassthrough">SPIHOST.USECASE.PASSTHROUGH</a></td>
</tr>
  </tbody>
</table>

## performance

Send/receive transactions at max bandwidth

Stimulus:

  - Program the content of timing fields of CONFIGOPTS to the min values
  - Programming TX1_CNT and TXN_CNT to issue read/write back-to-back transactions
  - Read/write rx_fifo/tx_fifo as soon as possible (avoid stalling transactions)

Checking:

  - Ensure transactions are transmitted/received correctly


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_host_performance">spi_host_performance</a></td>
  <td><a href="01_feature_report.md#spihostconfigclockdiv">SPIHOST.CONFIG.CLOCKDIV</a><br><a href="01_feature_report.md#spihostconfigcpol">SPIHOST.CONFIG.CPOL</a><br><a href="01_feature_report.md#spihostratedual">SPIHOST.RATE.DUAL</a><br><a href="01_feature_report.md#spihostratequad">SPIHOST.RATE.QUAD</a><br><a href="01_feature_report.md#spihostratestandard">SPIHOST.RATE.STANDARD</a></td>
</tr>
  </tbody>
</table>

## smoke

SPI_HOST smoke test in which random (rd/wr) transactions are sent to the DUT and
received asynchronously with scoreboard checks.

Stimulus:

  - Enable spi_host ip
  - Write data in standard mode - and read it back

Checking:

  - Ensure transactions are transmitted/received correctly


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_host_smoke">spi_host_smoke</a></td>
  <td><a href="01_feature_report.md#spihostratestandard">SPIHOST.RATE.STANDARD</a></td>
</tr>
  </tbody>
</table>

## speed

Stimulus:

  - randomly select the DUT to run single/dual/quad mode

Checking:

  - verify that all speeds are supported


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_host_speed">spi_host_speed</a></td>
  <td><a href="01_feature_report.md#spihostconfigclockdiv">SPIHOST.CONFIG.CLOCKDIV</a><br><a href="01_feature_report.md#spihostconfigcpol">SPIHOST.CONFIG.CPOL</a><br><a href="01_feature_report.md#spihostratedual">SPIHOST.RATE.DUAL</a><br><a href="01_feature_report.md#spihostratequad">SPIHOST.RATE.QUAD</a><br><a href="01_feature_report.md#spihostratestandard">SPIHOST.RATE.STANDARD</a></td>
</tr>
  </tbody>
</table>

## spien

Check that with mid-transaction writes to CONTROL.SPIEN, the block behaves according
to the documentation.

- Writing a zero to this register temporarily suspends any previously
  submitted transactions.
- If the block is re-enabled by writing a one to CONTROL.SPIEN, any previously
  executing commands will continue from wherever they left off.

Stimulus:

  - Issue a transaction
  - De-assert CONTROL.SPIEN after the command byte is received
  - Re-assert after a randomized delay

Checking:

  - Ensure transactions are transmitted/received correctly, even with a large
    temporary suspension in the middle.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_host_spien">spi_host_spien</a></td>
  <td><a href="01_feature_report.md#spihostratestandard">SPIHOST.RATE.STANDARD</a></td>
</tr>
  </tbody>
</table>

## stall

Stimulus:

  - Ongoing transaction has stalled due to lack of available space in the RX FIFO
    and continues when RX fifo is cleared
  - Ongoing transaction has stalled due to lack of data in the TX FIFO
    and continues when data is provided in TX FIFO

Checking:

  - Ensure Rxstall occurs and recovers
  - Ensure Txstall occurs and recovers


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_host_status_stall">spi_host_status_stall</a></td>
  <td><a href="01_feature_report.md#spihosteventempty">SPIHOST.EVENT.EMPTY</a><br><a href="01_feature_report.md#spihosteventfull">SPIHOST.EVENT.FULL</a><br><a href="01_feature_report.md#spihostratestandard">SPIHOST.RATE.STANDARD</a></td>
</tr>
  </tbody>
</table>

## stress_all

Support vseq (context) switching with random reset in between.

Stimulus:

  - Combine the above sequences in one test to run sequentially
    except csr sequence and (requires zero_delays)
  - Randomly add reset between each sequence

Checking:

  - Ensure transactions are transmitted/received correctly
  - Ensure reset is handled correctly


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_host_stress_all">spi_host_stress_all</a></td>
  <td><a href="01_feature_report.md#spihostconfigclockdiv">SPIHOST.CONFIG.CLOCKDIV</a><br><a href="01_feature_report.md#spihostconfigcpol">SPIHOST.CONFIG.CPOL</a><br><a href="01_feature_report.md#spihosteventempty">SPIHOST.EVENT.EMPTY</a><br><a href="01_feature_report.md#spihosteventfull">SPIHOST.EVENT.FULL</a><br><a href="01_feature_report.md#spihosteventwatermark">SPIHOST.EVENT.WATERMARK</a><br><a href="01_feature_report.md#spihostratedual">SPIHOST.RATE.DUAL</a><br><a href="01_feature_report.md#spihostratequad">SPIHOST.RATE.QUAD</a><br><a href="01_feature_report.md#spihostratestandard">SPIHOST.RATE.STANDARD</a></td>
</tr>
  </tbody>
</table>

## sw_reset

verify software reset behavior

Stimulus:

  - Reset the spi_host randomly
    after a random number of data shows up on FIFOs

Checking:

  - Ensure that reads to RXDATA register yield 0s after the rx_fifo is reset
  - Ensure that transactions are dropped in both the scoreboard and spi_agent monitor
    after the tx_fifo or spi_fsm is reset


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_host_sw_reset">spi_host_sw_reset</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## tx_rx_only

Stimulus:

  - in standard mode enable tx only and have the env send garbage back
  - in standard mode enable rx only and have the env ignore the incoming data

Checking:

  - verify that the DUT ignores rx line when in tx only mode
  - verify that the DUT does not drain the tx fifo in rx only mode


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_host_smoke">spi_host_smoke</a></td>
  <td><a href="01_feature_report.md#spihostratestandard">SPIHOST.RATE.STANDARD</a></td>
</tr>
  </tbody>
</table>

## winbond

Replace SPI agent with the Winbond Flash model

Stimulus:

  - constraint the Sequence to create well-formed transactions that the model understands

Checking:

  - Verify the DUT against the WindBond bfm by making the SPI agent passive
    to verify that we comply with the SPI targeted for Pavona


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
  <td>No features</td>
</tr>
  </tbody>
</table>
