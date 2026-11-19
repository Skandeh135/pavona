# dma Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="dmaabort">
      <td>DMA.ABORT</td>
      <td>Setting CONTROL.abort terminates an in-progress transfer, drains the outstanding   secure-side transactions and reports completion of the abort in STATUS.</td>
    </tr>
    <tr id="dmaaddressing">
      <td>DMA.ADDRESSING</td>
      <td>Per-endpoint addressing modes selected by SRC_CONFIG and DST_CONFIG: increment   controls whether consecutive transfers within a chunk advance the address, and wrap   controls whether the address returns to its programmed start at each chunk boundary.</td>
    </tr>
    <tr id="dmaconfig_lock">
      <td>DMA.CONFIG_LOCK</td>
      <td>While a transfer is in progress the hardware clears CFG_REGWEN, locking the transfer   configuration registers against modification; the control, status and comportable   registers remain writable.</td>
    </tr>
    <tr id="dmaerror_handling">
      <td>DMA.ERROR_HANDLING</td>
      <td>Bus errors encountered on any of the host interfaces stop the transfer, set the   error status together with the corresponding ERROR_CODE bit, and raise the error   interrupt.</td>
    </tr>
    <tr id="dmainline_hashing">
      <td>DMA.INLINE_HASHING</td>
      <td>Selecting a SHA-2 opcode computes a SHA-256, SHA-384 or SHA-512 digest over the   transferred data as it moves, leaving the result in the SHA2_DIGEST registers.</td>
    </tr>
    <tr id="dmamemory_rangeconfig">
      <td>DMA.MEMORY_RANGE.CONFIG</td>
      <td>The DMA-enabled memory range, programmed through ENABLED_MEMORY_RANGE_BASE and   ENABLED_MEMORY_RANGE_LIMIT and marked usable by RANGE_VALID, defines the window of   the secure internal address space which DMA transfers may touch.</td>
    </tr>
    <tr id="dmamemory_rangelock">
      <td>DMA.MEMORY_RANGE.LOCK</td>
      <td>Clearing the multi-bit RANGE_REGWEN locks the DMA-enabled memory range registers   against further modification until the next reset.</td>
    </tr>
    <tr id="dmamodehandshake">
      <td>DMA.MODE.HANDSHAKE</td>
      <td>Hardware handshake mode: the transfer is paced by the low-speed IO trigger lines,   with one chunk moved per assertion, so that a peripheral FIFO can be drained or   filled as data or space becomes available.</td>
    </tr>
    <tr id="dmamodememory">
      <td>DMA.MODE.MEMORY</td>
      <td>Memory-to-memory data movement: a transfer of the programmed total size is moved   from the source to the destination address once software sets CONTROL.go, without   any external pacing.</td>
    </tr>
    <tr id="dmasecurity_checks">
      <td>DMA.SECURITY_CHECKS</td>
      <td>Hardware-enforced checks of the programmed configuration before and during a   transfer, covering the address space identifiers, the validity of the enabled memory   range, and the requirement that transfers between the SoC and the secure internal   address space are staged inside that range. A failing check aborts the transfer and   reports the reason in ERROR_CODE.</td>
    </tr>
    <tr id="dmatransfer_width">
      <td>DMA.TRANSFER_WIDTH</td>
      <td>Sub-word transfers: the configured transfer width selects byte, half-word or word   accesses, with extraction of the addressed lane on reads and replication across the   bus word together with the corresponding byte enables on writes.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>DMA.MODE.MEMORY</th>
    <th>DMA.MODE.HANDSHAKE</th>
    <th>DMA.ADDRESSING</th>
    <th>DMA.TRANSFER_WIDTH</th>
    <th>DMA.MEMORY_RANGE.CONFIG</th>
    <th>DMA.MEMORY_RANGE.LOCK</th>
    <th>DMA.CONFIG_LOCK</th>
    <th>DMA.SECURITY_CHECKS</th>
    <th>DMA.ABORT</th>
    <th>DMA.ERROR_HANDLING</th>
    <th>DMA.INLINE_HASHING</th>
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
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#defining-relevant-memory-regions">Defining Relevant Memory Regions</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#defining-relevant-memory-regions">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#mode-of-operation">Mode of operation</a></th>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#generic-dma-operation">Generic DMA operation</a></th>
    <td><a href="../theory_of_operation.md#generic-dma-operation">X</a></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#hardware-handshake-based-dma-operation">Hardware handshake based DMA operation</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#hardware-handshake-based-dma-operation">X</a></td>
    <td><a href="../theory_of_operation.md#hardware-handshake-based-dma-operation">X</a></td>
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
    <th><a href="../theory_of_operation.md#security-considerations">Security Considerations</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#security-considerations">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#dmac-hw-enforced-security-checks">DMAC HW Enforced Security Checks</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#dmac-hw-enforced-security-checks">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#dma-controller-configuration-notes">DMA Controller Configuration Notes</a></th>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#configuration-locking">Configuration Locking</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#configuration-locking">X</a></td>
    <td><a href="../theory_of_operation.md#configuration-locking">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#aborting-a-transfer">Aborting a Transfer</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#aborting-a-transfer">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#error-handling">Error Handling</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#error-handling">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#inline-hashing">Inline Hashing</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#inline-hashing">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#extension-inline-operations">Extension: Inline Operations</a></th>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#clocking-and-reset">Clocking and reset</a></th>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#clock-gating">Clock gating</a></th>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#integration-into-systems-on-chips-socs">Integration into Systems On Chips (SoCs)</a></th>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#soc-system-bus">SoC System Bus</a></th>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#soc-system-bus-request">SoC System Bus Request</a></th>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#soc-system-bus-response">SoC System Bus Response</a></th>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#sub-word-extraction-and-replication">Sub-word extraction and replication</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#sub-word-extraction-and-replication">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#low-speed-io-peripheral-interrupt-lines">Low Speed I/O peripheral interrupt lines</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#low-speed-io-peripheral-interrupt-lines">X</a></td>
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
    <th>DMA.MODE.MEMORY</th>
    <th>DMA.MODE.HANDSHAKE</th>
    <th>DMA.ADDRESSING</th>
    <th>DMA.TRANSFER_WIDTH</th>
    <th>DMA.MEMORY_RANGE.CONFIG</th>
    <th>DMA.MEMORY_RANGE.LOCK</th>
    <th>DMA.CONFIG_LOCK</th>
    <th>DMA.SECURITY_CHECKS</th>
    <th>DMA.ABORT</th>
    <th>DMA.ERROR_HANDLING</th>
    <th>DMA.INLINE_HASHING</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dma_memory_smoke">dma_memory_smoke</a></th>
    <td><a href="02_testpoint_report.md#dma_memory_smoke">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_memory_smoke">X</a></td>
    <td><a href="02_testpoint_report.md#dma_memory_smoke">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_memory_smoke">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dma_handshake_smoke">dma_handshake_smoke</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_handshake_smoke">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_handshake_smoke">X</a></td>
    <td><a href="02_testpoint_report.md#dma_handshake_smoke">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_handshake_smoke">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dma_generic_smoke">dma_generic_smoke</a></th>
    <td><a href="02_testpoint_report.md#dma_generic_smoke">X</a></td>
    <td><a href="02_testpoint_report.md#dma_generic_smoke">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_generic_smoke">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_generic_smoke">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dma_memory_region_lock">dma_memory_region_lock</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_memory_region_lock">X</a></td>
    <td><a href="02_testpoint_report.md#dma_memory_region_lock">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dma_memory_tl_error">dma_memory_tl_error</a></th>
    <td><a href="02_testpoint_report.md#dma_memory_tl_error">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_memory_tl_error">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dma_handshake_tl_error">dma_handshake_tl_error</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_handshake_tl_error">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_handshake_tl_error">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dma_handshake_stress">dma_handshake_stress</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_handshake_stress">X</a></td>
    <td><a href="02_testpoint_report.md#dma_handshake_stress">X</a></td>
    <td><a href="02_testpoint_report.md#dma_handshake_stress">X</a></td>
    <td><a href="02_testpoint_report.md#dma_handshake_stress">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_handshake_stress">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dma_memory_stress">dma_memory_stress</a></th>
    <td><a href="02_testpoint_report.md#dma_memory_stress">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_memory_stress">X</a></td>
    <td><a href="02_testpoint_report.md#dma_memory_stress">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_memory_stress">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dma_generic_stress">dma_generic_stress</a></th>
    <td><a href="02_testpoint_report.md#dma_generic_stress">X</a></td>
    <td><a href="02_testpoint_report.md#dma_generic_stress">X</a></td>
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
    <th><a href="02_testpoint_report.md#dma_short_transfer">dma_short_transfer</a></th>
    <td><a href="02_testpoint_report.md#dma_short_transfer">X</a></td>
    <td><a href="02_testpoint_report.md#dma_short_transfer">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_short_transfer">X</a></td>
    <td><a href="02_testpoint_report.md#dma_short_transfer">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_short_transfer">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dma_longer_transfer">dma_longer_transfer</a></th>
    <td><a href="02_testpoint_report.md#dma_longer_transfer">X</a></td>
    <td><a href="02_testpoint_report.md#dma_longer_transfer">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_longer_transfer">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_longer_transfer">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dma_handshake_mem_buffer_overflow">dma_handshake_mem_buffer_overflow</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_handshake_mem_buffer_overflow">X</a></td>
    <td><a href="02_testpoint_report.md#dma_handshake_mem_buffer_overflow">X</a></td>
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
    <th><a href="02_testpoint_report.md#dma_abort">dma_abort</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_abort">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dma_stress_all">dma_stress_all</a></th>
    <td><a href="02_testpoint_report.md#dma_stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#dma_stress_all">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#dma_stress_all">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_stress_all">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dma_illegal_addr_range">dma_illegal_addr_range</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_illegal_addr_range">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_illegal_addr_range">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dma_config_lock">dma_config_lock</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dma_config_lock">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_dma_inline_hashing-dragonfly">chip_sw_dma_inline_hashing (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_dma_inline_hashing-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_dma_inline_hashing-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_dma_inline_hashing-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_dma_abort-dragonfly">chip_sw_dma_abort (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_dma_abort-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_dma_abort-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_dma_abort-dragonfly">X</a></td>
  </tr>
</table>
</div>
</div>
