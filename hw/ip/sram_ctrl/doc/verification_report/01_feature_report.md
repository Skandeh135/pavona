# sram_ctrl Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="sram_ctrlfetch_allow">
      <td>SRAM_CTRL.FETCH_ALLOW</td>
      <td>Access for instruction fetches can be allowed or disallowed.Instruction fetches can be completely disallowed for an instance by a parameter.If possible in this instance, the choice depends on either life-cycle state or a CSR.</td>
    </tr>
    <tr id="sram_ctrlintegrity">
      <td>SRAM_CTRL.INTEGRITY</td>
      <td>Words are stored with integrity bits (7 integrity bits for each 32 data bits).</td>
    </tr>
    <tr id="sram_ctrllock_on_error">
      <td>SRAM_CTRL.LOCK_ON_ERROR</td>
      <td>The block disallows transactions and sends out an alert if it detects an error.This can come from a bus integrity failure or from a message from the lifecycle controller.</td>
    </tr>
    <tr id="sram_ctrlmemset">
      <td>SRAM_CTRL.MEMSET</td>
      <td>The block can initialise the contents of memory with a pseudo-random stream.This avoids leaking the cipher key (which would be possible with a CTR-based cipher).</td>
    </tr>
    <tr id="sram_ctrlreadback">
      <td>SRAM_CTRL.READBACK</td>
      <td>Software can read back SRAM contents after writes for verification.A configuration register can be set to lock this feature.</td>
    </tr>
    <tr id="sram_ctrlregwen">
      <td>SRAM_CTRL.REGWEN</td>
      <td>Configuration can be locked, using a REGWEN CSR.</td>
    </tr>
    <tr id="sram_ctrlscrambled">
      <td>SRAM_CTRL.SCRAMBLED</td>
      <td>Backing memory is scrambled.The scrambling depends on keys configurable by a CSR.</td>
    </tr>
    <tr id="sram_ctrlsubword_access">
      <td>SRAM_CTRL.SUBWORD_ACCESS</td>
      <td>Sub-word reads and writes are supported.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>SRAM_CTRL.INTEGRITY</th>
    <th>SRAM_CTRL.SCRAMBLED</th>
    <th>SRAM_CTRL.LOCK_ON_ERROR</th>
    <th>SRAM_CTRL.MEMSET</th>
    <th>SRAM_CTRL.FETCH_ALLOW</th>
    <th>SRAM_CTRL.SUBWORD_ACCESS</th>
    <th>SRAM_CTRL.REGWEN</th>
    <th>SRAM_CTRL.READBACK</th>
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
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td></td>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td></td>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#scrambling-primitive">Scrambling Primitive</a></th>
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
    <th><a href="../theory_of_operation.md#integrity-error-handling">Integrity Error Handling</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#integrity-error-handling">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#lfsr-initialization-feature">LFSR Initialization Feature</a></th>
    <td><a href="../theory_of_operation.md#lfsr-initialization-feature">X</a></td>
    <td><a href="../theory_of_operation.md#lfsr-initialization-feature">X</a></td>
    <td></td>
    <td><a href="../theory_of_operation.md#lfsr-initialization-feature">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#code-execution-from-sram">Code Execution from SRAM</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#code-execution-from-sram">X</a></td>
    <td></td>
    <td><a href="../theory_of_operation.md#code-execution-from-sram">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#read-and-write-sequencing">Read and Write Sequencing</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#read-and-write-sequencing">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#sram-readback">SRAM Readback</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#sram-readback">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#ecc-error-handling-and-correction">ECC Error Handling and Correction</a></th>
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
    <th><a href="../theory_of_operation.md#important-considerations">Important Considerations</a></th>
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
    <th>SRAM_CTRL.INTEGRITY</th>
    <th>SRAM_CTRL.SCRAMBLED</th>
    <th>SRAM_CTRL.LOCK_ON_ERROR</th>
    <th>SRAM_CTRL.MEMSET</th>
    <th>SRAM_CTRL.FETCH_ALLOW</th>
    <th>SRAM_CTRL.SUBWORD_ACCESS</th>
    <th>SRAM_CTRL.REGWEN</th>
    <th>SRAM_CTRL.READBACK</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#multiple_keys">multiple_keys</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#multiple_keys">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#multiple_keys">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#stress_pipeline">stress_pipeline</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#stress_pipeline">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#stress_pipeline">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#bijection">bijection</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#bijection">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#bijection">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#access_during_key_req">access_during_key_req</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#access_during_key_req">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#access_during_key_req">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#lc_escalation">lc_escalation</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#lc_escalation">X</a></td>
    <td><a href="02_testpoint_report.md#lc_escalation">X</a></td>
    <td><a href="02_testpoint_report.md#lc_escalation">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#executable">executable</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#executable">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#partial_access">partial_access</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#partial_access">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#max_throughput">max_throughput</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#max_throughput">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#regwen">regwen</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#regwen">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#ram_cfg">ram_cfg</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_sram_scrambled_access-dragonfly">chip_sw_sram_scrambled_access (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_sram_scrambled_access-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_sleep_sram_ret_contents-dragonfly">chip_sw_sleep_sram_ret_contents (dragonfly)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_sram_execution-dragonfly">chip_sw_sram_execution (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_sram_execution-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_sram_lc_escalation-dragonfly">chip_sw_sram_lc_escalation (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_sram_lc_escalation-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_sram_memset-dragonfly">chip_sw_sram_memset (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_sram_memset-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_sram_readback-dragonfly">chip_sw_sram_readback (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_sram_readback-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_sram_subword_access-dragonfly">chip_sw_sram_subword_access (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_sram_subword_access-dragonfly">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_sram_scrambled_access-egret">chip_sw_sram_scrambled_access (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_sram_scrambled_access-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_sleep_sram_ret_contents-egret">chip_sw_sleep_sram_ret_contents (egret)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_sram_execution-egret">chip_sw_sram_execution (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_sram_execution-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_sram_lc_escalation-egret">chip_sw_sram_lc_escalation (egret)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_sram_lc_escalation-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_sram_memset-egret">chip_sw_sram_memset (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_sram_memset-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_sram_readback-egret">chip_sw_sram_readback (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_sram_readback-egret">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_sram_subword_access-egret">chip_sw_sram_subword_access (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_sram_subword_access-egret">X</a></td>
    <td></td>
    <td></td>
  </tr>
</table>
</div>
</div>
