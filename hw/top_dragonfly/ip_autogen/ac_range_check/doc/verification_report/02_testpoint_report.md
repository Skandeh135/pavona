# ac_range_check Testpoint Report

## ac_range_bypass_enable

Test the bypass functionality for enabled ranges.

Stimulus:

- Assert range_check_overwrite_i to Mubi8::True
- Configure the AC range check to block certain address ranges
  * Randomize type of denial (R/W/X, RACL policies)
- Perform random TLUL requests that fall within blocked ranges and outside with:
  * Random request type (R/W/X) and random RACL role

Checking:

- Check if all transfers are allowed
- LOG_STATUS.deny_cnt must stay 0


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#ac_range_check_rst_safe_bypass">ac_range_check_rst_safe_bypass</a></td>
  <td><a href="01_feature_report.md#ac_range_checkbypass">AC_RANGE_CHECK.BYPASS</a><br><a href="01_feature_report.md#ac_range_checkdeny_log">AC_RANGE_CHECK.DENY_LOG</a></td>
</tr>
  </tbody>
</table>

## ac_range_check_attr_permissions

Test all read, write, and execute permission combinations for every range.

Stimulus:

- Configure deterministic, non-overlapping enabled ranges.
- Permit every RACL role.
- Apply all eight R/W/X permission combinations to every range.
- Issue read, write, and execute requests for each combination.

Checking:

- A request is granted only when its corresponding strict MuBi permission is true.
- Granted requests and downstream responses pass through unchanged.
- Denied requests return an error and zero read data.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#ac_range_check_rst_safe_attr_cov">ac_range_check_rst_safe_attr_cov</a></td>
  <td><a href="01_feature_report.md#ac_range_checkrangematch">AC_RANGE_CHECK.RANGE.MATCH</a><br><a href="01_feature_report.md#ac_range_checkrangepermissions">AC_RANGE_CHECK.RANGE.PERMISSIONS</a></td>
</tr>
  </tbody>
</table>

## ac_range_check_lock_range

Test the range lock functionality

Stimulus:

- Configure a range's RANGE_BASE, RANGE_LIMIT, RANGE_ATTR, RANGE_RACL_POLICY_SHADOWED
  register
- Clear RANGE_REGWEN to MuBi4::False in a randomized way
- Try to reconfigure the range with different values

Checking:

- If RANGE_REGWEN was cleared to MuBi4::False, the reconfigured register values
  The original configuration should remain in the registers. If RANGE_REGWEN was not
  cleared, the reconfigured values should have replaced the original ones.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#ac_range_check_rst_safe_lock_cov">ac_range_check_rst_safe_lock_cov</a><br><a href="03_test_report.md#ac_range_check_rst_safe_lock_range_with_rand_reset">ac_range_check_rst_safe_lock_range_with_rand_reset</a></td>
  <td><a href="01_feature_report.md#ac_range_checkrangelock">AC_RANGE_CHECK.RANGE.LOCK</a></td>
</tr>
  </tbody>
</table>

## ac_range_check_log_intr_boundaries

Test deny logging and interrupt behavior at low, middle, and high thresholds.

Stimulus:

- Use deterministic logging-enabled and logging-disabled denied ranges.
- Exercise thresholds 1-5, 128, and 250-255.
- Sample the deny counter at equality and, where possible, one count above.
- Clear the log and issue a denial while global logging is disabled.

Checking:

- The deny counter saturates and changes only for a strictly enabled range log field.
- The interrupt asserts only when deny_cnt is greater than the programmed threshold.
- Log status and address preserve the first logged denial until cleared.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#ac_range_check_rst_safe_log_intr_cov">ac_range_check_rst_safe_log_intr_cov</a></td>
  <td><a href="01_feature_report.md#ac_range_checkdeny_log">AC_RANGE_CHECK.DENY_LOG</a></td>
</tr>
  </tbody>
</table>

## ac_range_check_mubi_encodings

Test all raw MuBi4 encodings in range attributes and range write enables.

Stimulus:

- In separate reset epochs, write each of the 16 raw encodings.
- Apply each encoding to enable, R/W/X permission, logging, and RANGE_REGWEN fields.
- Attempt to modify protected range CSRs after programming RANGE_REGWEN.

Checking:

- ENABLE uses loose decoding: only MuBi4False disables a range.
- Permissions and logging use strict decoding: only MuBi4True enables behavior.
- Only MuBi4True leaves RANGE_REGWEN writable; all other encodings lock the range.
- Raw attribute values and the resulting RANGE_REGWEN state read back as expected.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#ac_range_check_rst_safe_mubi_cov">ac_range_check_rst_safe_mubi_cov</a></td>
  <td><a href="01_feature_report.md#ac_range_checkdeny_log">AC_RANGE_CHECK.DENY_LOG</a><br><a href="01_feature_report.md#ac_range_checkrangelock">AC_RANGE_CHECK.RANGE.LOCK</a><br><a href="01_feature_report.md#ac_range_checkrangematch">AC_RANGE_CHECK.RANGE.MATCH</a><br><a href="01_feature_report.md#ac_range_checkrangepermissions">AC_RANGE_CHECK.RANGE.PERMISSIONS</a></td>
</tr>
  </tbody>
</table>

## ac_range_check_smoke

Smoke test in which we configure a randomized number of ranges to allow a transfer
and perform transfers.

Stimulus:

  - Assert range_check_overwrite_i to MuBi8::False
  - Configure a random number of ranges:
    * Randomize the RANGE_BASE and RANGE_LIMIT register (RANGE_LIMIT > RANGE_BASE)
    * Randomize the RANGE_ATTR register and set the RANGE_ATTR.enable bit to 1
    * Set RANGE_RACL_POLICY_SHADOWED.read_perm and
      RANGE_RACL_POLICY_SHADOWED.write_perm to 0xFFFF (disables RACL checks)
  - Perform random TLUL requests on the unfiltered interface (ctn_tl_h2d_i) and
    provide random TLUL responses on the filtered interface (ctn_filtered_tl_d2h_i).

Checking:

  - If a request falls outside of any enabled range:
    * The request should be denied and an error should be returned in the response on
      the unfiltered TLUL D channel (ctn_tl_d2h_o).
    * Read and Execute requests should return all zero as data on the unfiltered TLUL
      D channel (ctn_tl_d2h_o).
  - If the request falls into the address space of at least one enabled range, the
    request is allowed if and only if the permissions of that range allow it (e.g., if
    the access is a data read, the range needs to allow reads for the access to be
    allowed) and it does not fall into the address space of any other enabled range
    with lower index whose permissions deny the request.
    Allowed requests should propagate without modifications on the A channel. And the
    corresponding responses should propagate unmodified on the D channel. One
    exception to this is the d_data field for AccessAck responses (i.e., responses to
    writes): the TL-UL spec defines that this field in this case can be any value, and
    the current implementation sets it to zero (for the reason described in PR #1236).


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#ac_range_check_rst_safe_smoke">ac_range_check_rst_safe_smoke</a><br><a href="03_test_report.md#ac_range_check_rst_safe_smoke_high_threshold">ac_range_check_rst_safe_smoke_high_threshold</a><br><a href="03_test_report.md#ac_range_check_rst_safe_smoke_with_rand_reset">ac_range_check_rst_safe_smoke_with_rand_reset</a></td>
  <td><a href="01_feature_report.md#ac_range_checkrangematch">AC_RANGE_CHECK.RANGE.MATCH</a><br><a href="01_feature_report.md#ac_range_checkrangepermissions">AC_RANGE_CHECK.RANGE.PERMISSIONS</a><br><a href="01_feature_report.md#ac_range_checkrangepriority">AC_RANGE_CHECK.RANGE.PRIORITY</a></td>
</tr>
  </tbody>
</table>

## ac_range_check_smoke_racl

Smoke test which exercises the RACL policy check of the ranges.

Stimulus:

  - Configure a random number of ranges with all of the read, write and execute
    permissions granted, so that the access decision is governed by the RACL policy.
  - Randomize RANGE_RACL_POLICY_SHADOWED.read_perm and
    RANGE_RACL_POLICY_SHADOWED.write_perm over their full range.
  - Perform random TLUL requests with random RACL roles on the unfiltered interface.

Checking:

  - A read or execute request is allowed only if the RACL role of the request is
    permitted by the read_perm mask of the matching range, and a write request only if
    the role is permitted by its write_perm mask.
  - Requests denied by the RACL check are handled like any other denied request: they
    do not propagate and an error is returned on the unfiltered TLUL D channel.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#ac_range_check_rst_safe_racl_cov">ac_range_check_rst_safe_racl_cov</a><br><a href="03_test_report.md#ac_range_check_rst_safe_smoke_racl">ac_range_check_rst_safe_smoke_racl</a></td>
  <td><a href="01_feature_report.md#ac_range_checkrangeracl_policy">AC_RANGE_CHECK.RANGE.RACL_POLICY</a></td>
</tr>
  </tbody>
</table>

## ac_range_check_tl_datapath

Test legal outstanding and reset behavior on the unfiltered and filtered TL paths.

Stimulus:

- Hold filtered responses while issuing all 16 legal source IDs to one address.
- Drain the burst and issue a request to a different address.
- Reset with one accepted request pending.
- After reset, return a downstream response with d_error asserted.

Checking:

- Requests and responses remain correctly paired at maximum legal occupancy.
- Same-address and different-address outstanding states are observed.
- Reset cleanly discards the pending request.
- A downstream d_error propagates unchanged to the unfiltered response.

Malformed upstream TL request bins are intentionally excluded from this testpoint
until the shared TL error-stimulus strategy is resolved.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#ac_range_check_rst_safe_tl_cov">ac_range_check_rst_safe_tl_cov</a></td>
  <td><a href="01_feature_report.md#ac_range_checkrangepermissions">AC_RANGE_CHECK.RANGE.PERMISSIONS</a></td>
</tr>
  </tbody>
</table>

## chip_ac_range_check_csr_access (dragonfly)
Verify that the AC Range Check CSRs are reachable and well behaved from the chip
level.

The AC Range Check is instantiated on the path between `soc_proxy` and the CTN fabric,
so its register file is part of the chip RAL and is walked by the chip-level CSR tests
along with every other peripheral.

The RANGE_RACL_POLICY_SHADOWED registers are deliberately excluded from writes in
`chip_common_vseq`: random generic CSR writes to them can revoke RACL permissions, which
would make later TL accesses through the block return `d_error` and fail unrelated parts
of the test. All remaining AC Range Check registers, including RANGE_BASE, RANGE_LIMIT,
RANGE_ATTR, RANGE_REGWEN and the LOG_* registers, participate normally.

Checks:

- The registers read back their expected reset values and honor their access policies,
  including the RANGE_REGWEN write-enable relationship of the range configuration
  registers.
- TL-UL error conditions on the register interface behave as expected.

The features below are covered at the level of their configuration registers only: this
testpoint exercises the register interface through which each feature is programmed, not
the filtering behavior itself. AC_RANGE_CHECK.BYPASS is absent because it is controlled
by the chip input `ac_range_check_overwrite_i` and has no CSR.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_csr_aliasing-dragonfly">chip_csr_aliasing (dragonfly)</a><br><a href="03_test_report.md#chip_csr_bit_bash-dragonfly">chip_csr_bit_bash (dragonfly)</a><br><a href="03_test_report.md#chip_same_csr_outstanding-dragonfly">chip_same_csr_outstanding (dragonfly)</a><br><a href="03_test_report.md#chip_tl_errors-dragonfly">chip_tl_errors (dragonfly)</a></td>
  <td><a href="01_feature_report.md#ac_range_checkdeny_log">AC_RANGE_CHECK.DENY_LOG</a><br><a href="01_feature_report.md#ac_range_checkrangelock">AC_RANGE_CHECK.RANGE.LOCK</a><br><a href="01_feature_report.md#ac_range_checkrangematch">AC_RANGE_CHECK.RANGE.MATCH</a><br><a href="01_feature_report.md#ac_range_checkrangepermissions">AC_RANGE_CHECK.RANGE.PERMISSIONS</a><br><a href="01_feature_report.md#ac_range_checkrangepriority">AC_RANGE_CHECK.RANGE.PRIORITY</a><br><a href="01_feature_report.md#ac_range_checkrangeracl_policy">AC_RANGE_CHECK.RANGE.RACL_POLICY</a></td>
</tr>
  </tbody>
</table>
