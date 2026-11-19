# alert_handler Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="alert_handleralertescalate">
      <td>ALERT_HANDLER.ALERT.ESCALATE</td>
      <td>   All incoming alerts can trigger the alert escalation mechanisms   of the classes they are allocated to</td>
    </tr>
    <tr id="alert_handleralertinterrupt">
      <td>ALERT_HANDLER.ALERT.INTERRUPT</td>
      <td>    All alert classes can raise an interrupt when an alert that is    allocated to them is raised.</td>
    </tr>
    <tr id="alert_handleralertobserve">
      <td>ALERT_HANDLER.ALERT.OBSERVE</td>
      <td>    All incoming alerts can be observed by the alert handler.</td>
    </tr>
    <tr id="alert_handlercrash_dump">
      <td>ALERT_HANDLER.CRASH_DUMP</td>
      <td>   A crashdump with the state of CSRs and alert handler state bits   is made available. When a programmable latching trigger condition   is met the crashdump is held constant at its value on that   trigger condition so it can be recorded and made available for   later analysis</td>
    </tr>
    <tr id="alert_handlerescalationcount">
      <td>ALERT_HANDLER.ESCALATION.COUNT</td>
      <td>    An escalation can be triggered when the number of alerts seen in    a particular class exceeds a software programmable threshold</td>
    </tr>
    <tr id="alert_handlerescalationphases">
      <td>ALERT_HANDLER.ESCALATION.PHASES</td>
      <td>   Each alert class can trigger the same 4 escalation phases. A   programmable timer specifies the delay between each of the   escalation phases. The actions taken on each of the escalation   signals are specific to the top-level integration.</td>
    </tr>
    <tr id="alert_handlerescalationtimeout">
      <td>ALERT_HANDLER.ESCALATION.TIMEOUT</td>
      <td>    An escalation can be triggered when an interrupt from a class    isn't acknowledged after a software programmable timeout</td>
    </tr>
    <tr id="alert_handlerping_timer">
      <td>ALERT_HANDLER.PING_TIMER</td>
      <td>    The alert handler periodically pings all alert receivers and    will raise an alert if the ping isn't responded to in good time </td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>ALERT_HANDLER.ALERT.OBSERVE</th>
    <th>ALERT_HANDLER.ALERT.INTERRUPT</th>
    <th>ALERT_HANDLER.ALERT.ESCALATE</th>
    <th>ALERT_HANDLER.PING_TIMER</th>
    <th>ALERT_HANDLER.ESCALATION.COUNT</th>
    <th>ALERT_HANDLER.ESCALATION.TIMEOUT</th>
    <th>ALERT_HANDLER.ESCALATION.PHASES</th>
    <th>ALERT_HANDLER.CRASH_DUMP</th>
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
    <th><a href="../theory_of_operation.md#hardware-interfaces">Hardware Interfaces</a></th>
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
    <th><a href="../theory_of_operation.md#parameters">Parameters</a></th>
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
    <th><a href="../theory_of_operation.md#signals">Signals</a></th>
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
    <th><a href="../theory_of_operation.md#entropy-network-connections">Entropy Network Connections</a></th>
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
    <th><a href="../theory_of_operation.md#alert-channels">Alert Channels</a></th>
    <td><a href="../theory_of_operation.md#alert-channels">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#escalation-channels">Escalation Channels</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#escalation-channels">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#low-power-indication-signals">Low-power Indication Signals</a></th>
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
    <th><a href="../theory_of_operation.md#crashdump-output">Crashdump Output</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#crashdump-output">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#design-details">Design Details</a></th>
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
    <th><a href="../theory_of_operation.md#alert-definition">Alert Definition</a></th>
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
    <th><a href="../theory_of_operation.md#differential-alert-signaling">Differential Alert Signaling</a></th>
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
    <th><a href="../theory_of_operation.md#ping-testing">Ping Testing</a></th>
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
    <th><a href="../theory_of_operation.md#monitoring-of-signal-integrity-issues">Monitoring of Signal Integrity Issues</a></th>
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
    <th><a href="../theory_of_operation.md#skew-on-asynchronous-differential-pairs">Skew on Asynchronous Differential Pairs</a></th>
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
    <th><a href="../theory_of_operation.md#lfsr-timer">LFSR Timer</a></th>
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
    <th><a href="../theory_of_operation.md#alert-receiving">Alert Receiving</a></th>
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
    <th><a href="../theory_of_operation.md#alert-classification-and-interrupts">Alert Classification and Interrupts</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#alert-classification-and-interrupts">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#escalation-mechanisms">Escalation Mechanisms</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#escalation-mechanisms">X</a></td>
    <td></td>
    <td><a href="../theory_of_operation.md#escalation-mechanisms">X</a></td>
    <td><a href="../theory_of_operation.md#escalation-mechanisms">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#programmable-escalation-protocol">Programmable Escalation Protocol</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#programmable-escalation-protocol">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#programmable-escalation-protocol">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#escalation-signaling">Escalation Signaling</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#escalation-signaling">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#ping-testing-of-the-escalation-signals">Ping Testing of the Escalation Signals</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#ping-testing-of-the-escalation-signals">X</a></td>
    <td><a href="../theory_of_operation.md#ping-testing-of-the-escalation-signals">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#monitoring-of-pings-at-the-escalation-receiver-side">Monitoring of Pings at the Escalation Receiver Side</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#monitoring-of-pings-at-the-escalation-receiver-side">X</a></td>
    <td><a href="../theory_of_operation.md#monitoring-of-pings-at-the-escalation-receiver-side">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#low-power-management-of-alert-channels">Low-power Management of Alert Channels</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#low-power-management-of-alert-channels">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#assumptions">Assumptions</a></th>
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
    <th><a href="../theory_of_operation.md#scenarios">Scenarios</a></th>
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
    <th><a href="../theory_of_operation.md#alert-handler-in-reset">Alert Handler in Reset</a></th>
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
    <th><a href="../theory_of_operation.md#alert-sender-in-reset-or-clock-gated">Alert Sender in Reset or Clock-gated</a></th>
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
    <th><a href="../theory_of_operation.md#employed-solution">Employed Solution</a></th>
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
    <th><a href="../theory_of_operation.md#implementation-aspects">Implementation Aspects</a></th>
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
    <th><a href="../theory_of_operation.md#ping-mechanism-bypass">Ping Mechanism Bypass</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#ping-mechanism-bypass">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#fsm-encoding">FSM Encoding</a></th>
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
    <th><a href="../theory_of_operation.md#latency--skew-considerations">Latency / Skew Considerations</a></th>
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
    <th><a href="../theory_of_operation.md#integration-considerations">Integration Considerations</a></th>
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
    <th><a href="../theory_of_operation.md#hardening-against-glitch-attacks">Hardening Against Glitch Attacks</a></th>
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
    <th>ALERT_HANDLER.ALERT.OBSERVE</th>
    <th>ALERT_HANDLER.ALERT.INTERRUPT</th>
    <th>ALERT_HANDLER.ALERT.ESCALATE</th>
    <th>ALERT_HANDLER.PING_TIMER</th>
    <th>ALERT_HANDLER.ESCALATION.COUNT</th>
    <th>ALERT_HANDLER.ESCALATION.TIMEOUT</th>
    <th>ALERT_HANDLER.ESCALATION.PHASES</th>
    <th>ALERT_HANDLER.CRASH_DUMP</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#esc_accum">esc_accum</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#esc_accum">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#esc_accum">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#esc_timeout">esc_timeout</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#esc_timeout">X</a></td>
    <td><a href="02_testpoint_report.md#esc_timeout">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#esc_timeout">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#entropy">entropy</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#entropy">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#sig_int_fail">sig_int_fail</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#sig_int_fail">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#clk_skew">clk_skew</a></th>
    <td><a href="02_testpoint_report.md#clk_skew">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#random_alerts">random_alerts</a></th>
    <td><a href="02_testpoint_report.md#random_alerts">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#random_alerts">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#random_classes">random_classes</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#random_classes">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#ping_timeout">ping_timeout</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#ping_timeout">X</a></td>
    <td><a href="02_testpoint_report.md#ping_timeout">X</a></td>
    <td><a href="02_testpoint_report.md#ping_timeout">X</a></td>
    <td><a href="02_testpoint_report.md#ping_timeout">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#lpg">lpg</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#lpg">X</a></td>
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
    <th><a href="02_testpoint_report.md#alert_handler_entropy_stress_test">alert_handler_entropy_stress_test</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#alert_handler_entropy_stress_test">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#alert_handler_alert_accum_saturation">alert_handler_alert_accum_saturation</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#alert_handler_alert_accum_saturation">X</a></td>
    <td><a href="02_testpoint_report.md#alert_handler_alert_accum_saturation">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#alert_handler_alert_accum_saturation">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_alert_handler_alerts-egret">chip_sw_alert_handler_alerts (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_alert_handler_alerts-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_alert_handler_alerts-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_alert_handler_escalations-egret">chip_sw_alert_handler_escalations (egret)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_alert_handler_escalations-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_alert_handler_escalations-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_alert_handler_escalation_nmi_reset-egret">chip_sw_alert_handler_escalation_nmi_reset (egret)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_alert_handler_escalation_nmi_reset-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_alert_handler_escalation_nmi_reset-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_alert_handler_escalation_methods-egret">chip_sw_alert_handler_escalation_methods (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_alert_handler_escalation_methods-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_alert_handler_escalation_methods-egret">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_all_escalation_resets-egret">chip_sw_all_escalation_resets (egret)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_alert_handler_irqs-egret">chip_sw_alert_handler_irqs (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_alert_handler_irqs-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_alert_handler_entropy-egret">chip_sw_alert_handler_entropy (egret)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_alert_handler_crashdump-egret">chip_sw_alert_handler_crashdump (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_alert_handler_crashdump-egret">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_alert_handler_ping_timeout-egret">chip_sw_alert_handler_ping_timeout (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_alert_handler_ping_timeout-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_alert_handler_lpg_sleep_mode_alerts-egret">chip_sw_alert_handler_lpg_sleep_mode_alerts (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_alert_handler_lpg_sleep_mode_alerts-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_alert_handler_lpg_sleep_mode_pings-egret">chip_sw_alert_handler_lpg_sleep_mode_pings (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_alert_handler_lpg_sleep_mode_pings-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_alert_handler_lpg_clock_off-egret">chip_sw_alert_handler_lpg_clock_off (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_alert_handler_lpg_clock_off-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_alert_handler_lpg_reset_toggle-egret">chip_sw_alert_handler_lpg_reset_toggle (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_alert_handler_lpg_reset_toggle-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_alert_handler_ping_ok-egret">chip_sw_alert_handler_ping_ok (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_alert_handler_ping_ok-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_alert_handler_reverse_ping_in_deep_sleep-egret">chip_sw_alert_handler_reverse_ping_in_deep_sleep (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_alert_handler_reverse_ping_in_deep_sleep-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>
</div>
</div>
