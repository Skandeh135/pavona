# rstmgr Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="rstmgralert_handlerreset_status">
      <td>RSTMGR.ALERT_HANDLER.RESET_STATUS</td>
      <td>Inform alert handler about reset enable status for each reset.</td>
    </tr>
    <tr id="rstmgralert_infocapture">
      <td>RSTMGR.ALERT_INFO.CAPTURE</td>
      <td>Capture alert crash dump information upon reset.</td>
    </tr>
    <tr id="rstmgralert_infoenable">
      <td>RSTMGR.ALERT_INFO.ENABLE</td>
      <td>Enable capture of alert crash dump information.</td>
    </tr>
    <tr id="rstmgrcpu_infocapture">
      <td>RSTMGR.CPU_INFO.CAPTURE</td>
      <td>Capture cpu crash dump information upon reset.</td>
    </tr>
    <tr id="rstmgrcpu_infoenable">
      <td>RSTMGR.CPU_INFO.ENABLE</td>
      <td>Enable capture of cpu crash dump information.</td>
    </tr>
    <tr id="rstmgrporstretcher">
      <td>RSTMGR.POR.STRETCHER</td>
      <td>Debounces external POR input, causing the internal POR tobe inactive after the external POR has been inactive for almost100 cycles. Conversely, there is only some synchronization delaybetween the external POR and the internal POR to become active.</td>
    </tr>
    <tr id="rstmgrreset_consistency_checks">
      <td>RSTMGR.RESET_CONSISTENCY_CHECKS</td>
      <td>Cause a fatal alert if any reset has no legitimate cause.</td>
    </tr>
    <tr id="rstmgrreset_infocapture">
      <td>RSTMGR.RESET_INFO.CAPTURE</td>
      <td>Capture information about the causes of a reset.</td>
    </tr>
    <tr id="rstmgrreset_infoclear">
      <td>RSTMGR.RESET_INFO.CLEAR</td>
      <td>Clear information about the causes of a reset.</td>
    </tr>
    <tr id="rstmgrsw_rstchip_reset">
      <td>RSTMGR.SW_RST.CHIP_RESET</td>
      <td>Cause a reset of all but some AON and system debug blocks via CSR.</td>
    </tr>
    <tr id="rstmgrsw_rstrequest">
      <td>RSTMGR.SW_RST.REQUEST</td>
      <td>Enable/trigger reset of some peripherals via CSR.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>RSTMGR.POR.STRETCHER</th>
    <th>RSTMGR.SW_RST.CHIP_RESET</th>
    <th>RSTMGR.SW_RST.REQUEST</th>
    <th>RSTMGR.RESET_INFO.CAPTURE</th>
    <th>RSTMGR.RESET_INFO.CLEAR</th>
    <th>RSTMGR.ALERT_INFO.CAPTURE</th>
    <th>RSTMGR.ALERT_INFO.ENABLE</th>
    <th>RSTMGR.CPU_INFO.CAPTURE</th>
    <th>RSTMGR.CPU_INFO.ENABLE</th>
    <th>RSTMGR.ALERT_HANDLER.RESET_STATUS</th>
    <th>RSTMGR.RESET_CONSISTENCY_CHECKS</th>
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
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#reset-topology">Reset Topology</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#reset-manager">Reset Manager</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#reset-manager">X</a></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#shadow-resets">Shadow Resets</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#reset-consistency-checks">Reset Consistency Checks</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#reset-consistency-checks">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#reset-indications-for-alert-handler">Reset Indications for Alert Handler</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#reset-indications-for-alert-handler">X</a></td>
    <td></td>
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
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#por-reset-tree">POR Reset Tree</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#life-cycle-reset-tree">Life Cycle Reset Tree</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#system-reset-tree">System Reset Tree</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#output-leaf-resets">Output Leaf Resets</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#power-domains-and-reset-trees">Power Domains and Reset Trees</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#software-controlled-resets">Software Controlled Resets</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#software-controlled-resets">X</a></td>
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
    <th><a href="../theory_of_operation.md#summary">Summary</a></th>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#reset-information">Reset Information</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#reset-information">X</a></td>
    <td></td>
    <td><a href="../theory_of_operation.md#reset-information">X</a></td>
    <td><a href="../theory_of_operation.md#reset-information">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#crash-dump-information">Crash Dump Information</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#crash-dump-information">X</a></td>
    <td><a href="../theory_of_operation.md#crash-dump-information">X</a></td>
    <td><a href="../theory_of_operation.md#crash-dump-information">X</a></td>
    <td><a href="../theory_of_operation.md#crash-dump-information">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#alert-information">Alert Information</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#alert-information">X</a></td>
    <td><a href="../theory_of_operation.md#alert-information">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#cpu-information">CPU Information</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#cpu-information">X</a></td>
    <td><a href="../theory_of_operation.md#cpu-information">X</a></td>
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
    <th>RSTMGR.POR.STRETCHER</th>
    <th>RSTMGR.SW_RST.CHIP_RESET</th>
    <th>RSTMGR.SW_RST.REQUEST</th>
    <th>RSTMGR.RESET_INFO.CAPTURE</th>
    <th>RSTMGR.RESET_INFO.CLEAR</th>
    <th>RSTMGR.ALERT_INFO.CAPTURE</th>
    <th>RSTMGR.ALERT_INFO.ENABLE</th>
    <th>RSTMGR.CPU_INFO.CAPTURE</th>
    <th>RSTMGR.CPU_INFO.ENABLE</th>
    <th>RSTMGR.ALERT_HANDLER.RESET_STATUS</th>
    <th>RSTMGR.RESET_CONSISTENCY_CHECKS</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#reset_stretcher">reset_stretcher</a></th>
    <td><a href="02_testpoint_report.md#reset_stretcher">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#sw_rst">sw_rst</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#sw_rst">X</a></td>
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
    <th><a href="02_testpoint_report.md#sw_rst_reset_race">sw_rst_reset_race</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#sw_rst_reset_race">X</a></td>
    <td><a href="02_testpoint_report.md#sw_rst_reset_race">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#reset_info">reset_info</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#reset_info">X</a></td>
    <td><a href="02_testpoint_report.md#reset_info">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#cpu_info">cpu_info</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cpu_info">X</a></td>
    <td><a href="02_testpoint_report.md#cpu_info">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#alert_info">alert_info</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#alert_info">X</a></td>
    <td><a href="02_testpoint_report.md#alert_info">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#reset_info_capture">reset_info_capture</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#reset_info_capture">X</a></td>
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
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#rstmgr_cnsty_chk">rstmgr_cnsty_chk</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#rstmgr_cnsty_chk">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rstmgr_non_sys_reset_info-egret">chip_sw_rstmgr_non_sys_reset_info (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rstmgr_non_sys_reset_info-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_rstmgr_non_sys_reset_info-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rstmgr_sys_reset_info-egret">chip_sw_rstmgr_sys_reset_info (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rstmgr_sys_reset_info-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_rstmgr_sys_reset_info-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rstmgr_cpu_info-egret">chip_sw_rstmgr_cpu_info (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rstmgr_cpu_info-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_rstmgr_cpu_info-egret">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rstmgr_sw_req_reset-egret">chip_sw_rstmgr_sw_req_reset (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rstmgr_sw_req_reset-egret">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_rstmgr_alert_info-egret">chip_sw_rstmgr_alert_info (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rstmgr_alert_info-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_rstmgr_alert_info-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rstmgr_sw_rst-egret">chip_sw_rstmgr_sw_rst (egret)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rstmgr_sw_rst-egret">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_rstmgr_escalation_reset-egret">chip_sw_rstmgr_escalation_reset (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rstmgr_escalation_reset-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rstmgr_escalation_reset-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rstmgr_alert_handler_reset_enables-egret">chip_sw_rstmgr_alert_handler_reset_enables (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rstmgr_alert_handler_reset_enables-egret">X</a></td>
    <td></td>
  </tr>
</table>
</div>
</div>
