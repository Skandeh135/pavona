# rv_core_ibex Testpoint Report

## chip_sw_nmi_irq (dragonfly)
Verify the NMI interrupt to the CPU and correctness of the cause.

Randomly use these two methods (simultaneously or choose one of them) to trigger the
NMI interrupt:

- Trigger the alert_handler escalation pair that maps to NMI.
- Trigger a watchdog bark.

Check rv_core_ibex's NMI interrupt register and clear the interrupt.
If the NMI interrupt is triggered by alert_handle and the `class_clr_regwen` register
is not locked, check that alert_handler can clear this NMI escalation stage. Then make
sure that the alert_handler won't move forward to the next escalation stage.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rv_core_ibex_nmi_irq-dragonfly">chip_sw_rv_core_ibex_nmi_irq (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcpuinterrupts">RV_CORE_IBEX.CPU.INTERRUPTS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rv_core_ibex_address_translation (dragonfly)
Verify the simple address translation functionality.

- Setup address translation for both slots on the I and D
  side and check correct translation for I and D accesses.
- Switch address translation to use different regions that
  overlap for both slots and check translation again. Ensure some
  test accesses match both regions, where the lowest indexed one
  takes priority.
- Turn off address translation and confirm regions are no longer
  being remapped.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rv_core_ibex_address_translation-dragonfly">chip_sw_rv_core_ibex_address_translation (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexaddress_translation">RV_CORE_IBEX.ADDRESS_TRANSLATION</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rv_core_ibex_alerts (dragonfly)
Inject and verify all available faults in rv_core_ibex / ibex_top.

Inject faults in the following areas and verify the alert is fired leading to an
escalation.

- Bus integrity error on the data and instruction TL interface (on the response channel)
- PC mismatch fault
- ECC error in the register file


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

## chip_sw_rv_core_ibex_double_fault (dragonfly)
Verify the functionality of the ibex double fault dump.

- Purposely create an ibex double exception during execution, by performing an
  unmapped read and in the exception handler perform another unmapped read.
- Ensure the rstmgr fault dump correctly captures both dumps correctly and indicates
  the previous dump is valid.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rstmgr_cpu_info-dragonfly">chip_sw_rstmgr_cpu_info (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcrash_dump">RV_CORE_IBEX.CRASH_DUMP</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rv_core_ibex_epmp_smoke (dragonfly)
Setup and test a few epmp regions

Check a range of ePMP access modes, ensure these include:

  - Shared execute, read and write
  - U-mode only execute, read and write
  - M-mode only execute, read and write

Also trial usage of the MML, MMWP and RLB bits in mseccfg.

Note that to fully implement this test it will need to injected into SRAM via JTAG
and run before the boot ROM executes in DEV/TEST_UNLOCKED, however a more limited
version can run in all lifecycle states using the standard load/execute mechanism
for all tests.


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
  <td><a href="01_feature_report.md#rv_core_ibexcpuepmp">RV_CORE_IBEX.CPU.EPMP</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rv_core_ibex_fault_dump (dragonfly)
Verify the functionality of the ibex fault dump.

- Purposely create an ibex exception during execution through reads to an ummapped
  address.
- Ensure the rstmgr fault dump correctly captures the related addresses to the
  exception.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rstmgr_cpu_info-dragonfly">chip_sw_rstmgr_cpu_info (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcrash_dump">RV_CORE_IBEX.CRASH_DUMP</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rv_core_ibex_icache_scrambled_access (dragonfly)
Verify scrambled memory accesses to CPU icache.

- Initialize the entropy_src subsystem to enable OTP_CTRL fetch random data (already
  done by the test_rom startup code).
- Execute the `fence` instruction to invalidate the icache.
- In simulation: verify using probes, that this resulted in a new scrambling key
  fetched from the OTP ctrl.
- In SiVal: loop reading the value of the Ibex CSR cpustrlsts.ic_scr_key_valid until it
  indicates a valid scrambling key, then continue executing some code to demonstrate
  continued functioning of the instruction cache.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rv_core_ibex_icache_invalidate-dragonfly">chip_sw_rv_core_ibex_icache_invalidate (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcpuicache">RV_CORE_IBEX.CPU.ICACHE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rv_core_ibex_lockstep_glitch (dragonfly)
Verify lockstep checking of the Ibex core.

Ensure suitable alerts are triggered when:

- Outputs from the lockstep or the main core are corrupted.
- Inputs into the lockstep core are corrupted.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rv_core_ibex_lockstep_glitch-dragonfly">chip_sw_rv_core_ibex_lockstep_glitch (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_rv_core_ibex_mem_smoke (dragonfly)
Check access to each kind of memory from Ibex

Read a known value from each of the following and check it
matches the expected value:

- ROM
- Flash

Write values to each of the following and then read it back to
ensure it's as expected:

- SRAM
- A device register (choose one that can have at least an 8-bit value written to and
  you can expect to read it back un-changed). Preferably cover multiple devices

Execute code from each of the following:

- ROM
- Flash
- SRAM

First with the ICache disabled and then with the ICache enabled.  (Note that SRAM
execution may be unavailable in some lifecycle states).


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
  <td><a href="01_feature_report.md#rv_core_ibexcpuicache">RV_CORE_IBEX.CPU.ICACHE</a><br><a href="01_feature_report.md#rv_core_ibexcpumemory">RV_CORE_IBEX.CPU.MEMORY</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rv_core_ibex_rnd (dragonfly)
Verify the functionality of the random number generation CSRs.

- Enable entropy complex so `RND_DATA` can get entropy.
- Perform multiple reads from `RND_DATA` polling `RND_STATUS` in
  between to only read valid data. Check different random bits
  are provided each time and that the random data is never zero or all ones.
- Ensure `RND_STATUS` indicate invalid data immediately after
  `RND_DATA` read.
- Perform repeated reads from `RND_DATA` without `RND_STATUS`
  polling to check read when invalid doesn't block.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rv_core_ibex_rnd-dragonfly">chip_sw_rv_core_ibex_rnd (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexrnd">RV_CORE_IBEX.RND</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rv_core_ibex_smoke (dragonfly)
Execute each instruction implemented by Ibex at least once. Then check the register
state against expected values.

The core of this test will be written in assembler and at least partially
auto-generated. It should be constructed such that a failure of any of the
instructions should (but is not guaranteed) to have some impact on the final
register state


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
  <td><a href="01_feature_report.md#rv_core_ibexcpuisa">RV_CORE_IBEX.CPU.ISA</a></td>
</tr>
  </tbody>
</table>

## riscv_arithmetic_basic_test

Sanity test for basic RV32I instructions

  - Generate instruction binary and load to memory model
  - Only arithmetic instructions are generated
  - Assert fetch enable to start the core execution
  - Terminate the test after ecall instructinon in detected
  - All instruction results are compared against spike simulation


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_arithmetic_basic_test">riscv_arithmetic_basic_test</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcpuisa">RV_CORE_IBEX.CPU.ISA</a><br><a href="01_feature_report.md#rv_core_ibexcpumemory">RV_CORE_IBEX.CPU.MEMORY</a></td>
</tr>
  </tbody>
</table>

## riscv_csr_test

Perform all CSR instructions to implemented privileged CSR
Verify the reset value of the privileged CSR
Verify WARL field can be upated properly


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_csr_test">riscv_csr_test</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## riscv_debug_basic_test

Randomly assert debug_req_i signal

  - in debug_rom, insert normal random instruction sequence
    excluding control transfer instructions
  - verify wfi instructions act as NOPs
  - ensure normal execution finishes successfully


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_debug_basic_test">riscv_debug_basic_test</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## riscv_debug_branch_jump_test

Randomly assert debug_req_i signal

  - in debug_rom, insert random instruction sequence,
    including control transfer instructions and multiple subprograms to
    jump between


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_debug_branch_jump_test">riscv_debug_branch_jump_test</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## riscv_debug_csr_entry_test

Inject debug stimulus during CSR modification operations,
core should jump to debug mode and return without any issues


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_debug_csr_entry_test">riscv_debug_csr_entry_test</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## riscv_debug_ebreak_test


- insert ebreak instructions in M mode code, should be handled normally
- assert debug request
- in debug mode, insert ebreak instruction, verify that ibex re-enter debug mode


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_debug_ebreak_test">riscv_debug_ebreak_test</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## riscv_debug_ebreakmu_test


- set dcsr.ebreakm/u at begining of test
- randomly insert ebreak instructions in generated code
- boot randomly into either M/U modes
- verify that ebreak instructions (in either mode) now enter debug mode


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_debug_ebreakmu_test">riscv_debug_ebreakmu_test</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## riscv_debug_illegal_instr_test


- insert illegal instruction into debug rom to trigger internal exception
- verify that no registers have been updated
- verify that execution of debug rom ends


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_debug_illegal_instr_test">riscv_debug_illegal_instr_test</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## riscv_debug_interrupt_test

Randomly assert debug_req_i signal

  - in debug_rom, insert random instruction sequence
  - randomly toggle interrupts during debug code
  - verify that execution of debug_rom continues as normal, interrupts are
    ignored


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_debug_interrupt_test">riscv_debug_interrupt_test</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcpuinterrupts">RV_CORE_IBEX.CPU.INTERRUPTS</a></td>
</tr>
  </tbody>
</table>

## riscv_debug_single_step_test

Randomly assert debug_req_i signal to force core into debug mode.

  - in debug_rom, set dcsr.step
  - after exiting debug mode, core will execute one instruction and re-enter
    debug mode


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_debug_single_step_test">riscv_debug_single_step_test</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## riscv_debug_stress_test

Randomly assert debug_req signal

  - debug rom will consist of just a dret instructions, so any switches into
    debug mode will immediately return
  - will use this jointly with full instruction checking with spike


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_debug_stress_test">riscv_debug_stress_test</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## riscv_debug_wfi_test

Insert random generation of wfi instructions

  - while core is in wfi sleep state, assert debug request
  - verify core jumps to debug mode
  - debug rom consists of random generation instructions


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_debug_wfi_test">riscv_debug_wfi_test</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## riscv_dret_test

Randomly insert dret instructions into M mode instructions

  - verify that ibex treats them as illegal instructions


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_dret_test">riscv_dret_test</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## riscv_ebreak_test

Generate random instructions including ebreak, expect core to raise ebreak exception


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_ebreak_test">riscv_ebreak_test</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## riscv_hint_instr_test

Randomly inject HINT instructions as specified in RISC-V user mode specification 5.4
Verify the core execute it as NOP and no exception is raised


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_hint_instr_test">riscv_hint_instr_test</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## riscv_illegal_instr_test

Randomly inject below illegal instructions in the instruction stream

  - Instructions which not belong to RV32IMC
  - Reserved instructions as specified in RISC-V user mode spec
  - CSR instruction to not implemented CSR
  - Execute S/U mode instructions in machine mode

Verify the illlegal instruction exception is raised and the context is captured correctly in privieged mode CSRs

  - mstatus, mcause, mepc

Verify the core can resume execution after returning from trap handling


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_illegal_instr_test">riscv_illegal_instr_test</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## riscv_interrupt_csr_test

Randomly assert interrupt lines during CSR modification operations,
core should jump to proper handler


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_interrupt_csr_test">riscv_interrupt_csr_test</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcpuinterrupts">RV_CORE_IBEX.CPU.INTERRUPTS</a></td>
</tr>
  </tbody>
</table>

## riscv_interrupt_nested_test


- randomly assert interrupt lines during program execution
- verify that jumps to interrupt handler
- trigger another interrupt during first intr_handler execution
- verify that core takes this nested interrupt and handles it, then restores previous interrupt
  state and finishes executing first interrupt handler - ibex implements nonstandard MSTACK csrs to
  save/restore state in case of nested interrupt


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_interrupt_nested_test">riscv_interrupt_nested_test</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcpuinterrupts">RV_CORE_IBEX.CPU.INTERRUPTS</a></td>
</tr>
  </tbody>
</table>

## riscv_interrupt_wfi_test

Randomly assert interrupt lines while the core is sleeping due to a WFI instruction


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_interrupt_wfi_test">riscv_interrupt_wfi_test</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcpuinterrupts">RV_CORE_IBEX.CPU.INTERRUPTS</a></td>
</tr>
  </tbody>
</table>

## riscv_invalid_csr_test

Boot core into a random privilege mode and generate accesses to higher level CSRs,
expect to throw an illegal instruction exception for each of these accesses.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_invalid_csr_test">riscv_invalid_csr_test</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## riscv_irq_in_debug_mode_test

Randomly assert interrupt lines while the core is in debug mode execution,
verify that these interrupts are all completely ignored


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_irq_in_debug_mode_test">riscv_irq_in_debug_mode_test</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcpuinterrupts">RV_CORE_IBEX.CPU.INTERRUPTS</a></td>
</tr>
  </tbody>
</table>

## riscv_jump_stress_test

Stresses I-Fetch operation:

  - Generates sequences of many back-to-back jump instructions


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_jump_stress_test">riscv_jump_stress_test</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcpuicache">RV_CORE_IBEX.CPU.ICACHE</a></td>
</tr>
  </tbody>
</table>

## riscv_loop_test

Generate directed sequences of loops to test branch operations


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_loop_test">riscv_loop_test</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## riscv_machine_mode_rand_test

Fully randomized RV32IMC instructions

  - boot into Machine Mode


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_machine_mode_rand_test">riscv_machine_mode_rand_test</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcpuisa">RV_CORE_IBEX.CPU.ISA</a></td>
</tr>
  </tbody>
</table>

## riscv_mem_error_test

Randomly assert error bit for instruction fetch and load/store.
Expect the core to raise memory access fault exception
Verify the fault load instruction won't modify GPR
Verify the context of the exception is captured correctly in privileged CSRs

  - mstatus, mcause, mepc


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_mem_error_test">riscv_mem_error_test</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcpumemory">RV_CORE_IBEX.CPU.MEMORY</a></td>
</tr>
  </tbody>
</table>

## riscv_mmu_stress_test

Create various load/store patterns to stress LSU

  - load/store from random addresses
  - load/store from dense or sparse locations
  - back-to-back load/store instructions
  - cover all byte/half-word/word load/store instructions
  - load/store with hazard conditions


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_mmu_stress_test">riscv_mmu_stress_test</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcpumemory">RV_CORE_IBEX.CPU.MEMORY</a></td>
</tr>
  </tbody>
</table>

## riscv_multiple_interrupt_test

Randomly assert multiple interrupt lines during program execution,
core should jump to handler of highest priority interrupt


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_multiple_interrupt_test">riscv_multiple_interrupt_test</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcpuinterrupts">RV_CORE_IBEX.CPU.INTERRUPTS</a></td>
</tr>
  </tbody>
</table>

## riscv_perf_counter_test

Run random instruction test, and dump performance counters for checking


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_perf_counter_test">riscv_perf_counter_test</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcpuisa">RV_CORE_IBEX.CPU.ISA</a></td>
</tr>
  </tbody>
</table>

## riscv_rand_instr_test

Fully randomized RV32IMC instructions

  - Including all types of instructions
  - forward/backward branches
  - directed sequence for various hazard conditions
  - mixed load/store instructions
  - random jump instructions
  - fence instructions (treated as nop)
  - mret instruction
  - corner cases for each instruction (overflow, underflow, div by zero etc.)


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_rand_instr_test">riscv_rand_instr_test</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcpuisa">RV_CORE_IBEX.CPU.ISA</a><br><a href="01_feature_report.md#rv_core_ibexcpumemory">RV_CORE_IBEX.CPU.MEMORY</a></td>
</tr>
  </tbody>
</table>

## riscv_rand_jump_test

Stresses I-Fetch operation:

  - Generates a large number of subprograms and frequently jumps between them


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_rand_jump_test">riscv_rand_jump_test</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcpuicache">RV_CORE_IBEX.CPU.ICACHE</a></td>
</tr>
  </tbody>
</table>

## riscv_reset_test

Reset the core a random number of times during program execution, core
should jump back to start address and re-enter the program.
Ensure to flush all testbench state to prevent contamination after reset.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_reset_test">riscv_reset_test</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## riscv_rv32im_instr_test

Specify RV32IM architecture to compiler to generate target specific
instructions (no compressed instructions).


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_rv32im_instr_test">riscv_rv32im_instr_test</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcpuisa">RV_CORE_IBEX.CPU.ISA</a></td>
</tr>
  </tbody>
</table>

## riscv_single_interrupt_test

Randomly assert a single interrupt line during program execution, core
should jump to proper handler


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_single_interrupt_test">riscv_single_interrupt_test</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcpuinterrupts">RV_CORE_IBEX.CPU.INTERRUPTS</a></td>
</tr>
  </tbody>
</table>

## riscv_umode_tw_test

Set mstatus.tw, and enable random generation of WFI instructions.
Upon encountering WFI in U-mode, core should trap to M-mode
illegal instruction exception handler.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_umode_tw_test">riscv_umode_tw_test</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## riscv_unaligned_load_store_test

Random mis-aligned half-word/word load/store instruction
Expect the core finishes the load/store properly with no exception raised


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_unaligned_load_store_test">riscv_unaligned_load_store_test</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcpumemory">RV_CORE_IBEX.CPU.MEMORY</a></td>
</tr>
  </tbody>
</table>

## riscv_user_mode_rand_test

Fully randomized RV32IMC instructions, boot in U-mode,
test should finish successfully

  - includes all types of instructions
  - no external debug/irq stimulus, exceptions, security aspects are checked here


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#riscv_user_mode_rand_test">riscv_user_mode_rand_test</a></td>
  <td><a href="01_feature_report.md#rv_core_ibexcpuisa">RV_CORE_IBEX.CPU.ISA</a></td>
</tr>
  </tbody>
</table>
