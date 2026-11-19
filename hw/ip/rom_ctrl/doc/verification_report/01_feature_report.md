# rom_ctrl Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="rom_ctrldigests">
      <td>ROM_CTRL.DIGESTS</td>
      <td>A signature of the ROM contents is computed at startup.This is available in the DIGEST_<i> CSRs.</td>
    </tr>
    <tr id="rom_ctrlexp_digests">
      <td>ROM_CTRL.EXP_DIGESTS</td>
      <td>The chip has an expected ROM signature.This is available in the EXP_DIGEST_<i> CSRs.</td>
    </tr>
    <tr id="rom_ctrlfi_hardening">
      <td>ROM_CTRL.FI_HARDENING</td>
      <td>Fault injection targeting the control path is contained rather than allowed to propagateinto the rest of the system.Internal FSMs are sparsely encoded, the mux select and the "good" signal to the powermanager are multi-bit encoded, the mux is prevented from switching back to the checkeronce the bus has been given access, and the main FSM checks that other blocks do notsignal completion from states which do not expect it.Detecting any of these conditions raises a fatal alert.</td>
    </tr>
    <tr id="rom_ctrlscrambled">
      <td>ROM_CTRL.SCRAMBLED</td>
      <td>ROM data is scrambled.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>ROM_CTRL.SCRAMBLED</th>
    <th>ROM_CTRL.DIGESTS</th>
    <th>ROM_CTRL.EXP_DIGESTS</th>
    <th>ROM_CTRL.FI_HARDENING</th>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#theory-of-operation">Theory of Operation</a></th>
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
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#rom-access-when-chip-is-in-operation">ROM access when chip is in operation</a></th>
    <td><a href="../theory_of_operation.md#rom-access-when-chip-is-in-operation">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#the-startup-rom-check">The startup ROM check</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#the-startup-rom-check">X</a></td>
    <td><a href="../theory_of_operation.md#the-startup-rom-check">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#what-does-the-rom-check-do">What does the ROM check do?</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#what-does-the-rom-check-do">X</a></td>
    <td><a href="../theory_of_operation.md#what-does-the-rom-check-do">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#fault-injection-hardening">Fault-injection hardening</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#fault-injection-hardening">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#hardware-interfaces">Hardware Interfaces</a></th>
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
    <th>ROM_CTRL.SCRAMBLED</th>
    <th>ROM_CTRL.DIGESTS</th>
    <th>ROM_CTRL.EXP_DIGESTS</th>
    <th>ROM_CTRL.FI_HARDENING</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#corrupt_sig_fatal_chk">corrupt_sig_fatal_chk</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#corrupt_sig_fatal_chk">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#max_throughput_chk">max_throughput_chk</a></th>
    <td><a href="02_testpoint_report.md#max_throughput_chk">X</a></td>
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
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#kmac_err_chk">kmac_err_chk</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#kmac_err_chk">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rom_access-dragonfly">chip_sw_rom_access (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_rom_access-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rom_ctrl_integrity_check-dragonfly">chip_sw_rom_ctrl_integrity_check (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rom_ctrl_integrity_check-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_rom_ctrl_integrity_check-dragonfly">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rom_ctrl_kmac_error-dragonfly">chip_sw_rom_ctrl_kmac_error (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rom_ctrl_kmac_error-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rom_ctrl_kmac_error-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rom_access-egret">chip_sw_rom_access (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_rom_access-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rom_ctrl_integrity_check-egret">chip_sw_rom_ctrl_integrity_check (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rom_ctrl_integrity_check-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_rom_ctrl_integrity_check-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rom_ctrl_kmac_error-egret">chip_sw_rom_ctrl_kmac_error (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rom_ctrl_kmac_error-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rom_ctrl_kmac_error-egret">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rom_ctrl_digests-egret">chip_sw_rom_ctrl_digests (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rom_ctrl_digests-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_rom_ctrl_digests-egret">X</a></td>
    <td></td>
  </tr>
</table>
</div>
</div>
