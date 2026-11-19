# hmac Testpoint Report

## back_pressure
Back_pressure test is based on the long_msg test. The test disabled all the protocol
delays to make sure to have high chance of hitting the FIFO_FULL status.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#hmac_back_pressure">hmac_back_pressure</a></td>
  <td><a href="01_feature_report.md#hmacdigest_sizesha2-256">HMAC.DIGEST_SIZE.SHA2-256</a><br><a href="01_feature_report.md#hmacendiannessdigest">HMAC.ENDIANNESS.DIGEST</a><br><a href="01_feature_report.md#hmacendiannessmessage">HMAC.ENDIANNESS.MESSAGE</a><br><a href="01_feature_report.md#hmacmodehmac">HMAC.MODE.HMAC</a><br><a href="01_feature_report.md#hmacmodesha2">HMAC.MODE.SHA2</a></td>
</tr>
  </tbody>
</table>

## burst_wr
Burst_wr test is based on the long_msg test. The test intends to test burst write a
pre-defined size of message without any status or interrupt checking.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#hmac_burst_wr">hmac_burst_wr</a></td>
  <td><a href="01_feature_report.md#hmacdigest_sizesha2-256">HMAC.DIGEST_SIZE.SHA2-256</a><br><a href="01_feature_report.md#hmacendiannessdigest">HMAC.ENDIANNESS.DIGEST</a><br><a href="01_feature_report.md#hmacendiannessmessage">HMAC.ENDIANNESS.MESSAGE</a><br><a href="01_feature_report.md#hmacmodehmac">HMAC.MODE.HMAC</a><br><a href="01_feature_report.md#hmacmodesha2">HMAC.MODE.SHA2</a></td>
</tr>
  </tbody>
</table>

## chip_sw_hmac_all_configurations (dragonfly)
Verify HMAC 256/384 and 512 modes of operation.

- Verify the following security configurations for 6 hardcoded vectors:
  - SHA2-256
  - SHA2-384
  - SHA2-512
  - HMAC-SHA2-256
  - HMAC-SHA2-384
  - HMAC-SHA2-512
- Use endianness configuration used in the crypto library.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_hmac_oneshot-dragonfly">chip_sw_hmac_oneshot (dragonfly)</a></td>
  <td><a href="01_feature_report.md#hmacmodehmac">HMAC.MODE.HMAC</a><br><a href="01_feature_report.md#hmacmodesha2">HMAC.MODE.SHA2</a></td>
</tr>
  </tbody>
</table>

## chip_sw_hmac_all_configurations (egret)
Verify HMAC 256/384 and 512 modes of operation.

- Verify the following security configurations for 6 hardcoded vectors:
  - SHA2-256
  - SHA2-384
  - SHA2-512
  - HMAC-SHA2-256
  - HMAC-SHA2-384
  - HMAC-SHA2-512
- Use endianness configuration used in the crypto library.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_hmac_oneshot-egret">chip_sw_hmac_oneshot (egret)</a></td>
  <td><a href="01_feature_report.md#hmacmodehmac">HMAC.MODE.HMAC</a><br><a href="01_feature_report.md#hmacmodesha2">HMAC.MODE.SHA2</a></td>
</tr>
  </tbody>
</table>

## chip_sw_hmac_enc (dragonfly)
Verify HMAC operation.

SW test verifies an HMAC operation with a known key, plain text and digest (pick one of
the NIST vectors). SW test verifies the digest against the pre-computed value. Verify
the HMAC done and FIFO empty interrupts as a part of this test.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_hmac_enc-dragonfly">chip_sw_hmac_enc (dragonfly)</a><br><a href="03_test_report.md#chip_sw_hmac_enc_jitter_en-dragonfly">chip_sw_hmac_enc_jitter_en (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_hmac_enc (egret)
Verify HMAC operation.

SW test verifies an HMAC operation with a known key, plain text and digest (pick one of
the NIST vectors). SW test verifies the digest against the pre-computed value. Verify
the HMAC done and FIFO empty interrupts as a part of this test.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_hmac_enc-egret">chip_sw_hmac_enc (egret)</a><br><a href="03_test_report.md#chip_sw_hmac_enc_jitter_en-egret">chip_sw_hmac_enc_jitter_en (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_hmac_endianness (dragonfly)
Verify all HMAC endianness options

This is a low priority test P3.

Test the permutation of all endianness configuration options for message and digest
registers.


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
  <td><a href="01_feature_report.md#hmacendiannessdigest">HMAC.ENDIANNESS.DIGEST</a><br><a href="01_feature_report.md#hmacendiannessmessage">HMAC.ENDIANNESS.MESSAGE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_hmac_endianness (egret)
Verify all HMAC endianness options

This is a low priority test P3.

Test the permutation of all endianness configuration options for message and digest
registers.


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
  <td><a href="01_feature_report.md#hmacendiannessdigest">HMAC.ENDIANNESS.DIGEST</a><br><a href="01_feature_report.md#hmacendiannessmessage">HMAC.ENDIANNESS.MESSAGE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_hmac_error_conditions (dragonfly)
Verify reporting of HMAC errors

This is a negative test case covering the following error conditions:

- `SwPushMsgWhenShaDisabled`: Push message when SHA is disabled.
- `SwHashStartWhenShaDisabled`: Start hash operation when SHA is disabled.
- `SwUpdateSecretKeyInProcess`: Update secret key when hash is in progress.
- `SwHashStartWhenActive`: Issue hash start when hash is in progress.
- `SwPushMsgWhenDisallowed`: Push message when HMAC is not idle.
- `SwInvalidConfig`: Issue when HMAC configured with incorrect digest-size or key-length


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
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_hmac_error_conditions (egret)
Verify reporting of HMAC errors

This is a negative test case covering the following error conditions:

- `SwPushMsgWhenShaDisabled`: Push message when SHA is disabled.
- `SwHashStartWhenShaDisabled`: Start hash operation when SHA is disabled.
- `SwUpdateSecretKeyInProcess`: Update secret key when hash is in progress.
- `SwHashStartWhenActive`: Issue hash start when hash is in progress.
- `SwPushMsgWhenDisallowed`: Push message when HMAC is not idle.
- `SwInvalidConfig`: Issue when HMAC configured with incorrect digest-size or key-length


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
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_hmac_idle (dragonfly)
Verify the HMAC clk idle signal to clkmgr.

- Write the HMAC clk hint to 0 within clkmgr to indicate HMAC clk can be gated and
  verify that the HMAC clk hint status within clkmgr reads 0 (HMAC is disabled).
- Write the HMAC clk hint to 1 within clkmgr to indicate HMAC clk can be enabled.
  Verify that the HMAC clk hint status within clkmgr reads 1 (HMAC is enabled).
- Initiate an HMAC operation with a known key, plain text and digest.
  Write HMAC clock hint to 0 and verify the HMAC clk hint status within clkmgr reads 1
  (HMAC is enabled), before the HMAC operation is complete.
- After the HMAC operation is complete, verify the digest for correctness. Verify that
  the HMAC clk hint status within clkmgr now reads 0 again (HMAC is disabled).
- This process is repeated for two hmac operations needed to verify the resulting hmac
  digest.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_hmac_enc_idle-dragonfly">chip_sw_hmac_enc_idle (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_hmac_idle (egret)
Verify the HMAC clk idle signal to clkmgr.

- Write the HMAC clk hint to 0 within clkmgr to indicate HMAC clk can be gated and
  verify that the HMAC clk hint status within clkmgr reads 0 (HMAC is disabled).
- Write the HMAC clk hint to 1 within clkmgr to indicate HMAC clk can be enabled.
  Verify that the HMAC clk hint status within clkmgr reads 1 (HMAC is enabled).
- Initiate an HMAC operation with a known key, plain text and digest.
  Write HMAC clock hint to 0 and verify the HMAC clk hint status within clkmgr reads 1
  (HMAC is enabled), before the HMAC operation is complete.
- After the HMAC operation is complete, verify the digest for correctness. Verify that
  the HMAC clk hint status within clkmgr now reads 0 again (HMAC is disabled).
- This process is repeated for two hmac operations needed to verify the resulting hmac
  digest.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_hmac_enc_idle-egret">chip_sw_hmac_enc_idle (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_hmac_multistream_mode (dragonfly)
Verify HMAC context save/restore functionality.

- Verify that HMAC block can stream 6 SHA-2/HMAC operations in parallel:
  - One test vector for each configuration:
    - SHA2-256
    - SHA2-384
    - SHA2-512
    - HMAC-SHA2-256
    - HMAC-SHA2-384
    - HMAC-SHA2-512
  - For each vector, message input is split into two chunks, and each
    operation is completed with 2 update calls.
    - Initiate all 6 operations.
    - Feed the first message chunk to each stream, by resuming,
      updating and removing context for each operation.
    - Once all streams receive their first chunk, then feed their
      second message chunk similarly.
    - Once all streams receive all their message inputs, then finalize
      them in a loop and check their result.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_hmac_multistream-dragonfly">chip_sw_hmac_multistream (dragonfly)</a></td>
  <td><a href="01_feature_report.md#hmacstream_mode">HMAC.STREAM_MODE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_hmac_multistream_mode (egret)
Verify HMAC context save/restore functionality.

- Verify that HMAC block can stream 6 SHA-2/HMAC operations in parallel:
  - One test vector for each configuration:
    - SHA2-256
    - SHA2-384
    - SHA2-512
    - HMAC-SHA2-256
    - HMAC-SHA2-384
    - HMAC-SHA2-512
  - For each vector, message input is split into two chunks, and each
    operation is completed with 2 update calls.
    - Initiate all 6 operations.
    - Feed the first message chunk to each stream, by resuming,
      updating and removing context for each operation.
    - Once all streams receive their first chunk, then feed their
      second message chunk similarly.
    - Once all streams receive all their message inputs, then finalize
      them in a loop and check their result.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_hmac_multistream-egret">chip_sw_hmac_multistream (egret)</a></td>
  <td><a href="01_feature_report.md#hmacstream_mode">HMAC.STREAM_MODE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_hmac_secure_wipe (dragonfly)
Verify HMAC secure wipe

- Perform HMAC operation with known key and message.
- Store MAC digest in memory after finalizing HMAC operation.
- Perform secure wipe operation.
- Read digest registers. They should not match the previously calculated digest.
- Process HMAC operation with initial known message.
- Compare MAC digest against original result. The result must not match.


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
  <td><a href="01_feature_report.md#hmacsecure_wipe">HMAC.SECURE_WIPE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_hmac_secure_wipe (egret)
Verify HMAC secure wipe

- Perform HMAC operation with known key and message.
- Store MAC digest in memory after finalizing HMAC operation.
- Perform secure wipe operation.
- Read digest registers. They should not match the previously calculated digest.
- Process HMAC operation with initial known message.
- Compare MAC digest against original result. The result must not match.


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
  <td><a href="01_feature_report.md#hmacsecure_wipe">HMAC.SECURE_WIPE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_hmac_sha2_stress (dragonfly)
Verify SHA2 mode of operation.

- Verify the following digest sizes: 256, 384, 512
- Verify input message size of 0 bytes.
- Verify multiple input message sizes as defined in NIST test vectors.
- Use endianness configuration used in the crypto library.


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
  <td><a href="01_feature_report.md#hmacdigest_sizesha2-256">HMAC.DIGEST_SIZE.SHA2-256</a><br><a href="01_feature_report.md#hmacdigest_sizesha2-384">HMAC.DIGEST_SIZE.SHA2-384</a><br><a href="01_feature_report.md#hmacdigest_sizesha2-512">HMAC.DIGEST_SIZE.SHA2-512</a><br><a href="01_feature_report.md#hmacmodesha2">HMAC.MODE.SHA2</a></td>
</tr>
  </tbody>
</table>

## chip_sw_hmac_sha2_stress (egret)
Verify SHA2 mode of operation.

- Verify the following digest sizes: 256, 384, 512
- Verify input message size of 0 bytes.
- Verify multiple input message sizes as defined in NIST test vectors.
- Use endianness configuration used in the crypto library.


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
  <td><a href="01_feature_report.md#hmacdigest_sizesha2-256">HMAC.DIGEST_SIZE.SHA2-256</a><br><a href="01_feature_report.md#hmacdigest_sizesha2-384">HMAC.DIGEST_SIZE.SHA2-384</a><br><a href="01_feature_report.md#hmacdigest_sizesha2-512">HMAC.DIGEST_SIZE.SHA2-512</a><br><a href="01_feature_report.md#hmacmodesha2">HMAC.MODE.SHA2</a></td>
</tr>
  </tbody>
</table>

## chip_sw_hmac_stress (dragonfly)
Verify HMAC mode of operation.

- Verify all HMAC modes of operation:
  - HMAC-SHA2-256
  - HMAC-SHA2-384
  - HMAC-SHA2-512
- Verify input message size of 0 bytes.
- Verify multiple input message sizes as defined in NIST test vectors.
- Use endianness configuration used in the crypto library.


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
  <td><a href="01_feature_report.md#hmacmodehmac">HMAC.MODE.HMAC</a></td>
</tr>
  </tbody>
</table>

## chip_sw_hmac_stress (egret)
Verify HMAC mode of operation.

- Verify all HMAC modes of operation:
  - HMAC-SHA2-256
  - HMAC-SHA2-384
  - HMAC-SHA2-512
- Verify input message size of 0 bytes.
- Verify multiple input message sizes as defined in NIST test vectors.
- Use endianness configuration used in the crypto library.


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
  <td><a href="01_feature_report.md#hmacmodehmac">HMAC.MODE.HMAC</a></td>
</tr>
  </tbody>
</table>

## datapath_stress
Datapath_stress test is based on the long_msg test. It enabled HMAC and message length
is set to N*64+1 in order to stress the datapath.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#hmac_datapath_stress">hmac_datapath_stress</a></td>
  <td><a href="01_feature_report.md#hmacdigest_sizesha2-256">HMAC.DIGEST_SIZE.SHA2-256</a><br><a href="01_feature_report.md#hmacendiannessdigest">HMAC.ENDIANNESS.DIGEST</a><br><a href="01_feature_report.md#hmacendiannessmessage">HMAC.ENDIANNESS.MESSAGE</a><br><a href="01_feature_report.md#hmacmodehmac">HMAC.MODE.HMAC</a><br><a href="01_feature_report.md#hmacmodesha2">HMAC.MODE.SHA2</a></td>
</tr>
  </tbody>
</table>

## error
This error case runs sequences that will cause interrupt bit hmac_err to set.
This sequence includes:

- Write msg_fifo or set hash_start when sha is disabled
- Update secret key when hash is in process
- Set hash_start when hash is active
- Write msg before hash_start is set


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#hmac_error">hmac_error</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## fifo_empty_status_interrupt
Verify the FIFO empty status interrupt.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#hmac_back_pressure">hmac_back_pressure</a><br><a href="03_test_report.md#hmac_datapath_stress">hmac_datapath_stress</a><br><a href="03_test_report.md#hmac_long_msg">hmac_long_msg</a><br><a href="03_test_report.md#hmac_smoke">hmac_smoke</a><br><a href="03_test_report.md#hmac_test_hmac256_vectors">hmac_test_hmac256_vectors</a><br><a href="03_test_report.md#hmac_test_hmac384_vectors">hmac_test_hmac384_vectors</a><br><a href="03_test_report.md#hmac_test_hmac512_vectors">hmac_test_hmac512_vectors</a><br><a href="03_test_report.md#hmac_test_sha256_vectors">hmac_test_sha256_vectors</a><br><a href="03_test_report.md#hmac_test_sha384_vectors">hmac_test_sha384_vectors</a><br><a href="03_test_report.md#hmac_test_sha512_vectors">hmac_test_sha512_vectors</a><br><a href="03_test_report.md#hmac_wipe_secret">hmac_wipe_secret</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## long_msg
Long_msg test is based on the smoke test. The message length is between 0 and
10,000 bytes.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#hmac_long_msg">hmac_long_msg</a></td>
  <td><a href="01_feature_report.md#hmacdigest_sizesha2-256">HMAC.DIGEST_SIZE.SHA2-256</a><br><a href="01_feature_report.md#hmacendiannessdigest">HMAC.ENDIANNESS.DIGEST</a><br><a href="01_feature_report.md#hmacendiannessmessage">HMAC.ENDIANNESS.MESSAGE</a><br><a href="01_feature_report.md#hmacmodehmac">HMAC.MODE.HMAC</a><br><a href="01_feature_report.md#hmacmodesha2">HMAC.MODE.SHA2</a></td>
</tr>
  </tbody>
</table>

## save_and_restore
Verify save & restore, which allows SW to switch between different parallel message streams.

- This feature is randomly exercised during most of the tests.
- When triggered it could go into 3 different scenarios:
  - Stop and Continue without Saving and Restoring
  - Save and Restore with same context
  - Save and Restore with different contexts


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#hmac_back_pressure">hmac_back_pressure</a><br><a href="03_test_report.md#hmac_burst_wr">hmac_burst_wr</a><br><a href="03_test_report.md#hmac_datapath_stress">hmac_datapath_stress</a><br><a href="03_test_report.md#hmac_long_msg">hmac_long_msg</a><br><a href="03_test_report.md#hmac_smoke">hmac_smoke</a><br><a href="03_test_report.md#hmac_stress_all">hmac_stress_all</a></td>
  <td><a href="01_feature_report.md#hmacstream_mode">HMAC.STREAM_MODE</a></td>
</tr>
  </tbody>
</table>

## smoke
HMAC smoke test performs a few round of HMAC or SHA256-ONLY transactions with the
procedures below:

  - Set configuration register to randomly enable SHA256, hmac, endian_swap, and digest_swap
  - Set interrupt enable register to randomly enable fifo_full, hmac_done, and err_code
    interrupts
  - Randomly read previous digest result
  - Write key
  - Trigger HMAC hash_start
  - Write HMAC message fifo with message length between 0 and 64 bytes
  - check status and interrupt
  - Trigger HMAC hash_process
  - After hmac_done interrupt, read and check digest data


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#hmac_smoke">hmac_smoke</a></td>
  <td><a href="01_feature_report.md#hmacdigest_sizesha2-256">HMAC.DIGEST_SIZE.SHA2-256</a><br><a href="01_feature_report.md#hmacendiannessdigest">HMAC.ENDIANNESS.DIGEST</a><br><a href="01_feature_report.md#hmacendiannessmessage">HMAC.ENDIANNESS.MESSAGE</a><br><a href="01_feature_report.md#hmacmodehmac">HMAC.MODE.HMAC</a><br><a href="01_feature_report.md#hmacmodesha2">HMAC.MODE.SHA2</a></td>
</tr>
  </tbody>
</table>

## stress_all
Stress_all test is a random mix of all the test above except csr tests.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#hmac_stress_all">hmac_stress_all</a></td>
  <td><a href="01_feature_report.md#hmacdigest_sizesha2-256">HMAC.DIGEST_SIZE.SHA2-256</a><br><a href="01_feature_report.md#hmacdigest_sizesha2-384">HMAC.DIGEST_SIZE.SHA2-384</a><br><a href="01_feature_report.md#hmacdigest_sizesha2-512">HMAC.DIGEST_SIZE.SHA2-512</a><br><a href="01_feature_report.md#hmackey_lengthkey_1024">HMAC.KEY_LENGTH.KEY_1024</a><br><a href="01_feature_report.md#hmackey_lengthkey_128">HMAC.KEY_LENGTH.KEY_128</a><br><a href="01_feature_report.md#hmackey_lengthkey_256">HMAC.KEY_LENGTH.KEY_256</a><br><a href="01_feature_report.md#hmackey_lengthkey_384">HMAC.KEY_LENGTH.KEY_384</a><br><a href="01_feature_report.md#hmackey_lengthkey_512">HMAC.KEY_LENGTH.KEY_512</a></td>
</tr>
  </tbody>
</table>

## stress_reset
Run multiple hmac_long_msg sequences with random on-the-fly reset to ensure that all
FSM transitions are exercised.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#hmac_stress_reset">hmac_stress_reset</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## test_vectors
From [NIST](https://csrc.nist.gov/Projects/Cryptographic-Algorithm-Validation-Program/Secure-Hashing#shavs)
and [IETF](https://tools.ietf.org/html/rfc4868) websites, this test intends to use HMAC
and SHA test vectors to check if the reference model predicts correct data, and check if
DUT returns correct data.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#hmac_test_hmac256_vectors">hmac_test_hmac256_vectors</a><br><a href="03_test_report.md#hmac_test_hmac384_vectors">hmac_test_hmac384_vectors</a><br><a href="03_test_report.md#hmac_test_hmac512_vectors">hmac_test_hmac512_vectors</a><br><a href="03_test_report.md#hmac_test_sha256_vectors">hmac_test_sha256_vectors</a><br><a href="03_test_report.md#hmac_test_sha384_vectors">hmac_test_sha384_vectors</a><br><a href="03_test_report.md#hmac_test_sha512_vectors">hmac_test_sha512_vectors</a></td>
  <td><a href="01_feature_report.md#hmacdigest_sizesha2-256">HMAC.DIGEST_SIZE.SHA2-256</a><br><a href="01_feature_report.md#hmacdigest_sizesha2-384">HMAC.DIGEST_SIZE.SHA2-384</a><br><a href="01_feature_report.md#hmacdigest_sizesha2-512">HMAC.DIGEST_SIZE.SHA2-512</a><br><a href="01_feature_report.md#hmacmodehmac">HMAC.MODE.HMAC</a><br><a href="01_feature_report.md#hmacmodesha2">HMAC.MODE.SHA2</a></td>
</tr>
  </tbody>
</table>

## wide_digest_configurable_key_length
Verify wider (SHA-384 and SHA-512) digests as well as configurable key lengths.

- This feature is randomly exercised during most of the tests.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#hmac_back_pressure">hmac_back_pressure</a><br><a href="03_test_report.md#hmac_burst_wr">hmac_burst_wr</a><br><a href="03_test_report.md#hmac_datapath_stress">hmac_datapath_stress</a><br><a href="03_test_report.md#hmac_error">hmac_error</a><br><a href="03_test_report.md#hmac_long_msg">hmac_long_msg</a><br><a href="03_test_report.md#hmac_smoke">hmac_smoke</a><br><a href="03_test_report.md#hmac_stress_all">hmac_stress_all</a><br><a href="03_test_report.md#hmac_test_hmac256_vectors">hmac_test_hmac256_vectors</a><br><a href="03_test_report.md#hmac_test_hmac384_vectors">hmac_test_hmac384_vectors</a><br><a href="03_test_report.md#hmac_test_hmac512_vectors">hmac_test_hmac512_vectors</a><br><a href="03_test_report.md#hmac_test_sha256_vectors">hmac_test_sha256_vectors</a><br><a href="03_test_report.md#hmac_test_sha384_vectors">hmac_test_sha384_vectors</a><br><a href="03_test_report.md#hmac_test_sha512_vectors">hmac_test_sha512_vectors</a><br><a href="03_test_report.md#hmac_wipe_secret">hmac_wipe_secret</a></td>
  <td><a href="01_feature_report.md#hmacdigest_sizesha2-384">HMAC.DIGEST_SIZE.SHA2-384</a><br><a href="01_feature_report.md#hmacdigest_sizesha2-512">HMAC.DIGEST_SIZE.SHA2-512</a><br><a href="01_feature_report.md#hmackey_lengthkey_1024">HMAC.KEY_LENGTH.KEY_1024</a><br><a href="01_feature_report.md#hmackey_lengthkey_128">HMAC.KEY_LENGTH.KEY_128</a><br><a href="01_feature_report.md#hmackey_lengthkey_256">HMAC.KEY_LENGTH.KEY_256</a><br><a href="01_feature_report.md#hmackey_lengthkey_384">HMAC.KEY_LENGTH.KEY_384</a><br><a href="01_feature_report.md#hmackey_lengthkey_512">HMAC.KEY_LENGTH.KEY_512</a></td>
</tr>
  </tbody>
</table>

## wipe_secret
This test issues wipe_secret on hmac process datapath.
Based on the smoke sequence, this sequence increases the message length, and randomly
issues wipe_secret in one of the following scenarios:

- Before entering HMAC secret keys.
  This scenario represents wiping secrets when HMAC is idle.
- Before issuing HMAC start command.
  This scenario represents wiping secrets when HMAC entered secret keys.
- Before issuing HMAC process command.
  This scenario represents wiping secrets when HMAC is streaming in message data.
- Before HMAC finishes hashing process.
  This scenario represents wiping secrets when HMAC is hashing messages and keys.

**Checks**:
The scoreboard will check if digest data are corrupted.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#hmac_wipe_secret">hmac_wipe_secret</a></td>
  <td><a href="01_feature_report.md#hmacsecure_wipe">HMAC.SECURE_WIPE</a></td>
</tr>
  </tbody>
</table>

## write_config_and_secret_key_during_msg_wr
Change config registers and secret keys during msg write, make sure access is blocked.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#hmac_smoke">hmac_smoke</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>
