# acc Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="accisa">
      <td>ACC.ISA</td>
      <td>ACC implements a custom ISA based on RV32I. It is split into base (32-bit) and bignum(256-bit) parts. There is a separate register file for each.</td>
    </tr>
    <tr id="acckeymgr">
      <td>ACC.KEYMGR</td>
      <td>ACC has a connection to the keymgr and it can receive key material from it.</td>
    </tr>
    <tr id="accmem_scramble">
      <td>ACC.MEM_SCRAMBLE</td>
      <td>ACC scrambles its instruction and data memories using keys received from OTP.</td>
    </tr>
    <tr id="accrandom">
      <td>ACC.RANDOM</td>
      <td>ACC has a connection to the EDN allowing it to receive 256-bits of entropy.</td>
    </tr>
    <tr id="accsecurewipe">
      <td>ACC.SECUREWIPE</td>
      <td>ACC has a secure wipe facility that can target the internal state as well as theinstruction and data memories.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>ACC.ISA</th>
    <th>ACC.RANDOM</th>
    <th>ACC.KEYMGR</th>
    <th>ACC.SECUREWIPE</th>
    <th>ACC.MEM_SCRAMBLE</th>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#theory-of-operation">Theory of Operation</a></th>
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
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#design-details">Design Details</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#configurations">Configurations</a></th>
    <td><a href="../theory_of_operation.md#configurations">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#memories">Memories</a></th>
    <td><a href="../theory_of_operation.md#memories">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#instruction-prefetch">Instruction Prefetch</a></th>
    <td><a href="../theory_of_operation.md#instruction-prefetch">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#random-numbers">Random Numbers</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#random-numbers">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#operational-states">Operational States</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#operations-and-commands">Operations and Commands</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#software-execution">Software Execution</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#errors">Errors</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#reaction-to-recoverable-errors">Reaction to Recoverable Errors</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#reaction-to-fatal-errors">Reaction to Fatal Errors</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#list-of-errors">List of Errors</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#alerts">Alerts</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#reaction-to-life-cycle-escalation-requests">Reaction to Life Cycle Escalation Requests</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#idle">Idle</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#data-integrity-protection">Data Integrity Protection</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#data-integrity-protection">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#integrity-protection-code">Integrity Protection Code</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#integrity-protection-code">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#memory-scrambling">Memory Scrambling</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#memory-scrambling">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#actions-on-integrity-errors">Actions on Integrity Errors</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#register-file-integrity-protection">Register File Integrity Protection</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#data-memory-dmem-integrity-protection">Data Memory (DMEM) Integrity Protection</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#instruction-memory-imem-integrity-protection">Instruction Memory (IMEM) Integrity Protection</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#memory-load-integrity">Memory Load Integrity</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#secure-wipe">Secure Wipe</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#secure-wipe">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#data-memory-dmem-secure-wipe">Data Memory (DMEM) Secure Wipe</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#data-memory-dmem-secure-wipe">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#instruction-memory-imem-secure-wipe">Instruction Memory (IMEM) Secure Wipe</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#instruction-memory-imem-secure-wipe">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#internal-state-secure-wipe">Internal State Secure Wipe</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#internal-state-secure-wipe">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#kmac-application-interface">KMAC Application Interface</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#kmac-application-interface">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#vector-instructions">Vector Instructions</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#references">References</a></th>
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
    <th>ACC.ISA</th>
    <th>ACC.RANDOM</th>
    <th>ACC.KEYMGR</th>
    <th>ACC.SECUREWIPE</th>
    <th>ACC.MEM_SCRAMBLE</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#single_binary">single_binary</a></th>
    <td><a href="02_testpoint_report.md#single_binary">X</a></td>
    <td><a href="02_testpoint_report.md#single_binary">X</a></td>
    <td><a href="02_testpoint_report.md#single_binary">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#single_binary">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#reset_recovery">reset_recovery</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#multi_error">multi_error</a></th>
    <td><a href="02_testpoint_report.md#multi_error">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#mem_integrity">mem_integrity</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#mem_integrity">X</a></td>
    <td><a href="02_testpoint_report.md#mem_integrity">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#internal_integrity">internal_integrity</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#internal_integrity">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#kmac_error">kmac_error</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#kmac_error">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#back_to_back">back_to_back</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#back_to_back">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#stress_all">stress_all</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#lc_escalation">lc_escalation</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#lc_escalation">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#zero_state_err_urnd">zero_state_err_urnd</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#zero_state_err_urnd">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#illegal_bus_access">illegal_bus_access</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#illegal_bus_access">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#sw_errs_fatal_chk">sw_errs_fatal_chk</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#sw_errs_fatal_chk">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#acc_mem_gnt_acc_err">acc_mem_gnt_acc_err</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#acc_mem_gnt_acc_err">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#acc_non_sec_partial_wipe">acc_non_sec_partial_wipe</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#acc_non_sec_partial_wipe">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_acc_isa-dragonfly">chip_sw_acc_isa (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_acc_isa-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_acc_isa-dragonfly">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_acc_op-dragonfly">chip_sw_acc_op (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_acc_op-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_acc_rnd_entropy-dragonfly">chip_sw_acc_rnd_entropy (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_acc_rnd_entropy-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_acc_urnd_entropy-dragonfly">chip_sw_acc_urnd_entropy (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_acc_urnd_entropy-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_acc_idle-dragonfly">chip_sw_acc_idle (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_acc_mem_scramble-dragonfly">chip_sw_acc_mem_scramble (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_acc_mem_scramble-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_acc_mem_scramble-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_acc_keymgr-dragonfly">chip_sw_acc_keymgr (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_acc_keymgr-dragonfly">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_acc_isa-egret">chip_sw_acc_isa (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_acc_isa-egret">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_acc_isa-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_acc_op-egret">chip_sw_acc_op (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_acc_op-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_acc_rnd_entropy-egret">chip_sw_acc_rnd_entropy (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_acc_rnd_entropy-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_acc_urnd_entropy-egret">chip_sw_acc_urnd_entropy (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_acc_urnd_entropy-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_acc_idle-egret">chip_sw_acc_idle (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_acc_mem_scramble-egret">chip_sw_acc_mem_scramble (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_acc_mem_scramble-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_acc_mem_scramble-egret">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_acc_keymgr-egret">chip_sw_acc_keymgr (egret)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_acc_keymgr-egret">X</a></td>
    <td></td>
    <td></td>
  </tr>
</table>
</div>
</div>
