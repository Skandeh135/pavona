# soc_dbg_ctrl Testpoint Report

## smoke

This test exercises the main policy datapath, the core-to-JTAG status mirror,
and the early-boot halt FSM end-to-end through both the core and JTAG register
interfaces.

Stimulus:

- Initial state:
  - `soc_dbg_state_i = SocDbgStProd`
  - `lc_cpu_en = On`
  - `lc_rma_state = Off`
  - `lc_raw_test_rma = On`
  - `lc_dft_en = Off`
  - `halt_cpu_boot_i = 1'b1`
  - `boot_status.lc_done = 1'b1`
- Repeat the following steps a random number of times (5 to 20):
  - Write a random `dbg_category_e` value to `DEBUG_POLICY_CATEGORY_SHADOWED`
    over the core interface. On the first iteration, set `DEBUG_POLICY_VALID_SHADOWED`
    to `MuBi4True` after a random delay so the category register locks; later
    iterations continue to issue writes to exercise the write-gating.
  - Read the four trace registers (two core-side, two JTAG-side) in interleaved order
    with random inter-access delays.
  - Write a random `MuBi4` value to `DEBUG_POLICY_RELOCKED` and read the `relocked` field
    over both interfaces.
  - Write random 5-bit patterns to the core-side `STATUS` and read `JTAG_STATUS`.
- After the loop, pick one of the two halt-release paths at random:
  - Halt-pin path: de-assert `halt_cpu_boot_i`, wait, then assert `lc_dft_en`.
  - JTAG-release path: keep `halt_cpu_boot_i` asserted, assert `lc_dft_en = On`, wait
    for the FSM to reach `CheckJtagGo`, then write `JTAG_CONTROL.boot_continue = 1`
    after a random delay.

Checks:

- Each pair of core/JTAG trace readbacks must be identical to each other and match
  the most recent write that should be honored by policy decode.
- `JTAG_STATUS` matches most recent `STATUS` write.
- `continue_cpu_boot_o.done` is `MuBi4False` before the release trigger and transitions
  to `MuBi4True` after the selected release path completes.
- No alerts are raised.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#soc_dbg_ctrl_smoke">soc_dbg_ctrl_smoke</a></td>
  <td><a href="01_feature_report.md#soc_dbg_ctrlhaltfsm">SOC_DBG_CTRL.HALT.FSM</a><br><a href="01_feature_report.md#soc_dbg_ctrlpolicyrelock_reunlock">SOC_DBG_CTRL.POLICY.RELOCK_REUNLOCK</a><br><a href="01_feature_report.md#soc_dbg_ctrlpolicysw_programmable">SOC_DBG_CTRL.POLICY.SW_PROGRAMMABLE</a><br><a href="01_feature_report.md#soc_dbg_ctrltraceauth_progress_mirroring">SOC_DBG_CTRL.TRACE.AUTH_PROGRESS_MIRRORING</a><br><a href="01_feature_report.md#soc_dbg_ctrltracecore_policy_readback">SOC_DBG_CTRL.TRACE.CORE_POLICY_READBACK</a><br><a href="01_feature_report.md#soc_dbg_ctrltracejtag_boot_status_gated_by_dft">SOC_DBG_CTRL.TRACE.JTAG_BOOT_STATUS_GATED_BY_DFT</a><br><a href="01_feature_report.md#soc_dbg_ctrltracejtag_policy_readback">SOC_DBG_CTRL.TRACE.JTAG_POLICY_READBACK</a></td>
</tr>
  </tbody>
</table>
