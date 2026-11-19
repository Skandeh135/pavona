# lc_ctrl Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="lc_ctrlaccessext_clk">
      <td>LC_CTRL.ACCESS.EXT_CLK</td>
      <td>The lifecycle controller supports switching to an external clock source via a CSRinterface.</td>
    </tr>
    <tr id="lc_ctrlaccessjtag">
      <td>LC_CTRL.ACCESS.JTAG</td>
      <td>Lifecycle controller CSRs are accessible via a dedicated JTAG interface, supportingmanufacturing life cycle transitions and RMA flows. The CSRs support a hardware mutexto arbitrate access through the JTAG interface versus from the TL-UL bus.</td>
    </tr>
    <tr id="lc_ctrlauthenticated_transitions">
      <td>LC_CTRL.AUTHENTICATED_TRANSITIONS</td>
      <td>The following transitions require an user provided token, which is verified againsta pre-hashed image stored in OTP: 1) Transition from `RAW` into `TEST_UNLOCKED0` state,2) Transition from any `TEST_LOCKED` state into a `TEST_UNLOCKED` state, 3) Transitionfrom any `TEST_UNLOCKED` state into `PROD`, `DEV` or `PROD_END` states; or 4)Transition into `RMA` state.</td>
    </tr>
    <tr id="lc_ctrllogical_scrap">
      <td>LC_CTRL.LOGICAL_SCRAP</td>
      <td>The lifecycle controller supports escalating to a logical scrap state as part ofalert escalations. The life cycle can be reverted to the configured state byperforming a hard reset.</td>
    </tr>
    <tr id="lc_ctrlstatedev">
      <td>LC_CTRL.STATE.DEV</td>
      <td>This state is used to develop provisioning and mission mode software. It can alsobe used to debug software via `rv_dm`. All other debug functionality is disabled. Thekey manager (`keymgr`) is enabled. This is a mutually exclusive state to `PROD` and`PROD_END`.Entry into `DEV` from any `TEST_UNLOCKED` state requires a valid test exit token whichneeds to be provisioned in a `TEST_UNLOCKED` state.</td>
    </tr>
    <tr id="lc_ctrlstateprod">
      <td>LC_CTRL.STATE.PROD</td>
      <td>This state state is used both for provisioning and mission mode. CPU execution andall debug functionality is disabled. The key manager (`keymgr`) is enabled. This is amutually exclusive state to `DEV` and `PROD_END`.Entry into `PROD` from any `TEST_UNLOCKED` state requires a valid test exit token whichneeds to be provisioned in a `TEST_UNLOCKED` state.</td>
    </tr>
    <tr id="lc_ctrlstateprod_end">
      <td>LC_CTRL.STATE.PROD_END</td>
      <td>This state is used both for provisioning and mission mode. This state is logicallyequivalent to `PROD`, with the only difference being that transitions from this stateto `RMA` are not allowed.</td>
    </tr>
    <tr id="lc_ctrlstateraw">
      <td>LC_CTRL.STATE.RAW</td>
      <td>Initial state. No functions other than transition to `TEST_UNLOCKED0` are available.</td>
    </tr>
    <tr id="lc_ctrlstaterma">
      <td>LC_CTRL.STATE.RMA</td>
      <td>This state is logically equivalent to `TEST_UNLOCKED`. It can be entered from anymission mode state (`DEV`, `PROD` and `PROD_END`) states using an authenticationtoken provisioned at manufacturing time by the Silicon Creator.</td>
    </tr>
    <tr id="lc_ctrlstatescrap">
      <td>LC_CTRL.STATE.SCRAP</td>
      <td>This state is logically equivalent to `RAW` state, with the following exceptions:1) `SCRAP` is a final state; and, 2) Life cycle JTAG interface is disabled uponsuccessful entry into this state.</td>
    </tr>
    <tr id="lc_ctrlstatetest_locked">
      <td>LC_CTRL.STATE.TEST_LOCKED</td>
      <td>This state is logically equivalent to `RAW`, where only transitions to`TEST_UNLOCKED` states are available. The transition requires a test unlock token whichneeds to be provisioned in the `TEST_UNLOCKED0` state.</td>
    </tr>
    <tr id="lc_ctrlstatetest_unlocked">
      <td>LC_CTRL.STATE.TEST_UNLOCKED</td>
      <td>State used for manufacturing and production testing. CPU execution and all debugfunctionality is enabled in this state. The key manager (`keymgr`) is disabled.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>LC_CTRL.STATE.RAW</th>
    <th>LC_CTRL.STATE.TEST_UNLOCKED</th>
    <th>LC_CTRL.STATE.TEST_LOCKED</th>
    <th>LC_CTRL.STATE.DEV</th>
    <th>LC_CTRL.STATE.PROD</th>
    <th>LC_CTRL.STATE.PROD_END</th>
    <th>LC_CTRL.STATE.RMA</th>
    <th>LC_CTRL.STATE.SCRAP</th>
    <th>LC_CTRL.ACCESS.JTAG</th>
    <th>LC_CTRL.ACCESS.EXT_CLK</th>
    <th>LC_CTRL.AUTHENTICATED_TRANSITIONS</th>
    <th>LC_CTRL.LOGICAL_SCRAP</th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#life-cycle-state-overview">Life Cycle State Overview</a></th>
    <td><a href="../theory_of_operation.md#life-cycle-state-overview">X</a></td>
    <td><a href="../theory_of_operation.md#life-cycle-state-overview">X</a></td>
    <td><a href="../theory_of_operation.md#life-cycle-state-overview">X</a></td>
    <td><a href="../theory_of_operation.md#life-cycle-state-overview">X</a></td>
    <td><a href="../theory_of_operation.md#life-cycle-state-overview">X</a></td>
    <td><a href="../theory_of_operation.md#life-cycle-state-overview">X</a></td>
    <td><a href="../theory_of_operation.md#life-cycle-state-overview">X</a></td>
    <td><a href="../theory_of_operation.md#life-cycle-state-overview">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#power-up-sequence">Power Up Sequence</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#normal-operation">Normal Operation</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#unconditional-transitions">Unconditional Transitions</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#conditional-transitions">Conditional Transitions</a></th>
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
    <td><a href="../theory_of_operation.md#conditional-transitions">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#transition-counter-limits">Transition Counter Limits</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#token-hashing-mechanism">Token Hashing Mechanism</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#post-transition-handling">Post Transition Handling</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#security-escalation">Security Escalation</a></th>
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
    <td><a href="../theory_of_operation.md#security-escalation">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#life-cycle-decoded-outputs-and-controls">Life Cycle Decoded Outputs and Controls</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#life-cycle-function-control-signals">Life Cycle Function Control Signals</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#dft_en">DFT_EN</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#nvm_debug_en">NVM_DEBUG_EN</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#hw_debug_en">HW_DEBUG_EN</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#cpu_en">CPU_EN</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#key_manager_en">KEY_MANAGER_EN</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#escalate_en">ESCALATE_EN</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#check_byp_en">CHECK_BYP_EN</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#clk_byp_req">CLK_BYP_REQ</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#clk_byp_req">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#life-cycle-access-control-signals">Life Cycle Access Control Signals</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#creator_seed_sw_rw_en-and-owner_seed_sw_rw_en">CREATOR_SEED_SW_RW_EN and OWNER_SEED_SW_RW_EN</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#seed_hw_rd_en">SEED_HW_RD_EN</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#rma_state">RMA_STATE</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#iso_part_sw_rd_en-and-iso_part_sw_wr_en">ISO_PART_SW_RD_EN and ISO_PART_SW_WR_EN</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#otp-collateral">OTP Collateral</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#id-state-of-the-device">ID State of the Device</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#secret-collateral">Secret Collateral</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#otp-accessibility-summary-and-impact-of-life-cycle-signals">OTP Accessibility Summary and Impact of Life Cycle Signals</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#flash-collateral">Flash Collateral</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#flash-accessibility-summary-and-impact-of-life-cycle-signals">Flash Accessibility Summary and Impact of Life Cycle Signals</a></th>
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
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#system-integration-and-tap-isolation">System Integration and TAP Isolation</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#life-cycle-manufacturing-state-encodings">Life Cycle Manufacturing State Encodings</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#life-cycle-readout-consistency-checks-in-otp">Life Cycle Readout Consistency Checks in OTP</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#transition-counter-encoding">Transition Counter Encoding</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#life-cycle-state-controller">Life Cycle State Controller</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#escalation-handling">Escalation Handling</a></th>
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
    <td><a href="../theory_of_operation.md#escalation-handling">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#fsm-glitch-countermeasures">FSM Glitch Countermeasures</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#life-cycle-request-interface">Life Cycle Request Interface</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#life-cycle-request-interface">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#vendor-specific-test-control-register">Vendor-specific Test Control Register</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#tap-construction-and-isolation">TAP Construction and Isolation</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#life-cycle-tap-controller">Life Cycle TAP Controller</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#tap-and-isolation">TAP and Isolation</a></th>
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
    <th>LC_CTRL.STATE.RAW</th>
    <th>LC_CTRL.STATE.TEST_UNLOCKED</th>
    <th>LC_CTRL.STATE.TEST_LOCKED</th>
    <th>LC_CTRL.STATE.DEV</th>
    <th>LC_CTRL.STATE.PROD</th>
    <th>LC_CTRL.STATE.PROD_END</th>
    <th>LC_CTRL.STATE.RMA</th>
    <th>LC_CTRL.STATE.SCRAP</th>
    <th>LC_CTRL.ACCESS.JTAG</th>
    <th>LC_CTRL.ACCESS.EXT_CLK</th>
    <th>LC_CTRL.AUTHENTICATED_TRANSITIONS</th>
    <th>LC_CTRL.LOGICAL_SCRAP</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#state_post_trans">state_post_trans</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#regwen_during_op">regwen_during_op</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#rand_wr_claim_transition_if">rand_wr_claim_transition_if</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#lc_prog_failure">lc_prog_failure</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#lc_state_failure">lc_state_failure</a></th>
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
    <td><a href="02_testpoint_report.md#lc_state_failure">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#lc_errors">lc_errors</a></th>
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
    <td><a href="02_testpoint_report.md#lc_errors">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#security_escalation">security_escalation</a></th>
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
    <td><a href="02_testpoint_report.md#security_escalation">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#jtag_access">jtag_access</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#jtag_access">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#jtag_priority">jtag_priority</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#jtag_priority">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#lc_ctrl_volatile_unlock">lc_ctrl_volatile_unlock</a></th>
    <td><a href="02_testpoint_report.md#lc_ctrl_volatile_unlock">X</a></td>
    <td><a href="02_testpoint_report.md#lc_ctrl_volatile_unlock">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#lc_ctrl_volatile_unlock">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#lc_ctrl_volatile_unlock">X</a></td>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_alert_handler_escalation-dragonfly">chip_sw_lc_ctrl_alert_handler_escalation (dragonfly)</a></th>
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
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_alert_handler_escalation-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_jtag_access-dragonfly">chip_sw_lc_ctrl_jtag_access (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_jtag_access-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_jtag_access-dragonfly">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_otp_hw_cfg0-dragonfly">chip_sw_lc_ctrl_otp_hw_cfg0 (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_otp_hw_cfg0-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_init-dragonfly">chip_sw_lc_ctrl_init (dragonfly)</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_transitions-dragonfly">chip_sw_lc_ctrl_transitions (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_transitions-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_transitions-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_transitions-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_transitions-dragonfly">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_kmac_req-dragonfly">chip_sw_lc_ctrl_kmac_req (dragonfly)</a></th>
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
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_kmac_req-dragonfly">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_key_div-dragonfly">chip_sw_lc_ctrl_key_div (dragonfly)</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_broadcast-dragonfly">chip_sw_lc_ctrl_broadcast (dragonfly)</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_kmac_error-dragonfly">chip_sw_lc_ctrl_kmac_error (dragonfly)</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_lc_scrap-dragonfly">chip_lc_scrap (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_lc_scrap-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_lc_test_locked-dragonfly">chip_lc_test_locked (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_lc_test_locked-dragonfly">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_lc_walkthrough-dragonfly">chip_sw_lc_walkthrough (dragonfly)</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_volatile_raw_unlock-dragonfly">chip_sw_lc_ctrl_volatile_raw_unlock (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_volatile_raw_unlock-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_volatile_raw_unlock-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_volatile_raw_unlock-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_volatile_raw_unlock-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_volatile_raw_unlock-dragonfly">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_debug_access-dragonfly">chip_sw_lc_ctrl_debug_access (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_debug_access-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_debug_access-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_debug_access-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_debug_access-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_debug_access-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_debug_access-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_debug_access-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_debug_access-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_alert_handler_escalation-egret">chip_sw_lc_ctrl_alert_handler_escalation (egret)</a></th>
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
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_alert_handler_escalation-egret">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_jtag_access-egret">chip_sw_lc_ctrl_jtag_access (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_jtag_access-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_jtag_access-egret">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_otp_hw_cfg0-egret">chip_sw_lc_ctrl_otp_hw_cfg0 (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_otp_hw_cfg0-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_init-egret">chip_sw_lc_ctrl_init (egret)</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_transitions-egret">chip_sw_lc_ctrl_transitions (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_transitions-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_transitions-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_transitions-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_transitions-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_kmac_req-egret">chip_sw_lc_ctrl_kmac_req (egret)</a></th>
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
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_kmac_req-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_key_div-egret">chip_sw_lc_ctrl_key_div (egret)</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_broadcast-egret">chip_sw_lc_ctrl_broadcast (egret)</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_kmac_error-egret">chip_sw_lc_ctrl_kmac_error (egret)</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_lc_scrap-egret">chip_lc_scrap (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_lc_scrap-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_lc_test_locked-egret">chip_lc_test_locked (egret)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_lc_test_locked-egret">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_lc_walkthrough-egret">chip_sw_lc_walkthrough (egret)</a></th>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_volatile_raw_unlock-egret">chip_sw_lc_ctrl_volatile_raw_unlock (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_volatile_raw_unlock-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_volatile_raw_unlock-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_volatile_raw_unlock-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_volatile_raw_unlock-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_volatile_raw_unlock-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_lc_ctrl_debug_access-egret">chip_sw_lc_ctrl_debug_access (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_debug_access-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_debug_access-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_debug_access-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_debug_access-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_debug_access-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_debug_access-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_debug_access-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_lc_ctrl_debug_access-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>
</div>
</div>
