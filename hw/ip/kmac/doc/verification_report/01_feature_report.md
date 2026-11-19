# kmac Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="kmacendiannessdigest">
      <td>KMAC.ENDIANNESS.DIGEST</td>
      <td>Configurable output digest endianness.</td>
    </tr>
    <tr id="kmacendiannessmessage">
      <td>KMAC.ENDIANNESS.MESSAGE</td>
      <td>Configurable input message endianness.</td>
    </tr>
    <tr id="kmacentropy_modes">
      <td>KMAC.ENTROPY_MODES</td>
      <td>Entropy required for countermeasures can be configured to be provided by software orEDN. In EDN mode, KMAC can be configured to set an error flag if entropy is notprovided within a configurable time window. The cadence of entropy requested from EDNis also configurable.</td>
    </tr>
    <tr id="kmackeysideload">
      <td>KMAC.KEY.SIDELOAD</td>
      <td>Key can be loaded directly from the keymgr.</td>
    </tr>
    <tr id="kmacmodecshake">
      <td>KMAC.MODE.CSHAKE</td>
      <td>cSHAKE hashing algorithm supporting the following security strength configurations:cSHAKE128, and cSHAKE256. Compliant with NIST SP 800-185.</td>
    </tr>
    <tr id="kmacmodekmac">
      <td>KMAC.MODE.KMAC</td>
      <td>KMAC Keccak Message Authentication Code supporting the following security strengthconfigurations: KMAC128, KMAC256. Compliant with NIST SP 800-185.</td>
    </tr>
    <tr id="kmacmodesha3">
      <td>KMAC.MODE.SHA3</td>
      <td>SHA3 hashing algorithm supporting the following security strength configurations:SHA3-224, SHA3-256, SHA3-384, and SHA3-512. Compliant with NIST FIPS 202.</td>
    </tr>
    <tr id="kmacmodeshake">
      <td>KMAC.MODE.SHAKE</td>
      <td>SHAKE hashing algorithm supporting the following security strength configurations:SHAKE128, and SHAKE256. Compliant with NIST FIPS 202.</td>
    </tr>
    <tr id="kmacmodexof">
      <td>KMAC.MODE.XOF</td>
      <td>SHAKE, cSHAKE and KMAC modes of operation support eXtendable-Output Format (XOF)as specified in NIST SP 800-185.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>KMAC.MODE.SHA3</th>
    <th>KMAC.MODE.SHAKE</th>
    <th>KMAC.MODE.CSHAKE</th>
    <th>KMAC.MODE.KMAC</th>
    <th>KMAC.MODE.XOF</th>
    <th>KMAC.ENDIANNESS.MESSAGE</th>
    <th>KMAC.ENDIANNESS.DIGEST</th>
    <th>KMAC.KEY.SIDELOAD</th>
    <th>KMAC.ENTROPY_MODES</th>
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
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#block-diagram">Block Diagram</a></th>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td></td>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
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
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#keccak-round">Keccak Round</a></th>
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
    <th><a href="../theory_of_operation.md#padding-for-keccak">Padding for Keccak</a></th>
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
    <th><a href="../theory_of_operation.md#padding-for-kmac">Padding for KMAC</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#padding-for-kmac">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#message-fifo">Message FIFO</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#message-fifo">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#fifo-depth-calculation">FIFO Depth calculation</a></th>
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
    <th><a href="../theory_of_operation.md#empty-and-full-status">Empty and Full status</a></th>
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
    <th><a href="../theory_of_operation.md#masking">Masking</a></th>
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
    <th><a href="../theory_of_operation.md#keccak-state-access">Keccak State Access</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#keccak-state-access">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#application-interface">Application Interface</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#application-interface">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#acc-interface-connection">ACC Interface Connection</a></th>
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
    <th><a href="../theory_of_operation.md#entropy-generator">Entropy Generator</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#entropy-generator">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#error-report">Error Report</a></th>
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
    <th><a href="../theory_of_operation.md#keynotvalid-0x01">KeyNotValid (0x01)</a></th>
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
    <th><a href="../theory_of_operation.md#swpushedmsgfifo-0x02">SwPushedMsgFifo (0x02)</a></th>
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
    <th><a href="../theory_of_operation.md#swissuedcmdinappactive-0x03">SwIssuedCmdInAppActive (0x03)</a></th>
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
    <th><a href="../theory_of_operation.md#waittimerexpired-0x04">WaitTimerExpired (0x04)</a></th>
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
    <th><a href="../theory_of_operation.md#incorrectentropymode-0x05">IncorrectEntropyMode (0x05)</a></th>
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
    <th><a href="../theory_of_operation.md#unexpectedmodestrength-0x06">UnexpectedModeStrength (0x06)</a></th>
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
    <th><a href="../theory_of_operation.md#incorrectfunctionname-0x07">IncorrectFunctionName (0x07)</a></th>
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
    <th><a href="../theory_of_operation.md#swcmdsequence-0x08">SwCmdSequence (0x08)</a></th>
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
    <th>KMAC.MODE.SHA3</th>
    <th>KMAC.MODE.SHAKE</th>
    <th>KMAC.MODE.CSHAKE</th>
    <th>KMAC.MODE.KMAC</th>
    <th>KMAC.MODE.XOF</th>
    <th>KMAC.ENDIANNESS.MESSAGE</th>
    <th>KMAC.ENDIANNESS.DIGEST</th>
    <th>KMAC.KEY.SIDELOAD</th>
    <th>KMAC.ENTROPY_MODES</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#long_msg_and_output">long_msg_and_output</a></th>
    <td><a href="02_testpoint_report.md#long_msg_and_output">X</a></td>
    <td><a href="02_testpoint_report.md#long_msg_and_output">X</a></td>
    <td><a href="02_testpoint_report.md#long_msg_and_output">X</a></td>
    <td><a href="02_testpoint_report.md#long_msg_and_output">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#long_msg_and_output">X</a></td>
    <td><a href="02_testpoint_report.md#long_msg_and_output">X</a></td>
    <td><a href="02_testpoint_report.md#long_msg_and_output">X</a></td>
    <td><a href="02_testpoint_report.md#long_msg_and_output">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#burst_write">burst_write</a></th>
    <td><a href="02_testpoint_report.md#burst_write">X</a></td>
    <td><a href="02_testpoint_report.md#burst_write">X</a></td>
    <td><a href="02_testpoint_report.md#burst_write">X</a></td>
    <td><a href="02_testpoint_report.md#burst_write">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#burst_write">X</a></td>
    <td><a href="02_testpoint_report.md#burst_write">X</a></td>
    <td><a href="02_testpoint_report.md#burst_write">X</a></td>
    <td><a href="02_testpoint_report.md#burst_write">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#test_vectors">test_vectors</a></th>
    <td><a href="02_testpoint_report.md#test_vectors">X</a></td>
    <td><a href="02_testpoint_report.md#test_vectors">X</a></td>
    <td><a href="02_testpoint_report.md#test_vectors">X</a></td>
    <td><a href="02_testpoint_report.md#test_vectors">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#sideload">sideload</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#sideload">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#app">app</a></th>
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
    <th><a href="02_testpoint_report.md#app_with_partial_data">app_with_partial_data</a></th>
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
    <th><a href="02_testpoint_report.md#entropy_refresh">entropy_refresh</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#entropy_refresh">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#error">error</a></th>
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
    <th><a href="02_testpoint_report.md#key_error">key_error</a></th>
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
    <th><a href="02_testpoint_report.md#sideload_invalid">sideload_invalid</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#sideload_invalid">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#edn_timeout_error">edn_timeout_error</a></th>
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
    <th><a href="02_testpoint_report.md#entropy_mode_error">entropy_mode_error</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#entropy_mode_error">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#entropy_ready_error">entropy_ready_error</a></th>
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
    <th><a href="02_testpoint_report.md#lc_escalation">lc_escalation</a></th>
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
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#throughput">throughput</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_kmac_enc-dragonfly">chip_sw_kmac_enc (dragonfly)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_kmac_app_keymgr-dragonfly">chip_sw_kmac_app_keymgr (dragonfly)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_kmac_app_lc-dragonfly">chip_sw_kmac_app_lc (dragonfly)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_kmac_app_rom-dragonfly">chip_sw_kmac_app_rom (dragonfly)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_kmac_entropy-dragonfly">chip_sw_kmac_entropy (dragonfly)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_kmac_idle-dragonfly">chip_sw_kmac_idle (dragonfly)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_kmac_sha3_stress-dragonfly">chip_sw_kmac_sha3_stress (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_sha3_stress-dragonfly">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_kmac_shake_stress-dragonfly">chip_sw_kmac_shake_stress (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_shake_stress-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_shake_stress-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_kmac_cshake_stress-dragonfly">chip_sw_kmac_cshake_stress (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_cshake_stress-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_cshake_stress-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_kmac_kmac_stress-dragonfly">chip_sw_kmac_kmac_stress (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_kmac_stress-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_kmac_kmac_key_sideload-dragonfly">chip_sw_kmac_kmac_key_sideload (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_kmac_key_sideload-dragonfly">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_kmac_endianness-dragonfly">chip_sw_kmac_endianness (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_endianness-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_endianness-dragonfly">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_kmac_entropy_stress-dragonfly">chip_sw_kmac_entropy_stress (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_entropy_stress-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_entropy_stress-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_entropy_stress-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_kmac_error_conditions-dragonfly">chip_sw_kmac_error_conditions (dragonfly)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_kmac_enc-egret">chip_sw_kmac_enc (egret)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_kmac_app_keymgr-egret">chip_sw_kmac_app_keymgr (egret)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_kmac_app_lc-egret">chip_sw_kmac_app_lc (egret)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_kmac_app_rom-egret">chip_sw_kmac_app_rom (egret)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_kmac_entropy-egret">chip_sw_kmac_entropy (egret)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_kmac_idle-egret">chip_sw_kmac_idle (egret)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_kmac_sha3_stress-egret">chip_sw_kmac_sha3_stress (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_sha3_stress-egret">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_kmac_shake_stress-egret">chip_sw_kmac_shake_stress (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_shake_stress-egret">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_shake_stress-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_kmac_cshake_stress-egret">chip_sw_kmac_cshake_stress (egret)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_cshake_stress-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_cshake_stress-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_kmac_kmac_stress-egret">chip_sw_kmac_kmac_stress (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_kmac_stress-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_kmac_kmac_key_sideload-egret">chip_sw_kmac_kmac_key_sideload (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_kmac_key_sideload-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_kmac_endianness-egret">chip_sw_kmac_endianness (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_endianness-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_endianness-egret">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_kmac_entropy_stress-egret">chip_sw_kmac_entropy_stress (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_entropy_stress-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_entropy_stress-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_kmac_entropy_stress-egret">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_kmac_error_conditions-egret">chip_sw_kmac_error_conditions (egret)</a></th>
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
