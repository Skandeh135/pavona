# rv_dm Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="rv_dmdbgabstract_command">
      <td>RV_DM.DBG.ABSTRACT_COMMAND</td>
      <td>    The DMI registers abstractcs/command/abstractauto are    implemented.    Only the Access Register Command is implemented. </td>
    </tr>
    <tr id="rv_dmdbgdata_regs">
      <td>RV_DM.DBG.DATA_REGS</td>
      <td>     The DMI regs data0 and data1 are implemented. </td>
    </tr>
    <tr id="rv_dmdbgdmcontrol_reg">
      <td>RV_DM.DBG.DMCONTROL_REG</td>
      <td>     The DMI register dmcontrol is implemented. The following     optional fields have limited function or are not implemented:      - hartreset - Not implemented, writes ignored read zero      - hasel - HART masks not supported, writes ignored, read zero      - setresethaltreq - Not implemented, writes ignored read zero      - clrresethaltreq - Not implemented, writes ignored read zero </td>
    </tr>
    <tr id="rv_dmdbgdmstatus_reg">
      <td>RV_DM.DBG.DMSTATUS_REG</td>
      <td>     The DMI register dmstatus is implemented. As HART masks are not     supported the various allX/anyX register pairs are identical. </td>
    </tr>
    <tr id="rv_dmdbggdb">
      <td>RV_DM.DBG.GDB</td>
      <td>    The debug module will work with GDB connected via OpenOCD over    JTAG. In particular the following features will be functional    from GDB:      - Halting execution and resetting      - Setting, hitting and deleting breakpoints using all        available hardware breakpoints      - Single stepping      - Reading and writing all registers      - Reading and writing CSRs      - Reading and writing memory      - Setting the PC to jump to some location      - Executing code from GDB (using the call command) </td>
    </tr>
    <tr id="rv_dmdbghaltsum0_reg">
      <td>RV_DM.DBG.HALTSUM0_REG</td>
      <td>    The DMI register haltsum0 is implemented. </td>
    </tr>
    <tr id="rv_dmdbghartinfo_reg">
      <td>RV_DM.DBG.HARTINFO_REG</td>
      <td>    The DMI register hartinfo is implemented. </td>
    </tr>
    <tr id="rv_dmdbgndm_reset">
      <td>RV_DM.DBG.NDM_RESET</td>
      <td>    The debug module implements a non-debug reset, that resets the    whole system other than the debug module. It is controlled via    the DMI DMCONTROL register </td>
    </tr>
    <tr id="rv_dmdbgprogbuf">
      <td>RV_DM.DBG.PROGBUF</td>
      <td>    The DMI implements the program buffer, with all registers    progbuf0 - progbuf15 usable </td>
    </tr>
    <tr id="rv_dmdbgsba">
      <td>RV_DM.DBG.SBA</td>
      <td>    The DMI implements system bus access. sbdata0/sbdata1 and    sbaddress0/sbaddress1 are implemented. However as the data and    address bus with is 32-bits the second register of each has no    functionality but can still be read and written. </td>
    </tr>
    <tr id="rv_dmjtagdtm">
      <td>RV_DM.JTAG.DTM</td>
      <td>    A RISC-V DTM (debug transport module) is implemented accessible    via JTAG. In particular implements the dtmcs and dmi registers    specified in the RISC-V debug spec (along with standard JTAG TAP    registers). </td>
    </tr>
    <tr id="rv_dmjtagfsm">
      <td>RV_DM.JTAG.FSM</td>
      <td>   Full JTAG state machine is implemented including mandatory BYPASS   register and optional IDCODE register.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>RV_DM.JTAG.FSM</th>
    <th>RV_DM.JTAG.DTM</th>
    <th>RV_DM.DBG.DATA_REGS</th>
    <th>RV_DM.DBG.DMCONTROL_REG</th>
    <th>RV_DM.DBG.DMSTATUS_REG</th>
    <th>RV_DM.DBG.HARTINFO_REG</th>
    <th>RV_DM.DBG.HALTSUM0_REG</th>
    <th>RV_DM.DBG.ABSTRACT_COMMAND</th>
    <th>RV_DM.DBG.PROGBUF</th>
    <th>RV_DM.DBG.SBA</th>
    <th>RV_DM.DBG.NDM_RESET</th>
    <th>RV_DM.DBG.GDB</th>
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
    <th><a href="../theory_of_operation.md#memory-maps">Memory Maps</a></th>
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
    <th><a href="../theory_of_operation.md#tl-ul-device">TL-UL device</a></th>
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
    <th><a href="../theory_of_operation.md#debug-module-registers">Debug Module Registers</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#debug-module-registers">X</a></td>
    <td><a href="../theory_of_operation.md#debug-module-registers">X</a></td>
    <td><a href="../theory_of_operation.md#debug-module-registers">X</a></td>
    <td><a href="../theory_of_operation.md#debug-module-registers">X</a></td>
    <td><a href="../theory_of_operation.md#debug-module-registers">X</a></td>
    <td><a href="../theory_of_operation.md#debug-module-registers">X</a></td>
    <td><a href="../theory_of_operation.md#debug-module-registers">X</a></td>
    <td><a href="../theory_of_operation.md#debug-module-registers">X</a></td>
    <td><a href="../theory_of_operation.md#debug-module-registers">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#late-debug-enable-mechanism">Late Debug Enable Mechanism</a></th>
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
    <th><a href="../theory_of_operation.md#non-debug-module-reset-support">Non-debug Module Reset Support</a></th>
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
    <th>RV_DM.JTAG.FSM</th>
    <th>RV_DM.JTAG.DTM</th>
    <th>RV_DM.DBG.DATA_REGS</th>
    <th>RV_DM.DBG.DMCONTROL_REG</th>
    <th>RV_DM.DBG.DMSTATUS_REG</th>
    <th>RV_DM.DBG.HARTINFO_REG</th>
    <th>RV_DM.DBG.HALTSUM0_REG</th>
    <th>RV_DM.DBG.ABSTRACT_COMMAND</th>
    <th>RV_DM.DBG.PROGBUF</th>
    <th>RV_DM.DBG.SBA</th>
    <th>RV_DM.DBG.NDM_RESET</th>
    <th>RV_DM.DBG.GDB</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#jtag_dtm_csr_hw_reset">jtag_dtm_csr_hw_reset</a></th>
    <td><a href="02_testpoint_report.md#jtag_dtm_csr_hw_reset">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dtm_csr_hw_reset">X</a></td>
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
    <th><a href="02_testpoint_report.md#jtag_dtm_csr_rw">jtag_dtm_csr_rw</a></th>
    <td><a href="02_testpoint_report.md#jtag_dtm_csr_rw">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dtm_csr_rw">X</a></td>
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
    <th><a href="02_testpoint_report.md#jtag_dtm_csr_bit_bash">jtag_dtm_csr_bit_bash</a></th>
    <td><a href="02_testpoint_report.md#jtag_dtm_csr_bit_bash">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dtm_csr_bit_bash">X</a></td>
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
    <th><a href="02_testpoint_report.md#jtag_dtm_csr_aliasing">jtag_dtm_csr_aliasing</a></th>
    <td><a href="02_testpoint_report.md#jtag_dtm_csr_aliasing">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dtm_csr_aliasing">X</a></td>
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
    <th><a href="02_testpoint_report.md#jtag_dmi_csr_hw_reset">jtag_dmi_csr_hw_reset</a></th>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_hw_reset">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_hw_reset">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_hw_reset">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_hw_reset">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_hw_reset">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_hw_reset">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_hw_reset">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_hw_reset">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_hw_reset">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_hw_reset">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#jtag_dmi_csr_rw">jtag_dmi_csr_rw</a></th>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_rw">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_rw">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_rw">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_rw">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_rw">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_rw">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_rw">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_rw">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_rw">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_rw">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#jtag_dmi_csr_bit_bash">jtag_dmi_csr_bit_bash</a></th>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_bit_bash">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_bit_bash">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_bit_bash">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_bit_bash">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_bit_bash">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_bit_bash">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_bit_bash">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_bit_bash">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_bit_bash">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_bit_bash">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#jtag_dmi_csr_aliasing">jtag_dmi_csr_aliasing</a></th>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_aliasing">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_aliasing">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_aliasing">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_aliasing">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_aliasing">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_aliasing">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_aliasing">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_aliasing">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_aliasing">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_csr_aliasing">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#idcode">idcode</a></th>
    <td><a href="02_testpoint_report.md#idcode">X</a></td>
    <td><a href="02_testpoint_report.md#idcode">X</a></td>
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
    <th><a href="02_testpoint_report.md#jtag_dtm_hard_reset">jtag_dtm_hard_reset</a></th>
    <td><a href="02_testpoint_report.md#jtag_dtm_hard_reset">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dtm_hard_reset">X</a></td>
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
    <th><a href="02_testpoint_report.md#jtag_dtm_idle_hint">jtag_dtm_idle_hint</a></th>
    <td><a href="02_testpoint_report.md#jtag_dtm_idle_hint">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dtm_idle_hint">X</a></td>
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
    <th><a href="02_testpoint_report.md#jtag_dmi_failed_op">jtag_dmi_failed_op</a></th>
    <td><a href="02_testpoint_report.md#jtag_dmi_failed_op">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_failed_op">X</a></td>
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
    <th><a href="02_testpoint_report.md#jtag_dmi_dm_inactive">jtag_dmi_dm_inactive</a></th>
    <td><a href="02_testpoint_report.md#jtag_dmi_dm_inactive">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_dm_inactive">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_dm_inactive">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_dm_inactive">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_dm_inactive">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_dm_inactive">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_dm_inactive">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_dm_inactive">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_dm_inactive">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_dm_inactive">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#sba">sba</a></th>
    <td><a href="02_testpoint_report.md#sba">X</a></td>
    <td><a href="02_testpoint_report.md#sba">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#sba">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#bad_sba">bad_sba</a></th>
    <td><a href="02_testpoint_report.md#bad_sba">X</a></td>
    <td><a href="02_testpoint_report.md#bad_sba">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#bad_sba">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#sba_autoincrement">sba_autoincrement</a></th>
    <td><a href="02_testpoint_report.md#sba_autoincrement">X</a></td>
    <td><a href="02_testpoint_report.md#sba_autoincrement">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#sba_autoincrement">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#jtag_dmi_debug_disabled">jtag_dmi_debug_disabled</a></th>
    <td><a href="02_testpoint_report.md#jtag_dmi_debug_disabled">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_debug_disabled">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_debug_disabled">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_debug_disabled">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_debug_disabled">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_debug_disabled">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_debug_disabled">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_debug_disabled">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_debug_disabled">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_debug_disabled">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#sba_debug_disabled">sba_debug_disabled</a></th>
    <td><a href="02_testpoint_report.md#sba_debug_disabled">X</a></td>
    <td><a href="02_testpoint_report.md#sba_debug_disabled">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#sba_debug_disabled">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#ndmreset_req">ndmreset_req</a></th>
    <td><a href="02_testpoint_report.md#ndmreset_req">X</a></td>
    <td><a href="02_testpoint_report.md#ndmreset_req">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#ndmreset_req">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#ndmreset_req">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#hart_unavail">hart_unavail</a></th>
    <td><a href="02_testpoint_report.md#hart_unavail">X</a></td>
    <td><a href="02_testpoint_report.md#hart_unavail">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#hart_unavail">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#tap_ctrl_transitions">tap_ctrl_transitions</a></th>
    <td><a href="02_testpoint_report.md#tap_ctrl_transitions">X</a></td>
    <td><a href="02_testpoint_report.md#tap_ctrl_transitions">X</a></td>
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
    <th><a href="02_testpoint_report.md#jtag_dmi_cmderr_busy">jtag_dmi_cmderr_busy</a></th>
    <td><a href="02_testpoint_report.md#jtag_dmi_cmderr_busy">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_cmderr_busy">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_cmderr_busy">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#jtag_dmi_cmderr_not_supported">jtag_dmi_cmderr_not_supported</a></th>
    <td><a href="02_testpoint_report.md#jtag_dmi_cmderr_not_supported">X</a></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_cmderr_not_supported">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#jtag_dmi_cmderr_not_supported">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#cmderr_exception">cmderr_exception</a></th>
    <td><a href="02_testpoint_report.md#cmderr_exception">X</a></td>
    <td><a href="02_testpoint_report.md#cmderr_exception">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cmderr_exception">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cmderr_exception">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#mem_tl_access_resuming">mem_tl_access_resuming</a></th>
    <td><a href="02_testpoint_report.md#mem_tl_access_resuming">X</a></td>
    <td><a href="02_testpoint_report.md#mem_tl_access_resuming">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#mem_tl_access_resuming">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#mem_tl_access_resuming">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#mem_tl_access_halted">mem_tl_access_halted</a></th>
    <td><a href="02_testpoint_report.md#mem_tl_access_halted">X</a></td>
    <td><a href="02_testpoint_report.md#mem_tl_access_halted">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#mem_tl_access_halted">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#mem_tl_access_halted">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#cmderr_halt_resume">cmderr_halt_resume</a></th>
    <td><a href="02_testpoint_report.md#cmderr_halt_resume">X</a></td>
    <td><a href="02_testpoint_report.md#cmderr_halt_resume">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cmderr_halt_resume">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cmderr_halt_resume">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dataaddr_rw_access">dataaddr_rw_access</a></th>
    <td><a href="02_testpoint_report.md#dataaddr_rw_access">X</a></td>
    <td><a href="02_testpoint_report.md#dataaddr_rw_access">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dataaddr_rw_access">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#halt_resume">halt_resume</a></th>
    <td><a href="02_testpoint_report.md#halt_resume">X</a></td>
    <td><a href="02_testpoint_report.md#halt_resume">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#halt_resume">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#halt_resume">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#progbuf_busy">progbuf_busy</a></th>
    <td><a href="02_testpoint_report.md#progbuf_busy">X</a></td>
    <td><a href="02_testpoint_report.md#progbuf_busy">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#progbuf_busy">X</a></td>
    <td><a href="02_testpoint_report.md#progbuf_busy">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#abstractcmd_status">abstractcmd_status</a></th>
    <td><a href="02_testpoint_report.md#abstractcmd_status">X</a></td>
    <td><a href="02_testpoint_report.md#abstractcmd_status">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#abstractcmd_status">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#progbuf_read_write_execute">progbuf_read_write_execute</a></th>
    <td><a href="02_testpoint_report.md#progbuf_read_write_execute">X</a></td>
    <td><a href="02_testpoint_report.md#progbuf_read_write_execute">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#progbuf_read_write_execute">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#progbuf_read_write_execute">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#progbuf_exception">progbuf_exception</a></th>
    <td><a href="02_testpoint_report.md#progbuf_exception">X</a></td>
    <td><a href="02_testpoint_report.md#progbuf_exception">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#progbuf_exception">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#progbuf_exception">X</a></td>
    <td><a href="02_testpoint_report.md#progbuf_exception">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#rom_read_access">rom_read_access</a></th>
    <td><a href="02_testpoint_report.md#rom_read_access">X</a></td>
    <td><a href="02_testpoint_report.md#rom_read_access">X</a></td>
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
    <th><a href="02_testpoint_report.md#hartsel_warl">hartsel_warl</a></th>
    <td><a href="02_testpoint_report.md#hartsel_warl">X</a></td>
    <td><a href="02_testpoint_report.md#hartsel_warl">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#hartsel_warl">X</a></td>
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
    <th><a href="02_testpoint_report.md#stress_all">stress_all</a></th>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_jtag_csr_rw-dragonfly">chip_jtag_csr_rw (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_jtag_csr_rw-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_jtag_csr_rw-dragonfly">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_jtag_mem_access-dragonfly">chip_jtag_mem_access (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_jtag_mem_access-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_jtag_mem_access-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_jtag_mem_access-dragonfly">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_rv_dm_perform_debug-dragonfly">chip_rv_dm_perform_debug (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_rv_dm_perform_debug-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_rv_dm_perform_debug-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_rv_dm_perform_debug-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_rv_dm_ndm_reset_req-dragonfly">chip_rv_dm_ndm_reset_req (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_rv_dm_ndm_reset_req-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_rv_dm_ndm_reset_req-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_rv_dm_ndm_reset_req-dragonfly">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rv_dm_ndm_reset_req_when_cpu_halted-dragonfly">chip_sw_rv_dm_ndm_reset_req_when_cpu_halted (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_rv_dm_ndm_reset_req_when_cpu_halted-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_rv_dm_ndm_reset_req_when_cpu_halted-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rv_dm_ndm_reset_req_when_cpu_halted-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rv_dm_ndm_reset_req_when_cpu_halted-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rv_dm_ndm_reset_req_when_cpu_halted-dragonfly">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_rv_dm_access_after_wakeup-dragonfly">chip_rv_dm_access_after_wakeup (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_rv_dm_access_after_wakeup-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_rv_dm_access_after_wakeup-dragonfly">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_rv_dm_access_after_hw_reset-dragonfly">chip_sw_rv_dm_access_after_hw_reset (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_rv_dm_access_after_hw_reset-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_rv_dm_access_after_hw_reset-dragonfly">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_rv_dm_lc_disabled-dragonfly">chip_rv_dm_lc_disabled (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_rv_dm_lc_disabled-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_rv_dm_lc_disabled-dragonfly">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_jtag_csr_rw-egret">chip_jtag_csr_rw (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_jtag_csr_rw-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_jtag_csr_rw-egret">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_jtag_mem_access-egret">chip_jtag_mem_access (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_jtag_mem_access-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_jtag_mem_access-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_jtag_mem_access-egret">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_rv_dm_perform_debug-egret">chip_rv_dm_perform_debug (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_rv_dm_perform_debug-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_rv_dm_perform_debug-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_rv_dm_perform_debug-egret">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_rv_dm_ndm_reset_req-egret">chip_rv_dm_ndm_reset_req (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_rv_dm_ndm_reset_req-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_rv_dm_ndm_reset_req-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_rv_dm_ndm_reset_req-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_rv_dm_ndm_reset_req_when_cpu_halted-egret">chip_sw_rv_dm_ndm_reset_req_when_cpu_halted (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_rv_dm_ndm_reset_req_when_cpu_halted-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_rv_dm_ndm_reset_req_when_cpu_halted-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_rv_dm_ndm_reset_req_when_cpu_halted-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_rv_dm_access_after_wakeup-egret">chip_rv_dm_access_after_wakeup (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_rv_dm_access_after_wakeup-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_rv_dm_access_after_wakeup-egret">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_rv_dm_access_after_hw_reset-egret">chip_sw_rv_dm_access_after_hw_reset (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_rv_dm_access_after_hw_reset-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_rv_dm_access_after_hw_reset-egret">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_rv_dm_jtag_tap_sel-egret">chip_sw_rv_dm_jtag_tap_sel (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_rv_dm_jtag_tap_sel-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_rv_dm_jtag_tap_sel-egret">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_rv_dm_lc_disabled-egret">chip_rv_dm_lc_disabled (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_rv_dm_lc_disabled-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_rv_dm_lc_disabled-egret">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_rv_dm_jtag-egret">chip_rv_dm_jtag (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_rv_dm_jtag-egret">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_rv_dm_dtm-egret">chip_rv_dm_dtm (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_rv_dm_dtm-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_rv_dm_dtm-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_rv_dm_dtm-egret">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_rv_dm_dtm-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_rv_dm_control_status-egret">chip_rv_dm_control_status (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_rv_dm_control_status-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_rv_dm_control_status-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_rv_dm_control_status-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_rv_dm_control_status-egret">X</a></td>
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
