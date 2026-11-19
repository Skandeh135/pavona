# mbx Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="mbxabort">
      <td>MBX.ABORT</td>
      <td>The outbound side can abort a mailbox transaction.</td>
    </tr>
    <tr id="mbxaddress_range">
      <td>MBX.ADDRESS_RANGE</td>
      <td>When valid inbound and outbound address ranges are defined,the inbound side can declare them valid and optionally lockthese ranges from subsequent modification.</td>
    </tr>
    <tr id="mbxinbound">
      <td>MBX.INBOUND</td>
      <td>Mailbox can receive inbound messages.</td>
    </tr>
    <tr id="mbxoutbound">
      <td>MBX.OUTBOUND</td>
      <td>Mailbox can transmit outbound messages.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>MBX.INBOUND</th>
    <th>MBX.OUTBOUND</th>
    <th>MBX.ADDRESS_RANGE</th>
    <th>MBX.ABORT</th>
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
    <th><a href="../theory_of_operation.md#secure-mailbox-interface">Secure Mailbox Interface</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#mailbox-terminology">Mailbox Terminology</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#mailbox-memory-topology">Mailbox Memory Topology</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#shared-mailbox-memory-on-rot-fabric">**Shared Mailbox Memory On RoT Fabric**</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#shared-mailbox-memory-carved-out-of-existing-rot-memory">**Shared Mailbox Memory (carved out of existing RoT memory)**</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#mailbox-basics">Mailbox Basics</a></th>
    <td><a href="../theory_of_operation.md#mailbox-basics">X</a></td>
    <td><a href="../theory_of_operation.md#mailbox-basics">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#address-ranges">Address Ranges</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#address-ranges">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#integrated-root-of-trust-usage-of-doe-mailbox-mechanism">Integrated Root-of-Trust Usage Of DOE Mailbox Mechanism</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#mailbox-use-cases">Mailbox Use Cases</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#interprocessor-communication">Interprocessor Communication</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#system-level-use-cases">System level use cases</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#pcie-component-measurement">PCIe component measurement</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#setup-of-trusted-execution-environments">Setup of Trusted Execution Environments</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#generic-security-services">Generic security services</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#data-object-definition">Data Object Definition</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#pcie-defined">PCIe defined</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#doe-mapping">DOE mapping</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#external-doe-registers">External DOE Registers</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#doe-extended-capability-header">DOE Extended Capability Header</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#doe-capability-header">DOE Capability Header</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#glossary">Glossary</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#appendix">Appendix</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#appendix">X</a></td>
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
    <th>MBX.INBOUND</th>
    <th>MBX.OUTBOUND</th>
    <th>MBX.ADDRESS_RANGE</th>
    <th>MBX.ABORT</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#mbx_smoke">mbx_smoke</a></th>
    <td><a href="02_testpoint_report.md#mbx_smoke">X</a></td>
    <td><a href="02_testpoint_report.md#mbx_smoke">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#mbx_stress">mbx_stress</a></th>
    <td><a href="02_testpoint_report.md#mbx_stress">X</a></td>
    <td><a href="02_testpoint_report.md#mbx_stress">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#mbx_stress">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#mbx_max_activity">mbx_max_activity</a></th>
    <td><a href="02_testpoint_report.md#mbx_max_activity">X</a></td>
    <td><a href="02_testpoint_report.md#mbx_max_activity">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#mbx_max_activity">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#mbx_stress_all">mbx_stress_all</a></th>
    <td><a href="02_testpoint_report.md#mbx_stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#mbx_stress_all">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#mbx_stress_all">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#mbx_imbx_oob">mbx_imbx_oob</a></th>
    <td><a href="02_testpoint_report.md#mbx_imbx_oob">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#mbx_imbx_oob">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#mbx_range_lock">mbx_range_lock</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#mbx_range_lock">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#mbx_doe_intr_msg">mbx_doe_intr_msg</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_mbx_smoke-dragonfly">chip_sw_mbx_smoke (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_mbx_smoke-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_mbx_smoke-dragonfly">X</a></td>
    <td></td>
    <td></td>
  </tr>
</table>
</div>
</div>
