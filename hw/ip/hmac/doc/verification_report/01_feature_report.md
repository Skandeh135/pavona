# hmac Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="hmacdigest_sizesha2-256">
      <td>HMAC.DIGEST_SIZE.SHA2-256</td>
      <td>SHA-2 256 hashing algorithm for SHA-2 and keyed HMAC.</td>
    </tr>
    <tr id="hmacdigest_sizesha2-384">
      <td>HMAC.DIGEST_SIZE.SHA2-384</td>
      <td>SHA-2 384 hashing algorithm for SHA-2 and keyed HMAC.</td>
    </tr>
    <tr id="hmacdigest_sizesha2-512">
      <td>HMAC.DIGEST_SIZE.SHA2-512</td>
      <td>SHA-2 512 hashing algorithm or SHA-2 and keyed HMAC.</td>
    </tr>
    <tr id="hmacendiannessdigest">
      <td>HMAC.ENDIANNESS.DIGEST</td>
      <td>Configurable output digest endianness.</td>
    </tr>
    <tr id="hmacendiannessmessage">
      <td>HMAC.ENDIANNESS.MESSAGE</td>
      <td>Configurable input message endianness.</td>
    </tr>
    <tr id="hmackey_lengthkey_1024">
      <td>HMAC.KEY_LENGTH.KEY_1024</td>
      <td>HMAC based on SHA-2 384/SHA-2 512 using 1024-bit key.</td>
    </tr>
    <tr id="hmackey_lengthkey_128">
      <td>HMAC.KEY_LENGTH.KEY_128</td>
      <td>HMAC based on any digest size using 128-bit key.</td>
    </tr>
    <tr id="hmackey_lengthkey_256">
      <td>HMAC.KEY_LENGTH.KEY_256</td>
      <td>HMAC based on any digest size using 256-bit key.</td>
    </tr>
    <tr id="hmackey_lengthkey_384">
      <td>HMAC.KEY_LENGTH.KEY_384</td>
      <td>HMAC based on any digest size using 384-bit key.</td>
    </tr>
    <tr id="hmackey_lengthkey_512">
      <td>HMAC.KEY_LENGTH.KEY_512</td>
      <td>HMAC based on any digest size using 512-bit key.</td>
    </tr>
    <tr id="hmacmodehmac">
      <td>HMAC.MODE.HMAC</td>
      <td>Keyed-Hash Message Authentication Code (HMAC) supporting the following security strength configurations: HMAC/SHA-2 256/384/512.Compliant with NIST FIPS 198-1 which will be superseded by NIST SP 800-224.</td>
    </tr>
    <tr id="hmacmodesha2">
      <td>HMAC.MODE.SHA2</td>
      <td>SHA-2 hashing algorithm supporting the following security strength configurations: SHA-2 256/384/512. Compliant with NIST FIPS 180-4.</td>
    </tr>
    <tr id="hmacsecure_wipe">
      <td>HMAC.SECURE_WIPE</td>
      <td>Wipe of internal state and secret key with constant value provided by software.</td>
    </tr>
    <tr id="hmacstream_mode">
      <td>HMAC.STREAM_MODE</td>
      <td>HMAC block can stream 6 SHA-2/HMAC operations in parallel</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>HMAC.MODE.SHA2</th>
    <th>HMAC.MODE.HMAC</th>
    <th>HMAC.DIGEST_SIZE.SHA2-256</th>
    <th>HMAC.DIGEST_SIZE.SHA2-384</th>
    <th>HMAC.DIGEST_SIZE.SHA2-512</th>
    <th>HMAC.KEY_LENGTH.KEY_128</th>
    <th>HMAC.KEY_LENGTH.KEY_256</th>
    <th>HMAC.KEY_LENGTH.KEY_384</th>
    <th>HMAC.KEY_LENGTH.KEY_512</th>
    <th>HMAC.KEY_LENGTH.KEY_1024</th>
    <th>HMAC.ENDIANNESS.MESSAGE</th>
    <th>HMAC.ENDIANNESS.DIGEST</th>
    <th>HMAC.SECURE_WIPE</th>
    <th>HMAC.STREAM_MODE</th>
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
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#sha-2-message-feed-and-pad">SHA-2 message feed and pad</a></th>
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
    <td><a href="../theory_of_operation.md#sha-2-message-feed-and-pad">X</a></td>
    <td><a href="../theory_of_operation.md#sha-2-message-feed-and-pad">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#sha-2-computation">SHA-2 computation</a></th>
    <td><a href="../theory_of_operation.md#sha-2-computation">X</a></td>
    <td><a href="../theory_of_operation.md#sha-2-computation">X</a></td>
    <td><a href="../theory_of_operation.md#sha-2-computation">X</a></td>
    <td><a href="../theory_of_operation.md#sha-2-computation">X</a></td>
    <td><a href="../theory_of_operation.md#sha-2-computation">X</a></td>
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
    <th><a href="../theory_of_operation.md#hmac-computation">HMAC computation</a></th>
    <td><a href="../theory_of_operation.md#hmac-computation">X</a></td>
    <td><a href="../theory_of_operation.md#hmac-computation">X</a></td>
    <td><a href="../theory_of_operation.md#hmac-computation">X</a></td>
    <td><a href="../theory_of_operation.md#hmac-computation">X</a></td>
    <td><a href="../theory_of_operation.md#hmac-computation">X</a></td>
    <td><a href="../theory_of_operation.md#hmac-computation">X</a></td>
    <td><a href="../theory_of_operation.md#hmac-computation">X</a></td>
    <td><a href="../theory_of_operation.md#hmac-computation">X</a></td>
    <td><a href="../theory_of_operation.md#hmac-computation">X</a></td>
    <td><a href="../theory_of_operation.md#hmac-computation">X</a></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#hmac-computation">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#performance-in-sha-2-mode-and-hmac-mode">Performance in SHA-2 mode and HMAC mode</a></th>
    <td><a href="../theory_of_operation.md#performance-in-sha-2-mode-and-hmac-mode">X</a></td>
    <td><a href="../theory_of_operation.md#performance-in-sha-2-mode-and-hmac-mode">X</a></td>
    <td><a href="../theory_of_operation.md#performance-in-sha-2-mode-and-hmac-mode">X</a></td>
    <td><a href="../theory_of_operation.md#performance-in-sha-2-mode-and-hmac-mode">X</a></td>
    <td><a href="../theory_of_operation.md#performance-in-sha-2-mode-and-hmac-mode">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#performance-in-sha-2-mode-and-hmac-mode">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#msg_fifo">MSG_FIFO</a></th>
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
    <th>HMAC.MODE.SHA2</th>
    <th>HMAC.MODE.HMAC</th>
    <th>HMAC.DIGEST_SIZE.SHA2-256</th>
    <th>HMAC.DIGEST_SIZE.SHA2-384</th>
    <th>HMAC.DIGEST_SIZE.SHA2-512</th>
    <th>HMAC.KEY_LENGTH.KEY_128</th>
    <th>HMAC.KEY_LENGTH.KEY_256</th>
    <th>HMAC.KEY_LENGTH.KEY_384</th>
    <th>HMAC.KEY_LENGTH.KEY_512</th>
    <th>HMAC.KEY_LENGTH.KEY_1024</th>
    <th>HMAC.ENDIANNESS.MESSAGE</th>
    <th>HMAC.ENDIANNESS.DIGEST</th>
    <th>HMAC.SECURE_WIPE</th>
    <th>HMAC.STREAM_MODE</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#long_msg">long_msg</a></th>
    <td><a href="02_testpoint_report.md#long_msg">X</a></td>
    <td><a href="02_testpoint_report.md#long_msg">X</a></td>
    <td><a href="02_testpoint_report.md#long_msg">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#long_msg">X</a></td>
    <td><a href="02_testpoint_report.md#long_msg">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#back_pressure">back_pressure</a></th>
    <td><a href="02_testpoint_report.md#back_pressure">X</a></td>
    <td><a href="02_testpoint_report.md#back_pressure">X</a></td>
    <td><a href="02_testpoint_report.md#back_pressure">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#back_pressure">X</a></td>
    <td><a href="02_testpoint_report.md#back_pressure">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#test_vectors">test_vectors</a></th>
    <td><a href="02_testpoint_report.md#test_vectors">X</a></td>
    <td><a href="02_testpoint_report.md#test_vectors">X</a></td>
    <td><a href="02_testpoint_report.md#test_vectors">X</a></td>
    <td><a href="02_testpoint_report.md#test_vectors">X</a></td>
    <td><a href="02_testpoint_report.md#test_vectors">X</a></td>
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
    <th><a href="02_testpoint_report.md#burst_wr">burst_wr</a></th>
    <td><a href="02_testpoint_report.md#burst_wr">X</a></td>
    <td><a href="02_testpoint_report.md#burst_wr">X</a></td>
    <td><a href="02_testpoint_report.md#burst_wr">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#burst_wr">X</a></td>
    <td><a href="02_testpoint_report.md#burst_wr">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#datapath_stress">datapath_stress</a></th>
    <td><a href="02_testpoint_report.md#datapath_stress">X</a></td>
    <td><a href="02_testpoint_report.md#datapath_stress">X</a></td>
    <td><a href="02_testpoint_report.md#datapath_stress">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#datapath_stress">X</a></td>
    <td><a href="02_testpoint_report.md#datapath_stress">X</a></td>
    <td></td>
    <td></td>
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
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#wipe_secret">wipe_secret</a></th>
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
    <td><a href="02_testpoint_report.md#wipe_secret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#save_and_restore">save_and_restore</a></th>
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
    <td></td>
    <td><a href="02_testpoint_report.md#save_and_restore">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#fifo_empty_status_interrupt">fifo_empty_status_interrupt</a></th>
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
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#wide_digest_configurable_key_length">wide_digest_configurable_key_length</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#wide_digest_configurable_key_length">X</a></td>
    <td><a href="02_testpoint_report.md#wide_digest_configurable_key_length">X</a></td>
    <td><a href="02_testpoint_report.md#wide_digest_configurable_key_length">X</a></td>
    <td><a href="02_testpoint_report.md#wide_digest_configurable_key_length">X</a></td>
    <td><a href="02_testpoint_report.md#wide_digest_configurable_key_length">X</a></td>
    <td><a href="02_testpoint_report.md#wide_digest_configurable_key_length">X</a></td>
    <td><a href="02_testpoint_report.md#wide_digest_configurable_key_length">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#stress_all">stress_all</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#write_config_and_secret_key_during_msg_wr">write_config_and_secret_key_during_msg_wr</a></th>
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
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#stress_reset">stress_reset</a></th>
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
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_hmac_enc-dragonfly">chip_sw_hmac_enc (dragonfly)</a></th>
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
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_hmac_idle-dragonfly">chip_sw_hmac_idle (dragonfly)</a></th>
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
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_hmac_all_configurations-dragonfly">chip_sw_hmac_all_configurations (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_hmac_all_configurations-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_hmac_all_configurations-dragonfly">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_hmac_multistream_mode-dragonfly">chip_sw_hmac_multistream_mode (dragonfly)</a></th>
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
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_hmac_multistream_mode-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_hmac_sha2_stress-dragonfly">chip_sw_hmac_sha2_stress (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_hmac_sha2_stress-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_hmac_sha2_stress-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_hmac_sha2_stress-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_hmac_sha2_stress-dragonfly">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_hmac_stress-dragonfly">chip_sw_hmac_stress (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_hmac_stress-dragonfly">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_hmac_endianness-dragonfly">chip_sw_hmac_endianness (dragonfly)</a></th>
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
    <td><a href="02_testpoint_report.md#chip_sw_hmac_endianness-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_hmac_endianness-dragonfly">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_hmac_secure_wipe-dragonfly">chip_sw_hmac_secure_wipe (dragonfly)</a></th>
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
    <td><a href="02_testpoint_report.md#chip_sw_hmac_secure_wipe-dragonfly">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_hmac_error_conditions-dragonfly">chip_sw_hmac_error_conditions (dragonfly)</a></th>
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
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_hmac_enc-egret">chip_sw_hmac_enc (egret)</a></th>
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
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_hmac_idle-egret">chip_sw_hmac_idle (egret)</a></th>
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
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_hmac_all_configurations-egret">chip_sw_hmac_all_configurations (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_hmac_all_configurations-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_hmac_all_configurations-egret">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_hmac_multistream_mode-egret">chip_sw_hmac_multistream_mode (egret)</a></th>
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
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_hmac_multistream_mode-egret">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_hmac_sha2_stress-egret">chip_sw_hmac_sha2_stress (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_hmac_sha2_stress-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_hmac_sha2_stress-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_hmac_sha2_stress-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_hmac_sha2_stress-egret">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_hmac_stress-egret">chip_sw_hmac_stress (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_hmac_stress-egret">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_hmac_endianness-egret">chip_sw_hmac_endianness (egret)</a></th>
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
    <td><a href="02_testpoint_report.md#chip_sw_hmac_endianness-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_hmac_endianness-egret">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_hmac_secure_wipe-egret">chip_sw_hmac_secure_wipe (egret)</a></th>
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
    <td><a href="02_testpoint_report.md#chip_sw_hmac_secure_wipe-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_hmac_error_conditions-egret">chip_sw_hmac_error_conditions (egret)</a></th>
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
    <td></td>
    <td></td>
  </tr>
</table>
</div>
</div>
