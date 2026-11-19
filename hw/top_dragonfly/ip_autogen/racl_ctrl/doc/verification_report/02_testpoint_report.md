# racl_ctrl Testpoint Report

## error_log

Drive the racl_error_i and racl_error_external_i inputs, and report errors with racl_ctrl.

Verify that simultaneous reports are correctly arbitrated and that the expected error is logged.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td>No tests</td>
  <td><a href="01_feature_report.md#raclerror_arbitration">RACL.ERROR_ARBITRATION</a><br><a href="01_feature_report.md#raclerror_log">RACL.ERROR_LOG</a><br><a href="01_feature_report.md#raclext_use">RACL.EXT_USE</a></td>
</tr>
  </tbody>
</table>

## rot_private
Verify that there is only one designated ROT policy and that only an IP with the ROT role can modify policy registers.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td>No tests</td>
  <td><a href="01_feature_report.md#raclpolicy_enforcement">RACL.POLICY_ENFORCEMENT</a><br><a href="01_feature_report.md#raclrot_policy">RACL.ROT_POLICY</a></td>
</tr>
  </tbody>
</table>

## smoke

Write an arbitrary value to each policy register and check that this gets correctly
reflected in the racl_policies_o output.

Also drive the racl_error_i and racl_error_external_i inputs. Check that
intr_racl_error_o is raised correctly.

Note: the racl_ctrl cannot verify the various blocks whose registers are racl-protected
handle the protocol correctly.
This can be verified by tests run on those blocks.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#racl_ctrl_smoke">racl_ctrl_smoke</a></td>
  <td><a href="01_feature_report.md#raclext_use">RACL.EXT_USE</a><br><a href="01_feature_report.md#raclpolicy_enforcement">RACL.POLICY_ENFORCEMENT</a></td>
</tr>
  </tbody>
</table>
