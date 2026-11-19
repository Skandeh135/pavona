# aes Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="aescleardata_out">
      <td>AES.CLEAR.DATA_OUT</td>
      <td>Output data registers can be cleared using pseudo-random data.</td>
    </tr>
    <tr id="aesclearkey_iv_data_in">
      <td>AES.CLEAR.KEY_IV_DATA_IN</td>
      <td>Keys, IV registers and input data registers can be cleared using pseudo-random data.</td>
    </tr>
    <tr id="aeskeysideload">
      <td>AES.KEY.SIDELOAD</td>
      <td>The key can be loaded directly from the keymgr.</td>
    </tr>
    <tr id="aeskey_len128">
      <td>AES.KEY_LEN.128</td>
      <td>AES can perform both operations (encryption and decryption) for key length 128.</td>
    </tr>
    <tr id="aeskey_len192">
      <td>AES.KEY_LEN.192</td>
      <td>AES can perform both operations (encryption and decryption) for key length 192.This feature can be disabled using a compile-time Verilog parameter.</td>
    </tr>
    <tr id="aeskey_len256">
      <td>AES.KEY_LEN.256</td>
      <td>AES can perform both operations (encryption and decryption) for key length 256.</td>
    </tr>
    <tr id="aesmanual_operation">
      <td>AES.MANUAL_OPERATION</td>
      <td>Operations (encryption and decryption) could be processed in two ways:-AES tracks whether data has been written/read, and starts the operation automatically (default).-AES only starts the operation after receiving a start trigger.</td>
    </tr>
    <tr id="aesmodecbc">
      <td>AES.MODE.CBC</td>
      <td>AES can perform both operations (encryption and decryption) in Cipher Block Chaining (CBC) Mode for all three key lengths (128/192/256).</td>
    </tr>
    <tr id="aesmodecfb-128">
      <td>AES.MODE.CFB-128</td>
      <td>AES can perform both operations (encryption and decryption) in Cipher Feedback (CFB) Mode for all three key lengths (128/192/256).Note that the only supported data-segment size is 128.</td>
    </tr>
    <tr id="aesmodectr">
      <td>AES.MODE.CTR</td>
      <td>AES can perform both operations (encryption and decryption) in Counter (CTR) Mode for all three key lengths (128/192/256).</td>
    </tr>
    <tr id="aesmodeecb">
      <td>AES.MODE.ECB</td>
      <td>AES can perform both operations (encryption and decryption) in Electronic Codebook (ECB) Mode for all three key lengths (128/192/256).</td>
    </tr>
    <tr id="aesmodegcm">
      <td>AES.MODE.GCM</td>
      <td>AES can perform both operations (encryption and decryption) in Galois/Counter Mode (GCM) for all three key lengths (128/192/256).</td>
    </tr>
    <tr id="aesmodeofb">
      <td>AES.MODE.OFB</td>
      <td>AES can perform both operations (encryption and decryption) in Output Feedback (OFB) Mode for all three key lengths (128/192/256).</td>
    </tr>
    <tr id="aesprngforce_masks">
      <td>AES.PRNG.FORCE_MASKS</td>
      <td>AES can block advancing of the internal PRNG used for masking, thereby forcing masks to a constant value.This feature can be disabled using a compile-time Verilog parameter.</td>
    </tr>
    <tr id="aesprngkey_touch_forces_reseed">
      <td>AES.PRNG.KEY_TOUCH_FORCES_RESEED</td>
      <td>AES can force re-seeding of internal PRNGs used for masking and clearing every time a new key is provided.</td>
    </tr>
    <tr id="aesprngreseed_rate">
      <td>AES.PRNG.RESEED_RATE</td>
      <td>Reseed rate of the internal PRNG used for masking.It can be set to three different values:-Once per block-Once per approximately 64 blocks-Once per approximately 8K blocks</td>
    </tr>
    <tr id="aesstatusstall">
      <td>AES.STATUS.STALL</td>
      <td>AES can stall to avoid overwriting output data not read yet by the processor.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>AES.KEY_LEN.128</th>
    <th>AES.KEY_LEN.192</th>
    <th>AES.KEY_LEN.256</th>
    <th>AES.MODE.ECB</th>
    <th>AES.MODE.CBC</th>
    <th>AES.MODE.CFB-128</th>
    <th>AES.MODE.OFB</th>
    <th>AES.MODE.CTR</th>
    <th>AES.MODE.GCM</th>
    <th>AES.KEY.SIDELOAD</th>
    <th>AES.CLEAR.DATA_OUT</th>
    <th>AES.CLEAR.KEY_IV_DATA_IN</th>
    <th>AES.PRNG.RESEED_RATE</th>
    <th>AES.PRNG.KEY_TOUCH_FORCES_RESEED</th>
    <th>AES.PRNG.FORCE_MASKS</th>
    <th>AES.MANUAL_OPERATION</th>
    <th>AES.STATUS.STALL</th>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#theory-of-operation">Theory of Operation</a></th>
    <td><a href="../theory_of_operation.md#theory-of-operation">X</a></td>
    <td><a href="../theory_of_operation.md#theory-of-operation">X</a></td>
    <td><a href="../theory_of_operation.md#theory-of-operation">X</a></td>
    <td><a href="../theory_of_operation.md#theory-of-operation">X</a></td>
    <td><a href="../theory_of_operation.md#theory-of-operation">X</a></td>
    <td><a href="../theory_of_operation.md#theory-of-operation">X</a></td>
    <td><a href="../theory_of_operation.md#theory-of-operation">X</a></td>
    <td><a href="../theory_of_operation.md#theory-of-operation">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#theory-of-operation">X</a></td>
    <td><a href="../theory_of_operation.md#theory-of-operation">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#block-diagram">Block Diagram</a></th>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#design-details">Design Details</a></th>
    <td><a href="../theory_of_operation.md#design-details">X</a></td>
    <td><a href="../theory_of_operation.md#design-details">X</a></td>
    <td><a href="../theory_of_operation.md#design-details">X</a></td>
    <td><a href="../theory_of_operation.md#design-details">X</a></td>
    <td><a href="../theory_of_operation.md#design-details">X</a></td>
    <td><a href="../theory_of_operation.md#design-details">X</a></td>
    <td><a href="../theory_of_operation.md#design-details">X</a></td>
    <td><a href="../theory_of_operation.md#design-details">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#design-details">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#datapath-architecture-and-operation">Datapath Architecture and Operation</a></th>
    <td><a href="../theory_of_operation.md#datapath-architecture-and-operation">X</a></td>
    <td><a href="../theory_of_operation.md#datapath-architecture-and-operation">X</a></td>
    <td><a href="../theory_of_operation.md#datapath-architecture-and-operation">X</a></td>
    <td><a href="../theory_of_operation.md#datapath-architecture-and-operation">X</a></td>
    <td><a href="../theory_of_operation.md#datapath-architecture-and-operation">X</a></td>
    <td><a href="../theory_of_operation.md#datapath-architecture-and-operation">X</a></td>
    <td><a href="../theory_of_operation.md#datapath-architecture-and-operation">X</a></td>
    <td><a href="../theory_of_operation.md#datapath-architecture-and-operation">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#datapath-architecture-and-operation">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#subbytes--s-box">SubBytes / S-Box</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#shiftrows">ShiftRows</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#mixcolumns">MixColumns</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#keyexpand">KeyExpand</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#system-key-manager-interface">System Key-Manager Interface</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#system-key-manager-interface">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#security-hardening">Security Hardening</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#side-channel-analysis">Side-Channel Analysis</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#1st-order-masking-of-the-cipher-core">1st-order Masking of the Cipher Core</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#1st-order-masking-of-the-cipher-core">X</a></td>
    <td><a href="../theory_of_operation.md#1st-order-masking-of-the-cipher-core">X</a></td>
    <td><a href="../theory_of_operation.md#1st-order-masking-of-the-cipher-core">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#fully-parallel-data-path">Fully-Parallel Data Path</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#1st-order-masking-of-the-ghash-module">1st-order Masking of the GHASH Module</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#masking-concept">Masking Concept</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#algorithmic-overview">Algorithmic Overview</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#mapping-the-masked-algorithm-to-the-hardware">Mapping the Masked Algorithm to the Hardware</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#formal-masking-verification">Formal Masking Verification</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#note-on-reset-vs-non-reset-flip-flops">Note on Reset vs. Non-Reset Flip-Flops</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#clearing-registers-with-pseudo-random-data">Clearing Registers with Pseudo-Random Data</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#clearing-registers-with-pseudo-random-data">X</a></td>
    <td><a href="../theory_of_operation.md#clearing-registers-with-pseudo-random-data">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#fault-injection">Fault Injection</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#control-path">Control Path</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#data-path">Data Path</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th>AES.KEY_LEN.128</th>
    <th>AES.KEY_LEN.192</th>
    <th>AES.KEY_LEN.256</th>
    <th>AES.MODE.ECB</th>
    <th>AES.MODE.CBC</th>
    <th>AES.MODE.CFB-128</th>
    <th>AES.MODE.OFB</th>
    <th>AES.MODE.CTR</th>
    <th>AES.MODE.GCM</th>
    <th>AES.KEY.SIDELOAD</th>
    <th>AES.CLEAR.DATA_OUT</th>
    <th>AES.CLEAR.KEY_IV_DATA_IN</th>
    <th>AES.PRNG.RESEED_RATE</th>
    <th>AES.PRNG.KEY_TOUCH_FORCES_RESEED</th>
    <th>AES.PRNG.FORCE_MASKS</th>
    <th>AES.MANUAL_OPERATION</th>
    <th>AES.STATUS.STALL</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#wake_up">wake_up</a></th>
    <td><a href="02_testpoint_report.md#wake_up">X</a></td>
    <td><a href="02_testpoint_report.md#wake_up">X</a></td>
    <td><a href="02_testpoint_report.md#wake_up">X</a></td>
    <td><a href="02_testpoint_report.md#wake_up">X</a></td>
    <td><a href="02_testpoint_report.md#wake_up">X</a></td>
    <td><a href="02_testpoint_report.md#wake_up">X</a></td>
    <td><a href="02_testpoint_report.md#wake_up">X</a></td>
    <td><a href="02_testpoint_report.md#wake_up">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#wake_up">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
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
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#algorithm">algorithm</a></th>
    <td><a href="02_testpoint_report.md#algorithm">X</a></td>
    <td><a href="02_testpoint_report.md#algorithm">X</a></td>
    <td><a href="02_testpoint_report.md#algorithm">X</a></td>
    <td><a href="02_testpoint_report.md#algorithm">X</a></td>
    <td><a href="02_testpoint_report.md#algorithm">X</a></td>
    <td><a href="02_testpoint_report.md#algorithm">X</a></td>
    <td><a href="02_testpoint_report.md#algorithm">X</a></td>
    <td><a href="02_testpoint_report.md#algorithm">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#algorithm">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#key_length">key_length</a></th>
    <td><a href="02_testpoint_report.md#key_length">X</a></td>
    <td><a href="02_testpoint_report.md#key_length">X</a></td>
    <td><a href="02_testpoint_report.md#key_length">X</a></td>
    <td><a href="02_testpoint_report.md#key_length">X</a></td>
    <td><a href="02_testpoint_report.md#key_length">X</a></td>
    <td><a href="02_testpoint_report.md#key_length">X</a></td>
    <td><a href="02_testpoint_report.md#key_length">X</a></td>
    <td><a href="02_testpoint_report.md#key_length">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#key_length">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#back2back">back2back</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#backpressure">backpressure</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#backpressure">X</a></td>
    <td><a href="02_testpoint_report.md#backpressure">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#multi_message">multi_message</a></th>
    <td><a href="02_testpoint_report.md#multi_message">X</a></td>
    <td><a href="02_testpoint_report.md#multi_message">X</a></td>
    <td><a href="02_testpoint_report.md#multi_message">X</a></td>
    <td><a href="02_testpoint_report.md#multi_message">X</a></td>
    <td><a href="02_testpoint_report.md#multi_message">X</a></td>
    <td><a href="02_testpoint_report.md#multi_message">X</a></td>
    <td><a href="02_testpoint_report.md#multi_message">X</a></td>
    <td><a href="02_testpoint_report.md#multi_message">X</a></td>
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
    <th><a href="02_testpoint_report.md#failure_test">failure_test</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#trigger_clear_test">trigger_clear_test</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#trigger_clear_test">X</a></td>
    <td><a href="02_testpoint_report.md#trigger_clear_test">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#trigger_clear_test">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#nist_test_vectors">nist_test_vectors</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#reset_recovery">reset_recovery</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#stress">stress</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#sideload">sideload</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#sideload">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#sideload">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#deinitialization">deinitialization</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#reseeding">reseeding</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#reseeding">X</a></td>
    <td><a href="02_testpoint_report.md#reseeding">X</a></td>
    <td><a href="02_testpoint_report.md#reseeding">X</a></td>
    <td><a href="02_testpoint_report.md#reseeding">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#fault_inject">fault_inject</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_aes_enc-dragonfly">chip_sw_aes_enc (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_enc-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_enc-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_enc-dragonfly">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aes_multi_block-dragonfly">chip_sw_aes_multi_block (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_aes_multi_block-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_multi_block-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_multi_block-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_multi_block-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_multi_block-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_multi_block-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_multi_block-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_multi_block-dragonfly">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_aes_interrupt_encryption-dragonfly">chip_sw_aes_interrupt_encryption (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_interrupt_encryption-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_interrupt_encryption-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_interrupt_encryption-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_interrupt_encryption-dragonfly">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_aes_entropy-dragonfly">chip_sw_aes_entropy (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_entropy-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_entropy-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_entropy-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aes_prng_reseed-dragonfly">chip_sw_aes_prng_reseed (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_prng_reseed-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_prng_reseed-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aes_force_prng_reseed-dragonfly">chip_sw_aes_force_prng_reseed (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_force_prng_reseed-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_force_prng_reseed-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aes_stall_test-dragonfly">chip_sw_aes_stall_test (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_stall_test-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_stall_test-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aes_idle-dragonfly">chip_sw_aes_idle (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_idle-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_aes_sideload-dragonfly">chip_sw_aes_sideload (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_sideload-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_sideload-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aes_masking_off-dragonfly">chip_sw_aes_masking_off (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_masking_off-dragonfly">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aes_enc-egret">chip_sw_aes_enc (egret)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_enc-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_enc-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_enc-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aes_multi_block-egret">chip_sw_aes_multi_block (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_aes_multi_block-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_multi_block-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_multi_block-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_multi_block-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_multi_block-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_multi_block-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_multi_block-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_multi_block-egret">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_aes_interrupt_encryption-egret">chip_sw_aes_interrupt_encryption (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_interrupt_encryption-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_interrupt_encryption-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_interrupt_encryption-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_interrupt_encryption-egret">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_aes_entropy-egret">chip_sw_aes_entropy (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_entropy-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_entropy-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_entropy-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aes_prng_reseed-egret">chip_sw_aes_prng_reseed (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_prng_reseed-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_prng_reseed-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aes_force_prng_reseed-egret">chip_sw_aes_force_prng_reseed (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_force_prng_reseed-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_force_prng_reseed-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aes_stall_test-egret">chip_sw_aes_stall_test (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_stall_test-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_stall_test-egret">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aes_idle-egret">chip_sw_aes_idle (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_idle-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_aes_sideload-egret">chip_sw_aes_sideload (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_sideload-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_sideload-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aes_masking_off-egret">chip_sw_aes_masking_off (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aes_masking_off-egret">X</a></td>
    <td></td>
    <td></td>
  </tr>
</table>
</div>
</div>
