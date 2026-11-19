# rv_core_ibex Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="rv_core_ibexaddress_translation">
      <td>RV_CORE_IBEX.ADDRESS_TRANSLATION</td>
      <td>The core wrapper implements address translation. RISC-V core memory accesses that match agiven range will have an offset applied before being sent to the memory system</td>
    </tr>
    <tr id="rv_core_ibexcpuepmp">
      <td>RV_CORE_IBEX.CPU.EPMP</td>
      <td>The RISC-V core implements the ePMP scheme specified in the RISC-V privileged architecturespecification, 16 regions are available for use.</td>
    </tr>
    <tr id="rv_core_ibexcpuicache">
      <td>RV_CORE_IBEX.CPU.ICACHE</td>
      <td>The RISC-V core implements an instruction caches that utilizes scrambling. The scramblingkey is rotated on a FENCE.I instruction being executed.</td>
    </tr>
    <tr id="rv_core_ibexcpuinterrupts">
      <td>RV_CORE_IBEX.CPU.INTERRUPTS</td>
      <td>The RISC-V core has a number of interrupt sources:- Software interrupt, controlled by a memory mapped PLIC register- External interrupt, from interrupts prioritise by the PLIC- Timer interrupt, from rv_timer module- Non-maskable interrupt, triggered by watchdog or alert handler</td>
    </tr>
    <tr id="rv_core_ibexcpuisa">
      <td>RV_CORE_IBEX.CPU.ISA</td>
      <td>Implements a RISC-V core capable of executing RV32ICMB instructions (a subset of bitmanip isimplemented, see the Ibex core documentation for details).</td>
    </tr>
    <tr id="rv_core_ibexcpumemory">
      <td>RV_CORE_IBEX.CPU.MEMORY</td>
      <td>The RISC-V core can send transactions on the TL-UL interconnect and access all of theaddress space that is available</td>
    </tr>
    <tr id="rv_core_ibexcrash_dump">
      <td>RV_CORE_IBEX.CRASH_DUMP</td>
      <td>The core wrapper provides a 'crash dump' to rstmgr providing information on what was beingexecuted and most recent exception taken on a reset event. Where the RISC-V core hasdetected a double fault a crash dump will be stored for when the double fault was detect aswell as the crash dump at reset.</td>
    </tr>
    <tr id="rv_core_ibexrnd">
      <td>RV_CORE_IBEX.RND</td>
      <td>The core wrapper has a connection to the EDN that provides 32-bit random numbers via amemory mapped register.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>RV_CORE_IBEX.CPU.ISA</th>
    <th>RV_CORE_IBEX.CPU.EPMP</th>
    <th>RV_CORE_IBEX.CPU.ICACHE</th>
    <th>RV_CORE_IBEX.CPU.MEMORY</th>
    <th>RV_CORE_IBEX.CPU.INTERRUPTS</th>
    <th>RV_CORE_IBEX.RND</th>
    <th>RV_CORE_IBEX.ADDRESS_TRANSLATION</th>
    <th>RV_CORE_IBEX.CRASH_DUMP</th>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#theory-of-operation">Theory of Operation</a></th>
    <td><a href="../theory_of_operation.md#theory-of-operation">X</a></td>
    <td><a href="../theory_of_operation.md#theory-of-operation">X</a></td>
    <td></td>
    <td><a href="../theory_of_operation.md#theory-of-operation">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#simple-address-translation">Simple Address Translation</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#simple-address-translation">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#translation-and-instruction-caching">Translation and Instruction Caching</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#translation-and-instruction-caching">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#random-number-generation">Random Number Generation</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#random-number-generation">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#interrupts">Interrupts</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#interrupts">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#crash-dump-collection">Crash Dump Collection</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#crash-dump-collection">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#hung-transaction">Hung Transaction</a></th>
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
    <th><a href="../theory_of_operation.md#double-exception">Double Exception</a></th>
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
    <th><a href="../theory_of_operation.md#fetch-enable">Fetch Enable</a></th>
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
    <th><a href="../theory_of_operation.md#local-escalation-path">Local Escalation Path</a></th>
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
    <th>RV_CORE_IBEX.CPU.ISA</th>
    <th>RV_CORE_IBEX.CPU.EPMP</th>
    <th>RV_CORE_IBEX.CPU.ICACHE</th>
    <th>RV_CORE_IBEX.CPU.MEMORY</th>
    <th>RV_CORE_IBEX.CPU.INTERRUPTS</th>
    <th>RV_CORE_IBEX.RND</th>
    <th>RV_CORE_IBEX.ADDRESS_TRANSLATION</th>
    <th>RV_CORE_IBEX.CRASH_DUMP</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#riscv_arithmetic_basic_test">riscv_arithmetic_basic_test</a></th>
    <td><a href="02_testpoint_report.md#riscv_arithmetic_basic_test">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#riscv_arithmetic_basic_test">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#riscv_rand_instr_test">riscv_rand_instr_test</a></th>
    <td><a href="02_testpoint_report.md#riscv_rand_instr_test">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#riscv_rand_instr_test">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#riscv_machine_mode_rand_test">riscv_machine_mode_rand_test</a></th>
    <td><a href="02_testpoint_report.md#riscv_machine_mode_rand_test">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#riscv_rand_jump_test">riscv_rand_jump_test</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#riscv_rand_jump_test">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#riscv_jump_stress_test">riscv_jump_stress_test</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#riscv_jump_stress_test">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#riscv_loop_test">riscv_loop_test</a></th>
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
    <th><a href="02_testpoint_report.md#riscv_mmu_stress_test">riscv_mmu_stress_test</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#riscv_mmu_stress_test">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#riscv_unaligned_load_store_test">riscv_unaligned_load_store_test</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#riscv_unaligned_load_store_test">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#riscv_mem_error_test">riscv_mem_error_test</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#riscv_mem_error_test">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#riscv_illegal_instr_test">riscv_illegal_instr_test</a></th>
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
    <th><a href="02_testpoint_report.md#riscv_hint_instr_test">riscv_hint_instr_test</a></th>
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
    <th><a href="02_testpoint_report.md#riscv_ebreak_test">riscv_ebreak_test</a></th>
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
    <th><a href="02_testpoint_report.md#riscv_debug_basic_test">riscv_debug_basic_test</a></th>
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
    <th><a href="02_testpoint_report.md#riscv_debug_stress_test">riscv_debug_stress_test</a></th>
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
    <th><a href="02_testpoint_report.md#riscv_debug_branch_jump_test">riscv_debug_branch_jump_test</a></th>
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
    <th><a href="02_testpoint_report.md#riscv_debug_interrupt_test">riscv_debug_interrupt_test</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#riscv_debug_interrupt_test">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#riscv_debug_illegal_instr_test">riscv_debug_illegal_instr_test</a></th>
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
    <th><a href="02_testpoint_report.md#riscv_debug_wfi_test">riscv_debug_wfi_test</a></th>
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
    <th><a href="02_testpoint_report.md#riscv_dret_test">riscv_dret_test</a></th>
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
    <th><a href="02_testpoint_report.md#riscv_debug_ebreak_test">riscv_debug_ebreak_test</a></th>
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
    <th><a href="02_testpoint_report.md#riscv_debug_ebreakmu_test">riscv_debug_ebreakmu_test</a></th>
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
    <th><a href="02_testpoint_report.md#riscv_debug_single_step_test">riscv_debug_single_step_test</a></th>
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
    <th><a href="02_testpoint_report.md#riscv_debug_csr_entry_test">riscv_debug_csr_entry_test</a></th>
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
    <th><a href="02_testpoint_report.md#riscv_irq_in_debug_mode_test">riscv_irq_in_debug_mode_test</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#riscv_irq_in_debug_mode_test">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#riscv_single_interrupt_test">riscv_single_interrupt_test</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#riscv_single_interrupt_test">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#riscv_multiple_interrupt_test">riscv_multiple_interrupt_test</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#riscv_multiple_interrupt_test">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#riscv_interrupt_wfi_test">riscv_interrupt_wfi_test</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#riscv_interrupt_wfi_test">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#riscv_interrupt_csr_test">riscv_interrupt_csr_test</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#riscv_interrupt_csr_test">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#riscv_interrupt_nested_test">riscv_interrupt_nested_test</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#riscv_interrupt_nested_test">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#riscv_csr_test">riscv_csr_test</a></th>
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
    <th><a href="02_testpoint_report.md#riscv_reset_test">riscv_reset_test</a></th>
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
    <th><a href="02_testpoint_report.md#riscv_perf_counter_test">riscv_perf_counter_test</a></th>
    <td><a href="02_testpoint_report.md#riscv_perf_counter_test">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#riscv_rv32im_instr_test">riscv_rv32im_instr_test</a></th>
    <td><a href="02_testpoint_report.md#riscv_rv32im_instr_test">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#riscv_user_mode_rand_test">riscv_user_mode_rand_test</a></th>
    <td><a href="02_testpoint_report.md#riscv_user_mode_rand_test">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#riscv_umode_tw_test">riscv_umode_tw_test</a></th>
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
    <th><a href="02_testpoint_report.md#riscv_invalid_csr_test">riscv_invalid_csr_test</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_nmi_irq-dragonfly">chip_sw_nmi_irq (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_nmi_irq-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rv_core_ibex_rnd-dragonfly">chip_sw_rv_core_ibex_rnd (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rv_core_ibex_rnd-dragonfly">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rv_core_ibex_address_translation-dragonfly">chip_sw_rv_core_ibex_address_translation (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rv_core_ibex_address_translation-dragonfly">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rv_core_ibex_icache_scrambled_access-dragonfly">chip_sw_rv_core_ibex_icache_scrambled_access (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rv_core_ibex_icache_scrambled_access-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rv_core_ibex_fault_dump-dragonfly">chip_sw_rv_core_ibex_fault_dump (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rv_core_ibex_fault_dump-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rv_core_ibex_double_fault-dragonfly">chip_sw_rv_core_ibex_double_fault (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rv_core_ibex_double_fault-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rv_core_ibex_smoke-dragonfly">chip_sw_rv_core_ibex_smoke (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_rv_core_ibex_smoke-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rv_core_ibex_epmp_smoke-dragonfly">chip_sw_rv_core_ibex_epmp_smoke (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rv_core_ibex_epmp_smoke-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rv_core_ibex_mem_smoke-dragonfly">chip_sw_rv_core_ibex_mem_smoke (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rv_core_ibex_mem_smoke-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_rv_core_ibex_mem_smoke-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rv_core_ibex_lockstep_glitch-dragonfly">chip_sw_rv_core_ibex_lockstep_glitch (dragonfly)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_rv_core_ibex_alerts-dragonfly">chip_sw_rv_core_ibex_alerts (dragonfly)</a></th>
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
