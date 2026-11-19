# ac_range_check Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="ac_range_checkbypass">
      <td>AC_RANGE_CHECK.BYPASS</td>
      <td>Asserting the multi-bit encoded range check overwrite input bypasses the matching,   permission and RACL logic, allowing all requests to pass unfiltered.</td>
    </tr>
    <tr id="ac_range_checkdeny_log">
      <td>AC_RANGE_CHECK.DENY_LOG</td>
      <td>Denied requests increment a global deny counter and the first denied request is   logged. Reaching the programmed deny count threshold raises an interrupt, and   clearing the log resets the counter and the logged information.</td>
    </tr>
    <tr id="ac_range_checkrangelock">
      <td>AC_RANGE_CHECK.RANGE.LOCK</td>
      <td>The configuration of each range can be locked individually, making its base, limit,   attribute and RACL policy registers immutable until the next reset.</td>
    </tr>
    <tr id="ac_range_checkrangematch">
      <td>AC_RANGE_CHECK.RANGE.MATCH</td>
      <td>Each enabled range matches an incoming request when its address falls between the   configured base and limit addresses. Disabled ranges never match.</td>
    </tr>
    <tr id="ac_range_checkrangepermissions">
      <td>AC_RANGE_CHECK.RANGE.PERMISSIONS</td>
      <td>Each range grants read, write and/or execute access. A request is allowed only if the   matching range permits its access type; otherwise it is denied. Requests which match   no enabled range are denied by default.</td>
    </tr>
    <tr id="ac_range_checkrangepriority">
      <td>AC_RANGE_CHECK.RANGE.PRIORITY</td>
      <td>When a request matches multiple enabled ranges, the enabled range with the lowest   index determines the permissions which apply to the request.</td>
    </tr>
    <tr id="ac_range_checkrangeracl_policy">
      <td>AC_RANGE_CHECK.RANGE.RACL_POLICY</td>
      <td>Each range carries a RACL policy which additionally checks the RACL role of the   requester against the read and write permission masks of the matching range.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>AC_RANGE_CHECK.RANGE.MATCH</th>
    <th>AC_RANGE_CHECK.RANGE.PERMISSIONS</th>
    <th>AC_RANGE_CHECK.RANGE.PRIORITY</th>
    <th>AC_RANGE_CHECK.RANGE.RACL_POLICY</th>
    <th>AC_RANGE_CHECK.RANGE.LOCK</th>
    <th>AC_RANGE_CHECK.DENY_LOG</th>
    <th>AC_RANGE_CHECK.BYPASS</th>
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
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#request-decoding">Request Decoding</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#request-decoding">X</a></td>
    <td></td>
    <td><a href="../theory_of_operation.md#request-decoding">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#range-matching">Range Matching</a></th>
    <td><a href="../theory_of_operation.md#range-matching">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#priority-resolution">Priority Resolution</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#priority-resolution">X</a></td>
    <td><a href="../theory_of_operation.md#priority-resolution">X</a></td>
    <td><a href="../theory_of_operation.md#priority-resolution">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#access-check-algorithm">Access Check Algorithm</a></th>
    <td><a href="../theory_of_operation.md#access-check-algorithm">X</a></td>
    <td><a href="../theory_of_operation.md#access-check-algorithm">X</a></td>
    <td><a href="../theory_of_operation.md#access-check-algorithm">X</a></td>
    <td><a href="../theory_of_operation.md#access-check-algorithm">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#squashing-of-denied-requests">Squashing of Denied Requests</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#squashing-of-denied-requests">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#range-configuration-locking">Range Configuration Locking</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#range-configuration-locking">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#denied-access-logging">Denied Access Logging</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#denied-access-logging">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#deny-counting-and-interrupt">Deny Counting and Interrupt</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#deny-counting-and-interrupt">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#bypass-mode">Bypass Mode</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#bypass-mode">X</a></td>
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
    <th>AC_RANGE_CHECK.RANGE.MATCH</th>
    <th>AC_RANGE_CHECK.RANGE.PERMISSIONS</th>
    <th>AC_RANGE_CHECK.RANGE.PRIORITY</th>
    <th>AC_RANGE_CHECK.RANGE.RACL_POLICY</th>
    <th>AC_RANGE_CHECK.RANGE.LOCK</th>
    <th>AC_RANGE_CHECK.DENY_LOG</th>
    <th>AC_RANGE_CHECK.BYPASS</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#ac_range_check_smoke">ac_range_check_smoke</a></th>
    <td><a href="02_testpoint_report.md#ac_range_check_smoke">X</a></td>
    <td><a href="02_testpoint_report.md#ac_range_check_smoke">X</a></td>
    <td><a href="02_testpoint_report.md#ac_range_check_smoke">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#ac_range_check_smoke_racl">ac_range_check_smoke_racl</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#ac_range_check_smoke_racl">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#ac_range_check_lock_range">ac_range_check_lock_range</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#ac_range_check_lock_range">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#ac_range_check_attr_permissions">ac_range_check_attr_permissions</a></th>
    <td><a href="02_testpoint_report.md#ac_range_check_attr_permissions">X</a></td>
    <td><a href="02_testpoint_report.md#ac_range_check_attr_permissions">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#ac_range_check_log_intr_boundaries">ac_range_check_log_intr_boundaries</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#ac_range_check_log_intr_boundaries">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#ac_range_check_mubi_encodings">ac_range_check_mubi_encodings</a></th>
    <td><a href="02_testpoint_report.md#ac_range_check_mubi_encodings">X</a></td>
    <td><a href="02_testpoint_report.md#ac_range_check_mubi_encodings">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#ac_range_check_mubi_encodings">X</a></td>
    <td><a href="02_testpoint_report.md#ac_range_check_mubi_encodings">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#ac_range_check_tl_datapath">ac_range_check_tl_datapath</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#ac_range_check_tl_datapath">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#ac_range_bypass_enable">ac_range_bypass_enable</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#ac_range_bypass_enable">X</a></td>
    <td><a href="02_testpoint_report.md#ac_range_bypass_enable">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_ac_range_check_csr_access-dragonfly">chip_ac_range_check_csr_access (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_ac_range_check_csr_access-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_ac_range_check_csr_access-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_ac_range_check_csr_access-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_ac_range_check_csr_access-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_ac_range_check_csr_access-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_ac_range_check_csr_access-dragonfly">X</a></td>
    <td></td>
  </tr>
</table>
</div>
</div>
