# ast Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="astclocks">
      <td>AST.CLOCKS</td>
      <td>AST provides clocks to the digital toplevel.</td>
    </tr>
    <tr id="astentropy">
      <td>AST.ENTROPY</td>
      <td>AST provides entropy to the digital toplevel.</td>
    </tr>
    <tr id="astpower">
      <td>AST.POWER</td>
      <td>AST provides power supplies to the digital toplevel.</td>
    </tr>
    <tr id="astregister_interface">
      <td>AST.REGISTER_INTERFACE</td>
      <td>AST provides a register-based interface for test and calibration.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>AST.CLOCKS</th>
    <th>AST.POWER</th>
    <th>AST.ENTROPY</th>
    <th>AST.REGISTER_INTERFACE</th>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#theory-of-operation">Theory of Operation</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#interface-signals-table">Interface Signals Table</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#table-notes">Table notes</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#signal-naming-conventions-used-in-this-document">Signal naming conventions used in this document</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#clock-domains-column">Clock domains column</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#interfaces-description-note">Interfaces Description Note</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#power-connectivity">Power Connectivity</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#external-supplies">External Supplies</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#core-supplies">Core Supplies</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#power-control-and-reset">Power Control and Reset</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#power-control-and-reset">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#core-power-control-and-indication">Core Power Control and Indication</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#core-power-control-and-indication">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#io-power-indication">IO Power Indication</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#io-power-indication">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#main-vcc-power-detection-and-flash-protection">Main (VCC) Power Detection and Flash Protection</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#main-vcc-power-detection-and-flash-protection">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#resets">Resets</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#clock-outputs">Clock Outputs</a></th>
    <td><a href="../theory_of_operation.md#clock-outputs">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#clock-and-reset-inputs">Clock and Reset Inputs</a></th>
    <td><a href="../theory_of_operation.md#clock-and-reset-inputs">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#register-access-interface">Register Access Interface</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#register-access-interface">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#ast-registers-initialization-during-boot">AST registers initialization during boot.</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#ast-registers-initialization-during-boot">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#random-number-generator">Random Number Generator</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#random-number-generator">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#entropy-consumption">Entropy Consumption</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#entropy-consumption">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#countermeasures-and-alerts">Countermeasures and Alerts</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#alert-events">Alert Events</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#alert-signaling">Alert Signaling</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#countermeasures">Countermeasures</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>
</div>
</div>


## Feature -> Testpoint Matrix
IP ast currently contains no **Feature → Testpoint** mapping
