# aes Testpoint Report

## algorithm

Compare cypher text from DUT with the output of a C model using same key and data.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aes_config_error">aes_config_error</a><br><a href="03_test_report.md#aes_smoke">aes_smoke</a><br><a href="03_test_report.md#aes_stress">aes_stress</a></td>
  <td><a href="01_feature_report.md#aeskey_len128">AES.KEY_LEN.128</a><br><a href="01_feature_report.md#aeskey_len192">AES.KEY_LEN.192</a><br><a href="01_feature_report.md#aeskey_len256">AES.KEY_LEN.256</a><br><a href="01_feature_report.md#aesmanual_operation">AES.MANUAL_OPERATION</a><br><a href="01_feature_report.md#aesmodecbc">AES.MODE.CBC</a><br><a href="01_feature_report.md#aesmodecfb-128">AES.MODE.CFB-128</a><br><a href="01_feature_report.md#aesmodectr">AES.MODE.CTR</a><br><a href="01_feature_report.md#aesmodeecb">AES.MODE.ECB</a><br><a href="01_feature_report.md#aesmodeofb">AES.MODE.OFB</a></td>
</tr>
  </tbody>
</table>

## back2back

Back to back Messages are not possible as the DUT need to be idle before writing a new configuration.
But Back2back verifies that DUT can handle back to back data blocks and other spacings.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aes_b2b">aes_b2b</a><br><a href="03_test_report.md#aes_stress">aes_stress</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## backpressure

Try to write data to registers without offloading the DUT output to verify Stall functionality.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aes_stress">aes_stress</a></td>
  <td><a href="01_feature_report.md#aesmanual_operation">AES.MANUAL_OPERATION</a><br><a href="01_feature_report.md#aesstatusstall">AES.STATUS.STALL</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aes_enc (dragonfly)
Verify the AES operation.

Procedure:

- Set up the desired operation, ECB mode, 256b key length, and set the engine to
  manual operation. Set mask_reseeding to 1 per block.
- Trigger the encryption by loading the plaintext.
- Wait for the AES operation to complete by polling the status register and read the
  result.

- The above procedure should be performed twice. First for encryption. Second for
  decryption of the result using the same key.
- Check that the decryption result matches the original plaintext.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_aes_enc-dragonfly">chip_sw_aes_enc (dragonfly)</a><br><a href="03_test_report.md#chip_sw_aes_enc_jitter_en-dragonfly">chip_sw_aes_enc_jitter_en (dragonfly)</a></td>
  <td><a href="01_feature_report.md#aeskey_len256">AES.KEY_LEN.256</a><br><a href="01_feature_report.md#aesmanual_operation">AES.MANUAL_OPERATION</a><br><a href="01_feature_report.md#aesmodeecb">AES.MODE.ECB</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aes_enc (egret)
Verify the AES operation.

Procedure:

- Set up the desired operation, ECB mode, 256b key length, and set the engine to
  manual operation. Set mask_reseeding to 1 per block.
- Trigger the encryption by loading the plaintext.
- Wait for the AES operation to complete by polling the status register and read the
  result.

- The above procedure should be performed twice. First for encryption. Second for
  decryption of the result using the same key.
- Check that the decryption result matches the original plaintext.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_aes_enc-egret">chip_sw_aes_enc (egret)</a><br><a href="03_test_report.md#chip_sw_aes_enc_jitter_en-egret">chip_sw_aes_enc_jitter_en (egret)</a></td>
  <td><a href="01_feature_report.md#aeskey_len256">AES.KEY_LEN.256</a><br><a href="01_feature_report.md#aesmanual_operation">AES.MANUAL_OPERATION</a><br><a href="01_feature_report.md#aesmodeecb">AES.MODE.ECB</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aes_entropy (dragonfly)
Verify the AES entropy input used by the internal PRNGs.

- Configure encryption using the CBC mode, key length 256, and set the engine to
  manual operation.
- Write the initial key share, IV and data in CSRs (known combinations).
- Write the PRNG_RESEED bit to reseed the internal state of the PRNG.
- Poll the status idle bit to ensure reseed operation is complete.
- Trigger the AES operation to run and wait for it to complete.
- Check the ciphertext against the expected value.
- Write the KEY_IV_DATA_IN_CLEAR and DATA_OUT_CLEAR trigger bits to 1 and wait for it to
  complete by polling the status idle bit.
- Read back the data out CSRs - they should all read garbage values.
- Assertion check verifies that the IV are also garbage, i.e. different from the
  originally written values.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_aes_entropy-dragonfly">chip_sw_aes_entropy (dragonfly)</a></td>
  <td><a href="01_feature_report.md#aescleardata_out">AES.CLEAR.DATA_OUT</a><br><a href="01_feature_report.md#aesclearkey_iv_data_in">AES.CLEAR.KEY_IV_DATA_IN</a><br><a href="01_feature_report.md#aesmodecbc">AES.MODE.CBC</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aes_entropy (egret)
Verify the AES entropy input used by the internal PRNGs.

- Configure encryption using the CBC mode, key length 256, and set the engine to
  manual operation.
- Write the initial key share, IV and data in CSRs (known combinations).
- Write the PRNG_RESEED bit to reseed the internal state of the PRNG.
- Poll the status idle bit to ensure reseed operation is complete.
- Trigger the AES operation to run and wait for it to complete.
- Check the ciphertext against the expected value.
- Write the KEY_IV_DATA_IN_CLEAR and DATA_OUT_CLEAR trigger bits to 1 and wait for it to
  complete by polling the status idle bit.
- Read back the data out CSRs - they should all read garbage values.
- Assertion check verifies that the IV are also garbage, i.e. different from the
  originally written values.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_aes_entropy-egret">chip_sw_aes_entropy (egret)</a></td>
  <td><a href="01_feature_report.md#aescleardata_out">AES.CLEAR.DATA_OUT</a><br><a href="01_feature_report.md#aesclearkey_iv_data_in">AES.CLEAR.KEY_IV_DATA_IN</a><br><a href="01_feature_report.md#aesmodecbc">AES.MODE.CBC</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aes_force_prng_reseed (dragonfly)
Verify that the AES module stalls/halts when the entropy
complex is disabled before starting encryption and enables
output of encryption once the entropy complex is re-enabled.

Procedure:

- After proper initialization of AES and entropy modules, disable
  the entire entropy complex using `entropy_testutils_stop_all()`.
  - Configure the AES encryption operation to process some number of
    blocks with:
    - Operation: Encrypt
    - Mode: ECB
    - Key Length: 128 bits
    - Key Provider: Software-provided key
    - Manual Operation: Enabled
    - Mask Reseeding: Reseed per block
    - Reseed on Key Change: Enabled (When KEY_TOUCH_FORCES_RESEED is
      set, the PRNG reseed is triggered every time a key changes)
    - Force Masks: Enabled
  - Generate AES key.
  - At this point dif_aes_start() will write the key register which
    will trigger reseed request.
  - This request will stall the output of the encrypted data until
    entropy is re-enabled.
  - Verify that the AES module is halted by checking that
    `kDifAesStatusOutputValid` is not set.
  - Re-enable the entropy complex using
    `entropy_testutils_auto_mode_init()`.
  - Wait for some time for the entropy complex to stabilize.
  - Wait for the AES module to produce output valid
    (`kDifAesStatusOutputValid`).
  - Read the encrypted output data using `dif_aes_read_output()`.
  - Process all the blocks and ensure AES completes encryption
    operation.
    - Verify that the AES module is idle at the end of encryption
      operation (`kDifAesStatusIdle`).

  Expected Outcome:

  - The AES module halts output when the entropy complex is disabled
    before starting encryption.
  - After re-enabling the entropy complex, the AES module resumes
    encryption and produces the expected output.
  - The test verifies that the AES module correctly handles halting
    and resuming based on the availability of entropy.


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
  <td><a href="01_feature_report.md#aesmodeecb">AES.MODE.ECB</a><br><a href="01_feature_report.md#aesprngkey_touch_forces_reseed">AES.PRNG.KEY_TOUCH_FORCES_RESEED</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aes_force_prng_reseed (egret)
Verify that the AES module stalls/halts when the entropy
complex is disabled before starting encryption and enables
output of encryption once the entropy complex is re-enabled.

Procedure:

- After proper initialization of AES and entropy modules, disable
  the entire entropy complex using `entropy_testutils_stop_all()`.
  - Configure the AES encryption operation to process some number of
    blocks with:
    - Operation: Encrypt
    - Mode: ECB
    - Key Length: 128 bits
    - Key Provider: Software-provided key
    - Manual Operation: Enabled
    - Mask Reseeding: Reseed per block
    - Reseed on Key Change: Enabled (When KEY_TOUCH_FORCES_RESEED is
      set, the PRNG reseed is triggered every time a key changes)
    - Force Masks: Enabled
  - Generate AES key.
  - At this point dif_aes_start() will write the key register which
    will trigger reseed request.
  - This request will stall the output of the encrypted data until
    entropy is re-enabled.
  - Verify that the AES module is halted by checking that
    `kDifAesStatusOutputValid` is not set.
  - Re-enable the entropy complex using
    `entropy_testutils_auto_mode_init()`.
  - Wait for some time for the entropy complex to stabilize.
  - Wait for the AES module to produce output valid
    (`kDifAesStatusOutputValid`).
  - Read the encrypted output data using `dif_aes_read_output()`.
  - Process all the blocks and ensure AES completes encryption
    operation.
    - Verify that the AES module is idle at the end of encryption
      operation (`kDifAesStatusIdle`).

  Expected Outcome:

  - The AES module halts output when the entropy complex is disabled
    before starting encryption.
  - After re-enabling the entropy complex, the AES module resumes
    encryption and produces the expected output.
  - The test verifies that the AES module correctly handles halting
    and resuming based on the availability of entropy.


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
  <td><a href="01_feature_report.md#aesmodeecb">AES.MODE.ECB</a><br><a href="01_feature_report.md#aesprngkey_touch_forces_reseed">AES.PRNG.KEY_TOUCH_FORCES_RESEED</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aes_idle (dragonfly)
Verify AES idle signaling to clkmgr.

- Write the AES clk hint to 0 within clkmgr to indicate AES clk can be gated and
  verify that the AES clk hint status within clkmgr reads 0 (AES is disabled).
- Write the AES clk hint to 1 within clkmgr to indicate AES clk can be enabled.
- Initiate an AES operation with a known key, plain text and digest, write AES clk
  hint to 0 and verify that the AES clk hint status within clkmgr now reads 1 (AES
  is enabled), before the AES operation is complete.
- After the AES operation is complete verify that the AES clk hint status within
  clkmgr now reads 0 again (AES is disabled).
- Write the AES clk hint to 1, read and check the AES output for correctness.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_aes_idle-dragonfly">chip_sw_aes_idle (dragonfly)</a></td>
  <td><a href="01_feature_report.md#aesmodeecb">AES.MODE.ECB</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aes_idle (egret)
Verify AES idle signaling to clkmgr.

- Write the AES clk hint to 0 within clkmgr to indicate AES clk can be gated and
  verify that the AES clk hint status within clkmgr reads 0 (AES is disabled).
- Write the AES clk hint to 1 within clkmgr to indicate AES clk can be enabled.
- Initiate an AES operation with a known key, plain text and digest, write AES clk
  hint to 0 and verify that the AES clk hint status within clkmgr now reads 1 (AES
  is enabled), before the AES operation is complete.
- After the AES operation is complete verify that the AES clk hint status within
  clkmgr now reads 0 again (AES is disabled).
- Write the AES clk hint to 1, read and check the AES output for correctness.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_aes_idle-egret">chip_sw_aes_idle (egret)</a></td>
  <td><a href="01_feature_report.md#aesmodeecb">AES.MODE.ECB</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aes_interrupt_encryption (dragonfly)
Verify that a multi-block encryption can be interrupted and continued.

This test should:

  - start the encryption of a four-block message.
  - interrupt it after two blocks by reading back the IV register.
  - perform an encryption of a different message using a different key.
  - re-store and complete the original encryption

Note: AES should start this test using the automatic (default) operation. This means
      that the MANUAL_OPERATION bit in CTRL_SHADOWED register is set to 0.

Procedure:

- Configure encryption using the desired mode, key length, IV, and set the engine to
  automatic operation.
- Using dif_aes_process_data, encrypt the first two blocks.
- Using dif_aes_read_iv read the IV. Note that AES has automatically updated the content
  of this register. This IV will be needed later to continue this encryption.
- De-initialize automatic operation. This step is necessary to clear all registers.
- Perform an encryption using a different data and key. Message size, key size and mode
  can be chosen arbitrarily.
- Continue the original encryption:
    - Configure the operation using the previously read IV
    - Process the remaining plaintext blocks using dif_aes_process_data
- Decrypt the result (using the original key and IV)
- Check that the decryption result matches the original plaintext.


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
  <td><a href="01_feature_report.md#aesmodecbc">AES.MODE.CBC</a><br><a href="01_feature_report.md#aesmodecfb-128">AES.MODE.CFB-128</a><br><a href="01_feature_report.md#aesmodectr">AES.MODE.CTR</a><br><a href="01_feature_report.md#aesmodeofb">AES.MODE.OFB</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aes_interrupt_encryption (egret)
Verify that a multi-block encryption can be interrupted and continued.

This test should:

  - start the encryption of a four-block message.
  - interrupt it after two blocks by reading back the IV register.
  - perform an encryption of a different message using a different key.
  - re-store and complete the original encryption

Note: AES should start this test using the automatic (default) operation. This means
      that the MANUAL_OPERATION bit in CTRL_SHADOWED register is set to 0.

Procedure:

- Configure encryption using the desired mode, key length, IV, and set the engine to
  automatic operation.
- Using dif_aes_process_data, encrypt the first two blocks.
- Using dif_aes_read_iv read the IV. Note that AES has automatically updated the content
  of this register. This IV will be needed later to continue this encryption.
- De-initialize automatic operation. This step is necessary to clear all registers.
- Perform an encryption using a different data and key. Message size, key size and mode
  can be chosen arbitrarily.
- Continue the original encryption:
    - Configure the operation using the previously read IV
    - Process the remaining plaintext blocks using dif_aes_process_data
- Decrypt the result (using the original key and IV)
- Check that the decryption result matches the original plaintext.


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
  <td><a href="01_feature_report.md#aesmodecbc">AES.MODE.CBC</a><br><a href="01_feature_report.md#aesmodecfb-128">AES.MODE.CFB-128</a><br><a href="01_feature_report.md#aesmodectr">AES.MODE.CTR</a><br><a href="01_feature_report.md#aesmodeofb">AES.MODE.OFB</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aes_masking_off (dragonfly)
Verify the AES masking off feature for ES.

- Perform known-answer test using CSRNG SW application interface.
- Verify CSRNG produces the deterministic seed leading to an all-zero output of the AES
  masking PRNG.
- Configure EDN to perform a CSRNG instantiate followed by repeated generate and reseed
  commands using the maximum amount of additional data and no entropy input in automatic
  mode.
- Let CSRNG produce and forward to EDN the deterministic seed leading to an all-zero
  output of the AES masking PRNG.
- Initialize AES and set the force_masks configuration bit.
- Configure an AES key of which the second share is zero.
- Trigger a reseed operation of the masking PRNG inside AES to load the deterministic
  seed produced by CSRNG and distributed by EDN.
- Verify that the masking PRNG outputs an all-zero vector. (Note: This may not be
  possible to verify in silicon.)
- Encrypt a message of multiple blocks using AES.
- Verify that the second share of the initial, intermediate and output state is zero.
- Verify that the second share of the SubBytes input and output is zero. (Note: This
  may not possible to verify in silicon.)
- Verify that the produced cipher text is correct.
- Repeat the entire procedure with PRNG_RESEED_RATE set to PER_1. Verify that the
  second share of intermediate and output state is not zero.

Notes for silicon targets:

- The AES.PRNG.FORCE_MASKS feature is relevant for penetration testing only and a SCA evaluation setup is required for its verification.
  This is done using other routines as part of the experimental setup for penetration testing.
  The only thing that can be tested on silicon / FPGA for SiVal is the known-answer test using the CSRNG SW application interface for which a dedicated SiVal test exists.
  For this reason, the chip_sw_aes_masking_off test is run in simulation only.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_aes_masking_off-dragonfly">chip_sw_aes_masking_off (dragonfly)</a></td>
  <td><a href="01_feature_report.md#aesprngforce_masks">AES.PRNG.FORCE_MASKS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aes_masking_off (egret)
Verify the AES masking off feature for ES.

- Perform known-answer test using CSRNG SW application interface.
- Verify CSRNG produces the deterministic seed leading to an all-zero output of the AES
  masking PRNG.
- Configure EDN to perform a CSRNG instantiate followed by repeated generate and reseed
  commands using the maximum amount of additional data and no entropy input in automatic
  mode.
- Let CSRNG produce and forward to EDN the deterministic seed leading to an all-zero
  output of the AES masking PRNG.
- Initialize AES and set the force_masks configuration bit.
- Configure an AES key of which the second share is zero.
- Trigger a reseed operation of the masking PRNG inside AES to load the deterministic
  seed produced by CSRNG and distributed by EDN.
- Verify that the masking PRNG outputs an all-zero vector. (Note: This may not be
  possible to verify in silicon.)
- Encrypt a message of multiple blocks using AES.
- Verify that the second share of the initial, intermediate and output state is zero.
- Verify that the second share of the SubBytes input and output is zero. (Note: This
  may not possible to verify in silicon.)
- Verify that the produced cipher text is correct.
- Repeat the entire procedure with PRNG_RESEED_RATE set to PER_1. Verify that the
  second share of intermediate and output state is not zero.

Notes for silicon targets:

- The AES.PRNG.FORCE_MASKS feature is relevant for penetration testing only and a SCA evaluation setup is required for its verification.
  This is done using other routines as part of the experimental setup for penetration testing.
  The only thing that can be tested on silicon / FPGA for SiVal is the known-answer test using the CSRNG SW application interface for which a dedicated SiVal test exists.
  For this reason, the chip_sw_aes_masking_off test is run in simulation only.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_aes_masking_off-egret">chip_sw_aes_masking_off (egret)</a></td>
  <td><a href="01_feature_report.md#aesprngforce_masks">AES.PRNG.FORCE_MASKS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aes_multi_block (dragonfly)
Verify the AES operations on multi-block messages.
This test should be performed for all supported modes (ECB, CBC, CFB-128, OFB and CTR)
and all supported key lengths (128/192/256).

Note: The number of message blocks has to be at least 4.

Note: AES should start this test using the automatic (default) operation. This means
      that the MANUAL_OPERATION bit in CTRL_SHADOWED register is set to 0.

Procedure:

- Configure the desired operation, mode, key length, and set the engine to automatic
  operation. Configure the IV for modes that require it.
- Using dif_aes_start()  and dif_aes_process_data(), encrypt the message.
- Check the output for correctness against the expected value.

- The above procedure should be performed twice. First for encryption. Second for
  decryption of the result using the same key (and same IV if needed).
- Check that the decryption result matches the original plaintext.


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
  <td><a href="01_feature_report.md#aeskey_len128">AES.KEY_LEN.128</a><br><a href="01_feature_report.md#aeskey_len192">AES.KEY_LEN.192</a><br><a href="01_feature_report.md#aeskey_len256">AES.KEY_LEN.256</a><br><a href="01_feature_report.md#aesmodecbc">AES.MODE.CBC</a><br><a href="01_feature_report.md#aesmodecfb-128">AES.MODE.CFB-128</a><br><a href="01_feature_report.md#aesmodectr">AES.MODE.CTR</a><br><a href="01_feature_report.md#aesmodeecb">AES.MODE.ECB</a><br><a href="01_feature_report.md#aesmodeofb">AES.MODE.OFB</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aes_multi_block (egret)
Verify the AES operations on multi-block messages.
This test should be performed for all supported modes (ECB, CBC, CFB-128, OFB and CTR)
and all supported key lengths (128/192/256).

Note: The number of message blocks has to be at least 4.

Note: AES should start this test using the automatic (default) operation. This means
      that the MANUAL_OPERATION bit in CTRL_SHADOWED register is set to 0.

Procedure:

- Configure the desired operation, mode, key length, and set the engine to automatic
  operation. Configure the IV for modes that require it.
- Using dif_aes_start()  and dif_aes_process_data(), encrypt the message.
- Check the output for correctness against the expected value.

- The above procedure should be performed twice. First for encryption. Second for
  decryption of the result using the same key (and same IV if needed).
- Check that the decryption result matches the original plaintext.


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
  <td><a href="01_feature_report.md#aeskey_len128">AES.KEY_LEN.128</a><br><a href="01_feature_report.md#aeskey_len192">AES.KEY_LEN.192</a><br><a href="01_feature_report.md#aeskey_len256">AES.KEY_LEN.256</a><br><a href="01_feature_report.md#aesmodecbc">AES.MODE.CBC</a><br><a href="01_feature_report.md#aesmodecfb-128">AES.MODE.CFB-128</a><br><a href="01_feature_report.md#aesmodectr">AES.MODE.CTR</a><br><a href="01_feature_report.md#aesmodeecb">AES.MODE.ECB</a><br><a href="01_feature_report.md#aesmodeofb">AES.MODE.OFB</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aes_prng_reseed (dragonfly)
 Verify that the AES module halts when a PRNG reseed is
required but the entropy complex is disabled, and resumes
encryption once the entropy complex is re-enabled.

Procedure:

- After proper initialization of the AES and entropy modules,
  configure the AES encryption operation to process a number of
  blocks with:
  - Operation: Encrypt
  - Mode: ECB
  - Key Length: 128 bits
  - Key Provider: Software-provided key
  - Manual Operation: Disabled (Automatic operation)
  - Mask Reseeding: Reseed per 64 blocks
    (`kDifAesReseedPer64Block`)
  - Reseed on Key Change: Enabled
  - Force Masks: Disabled

- Generate AES key.

- Initialize the AES module and start the AES operation using
  `dif_aes_start()`.

- Process blocks using the following steps:
  - Disable entropy for a block fewer than 64.
  - For each block,
      - Continue encrypting blocks (fewer than 64 blocks)
      - Once processing reaches the block where the entropy complex
        is disabled
        - Disable the entire entropy complex using
          `entropy_testutils_stop_all()`.
        - This will halt the AES module when a PRNG reseed is
          required (i.e after 64 blocks).
      - Re-enable the entropy complex to resume encryption:
        - Verify that the AES module is halted by checking that
          `kDifAesStatusOutputValid` is not set for the 63rd block
        - Re-enable the entropy complex using
          `entropy_testutils_auto_mode_init()`.
        - Wait for some time for the entropy complex to stabilize.
        - Wait for the AES module to produce output valid
          (`kDifAesStatusOutputValid`).
        - Read the encrypted output data using
          `dif_aes_read_output()`.

- Finish the AES encryption operation by calling `dif_aes_end()`.

- Verify that the AES module is idle at the end of the encryption
  operation (`kDifAesStatusIdle`).
- Repeat the test for a reseed rate kDifAesReseedPer8kBlock and
  a message longer than 8K blocks.

Expected Outcome:

- The AES module halts when a PRNG reseed is required but the
  entropy complex is disabled.
- After re-enabling the entropy complex, the AES module resumes
  encryption and produces the expected output.
- The test verifies that the AES module correctly handles halting
  and resuming based on the availability of entropy and the
  configured mask reseeding rate.


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
  <td><a href="01_feature_report.md#aesmodeecb">AES.MODE.ECB</a><br><a href="01_feature_report.md#aesprngreseed_rate">AES.PRNG.RESEED_RATE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aes_prng_reseed (egret)
 Verify that the AES module halts when a PRNG reseed is
required but the entropy complex is disabled, and resumes
encryption once the entropy complex is re-enabled.

Procedure:

- After proper initialization of the AES and entropy modules,
  configure the AES encryption operation to process a number of
  blocks with:
  - Operation: Encrypt
  - Mode: ECB
  - Key Length: 128 bits
  - Key Provider: Software-provided key
  - Manual Operation: Disabled (Automatic operation)
  - Mask Reseeding: Reseed per 64 blocks
    (`kDifAesReseedPer64Block`)
  - Reseed on Key Change: Enabled
  - Force Masks: Disabled

- Generate AES key.

- Initialize the AES module and start the AES operation using
  `dif_aes_start()`.

- Process blocks using the following steps:
  - Disable entropy for a block fewer than 64.
  - For each block,
      - Continue encrypting blocks (fewer than 64 blocks)
      - Once processing reaches the block where the entropy complex
        is disabled
        - Disable the entire entropy complex using
          `entropy_testutils_stop_all()`.
        - This will halt the AES module when a PRNG reseed is
          required (i.e after 64 blocks).
      - Re-enable the entropy complex to resume encryption:
        - Verify that the AES module is halted by checking that
          `kDifAesStatusOutputValid` is not set for the 63rd block
        - Re-enable the entropy complex using
          `entropy_testutils_auto_mode_init()`.
        - Wait for some time for the entropy complex to stabilize.
        - Wait for the AES module to produce output valid
          (`kDifAesStatusOutputValid`).
        - Read the encrypted output data using
          `dif_aes_read_output()`.

- Finish the AES encryption operation by calling `dif_aes_end()`.

- Verify that the AES module is idle at the end of the encryption
  operation (`kDifAesStatusIdle`).
- Repeat the test for a reseed rate kDifAesReseedPer8kBlock and
  a message longer than 8K blocks.

Expected Outcome:

- The AES module halts when a PRNG reseed is required but the
  entropy complex is disabled.
- After re-enabling the entropy complex, the AES module resumes
  encryption and produces the expected output.
- The test verifies that the AES module correctly handles halting
  and resuming based on the availability of entropy and the
  configured mask reseeding rate.


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
  <td><a href="01_feature_report.md#aesmodeecb">AES.MODE.ECB</a><br><a href="01_feature_report.md#aesprngreseed_rate">AES.PRNG.RESEED_RATE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aes_sideload (dragonfly)
Verify the AES sideload mechanism.

- Configure the keymgr to generate an aes key.
- Configure the AES to use the sideloaded key.
- Load the plaintext into the AES.
- Trigger the AES encryption and wait for it to complete.
- Verify that the ciphertext is different from the plaintext.
- Load the ciphertext into the AES.
- Trigger the AES decryption and wait for it to complete.
- Verify that the output is equal to the plain text.
- Clear the key in the keymgr and decrypt the ciphertext again.
- Verify that output is not equal to the plain text.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_keymgr_sideload_aes-dragonfly">chip_sw_keymgr_sideload_aes (dragonfly)</a></td>
  <td><a href="01_feature_report.md#aeskeysideload">AES.KEY.SIDELOAD</a><br><a href="01_feature_report.md#aesmodeecb">AES.MODE.ECB</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aes_sideload (egret)
Verify the AES sideload mechanism.

- Configure the keymgr to generate an aes key.
- Configure the AES to use the sideloaded key.
- Load the plaintext into the AES.
- Trigger the AES encryption and wait for it to complete.
- Verify that the ciphertext is different from the plaintext.
- Load the ciphertext into the AES.
- Trigger the AES decryption and wait for it to complete.
- Verify that the output is equal to the plain text.
- Clear the key in the keymgr and decrypt the ciphertext again.
- Verify that output is not equal to the plain text.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_keymgr_sideload_aes-egret">chip_sw_keymgr_sideload_aes (egret)</a></td>
  <td><a href="01_feature_report.md#aeskeysideload">AES.KEY.SIDELOAD</a><br><a href="01_feature_report.md#aesmodeecb">AES.MODE.ECB</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aes_stall_test (dragonfly)
Verify that the AES module's stall bit assertion
when multiple input blocks are loaded without reading
output data, and resumes encryption once the output data is read.

Procedure:

- Initialize the AES.
- Configure the AES encryption operation with the following settings:
  - Operation: Encrypt
  - Mode: ECB
  - Key Length: 128 bits
  - Key Provider: Software-provided key
  - Mask Reseeding: Reseed per block
  - Manual Operation: Auto
  - Reseed on Key Change: Enabled
  - Force Masks: Enabled
- Generate an AES key and load it for encryption.
- Prepare input blocks with random plaintext data.
- Load multiple blocks into AES without reading output data to simulate
  a stall condition.
  - Verify that `kDifAesStatusStall` is set.
- Once the AES is stalled, read the output blocks one by one.
  - Verify that reading the output clears the stall condition.
- Ensure the AES encryption operation completes successfully
  and that the AES module reaches the idle state at the end of the test.

Expected Outcome:

- AES enters a stall condition when multiple input blocks are loaded without
  reading output.
- Reading the output clears the stall condition, allowing AES to resume
  encryption.
- The test verifies correct handling of the stall condition and that
  the AES operation completes as expected.


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
  <td><a href="01_feature_report.md#aesmodeecb">AES.MODE.ECB</a><br><a href="01_feature_report.md#aesstatusstall">AES.STATUS.STALL</a></td>
</tr>
  </tbody>
</table>

## chip_sw_aes_stall_test (egret)
Verify that the AES module's stall bit assertion
when multiple input blocks are loaded without reading
output data, and resumes encryption once the output data is read.

Procedure:

- Initialize the AES.
- Configure the AES encryption operation with the following settings:
  - Operation: Encrypt
  - Mode: ECB
  - Key Length: 128 bits
  - Key Provider: Software-provided key
  - Mask Reseeding: Reseed per block
  - Manual Operation: Auto
  - Reseed on Key Change: Enabled
  - Force Masks: Enabled
- Generate an AES key and load it for encryption.
- Prepare input blocks with random plaintext data.
- Load multiple blocks into AES without reading output data to simulate
  a stall condition.
  - Verify that `kDifAesStatusStall` is set.
- Once the AES is stalled, read the output blocks one by one.
  - Verify that reading the output clears the stall condition.
- Ensure the AES encryption operation completes successfully
  and that the AES module reaches the idle state at the end of the test.

Expected Outcome:

- AES enters a stall condition when multiple input blocks are loaded without
  reading output.
- Reading the output clears the stall condition, allowing AES to resume
  encryption.
- The test verifies correct handling of the stall condition and that
  the AES operation completes as expected.


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
  <td><a href="01_feature_report.md#aesmodeecb">AES.MODE.ECB</a><br><a href="01_feature_report.md#aesstatusstall">AES.STATUS.STALL</a></td>
</tr>
  </tbody>
</table>

## deinitialization

Make sure that there is no residual data from latest operation.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aes_deinit">aes_deinit</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## failure_test


- Tests what happens if a register is written a the wrong time?
  If a key does not match the key setting etc.
  Will the DUT ignore or fail gracefully.
- Enter a 256bit key but set DUT to use 128bit for encryption.
  Then enter the 128bit of the key and use for decryption.
  Will result match plain text and vice.
- Write unsupported configurations (Key length and mode are 1 hot, what happens if more than one bit is set.)


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aes_alert_reset">aes_alert_reset</a><br><a href="03_test_report.md#aes_config_error">aes_config_error</a><br><a href="03_test_report.md#aes_man_cfg_err">aes_man_cfg_err</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## fault_inject

Verify that injecting bit errors in one of the state machines or the round counter triggers an error


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aes_cipher_fi">aes_cipher_fi</a><br><a href="03_test_report.md#aes_cipher_fi_walk">aes_cipher_fi_walk</a><br><a href="03_test_report.md#aes_control_fi">aes_control_fi</a><br><a href="03_test_report.md#aes_control_fi_walk">aes_control_fi_walk</a><br><a href="03_test_report.md#aes_core_fi_walk">aes_core_fi_walk</a><br><a href="03_test_report.md#aes_fi">aes_fi</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## key_length

Randomly select key length to verify all supported key lengths are working.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aes_config_error">aes_config_error</a><br><a href="03_test_report.md#aes_smoke">aes_smoke</a><br><a href="03_test_report.md#aes_stress">aes_stress</a></td>
  <td><a href="01_feature_report.md#aeskey_len128">AES.KEY_LEN.128</a><br><a href="01_feature_report.md#aeskey_len192">AES.KEY_LEN.192</a><br><a href="01_feature_report.md#aeskey_len256">AES.KEY_LEN.256</a><br><a href="01_feature_report.md#aesmanual_operation">AES.MANUAL_OPERATION</a><br><a href="01_feature_report.md#aesmodecbc">AES.MODE.CBC</a><br><a href="01_feature_report.md#aesmodecfb-128">AES.MODE.CFB-128</a><br><a href="01_feature_report.md#aesmodectr">AES.MODE.CTR</a><br><a href="01_feature_report.md#aesmodeecb">AES.MODE.ECB</a><br><a href="01_feature_report.md#aesmodeofb">AES.MODE.OFB</a></td>
</tr>
  </tbody>
</table>

## multi_message

Run multiple messages in a random mix of encryption / decryption.
Each message should select its mode randomly.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aes_alert_reset">aes_alert_reset</a><br><a href="03_test_report.md#aes_config_error">aes_config_error</a><br><a href="03_test_report.md#aes_smoke">aes_smoke</a><br><a href="03_test_report.md#aes_stress">aes_stress</a></td>
  <td><a href="01_feature_report.md#aeskey_len128">AES.KEY_LEN.128</a><br><a href="01_feature_report.md#aeskey_len192">AES.KEY_LEN.192</a><br><a href="01_feature_report.md#aeskey_len256">AES.KEY_LEN.256</a><br><a href="01_feature_report.md#aesmodecbc">AES.MODE.CBC</a><br><a href="01_feature_report.md#aesmodecfb-128">AES.MODE.CFB-128</a><br><a href="01_feature_report.md#aesmodectr">AES.MODE.CTR</a><br><a href="01_feature_report.md#aesmodeecb">AES.MODE.ECB</a><br><a href="01_feature_report.md#aesmodeofb">AES.MODE.OFB</a></td>
</tr>
  </tbody>
</table>

## nist_test_vectors

Verify that the DUT handles the NIST test vectors correctly.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aes_nist_vectors">aes_nist_vectors</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## reseeding

Verify that internal PRNGs are effectively reseeded upon manually triggering a PRNG reseed, and - depending on the configuration - if the initial key changes.
Verify that the masking PRNG is reseeded automatically at the correct reseed rate.
To reduce simulation time, the block counter triggering the automatic reseeding is manually changed to lower values.
Verify that the PRNGs do not get reseeded unexpectedly.
Verify that the data received from EDN effectively propagates into the PRNGs.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aes_reseed">aes_reseed</a></td>
  <td><a href="01_feature_report.md#aesmanual_operation">AES.MANUAL_OPERATION</a><br><a href="01_feature_report.md#aesprngforce_masks">AES.PRNG.FORCE_MASKS</a><br><a href="01_feature_report.md#aesprngkey_touch_forces_reseed">AES.PRNG.KEY_TOUCH_FORCES_RESEED</a><br><a href="01_feature_report.md#aesprngreseed_rate">AES.PRNG.RESEED_RATE</a></td>
</tr>
  </tbody>
</table>

## reset_recovery

Pull reset at random times, make sure DUT recover/resets correctly and there is no residual data left in the registers.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aes_alert_reset">aes_alert_reset</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## sideload

Verify that DUT uses sideload correctly when sideload is enabled.
and that it ignores any valid on the bus when disabled.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aes_sideload">aes_sideload</a><br><a href="03_test_report.md#aes_stress">aes_stress</a></td>
  <td><a href="01_feature_report.md#aeskeysideload">AES.KEY.SIDELOAD</a><br><a href="01_feature_report.md#aesmanual_operation">AES.MANUAL_OPERATION</a></td>
</tr>
  </tbody>
</table>

## smoke

Encrypt a plain text read it back - decrypt and compare to input but use reference model to compare after both encryption and decryption.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aes_smoke">aes_smoke</a></td>
  <td><a href="01_feature_report.md#aeskey_len128">AES.KEY_LEN.128</a><br><a href="01_feature_report.md#aeskey_len192">AES.KEY_LEN.192</a><br><a href="01_feature_report.md#aeskey_len256">AES.KEY_LEN.256</a><br><a href="01_feature_report.md#aesmanual_operation">AES.MANUAL_OPERATION</a><br><a href="01_feature_report.md#aesmodecbc">AES.MODE.CBC</a><br><a href="01_feature_report.md#aesmodecfb-128">AES.MODE.CFB-128</a><br><a href="01_feature_report.md#aesmodectr">AES.MODE.CTR</a><br><a href="01_feature_report.md#aesmodeecb">AES.MODE.ECB</a><br><a href="01_feature_report.md#aesmodeofb">AES.MODE.OFB</a></td>
</tr>
  </tbody>
</table>

## stress

This will combine the other individual testpoints to ensure we stress test everything across the board.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aes_stress">aes_stress</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## stress_all

Run assorted sequences back-to-back.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aes_stress_all">aes_stress_all</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## trigger_clear_test

Exercise trigger and clear registers at random times to make sure we handle the different cornercases correctly.
Example of a cornercases clearing data input or data output before the data is consumed or the DUT finishes an operation.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aes_clear">aes_clear</a></td>
  <td><a href="01_feature_report.md#aescleardata_out">AES.CLEAR.DATA_OUT</a><br><a href="01_feature_report.md#aesclearkey_iv_data_in">AES.CLEAR.KEY_IV_DATA_IN</a><br><a href="01_feature_report.md#aesmanual_operation">AES.MANUAL_OPERATION</a></td>
</tr>
  </tbody>
</table>

## wake_up

Basic hello world,  encrypt a plain text read it back - decrypt and compare to input.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#aes_wake_up">aes_wake_up</a></td>
  <td><a href="01_feature_report.md#aeskey_len128">AES.KEY_LEN.128</a><br><a href="01_feature_report.md#aeskey_len192">AES.KEY_LEN.192</a><br><a href="01_feature_report.md#aeskey_len256">AES.KEY_LEN.256</a><br><a href="01_feature_report.md#aesmanual_operation">AES.MANUAL_OPERATION</a><br><a href="01_feature_report.md#aesmodecbc">AES.MODE.CBC</a><br><a href="01_feature_report.md#aesmodecfb-128">AES.MODE.CFB-128</a><br><a href="01_feature_report.md#aesmodectr">AES.MODE.CTR</a><br><a href="01_feature_report.md#aesmodeecb">AES.MODE.ECB</a><br><a href="01_feature_report.md#aesmodeofb">AES.MODE.OFB</a></td>
</tr>
  </tbody>
</table>
