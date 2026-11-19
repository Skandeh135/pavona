# rv_plic Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="rv_plicenable">
      <td>RV_PLIC.ENABLE</td>
      <td>Each target has an associated set of interrupt enable bits. Configuring these   controls whether a target will be notified when the interrupt is triggered.</td>
    </tr>
    <tr id="rv_plicpriority">
      <td>RV_PLIC.PRIORITY</td>
      <td>Each interrupt source can be given a configurable priority.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>RV_PLIC.PRIORITY</th>
    <th>RV_PLIC.ENABLE</th>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#theory-of-operation">Theory of Operation</a></th>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#block-diagram">Block Diagram</a></th>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#hardware-interfaces">Hardware Interfaces</a></th>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#design-details">Design Details</a></th>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#identifier">Identifier</a></th>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#priority-and-threshold">Priority and Threshold</a></th>
    <td><a href="../theory_of_operation.md#priority-and-threshold">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#interrupt-gateways">Interrupt Gateways</a></th>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#interrupt-enables">Interrupt Enables</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#interrupt-enables">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#interrupt-claims">Interrupt Claims</a></th>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#interrupt-completion">Interrupt Completion</a></th>
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
    <th>RV_PLIC.PRIORITY</th>
    <th>RV_PLIC.ENABLE</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#leveltriggeredip_a">LevelTriggeredIp_A</a></th>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#leveltriggeredipwithclaim_a">LevelTriggeredIpWithClaim_A</a></th>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#ipstableaftertriggered_a">IpStableAfterTriggered_A</a></th>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#ipclearafterclaim_a">IpClearAfterClaim_A</a></th>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#ipstableafterclaimed_a">IpStableAfterClaimed_A</a></th>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#triggerirqforwardcheck_a">TriggerIrqForwardCheck_A</a></th>
    <td><a href="02_testpoint_report.md#triggerirqforwardcheck_a">X</a></td>
    <td><a href="02_testpoint_report.md#triggerirqforwardcheck_a">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#triggerirqbackwardcheck_a">TriggerIrqBackwardCheck_A</a></th>
    <td><a href="02_testpoint_report.md#triggerirqbackwardcheck_a">X</a></td>
    <td><a href="02_testpoint_report.md#triggerirqbackwardcheck_a">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#idchangewithirq_a">IdChangeWithIrq_A</a></th>
    <td><a href="02_testpoint_report.md#idchangewithirq_a">X</a></td>
    <td><a href="02_testpoint_report.md#idchangewithirq_a">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_plic_all_irqs-egret">chip_sw_plic_all_irqs (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_plic_all_irqs-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_plic_all_irqs-egret">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_plic_sw_irq-egret">chip_sw_plic_sw_irq (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_plic_sw_irq-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_plic_sw_irq-egret">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_plic_alerts-egret">chip_sw_plic_alerts (egret)</a></th>
    <td></td>
    <td></td>
  </tr>
</table>
</div>
</div>
