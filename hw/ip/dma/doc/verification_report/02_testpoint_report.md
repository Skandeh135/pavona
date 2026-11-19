# dma Testpoint Report

## chip_sw_dma_abort (dragonfly)
Verify that an in-progress DMA transfer can be aborted at the chip level.

- SW configures the SPI host and the DMA controller for the same hardware handshake
  transfer with an inline SHA-2 digest as above.
- Once the transfer has started, SW sets CONTROL.abort.
- SW then reconfigures the SPI host and the DMA controller and runs the transfer again
  to completion.

Checks:

- STATUS.aborted is set after the abort request, indicating that the outstanding
  secure-side transactions have drained.
- The controller is left in a state from which a subsequent transfer can be configured
  and completed normally.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_dma_abort-dragonfly">chip_sw_dma_abort (dragonfly)</a></td>
  <td><a href="01_feature_report.md#dmaabort">DMA.ABORT</a><br><a href="01_feature_report.md#dmainline_hashing">DMA.INLINE_HASHING</a><br><a href="01_feature_report.md#dmamodehandshake">DMA.MODE.HANDSHAKE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_dma_inline_hashing (dragonfly)
Verify DMA hardware-handshake transfers from a peripheral FIFO with inline hashing.

- SW configures the SPI host and the DMA controller for a hardware handshake transfer,
  with the SPI host as the source of the data and an opcode selecting an inline SHA-2
  digest.
- The DV environment drives the SPI traffic so that the DMA controller is paced by the
  LSIO trigger of the SPI host.
- SW then performs a second, memory-to-memory transfer of the received data.

Checks:

- The transfer completes and the received data matches the data driven by the testbench.
- The digest collected from the SHA2_DIGEST registers matches the expected digest of the
  transferred data.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_dma_inline_hashing-dragonfly">chip_sw_dma_inline_hashing (dragonfly)</a></td>
  <td><a href="01_feature_report.md#dmainline_hashing">DMA.INLINE_HASHING</a><br><a href="01_feature_report.md#dmamodehandshake">DMA.MODE.HANDSHAKE</a><br><a href="01_feature_report.md#dmamodememory">DMA.MODE.MEMORY</a></td>
</tr>
  </tbody>
</table>

## dma_abort

Test to check DMAC.abort functionality

Stimulus:

- Configure DMA to perform a copy operation randomly with different source and destination parameters
- Randomly enable hardware_handshake mode
- Start DMA operation
- Abort DMA operation before completion by setting DMAC.abort
- Wait for PLIC interrupt assertion if INTR_ENABLE.int_enable is set else poll for DMAC.DONE bit
- Repeat operation with different source and destination parameters

Checking:

- Check if STATUS.aborted bit is set (This indicates DMA operation is aborted)
- Check that all outstanding transactions on secure internal TLUL interface are complete


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#dma_abort">dma_abort</a></td>
  <td><a href="01_feature_report.md#dmaabort">DMA.ABORT</a></td>
</tr>
  </tbody>
</table>

## dma_config_lock

Attempt to change the configuration registers whilst the DMA controller is active.
The majority of the configuration registers are protected using the `CFG_REGWEN` write enable register.
Since the enable is controlled exclusively by the hardware itself, the standard CSR tests are unable to test that it operates correctly.

Stimulus:

- Configure and start the DUT performing a long transfer.
- Choose one or more random configuration registers that should be protected by `CFG_REGWEN`.
- Whilst the DUT is still operating, attempt to invert the contents of the protected registers.

Checking:

- Check the value of the `CFG_REGWEN` register before and after starting the DMA transfer.
- Check that the contents of the chosen configuration registers do not change.
- Check the value of the `CFG_REGWEN` register after the transfer has completed.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#dma_config_lock">dma_config_lock</a></td>
  <td><a href="01_feature_report.md#dmaconfig_lock">DMA.CONFIG_LOCK</a></td>
</tr>
  </tbody>
</table>

## dma_generic_smoke

Smoke test with both 'memory-to-memory' and 'hardware handshaking' transfers.

Stimulus:

- FW allocates DMA enabled Memory Space for the data movement
- FW configures Source Address and ASID
- FW configures Destination Address and ASID
- FW completes other configuration such as:
  1. Operation Size
  2. Opcode
- FW triggers the DMA operation
- FW either
  1. Poll for completion
  2. Waits for Completion Interrupt
- Reset memory contents at the end of iteration


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#dma_generic_smoke">dma_generic_smoke</a></td>
  <td><a href="01_feature_report.md#dmainline_hashing">DMA.INLINE_HASHING</a><br><a href="01_feature_report.md#dmamemory_rangeconfig">DMA.MEMORY_RANGE.CONFIG</a><br><a href="01_feature_report.md#dmamodehandshake">DMA.MODE.HANDSHAKE</a><br><a href="01_feature_report.md#dmamodememory">DMA.MODE.MEMORY</a></td>
</tr>
  </tbody>
</table>

## dma_generic_stress

Stress test which combines `dma_memory_stress` and `dma_handshake_stress` to ensure that both 'memory-to-memory' and 'hardware handshaking' modes are exercised together without intervening resets.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#dma_generic_stress">dma_generic_stress</a></td>
  <td><a href="01_feature_report.md#dmamodehandshake">DMA.MODE.HANDSHAKE</a><br><a href="01_feature_report.md#dmamodememory">DMA.MODE.MEMORY</a></td>
</tr>
  </tbody>
</table>

## dma_handshake_mem_buffer_overflow

Test to check DMA memory buffer threshold and limit behavior with 'hardware handshake' mode

Stimulus:

- Configure DMA for 'hardware handshake' mode
- Set memory_buffer_addr_auto_increment
- Start DMA operation by setting DMAC.GO bit
- Assert Low Speed IO (LSIO) interrupt
- Wait for TLUL transaction on the output interface
- Deassert LSIO interrupt
- Wait for the operation to complete
- Repeat the operation with different source and destination parameters

Checking:

- Check if DMA operation is completed successfully in each iteration
  * Check if DMAC.GO bit is set until the DMA operation is complete
  * Check if STATUS.busy bit is set until 'hardware handshake' mode is disabled
  * Check if STATUS.done is set after LSIO interrupt is deasserted
- Check if PLIC interrupt is asserted when memory_buffer_auto_increment is enabled


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#dma_handshake_stress">dma_handshake_stress</a></td>
  <td><a href="01_feature_report.md#dmaaddressing">DMA.ADDRESSING</a><br><a href="01_feature_report.md#dmamodehandshake">DMA.MODE.HANDSHAKE</a></td>
</tr>
  </tbody>
</table>

## dma_handshake_smoke

Smoke test in which 'hardware handshake' DMA operations are performed

Stimulus:

  - Configure DMA
    * Randomize DMA memory region base and limit
    * Randomize source and destination address space IDs and address pointers such that all valid source and destination combinations are covered at least once
    * Randomize total transfer width and transaction sizes
    * Program DMAC.op_code and enable 'hardware handshake' mode
  - Start DMA operation by setting DMAC.GO bit
- Assert Low Speed IO (LSIO) interrupt
- Wait for TLUL transaction on the output interface
- Respond with random number of data items from TLUL agent in the testbench
- Deassert LSIO interrupt
- Wait for the operation to complete
- Repeat the copy operation with different source and destination parameters

Checking:

- Check if DMA operation is completed successfully
  * Check that the data presented at the source TLUL interface appears unchanged on the destination TLUL interface
  * Check for assertion of PLIC interrupt if INTR_ENABLE.int_enable else check for DMAC.DONE after every iteration
  * Check if the number of requests on TLUL agent matches the expected data size
- Check if STATUS.busy bit is set until 'hardware handshake' mode is disabled
- Check if STATUS.done is set after LSIO interrupt is deasserted


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#dma_handshake_smoke">dma_handshake_smoke</a></td>
  <td><a href="01_feature_report.md#dmainline_hashing">DMA.INLINE_HASHING</a><br><a href="01_feature_report.md#dmamemory_rangeconfig">DMA.MEMORY_RANGE.CONFIG</a><br><a href="01_feature_report.md#dmamodehandshake">DMA.MODE.HANDSHAKE</a><br><a href="01_feature_report.md#dmatransfer_width">DMA.TRANSFER_WIDTH</a></td>
</tr>
  </tbody>
</table>

## dma_handshake_stress

Stress test in which hardware handshake DMA operations are performed. Goal is to achieve maximum possible coverage of DMA configuration space in 'hardware handshake' mode

Stimulus:

  - Configure DMA
    * Randomize DMA memory region base and limit
    * Randomize source and destination address space IDs and address pointers
      such that all valid source and destination combinations are covered at least once
    * Randomize total transfer width and transaction size
    * Randomize DMAC.data_direction
    * Randomize DMAC.FIFO_addr_auto_increment_enable and DMAC.memory_addr_auto_increment_enable
    * Program DMAC register with OP code and enable 'hardware handshake' mode
  - Start DMA operation by setting DMAC.GO bit
- Start DMA operation by setting DMAC.GO bit
- Assert Low Speed IO (LSIO) interrupt
- Wait for TLUL transaction on the output interface
- Respond with random number of data items from TLUL agent in the testbench
- Deassert LSIO interrupt
- Wait for the operation to complete

Checking:

- Check if DMA operation is completed successfully in each iteration
  * Check if DMAC.GO bit is not set until the DMA operation is complete
  * Check if STATUS.busy bit is set until 'hardware handshake' mode is disabled
  * Check if STATUS.done is set after LSIO interrupt is deasserted


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#dma_handshake_stress">dma_handshake_stress</a></td>
  <td><a href="01_feature_report.md#dmaaddressing">DMA.ADDRESSING</a><br><a href="01_feature_report.md#dmainline_hashing">DMA.INLINE_HASHING</a><br><a href="01_feature_report.md#dmamemory_rangeconfig">DMA.MEMORY_RANGE.CONFIG</a><br><a href="01_feature_report.md#dmamodehandshake">DMA.MODE.HANDSHAKE</a><br><a href="01_feature_report.md#dmatransfer_width">DMA.TRANSFER_WIDTH</a></td>
</tr>
  </tbody>
</table>

## dma_handshake_tl_error

Test to check TLUL error behavior on DMA interfaces with 'hardware handshake' mode

Stimulus:

- Configure DMA to perform a copy operation with different source and destination parameters in hardware_handshake mode
- Start DMA operation by setting DMAC.GO bit
- Respond with an error on either source or destination TLUL interface request
- Wait for PLIC interrupt assertion if INTR_ENABLE.int_enable is set else poll for DMAC.DONE bit

Checking:

- Check if STATUS.error bit is set (This indicates DMA operation is aborted)
- Check that there are no TLUL transactions on source and destination interfaces after error response
- Check if DMA generates an alert


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#dma_handshake_stress">dma_handshake_stress</a></td>
  <td><a href="01_feature_report.md#dmaerror_handling">DMA.ERROR_HANDLING</a><br><a href="01_feature_report.md#dmamodehandshake">DMA.MODE.HANDSHAKE</a></td>
</tr>
  </tbody>
</table>

## dma_illegal_addr_range

Test to check DMA hardware enforced security check for illegal source or destination address

Stimulus:

- Configure DMA
  * Update DMA memory region base and limit
  * Update Source and Destination address pointers and address space IDs such that the address source or destination address is outside the DMA memory region
- Configure DMA with total transfer width and transaction size
- Enable 'hardware handshake' mode and direction randomly
- Start DMA operation
- Wait for interrupt assertion if INTR_ENABLE.int_enable is set else poll for STATUS.abort bit

Checking:

- Check if STATUS.aborted bit is set (This indicates DMA operation is aborted)
- Check if DMA generates an alert


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#dma_generic_stress">dma_generic_stress</a><br><a href="03_test_report.md#dma_handshake_stress">dma_handshake_stress</a><br><a href="03_test_report.md#dma_mem_enabled">dma_mem_enabled</a></td>
  <td><a href="01_feature_report.md#dmamemory_rangeconfig">DMA.MEMORY_RANGE.CONFIG</a><br><a href="01_feature_report.md#dmasecurity_checks">DMA.SECURITY_CHECKS</a></td>
</tr>
  </tbody>
</table>

## dma_longer_transfer

Test to check DMA behavior at the upper extreme of the transfer size range

Stimulus:

- Restrict the randomization to valid DMA configurations only
- Disable the default constraint which keeps transfers short, and instead choose the
  total transfer size from a range starting at 4KiB and extending upwards with
  inverse logarithmic probability, so that occasional very large transfers occur
- Restrict the transfer width to 4 bytes and remove the access and response delays, to
  keep the simulation time of these transfers manageable
- Perform a single transfer per run, relying on multiple seeds for coverage
- Cover all source and destination address space combinations, both 'memory-to-memory'
  and 'hardware handshake' modes, and inline hashing wherever its requirements are met

Checking:

- Check that the transfer completes successfully and that the data presented at the
  source appears unchanged at the destination
- Check that the transfer completes without any address, size or counter wrapping
  errors as the total size grows
- Check that any inline hash digest matches the expected digest of the transferred data


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#dma_longer_transfer">dma_longer_transfer</a></td>
  <td><a href="01_feature_report.md#dmainline_hashing">DMA.INLINE_HASHING</a><br><a href="01_feature_report.md#dmamemory_rangeconfig">DMA.MEMORY_RANGE.CONFIG</a><br><a href="01_feature_report.md#dmamodehandshake">DMA.MODE.HANDSHAKE</a><br><a href="01_feature_report.md#dmamodememory">DMA.MODE.MEMORY</a></td>
</tr>
  </tbody>
</table>

## dma_memory_region_lock

Test to check DMA memory region lock functionality

Stimulus:

  - Configure DMA
    * Randomize DMA memory region base and limit
    * Randomize source and destination address space IDs and address pointers such that all valid source and destination combinations are covered at least once
    * Randomize Total transfer width and transaction size
    * Lock DMA memory configuration registers
    * Program DMAC register with OP code and randomize 'hardware handshake' mode enable bit
  - Start DMA operation by setting DMAC.GO bit
- Randomly change the DMA memory region base and limit
- Wait for the operation to complete
- Reset the design by asserting rst_n
- Repeat DMA operation without locking the DMA memory configuration registers

Checking:

- Check that DMA operation is completed successfully
  * Check for assertion of interrupt if INTR_ENABLE.int_enable else check for DMAC.DONE after every iteration
- Check if writes to DMA memory region and base values are ignored until range_regwen.regwen is cleared
- Check if the range_regwen.regwen is set to MuBi4True after deassertion of reset


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#dma_memory_region_lock">dma_memory_region_lock</a></td>
  <td><a href="01_feature_report.md#dmamemory_rangeconfig">DMA.MEMORY_RANGE.CONFIG</a><br><a href="01_feature_report.md#dmamemory_rangelock">DMA.MEMORY_RANGE.LOCK</a></td>
</tr>
  </tbody>
</table>

## dma_memory_smoke

Smoke test in which random DMA operations are performed with 'memory-to-memory' mode

Stimulus:

  - Configure DMA
    * Randomize DMA memory region base and limit
    * Randomize source and destination address space IDs and address pointers such that all valid source and destination combinations are covered at least once
    * Randomize Total transfer width and transaction size
    * Update DMAC.op_code and disable hardware_handshake mode
  - Start DMA operation by setting DMAC.GO bit
  - Wait for TLUL transactions on the output interface
  - Respond with data from the TLUL agent in the testbench
  - Wait for the operation to complete
  - Repeat the operation randomly with different source and destination parameters

Checking:

  - Check that the data presented at the source TLUL interface appears unchanged on the destination TLUL interface
  - Check for the assertion of PLIC interrupt if INTR_ENABLE.int_enable else check for DMAC.DONE after every iteration
  - Check for any spurious requests from the remaining TLUL interfaces
  - Check if the number of requests on TLUL agent matches the expected data size
  - Check if DMAC.busy bit is set throughout the operation in each iteration


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#dma_memory_smoke">dma_memory_smoke</a></td>
  <td><a href="01_feature_report.md#dmainline_hashing">DMA.INLINE_HASHING</a><br><a href="01_feature_report.md#dmamemory_rangeconfig">DMA.MEMORY_RANGE.CONFIG</a><br><a href="01_feature_report.md#dmamodememory">DMA.MODE.MEMORY</a><br><a href="01_feature_report.md#dmatransfer_width">DMA.TRANSFER_WIDTH</a></td>
</tr>
  </tbody>
</table>

## dma_memory_stress

Stress test in which random DMA operations are performed with 'memory-to-memory' mode. Goal is to achieve maximum possible coverage of DMA configuration space in 'memory-to-memory' mode

Stimulus:

 - Configure DMA
   * Randomize DMA memory region base and limit
   * Randomize source and destination address space IDs and address pointers
   * Randomize Total transfer width and transaction size
   * Program DMAC register with OP code and disable 'hardware handshake' mode
 - Start DMA operation by setting DMAC.GO bit
 - Wait for the operation to complete
 - Repeat operation with different source and destination addresses

Checking:

 - Check that DMA operation is completed successfully
   * Check that the number of TLUL requests matches the expected data size
   * Check that the data presented at the source TLUL interface appears unchanged on the destination TLUL interface
   * Check if STATUS.busy bit is set until the copy operation is complete
   * Check if STATUS.done bit is set after the copy operation


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#dma_memory_stress">dma_memory_stress</a></td>
  <td><a href="01_feature_report.md#dmainline_hashing">DMA.INLINE_HASHING</a><br><a href="01_feature_report.md#dmamemory_rangeconfig">DMA.MEMORY_RANGE.CONFIG</a><br><a href="01_feature_report.md#dmamodememory">DMA.MODE.MEMORY</a><br><a href="01_feature_report.md#dmatransfer_width">DMA.TRANSFER_WIDTH</a></td>
</tr>
  </tbody>
</table>

## dma_memory_tl_error

Test to check TLUL error behavior on DMA interfaces

Stimulus:

- Configure DMA to perform a copy operation with different source and destination parameters in 'memory-to-memory' mode
- Start DMA operation by setting DMAC.GO bit
- Respond with an error on either source or destination TLUL interface request
- Wait for PLIC interrupt assertion if INTR_ENABLE.int_enable is set else poll for DMAC.ABORTED bit

Checking:

- Check if STATUS.error bit is set (This indicates DMA operation is aborted)
- Check that there are no TLUL transactions on source and destination interfaces after error response
- Check if DMA generates an alert


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#dma_memory_stress">dma_memory_stress</a></td>
  <td><a href="01_feature_report.md#dmaerror_handling">DMA.ERROR_HANDLING</a><br><a href="01_feature_report.md#dmamodememory">DMA.MODE.MEMORY</a></td>
</tr>
  </tbody>
</table>

## dma_short_transfer

Test to check DMA behavior at the lower extreme of the transfer size range

Stimulus:

- Restrict the randomization to valid DMA configurations only, since invalid
  configurations are covered by the stress tests
- Constrain the total transfer size to fewer than 16 bytes, so that transfers complete
  in very few bus transactions
- Randomize everything else, covering all source and destination address space
  combinations, both 'memory-to-memory' and 'hardware handshake' modes, all transfer
  widths, and inline hashing wherever its requirements are met
- Perform many iterations, since each transfer is short

Checking:

- Check that each transfer completes successfully and that the data presented at the
  source appears unchanged at the destination
- Check that transfers which are shorter than, or not a multiple of, the configured
  transfer width are handled without loss or corruption of data
- Check that any inline hash digest matches the expected digest of the transferred data


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#dma_short_transfer">dma_short_transfer</a></td>
  <td><a href="01_feature_report.md#dmainline_hashing">DMA.INLINE_HASHING</a><br><a href="01_feature_report.md#dmamemory_rangeconfig">DMA.MEMORY_RANGE.CONFIG</a><br><a href="01_feature_report.md#dmamodehandshake">DMA.MODE.HANDSHAKE</a><br><a href="01_feature_report.md#dmamodememory">DMA.MODE.MEMORY</a><br><a href="01_feature_report.md#dmatransfer_width">DMA.TRANSFER_WIDTH</a></td>
</tr>
  </tbody>
</table>

## dma_stress_all

Run the other tests in random order while injecting TL errors and running automated CSR tests in parallel.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#dma_stress_all">dma_stress_all</a></td>
  <td><a href="01_feature_report.md#dmaerror_handling">DMA.ERROR_HANDLING</a><br><a href="01_feature_report.md#dmamemory_rangeconfig">DMA.MEMORY_RANGE.CONFIG</a><br><a href="01_feature_report.md#dmamemory_rangelock">DMA.MEMORY_RANGE.LOCK</a><br><a href="01_feature_report.md#dmamodehandshake">DMA.MODE.HANDSHAKE</a><br><a href="01_feature_report.md#dmamodememory">DMA.MODE.MEMORY</a></td>
</tr>
  </tbody>
</table>
