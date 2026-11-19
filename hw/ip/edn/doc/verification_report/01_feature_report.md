# edn Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="ednbus_cmp_alert">
      <td>EDN.BUS_CMP_ALERT</td>
      <td>Entropy bits subsequently received from CSRNG are compared to each other.In case two values match, a recoverable alert is signaled and the !!RECOV_ALERT_STS.EDN_BUS_CMP_ALERT bit is set.</td>
    </tr>
    <tr id="ednmodeauto">
      <td>EDN.MODE.AUTO</td>
      <td>The purpose of the auto request mode is to continuously deliver entropy to consuming endpoints after the system has booted.To this end, EDN keeps replaying a sequence of `generate` and `reseed` commands, which can optionally come with additional data, provided by firmware via the !!RESEED_CMD and !!GENERATE_CMD registers, respectively.The first `instantiate` command must be provided by firmware through the !!SW_CMD_REQ register.</td>
    </tr>
    <tr id="ednmodeboot">
      <td>EDN.MODE.BOOT</td>
      <td>In boot-time request mode, EDN plays a fully hardware-controlled and fixed command sequence consisting of a single `instantiate` and a single `generate` command but no `reseed` commands.EDN delivers a fixed amount of entropy only in this mode (4K 128-bit blocks).</td>
    </tr>
    <tr id="ednmodesw">
      <td>EDN.MODE.SW</td>
      <td>In software port mode, EDN is fully software controlled.It will play any commands provided by firmware via the !!SW_CMD_REQ register.Firmware should check the !!SW_CMD_STS register to see if the command interface is ready before issuing a new command, and whether the command completed successfully afterwards.</td>
    </tr>
    <tr id="edntrack_seed_compliance">
      <td>EDN.TRACK_SEED_COMPLIANCE</td>
      <td>The entropy complex modules, including EDN, track whether seeds or the entropy bits generated using those seeds have been derived from FIPS/CC compliant entropy.EDN forwards this information to entropy consuming endpoints alongside the delivered entropy bits using the `edn_fips` bit.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>EDN.MODE.BOOT</th>
    <th>EDN.MODE.AUTO</th>
    <th>EDN.MODE.SW</th>
    <th>EDN.TRACK_SEED_COMPLIANCE</th>
    <th>EDN.BUS_CMP_ALERT</th>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#theory-of-operation">Theory of Operation</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#interaction-with-csrng-application-interface-ports">Interaction with CSRNG Application Interface Ports</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#interaction-with-csrng-application-interface-ports">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#boot-time-request-mode">Boot-time Request Mode</a></th>
    <td><a href="../theory_of_operation.md#boot-time-request-mode">X</a></td>
    <td></td>
    <td><a href="../theory_of_operation.md#boot-time-request-mode">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#note-on-security-considerations-when-using-boot-time-request-mode">Note on Security Considerations when Using Boot-time Request Mode</a></th>
    <td><a href="../theory_of_operation.md#note-on-security-considerations-when-using-boot-time-request-mode">X</a></td>
    <td></td>
    <td><a href="../theory_of_operation.md#note-on-security-considerations-when-using-boot-time-request-mode">X</a></td>
    <td><a href="../theory_of_operation.md#note-on-security-considerations-when-using-boot-time-request-mode">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#multiple-edns-in-boot-time-request-mode">Multiple EDNs in Boot-time Request Mode</a></th>
    <td><a href="../theory_of_operation.md#multiple-edns-in-boot-time-request-mode">X</a></td>
    <td></td>
    <td><a href="../theory_of_operation.md#multiple-edns-in-boot-time-request-mode">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#auto-request-mode">Auto Request Mode</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#auto-request-mode">X</a></td>
    <td><a href="../theory_of_operation.md#auto-request-mode">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#note-on-state-machine-shutdown-delays">Note on State Machine Shutdown Delays</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#note-on-sharing-of-csrng-instance-state-variables">Note on Sharing of CSRNG Instance State Variables</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#interactions-with-peripheral-devices">Interactions with Peripheral Devices</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#interactions-with-peripheral-devices">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#entropy-bus-comparison">Entropy Bus Comparison</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#entropy-bus-comparison">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#block-diagram">Block Diagram</a></th>
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
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#edn-initialization">EDN Initialization</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#waveforms">Waveforms</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#peripheral-hardware-interface---reqack">Peripheral Hardware Interface - Req/Ack</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#peripheral-hardware-interface---reqack">X</a></td>
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
    <th>EDN.MODE.BOOT</th>
    <th>EDN.MODE.AUTO</th>
    <th>EDN.MODE.SW</th>
    <th>EDN.TRACK_SEED_COMPLIANCE</th>
    <th>EDN.BUS_CMP_ALERT</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#firmware">firmware</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#firmware">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#csrng_commands">csrng_commands</a></th>
    <td><a href="02_testpoint_report.md#csrng_commands">X</a></td>
    <td><a href="02_testpoint_report.md#csrng_commands">X</a></td>
    <td><a href="02_testpoint_report.md#csrng_commands">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#genbits">genbits</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#genbits">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#interrupts">interrupts</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#alerts">alerts</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#alerts">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#errs">errs</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#disable">disable</a></th>
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
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_edn_entropy_reqs-dragonfly">chip_sw_edn_entropy_reqs (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_edn_boot_mode-dragonfly">chip_sw_edn_boot_mode (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_edn_boot_mode-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_edn_boot_mode-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_edn_boot_mode-dragonfly">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_edn_auto_mode-dragonfly">chip_sw_edn_auto_mode (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_edn_auto_mode-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_edn_sw_mode-dragonfly">chip_sw_edn_sw_mode (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_edn_sw_mode-dragonfly">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_edn_kat-dragonfly">chip_sw_edn_kat (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_edn_kat-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_edn_kat-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_edn_entropy_reqs-egret">chip_sw_edn_entropy_reqs (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_edn_boot_mode-egret">chip_sw_edn_boot_mode (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_edn_boot_mode-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_edn_boot_mode-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_edn_boot_mode-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_edn_auto_mode-egret">chip_sw_edn_auto_mode (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_edn_auto_mode-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_edn_sw_mode-egret">chip_sw_edn_sw_mode (egret)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_edn_sw_mode-egret">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_edn_kat-egret">chip_sw_edn_kat (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_edn_kat-egret">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_edn_kat-egret">X</a></td>
  </tr>
</table>
</div>
</div>
