# soc_dbg_ctrl Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="soc_dbg_ctrlhaltfsm">
      <td>SOC_DBG_CTRL.HALT.FSM</td>
      <td>A sparse-encoded FSM sequences the early-boot halt decision based on:- Whether the current lifecycle state is RMA- Whether DFT debug is enabled by LC as a result of Volatile Raw Unlock- Whether the external `halt_cpu_boot_i` pin is asserted- Whether the JTAG command to stop the boot flow is assertedThe FSM has a single terminal state such that once the halt is released,Ibex cannot be re-halted without reset.</td>
    </tr>
    <tr id="soc_dbg_ctrlhaltproduction_passthrough">
      <td>SOC_DBG_CTRL.HALT.PRODUCTION_PASSTHROUGH</td>
      <td>In lifecycle states that are not RMA, the halt FSM bypasses the halt path,releasing Ibex unconditionally. The halt mechanism is therefore unreachable on productionparts: neither the `halt_cpu_boot` pin nor JTAG_CONTROL can wedge boot.</td>
    </tr>
    <tr id="soc_dbg_ctrlpolicylc_blank_override">
      <td>SOC_DBG_CTRL.POLICY.LC_BLANK_OVERRIDE</td>
      <td>For the `SocDbgStBlank` state, the policy will be 'locked' unless:- DFT is enabled by the lifecycle controller- Hardware debug is enabled by the lifecycle controllerIn which case, it will broadcast a Category 4 policy, with no software override.</td>
    </tr>
    <tr id="soc_dbg_ctrlpolicylc_preprod_override">
      <td>SOC_DBG_CTRL.POLICY.LC_PREPROD_OVERRIDE</td>
      <td>For the `SocDbgStPreProd` lifecycle controller state, the broadcast policyis always set to Category 4, with no software override.</td>
    </tr>
    <tr id="soc_dbg_ctrlpolicylc_rma_override">
      <td>SOC_DBG_CTRL.POLICY.LC_RMA_OVERRIDE</td>
      <td>During the `SocDbgStProd` state, the RMA state (if strictly true) will override thesoftware-assigned category and set the policy to Category 4.</td>
    </tr>
    <tr id="soc_dbg_ctrlpolicyrelock_reunlock">
      <td>SOC_DBG_CTRL.POLICY.RELOCK_REUNLOCK</td>
      <td>Firmware may set `DEBUG_POLICY_RELOCKED` to indicate that the debugger hasrelocked the part. This `relocked` field is broadcast in the policy bus alongside`category` and `valid`. This capability is only allowed for the `SocDbgStProd` state,when not in RMA and with the CPU running.</td>
    </tr>
    <tr id="soc_dbg_ctrlpolicysw_programmable">
      <td>SOC_DBG_CTRL.POLICY.SW_PROGRAMMABLE</td>
      <td>The firmware can program the broadcast debug category through the `DEBUG_POLICY_CATEGORY_SHADOWED`CSR. Its written value reaches the output bus only during the `SocDbgStProd` lifecycle state,when not in RMA state and with the CPU running.</td>
    </tr>
    <tr id="soc_dbg_ctrltraceauth_progress_mirroring">
      <td>SOC_DBG_CTRL.TRACE.AUTH_PROGRESS_MIRRORING</td>
      <td>The Root-of-Trust firmware reports the state of the debug authorization exchange in thecore-side `STATUS` CSR. This same CSR is mirrored through the `JTAG_STATUS` CSR, whichis surfaced so the external debugger can read the authorization progress.</td>
    </tr>
    <tr id="soc_dbg_ctrltracecore_policy_readback">
      <td>SOC_DBG_CTRL.TRACE.CORE_POLICY_READBACK</td>
      <td>The live broadcast debug policy (`category`, `valid`, `relocked`) is continuouslyreflected to RoT firmware through the read-only `TRACE_DEBUG_POLICY_CATEGORY` and`TRACE_DEBUG_POLICY_VALID_RELOCKED` CSRs on the core TL-UL interface.</td>
    </tr>
    <tr id="soc_dbg_ctrltracejtag_boot_status_gated_by_dft">
      <td>SOC_DBG_CTRL.TRACE.JTAG_BOOT_STATUS_GATED_BY_DFT</td>
      <td>The `JTAG_BOOT_STATUS` and `JTAG_TRACE_SOC_DBG_STATE` CSRs will only reflect thehardware state when `lc_dft_en` is strictly true. Otherwise, all the fields willread as zero.</td>
    </tr>
    <tr id="soc_dbg_ctrltracejtag_policy_readback">
      <td>SOC_DBG_CTRL.TRACE.JTAG_POLICY_READBACK</td>
      <td>The live broadcast debug policy (`category`, `valid`, `relocked`) is reflected to theexternal debugger through the read-only `JTAG_TRACE_DEBUG_POLICY_CATEGORY` and`JTAG_TRACE_DEBUG_POLICY_VALID_RELOCKED` CSRs on the JTAG TL-UL interface.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>SOC_DBG_CTRL.POLICY.SW_PROGRAMMABLE</th>
    <th>SOC_DBG_CTRL.POLICY.LC_RMA_OVERRIDE</th>
    <th>SOC_DBG_CTRL.POLICY.LC_BLANK_OVERRIDE</th>
    <th>SOC_DBG_CTRL.POLICY.LC_PREPROD_OVERRIDE</th>
    <th>SOC_DBG_CTRL.POLICY.RELOCK_REUNLOCK</th>
    <th>SOC_DBG_CTRL.TRACE.CORE_POLICY_READBACK</th>
    <th>SOC_DBG_CTRL.TRACE.JTAG_POLICY_READBACK</th>
    <th>SOC_DBG_CTRL.TRACE.JTAG_BOOT_STATUS_GATED_BY_DFT</th>
    <th>SOC_DBG_CTRL.TRACE.AUTH_PROGRESS_MIRRORING</th>
    <th>SOC_DBG_CTRL.HALT.FSM</th>
    <th>SOC_DBG_CTRL.HALT.PRODUCTION_PASSTHROUGH</th>
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
    <th><a href="../theory_of_operation.md#soc_dbg_state">SOC_DBG_STATE</a></th>
    <td><a href="../theory_of_operation.md#soc_dbg_state">X</a></td>
    <td><a href="../theory_of_operation.md#soc_dbg_state">X</a></td>
    <td><a href="../theory_of_operation.md#soc_dbg_state">X</a></td>
    <td><a href="../theory_of_operation.md#soc_dbg_state">X</a></td>
    <td><a href="../theory_of_operation.md#soc_dbg_state">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#socdbgstblank">SocDbgStBlank</a></th>
    <td><a href="../theory_of_operation.md#socdbgstblank">X</a></td>
    <td><a href="../theory_of_operation.md#socdbgstblank">X</a></td>
    <td><a href="../theory_of_operation.md#socdbgstblank">X</a></td>
    <td><a href="../theory_of_operation.md#socdbgstblank">X</a></td>
    <td><a href="../theory_of_operation.md#socdbgstblank">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#socdbgstpreprod">SocDbgStPreProd</a></th>
    <td><a href="../theory_of_operation.md#socdbgstpreprod">X</a></td>
    <td><a href="../theory_of_operation.md#socdbgstpreprod">X</a></td>
    <td><a href="../theory_of_operation.md#socdbgstpreprod">X</a></td>
    <td><a href="../theory_of_operation.md#socdbgstpreprod">X</a></td>
    <td><a href="../theory_of_operation.md#socdbgstpreprod">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#socdbgstprod">SocDbgStProd</a></th>
    <td><a href="../theory_of_operation.md#socdbgstprod">X</a></td>
    <td><a href="../theory_of_operation.md#socdbgstprod">X</a></td>
    <td><a href="../theory_of_operation.md#socdbgstprod">X</a></td>
    <td><a href="../theory_of_operation.md#socdbgstprod">X</a></td>
    <td><a href="../theory_of_operation.md#socdbgstprod">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#csr-tracing">CSR Tracing</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#csr-tracing">X</a></td>
    <td><a href="../theory_of_operation.md#csr-tracing">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#lc_dft_en-gating">LC_DFT_EN Gating</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#lc_dft_en-gating">X</a></td>
    <td><a href="../theory_of_operation.md#lc_dft_en-gating">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#ibex-halting">Ibex Halting</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#ibex-halting">X</a></td>
    <td><a href="../theory_of_operation.md#ibex-halting">X</a></td>
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
    <th>SOC_DBG_CTRL.POLICY.SW_PROGRAMMABLE</th>
    <th>SOC_DBG_CTRL.POLICY.LC_RMA_OVERRIDE</th>
    <th>SOC_DBG_CTRL.POLICY.LC_BLANK_OVERRIDE</th>
    <th>SOC_DBG_CTRL.POLICY.LC_PREPROD_OVERRIDE</th>
    <th>SOC_DBG_CTRL.POLICY.RELOCK_REUNLOCK</th>
    <th>SOC_DBG_CTRL.TRACE.CORE_POLICY_READBACK</th>
    <th>SOC_DBG_CTRL.TRACE.JTAG_POLICY_READBACK</th>
    <th>SOC_DBG_CTRL.TRACE.JTAG_BOOT_STATUS_GATED_BY_DFT</th>
    <th>SOC_DBG_CTRL.TRACE.AUTH_PROGRESS_MIRRORING</th>
    <th>SOC_DBG_CTRL.HALT.FSM</th>
    <th>SOC_DBG_CTRL.HALT.PRODUCTION_PASSTHROUGH</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
  </tr>
</table>
</div>
</div>
