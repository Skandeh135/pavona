# racl_ctrl Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="raclerror_arbitration">
      <td>RACL.ERROR_ARBITRATION</td>
      <td>RACL control can handle multiple register access errors that arrive simultaneously.</td>
    </tr>
    <tr id="raclerror_log">
      <td>RACL.ERROR_LOG</td>
      <td>RACL control can deny access to a register from a processing element and log the attempt.</td>
    </tr>
    <tr id="raclext_use">
      <td>RACL.EXT_USE</td>
      <td>RACL control provides additional input to collect error logs from externally subscribing IPs.</td>
    </tr>
    <tr id="raclpolicy_enforcement">
      <td>RACL.POLICY_ENFORCEMENT</td>
      <td>Subscribing IPs can bind registers to RACL policies.Read/write permissions for roles (defined in RACL controller configuration file) dictate the access to registers.</td>
    </tr>
    <tr id="raclrot_policy">
      <td>RACL.ROT_POLICY</td>
      <td>RACL control offers exactly one special ROT policy such that only requesters in the ROT role may modify the policy bitmaps themselves.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>RACL.POLICY_ENFORCEMENT</th>
    <th>RACL.ROT_POLICY</th>
    <th>RACL.ERROR_LOG</th>
    <th>RACL.EXT_USE</th>
    <th>RACL.ERROR_ARBITRATION</th>
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
    <th><a href="../theory_of_operation.md#introduction">Introduction</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#racl-controller">RACL Controller</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#racl-policies">RACL Policies</a></th>
    <td><a href="../theory_of_operation.md#racl-policies">X</a></td>
    <td><a href="../theory_of_operation.md#racl-policies">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#distribution-of-policies">Distribution of policies</a></th>
    <td><a href="../theory_of_operation.md#distribution-of-policies">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#error-logs">Error logs</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#error-logs">X</a></td>
    <td><a href="../theory_of_operation.md#error-logs">X</a></td>
    <td><a href="../theory_of_operation.md#error-logs">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#alerts-and-security">Alerts and security</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#out-of-tree-usage">Out of Tree Usage</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#out-of-tree-usage">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#rtl-implementation">RTL Implementation</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#rtl-implementation">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#system-with-no-racl-use">System with No RACL Use</a></th>
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
    <th>RACL.POLICY_ENFORCEMENT</th>
    <th>RACL.ROT_POLICY</th>
    <th>RACL.ERROR_LOG</th>
    <th>RACL.EXT_USE</th>
    <th>RACL.ERROR_ARBITRATION</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#rot_private">rot_private</a></th>
    <td><a href="02_testpoint_report.md#rot_private">X</a></td>
    <td><a href="02_testpoint_report.md#rot_private">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#error_log">error_log</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#error_log">X</a></td>
    <td><a href="02_testpoint_report.md#error_log">X</a></td>
    <td><a href="02_testpoint_report.md#error_log">X</a></td>
  </tr>
</table>
</div>
</div>
