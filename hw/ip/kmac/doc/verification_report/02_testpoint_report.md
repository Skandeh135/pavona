# kmac Testpoint Report

## app

Test that the Keymgr/ROM/LC can all initiate a KMAC operation through
the application interface - Keymgr uses KMAC hash, while ROM/LC use CShake.
Use an array of kmac_app_agents to send message data to the KMAC and to control
the hashing logic, and set cfg.sideload if the Keymgr is enabled.
The result digest sent to the kmac_app_agent will be compared against the result from
the DPI reference model.
In addition, read from the STATE window afterwards and confirm that this access is
blocked and will return 0.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_app">{name}_app</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## app_with_partial_data

Based on the kmac_app test, this test will send partial data from application interface
by sending `strb` with values other than `8'hFF`.
Because the scoreboard is cycle accurate and does not support this feature, this test
will not check `status` and `intr_state` registers, but will check other registers and
all interface data including digest.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_app_with_partial_data">{name}_app_with_partial_data</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## burst_write

This is the same as the long_message test, except we burst-write chunks of the message
into the msg_fifo, and disable intermediate status/CSR checks.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_burst_write">{name}_burst_write</a></td>
  <td><a href="01_feature_report.md#kmacendiannessdigest">KMAC.ENDIANNESS.DIGEST</a><br><a href="01_feature_report.md#kmacendiannessmessage">KMAC.ENDIANNESS.MESSAGE</a><br><a href="01_feature_report.md#kmacentropy_modes">KMAC.ENTROPY_MODES</a><br><a href="01_feature_report.md#kmackeysideload">KMAC.KEY.SIDELOAD</a><br><a href="01_feature_report.md#kmacmodecshake">KMAC.MODE.CSHAKE</a><br><a href="01_feature_report.md#kmacmodekmac">KMAC.MODE.KMAC</a><br><a href="01_feature_report.md#kmacmodesha3">KMAC.MODE.SHA3</a><br><a href="01_feature_report.md#kmacmodeshake">KMAC.MODE.SHAKE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_app_keymgr (dragonfly)
Verify the keymgr interface to KMAC.

- Configure the keymgr to start sending known message data to the KMAC.
- Keymgr should transmit a sideloaded key to the KMAC as well.
- KMAC should finish hashing successfully (not visible to SW) and return digest to
  keymgr.
- This digest is compared against the known digest value for correctness.
- Verify that the keymgr has received valid output from the KMAC.

X-ref'ed with keymgr test.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_keymgr_key_derivation-dragonfly">chip_sw_keymgr_key_derivation (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_app_keymgr (egret)
Verify the keymgr interface to KMAC.

- Configure the keymgr to start sending known message data to the KMAC.
- Keymgr should transmit a sideloaded key to the KMAC as well.
- KMAC should finish hashing successfully (not visible to SW) and return digest to
  keymgr.
- This digest is compared against the known digest value for correctness.
- Verify that the keymgr has received valid output from the KMAC.

X-ref'ed with keymgr test.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_keymgr_key_derivation-egret">chip_sw_keymgr_key_derivation (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_app_lc (dragonfly)
Verify the LC interface to KMAC.

- Configure the LC_CTRL to start a token hash using KMAC interface.
- KMAC should finish hashing successfully (not visible to SW) and return digest to
  LC_CTRL.

X-ref'ed with LC_CTRL test/env.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_lc_ctrl_transition-dragonfly">chip_sw_lc_ctrl_transition (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_app_lc (egret)
Verify the LC interface to KMAC.

- Configure the LC_CTRL to start a token hash using KMAC interface.
- KMAC should finish hashing successfully (not visible to SW) and return digest to
  LC_CTRL.

X-ref'ed with LC_CTRL test/env.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_lc_ctrl_transition-egret">chip_sw_lc_ctrl_transition (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_app_rom (dragonfly)
Verify the ROM interface to KMAC.

- Backdoor initialize ROM memory immediately out of reset.
- ROM will send message to the KMAC containing its memory contents,
- KMAC will hash and return the digest to the ROM.
- ROM will compare received digest against its first 8 logical memory lines for
  correctness.

X-ref'ed with ROM_CTRL test/env.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_kmac_app_rom-dragonfly">chip_sw_kmac_app_rom (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_app_rom (egret)
Verify the ROM interface to KMAC.

- Backdoor initialize ROM memory immediately out of reset.
- ROM will send message to the KMAC containing its memory contents,
- KMAC will hash and return the digest to the ROM.
- ROM will compare received digest against its first 8 logical memory lines for
  correctness.

X-ref'ed with ROM_CTRL test/env.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_kmac_app_rom-egret">chip_sw_kmac_app_rom (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_cshake_stress (dragonfly)
Verify all cSHAKE modes of operation.

- Verify the following security configurations: 128, 256
- Verify input message size of 0 bytes.
- Verify multiple input message sizes as defined in NIST test vectors.
- Use endianness configuration used in the crypto library.
- Verify multiple XOF configurations.


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
  <td><a href="01_feature_report.md#kmacmodecshake">KMAC.MODE.CSHAKE</a><br><a href="01_feature_report.md#kmacmodexof">KMAC.MODE.XOF</a></td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_cshake_stress (egret)
Verify all cSHAKE modes of operation.

- Verify the following security configurations: 128, 256
- Verify input message size of 0 bytes.
- Verify multiple input message sizes as defined in NIST test vectors.
- Use endianness configuration used in the crypto library.
- Verify multiple XOF configurations.


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
  <td><a href="01_feature_report.md#kmacmodecshake">KMAC.MODE.CSHAKE</a><br><a href="01_feature_report.md#kmacmodexof">KMAC.MODE.XOF</a></td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_enc (dragonfly)
Verify the SHA3 operation.

SW test verifies SHA3 operation with a known key, plain text and digest (pick one of
the NIST vectors). SW validates the reception of kmac done and fifo empty interrupts.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_kmac_mode_cshake-dragonfly">chip_sw_kmac_mode_cshake (dragonfly)</a><br><a href="03_test_report.md#chip_sw_kmac_mode_kmac-dragonfly">chip_sw_kmac_mode_kmac (dragonfly)</a><br><a href="03_test_report.md#chip_sw_kmac_mode_kmac_jitter_en-dragonfly">chip_sw_kmac_mode_kmac_jitter_en (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_enc (egret)
Verify the SHA3 operation.

SW test verifies SHA3 operation with a known key, plain text and digest (pick one of
the NIST vectors). SW validates the reception of kmac done and fifo empty interrupts.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_kmac_mode_cshake-egret">chip_sw_kmac_mode_cshake (egret)</a><br><a href="03_test_report.md#chip_sw_kmac_mode_kmac-egret">chip_sw_kmac_mode_kmac (egret)</a><br><a href="03_test_report.md#chip_sw_kmac_mode_kmac_jitter_en-egret">chip_sw_kmac_mode_kmac_jitter_en (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_endianness (dragonfly)
Verify all KMAC endianness options

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
  <td><a href="01_feature_report.md#kmacendiannessdigest">KMAC.ENDIANNESS.DIGEST</a><br><a href="01_feature_report.md#kmacendiannessmessage">KMAC.ENDIANNESS.MESSAGE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_endianness (egret)
Verify all KMAC endianness options

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
  <td><a href="01_feature_report.md#kmacendiannessdigest">KMAC.ENDIANNESS.DIGEST</a><br><a href="01_feature_report.md#kmacendiannessmessage">KMAC.ENDIANNESS.MESSAGE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_entropy (dragonfly)
Verify the EDN interface to KMAC.

Requires `EnMasking` parameter to be enabled.
SW randomly configures the KMAC in any hashing mode/strength, and enable EDN mode.
Randomly enable/disable the `entropy_refresh`.
Randomly configure `wait_timer` values (zero for disable, non-zero for timer expire).

  - Program `wait_timer` to a small value.
    Check if EDN timeout error occurs after issuing the hashing op.
  - Adjust `wait_timer` greater than expected EDN latency (with correct `prescaler`
    too). Then check if Digest is correct.

KMAC should send EDN request after `entropy_ready` is set.
KMAC also should send out another request to EDN when either:

  - kmac hash counter hits the configured threshold (assuming it is non-zero)
  - Hash count exceeds the threshold.

SW verifies that KMAC produces the correct digest value.

TODO: This is pending security review discussion. It is unclear if this feature will be
implemented.

X-ref'ed with EDN test/env.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_kmac_entropy-dragonfly">chip_sw_kmac_entropy (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_entropy (egret)
Verify the EDN interface to KMAC.

Requires `EnMasking` parameter to be enabled.
SW randomly configures the KMAC in any hashing mode/strength, and enable EDN mode.
Randomly enable/disable the `entropy_refresh`.
Randomly configure `wait_timer` values (zero for disable, non-zero for timer expire).

  - Program `wait_timer` to a small value.
    Check if EDN timeout error occurs after issuing the hashing op.
  - Adjust `wait_timer` greater than expected EDN latency (with correct `prescaler`
    too). Then check if Digest is correct.

KMAC should send EDN request after `entropy_ready` is set.
KMAC also should send out another request to EDN when either:

  - kmac hash counter hits the configured threshold (assuming it is non-zero)
  - Hash count exceeds the threshold.

SW verifies that KMAC produces the correct digest value.

TODO: This is pending security review discussion. It is unclear if this feature will be
implemented.

X-ref'ed with EDN test/env.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_kmac_entropy-egret">chip_sw_kmac_entropy (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_entropy_stress (dragonfly)
Verify all KMAC entropy configuration options.

Verify all entropy modes of operation (e.g. software, EDN). Depending on the mode of
operation, exercise relevant functionality, for example:

- Entropy period
- Entropy refresh hash count
- Entropy seed

Process many message blocks in KMAC configuration for all entropy modes, and verify
that there are no error conditions.


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
  <td><a href="01_feature_report.md#kmacendiannessdigest">KMAC.ENDIANNESS.DIGEST</a><br><a href="01_feature_report.md#kmacendiannessmessage">KMAC.ENDIANNESS.MESSAGE</a><br><a href="01_feature_report.md#kmacentropy_modes">KMAC.ENTROPY_MODES</a></td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_entropy_stress (egret)
Verify all KMAC entropy configuration options.

Verify all entropy modes of operation (e.g. software, EDN). Depending on the mode of
operation, exercise relevant functionality, for example:

- Entropy period
- Entropy refresh hash count
- Entropy seed

Process many message blocks in KMAC configuration for all entropy modes, and verify
that there are no error conditions.


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
  <td><a href="01_feature_report.md#kmacendiannessdigest">KMAC.ENDIANNESS.DIGEST</a><br><a href="01_feature_report.md#kmacendiannessmessage">KMAC.ENDIANNESS.MESSAGE</a><br><a href="01_feature_report.md#kmacentropy_modes">KMAC.ENTROPY_MODES</a></td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_error_conditions (dragonfly)
Verify reporting of KMAC errors

This is a negative test case covering the following error conditions:

- ErrKeyNotValid: covers that secret key is invalid when KeyMgr initiates App operation
- ErrSwPushedMsgFifo: covers that SW writes the msgfifo while App interface is active
- ErrSwIssuedCmdInAppActive: covers that SW writes all possible commands to the KMAC
  while App interface is active
- ErrWaitTimerExpired: covers that the KMAC timed out while waiting for EDN entropy
- ErrIncorrectEntropyMode: covers that incorrect entropy modes are detected by the KMAC
- ErrUnexpectedModeStrength: covers that 128-bit strength is seen for SHA3, and all but
  128/256 bit strengths are seen for XOF functions
- ErrIncorrectFunctionName: covers that the function name is configured incorrectly
  when KMAC mode is enabled
- ErrSwCmdSequence: covers that SW issues commands to the KMAC out of order
- Shadow register update alert: covers that the an recoverable alert is triggered on active
  shadow register update error
- ErrSwHashingWithoutEntropyReady: covers that starting a hash operation when the entropy is
  not ready triggers an error

Some of the error conditions may be difficult to reproduce in silicon. In such cases,
update the test description to capture any limitations.


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

## chip_sw_kmac_error_conditions (egret)
Verify reporting of KMAC errors

This is a negative test case covering the following error conditions:

- ErrKeyNotValid: covers that secret key is invalid when KeyMgr initiates App operation
- ErrSwPushedMsgFifo: covers that SW writes the msgfifo while App interface is active
- ErrSwIssuedCmdInAppActive: covers that SW writes all possible commands to the KMAC
  while App interface is active
- ErrWaitTimerExpired: covers that the KMAC timed out while waiting for EDN entropy
- ErrIncorrectEntropyMode: covers that incorrect entropy modes are detected by the KMAC
- ErrUnexpectedModeStrength: covers that 128-bit strength is seen for SHA3, and all but
  128/256 bit strengths are seen for XOF functions
- ErrIncorrectFunctionName: covers that the function name is configured incorrectly
  when KMAC mode is enabled
- ErrSwCmdSequence: covers that SW issues commands to the KMAC out of order
- Shadow register update alert: covers that the an recoverable alert is triggered on active
  shadow register update error
- ErrSwHashingWithoutEntropyReady: covers that starting a hash operation when the entropy is
  not ready triggers an error

Some of the error conditions may be difficult to reproduce in silicon. In such cases,
update the test description to capture any limitations.


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

## chip_sw_kmac_idle (dragonfly)
Verify the KMAC idle signaling to clkmgr.

- Write the KMAC clk hint to 0 within clkmgr to indicate KMAC clk can be gated and
  verify that the KMAC clk hint status within clkmgr reads 0 (KMAC is disabled).
- Write the KMAC clk hint to 1 within clkmgr to indicate KMAC clk can be enabled.
  Verify that the KMAC clk hint status within clkmgr reads 1 (KMAC is enabled).
- Initiate a KMAC operation with a known key, plain text and digest.
  Write KMAC clock hint to 0 and verify the KMAC clk hint status within clkmgr reads 1
  (KMAC is enabled), before the KMAC operation is complete.
- After the KMAC operation is complete, verify the digest for correctness. Verify that
  the KMAC clk hint status within clkmgr now reads 0 again (KMAC is disabled).


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_kmac_idle-dragonfly">chip_sw_kmac_idle (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_idle (egret)
Verify the KMAC idle signaling to clkmgr.

- Write the KMAC clk hint to 0 within clkmgr to indicate KMAC clk can be gated and
  verify that the KMAC clk hint status within clkmgr reads 0 (KMAC is disabled).
- Write the KMAC clk hint to 1 within clkmgr to indicate KMAC clk can be enabled.
  Verify that the KMAC clk hint status within clkmgr reads 1 (KMAC is enabled).
- Initiate a KMAC operation with a known key, plain text and digest.
  Write KMAC clock hint to 0 and verify the KMAC clk hint status within clkmgr reads 1
  (KMAC is enabled), before the KMAC operation is complete.
- After the KMAC operation is complete, verify the digest for correctness. Verify that
  the KMAC clk hint status within clkmgr now reads 0 again (KMAC is disabled).


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_kmac_idle-egret">chip_sw_kmac_idle (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_kmac_key_sideload (dragonfly)
Verify all KMAC key sideload.

Procedure:

- Configure the keymgr to sideload a key to KMAC.
- Generate a KMAC output and store it in retention RAM.
- Clear sideload key from keymgr.
- Create a new sideload key with a different salt using keymgr.
- Verify that KMAC can no longer reproduce the same KMAC output.
- Perform software initiated reset.
- Configure the keymgr again to sideload a key to KMAC.
- Verify digest against value stored in retention RAM.

Additional test configurations:

- Verify the following security configurations: 128, 256
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
  <td><a href="01_feature_report.md#kmackeysideload">KMAC.KEY.SIDELOAD</a></td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_kmac_key_sideload (egret)
Verify all KMAC key sideload.

Procedure:

- Configure the keymgr to sideload a key to KMAC.
- Generate a KMAC output and store it in retention RAM.
- Clear sideload key from keymgr.
- Create a new sideload key with a different salt using keymgr.
- Verify that KMAC can no longer reproduce the same KMAC output.
- Perform software initiated reset.
- Configure the keymgr again to sideload a key to KMAC.
- Verify digest against value stored in retention RAM.

Additional test configurations:

- Verify the following security configurations: 128, 256
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
  <td><a href="01_feature_report.md#kmackeysideload">KMAC.KEY.SIDELOAD</a></td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_kmac_stress (dragonfly)
Verify all KMAC modes of operation.

- Verify the following security configurations: 128, 256
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
  <td><a href="01_feature_report.md#kmacmodekmac">KMAC.MODE.KMAC</a></td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_kmac_stress (egret)
Verify all KMAC modes of operation.

- Verify the following security configurations: 128, 256
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
  <td><a href="01_feature_report.md#kmacmodekmac">KMAC.MODE.KMAC</a></td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_sha3_stress (dragonfly)
Verify all SHA3 modes of operation.

- Verify the following digest sizes: 224, 256, 384, 512
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
  <td><a href="01_feature_report.md#kmacmodesha3">KMAC.MODE.SHA3</a></td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_sha3_stress (egret)
Verify all SHA3 modes of operation.

- Verify the following digest sizes: 224, 256, 384, 512
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
  <td><a href="01_feature_report.md#kmacmodesha3">KMAC.MODE.SHA3</a></td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_shake_stress (dragonfly)
Verify all SHAKE modes of operation.

- Verify the following security configurations: 128, 256
- Verify input message size of 0 bytes.
- Verify multiple input message sizes as defined in NIST test vectors.
- Use endianness configuration used in the crypto library.
- Verify multiple XOF configurations.


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
  <td><a href="01_feature_report.md#kmacmodeshake">KMAC.MODE.SHAKE</a><br><a href="01_feature_report.md#kmacmodexof">KMAC.MODE.XOF</a></td>
</tr>
  </tbody>
</table>

## chip_sw_kmac_shake_stress (egret)
Verify all SHAKE modes of operation.

- Verify the following security configurations: 128, 256
- Verify input message size of 0 bytes.
- Verify multiple input message sizes as defined in NIST test vectors.
- Use endianness configuration used in the crypto library.
- Verify multiple XOF configurations.


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
  <td><a href="01_feature_report.md#kmacmodeshake">KMAC.MODE.SHAKE</a><br><a href="01_feature_report.md#kmacmodexof">KMAC.MODE.XOF</a></td>
</tr>
  </tbody>
</table>

## edn_timeout_error
 Test kmac responses correctly when EDN response timeout.
Based on kmac app sequence, this sequence configures kmac to ensure an EDN timeout
error by writing `entropy_period.wait_timer` and `entropy_period.prescaler` registers.
**Check**:

- Check error related registers including `err_code`, `status`, and `interrupt`.
- Check keymgr interface responses with error bit sets to 1.
- Check kmac can resume normal functionalities after processing this error case.
- Check timeout error will not trigger if the `entropy_mode` is set to SW, or masking
  is disabled.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_edn_timeout_error">{name}_edn_timeout_error</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## entropy_mode_error
 Test kmac responses correctly when entropy mode is configured incorrectly.
Based on kmac edn_timeout sequence, this sequence write incorrect
`ral.cfg_shadowed.entropy_mode` before entropy is fetched.
**Check**:

- Check error related registers including `err_code`, `status`, and `interrupt`.
- Check keymgr interface responses with error bit sets to 1.
- Check kmac can resume normal functionalities after processing this error case.
- Check timeout error will not trigger if masking is disabled.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_entropy_mode_error">{name}_entropy_mode_error</a></td>
  <td><a href="01_feature_report.md#kmacentropy_modes">KMAC.ENTROPY_MODES</a></td>
</tr>
  </tbody>
</table>

## entropy_ready_error
 Test kmac responses correctly when entropy_ready field is not set.
Based on kmac app sequence, this sequence does not write `1` to
`ral.cfg_shadowed.entropy_ready` field before a kmac operation.
**Check**:

- If masking is enabled and the kmac operation is EDN mode:
  - If it is a SW operation, check error related registers including `err_code`,
    `status`, and `interrupt`.
  - If it is an APP operation, check keymgr interface responses with error bit sets to
    `1`.
- If masking is not enabled or the operation does not require entropy:
  - Check no error triggered.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_entropy_ready_error">{name}_entropy_ready_error</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## entropy_refresh
 Test entropy interface for KMAC.

This test randomly chooses to execute either a SW-controlled hash or a hash from the
App interface.
All configuration fields are left as is, but now we will request EDN entropy by setting
the following registers with random value:

- "cmd.entropy_req": Request an EDN entropy
- "cmd.hash_cnt_clear": Clear the entropy_refresh_hash_cnt
- "entropy_refresh_threshold_shadowed": The threshold when KMAC should request an EDN
  entropy

In masked mode, scoreboard will check:

- Register `entropy_refresh_hash_cnt` value
- KMAC requests EDN at the correct time

In unmasked mode, scoreboard will check:

- Register `entropy_refresh_hash_cnt` always returns 0


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_entropy_refresh">{name}_entropy_refresh</a></td>
  <td><a href="01_feature_report.md#kmacentropy_modes">KMAC.ENTROPY_MODES</a></td>
</tr>
  </tbody>
</table>

## error

Try several error sequences:

- Update key/prefix/config during absorption/process/squeeze stage.
- Write msg to msg_fifo during process/squeeze stage
- When in KMAC mode, set the function name to not "KMAC"
- Incorrect SHA3 control flow:
  - Issue Process/Run/Done cmds before issuing Start
  - Issue Run/Done before issuing Process
  - Issue Start after issuing Process
  - If squeezing data, issue Start/Process after issuing Run
- Incorrect KMAC configurations (e.g. set KMAC strength as 512).
- Provide software inputs during operation of the application interface


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_error">{name}_error</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## key_error
 Test kmac responses correctly when keymgr app sends request but key is not valid.
**Stimulus**:

- Configure kmac and send keymgr request, but did not set valid bit for keymgr key
  input.
- Wait randomly clock cycles.
- Issue `err_processed`, then wait for the keymgr interface handshake to finish.
- Repeat the above sequence a few times.
- Issue correct kmac request from app or sw interface.

**Check**:

- Check error related registers including `err_code`, `status`, and `interrupt`.
- Check keymgr interface responses with all zero digests and error bit is set.
- Check kmac can resume normal functionalities after processing this error case.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_key_error">{name}_key_error</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## lc_escalation

Randomly set `lc_escalate_en` to value that is not `Off` during Kmac operations.

**Checks**:

- Fatal alert fires continuously until reset is issued.
- Status fields: `alert_fatal_fault` is set to 1 and `sha3_idle` is reset to 0.
- Kmac does not accept any SW or APP requests.
- Digest window always output all 0s.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_lc_escalation">{name}_lc_escalation</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## long_msg_and_output

Same as the smoke test, except with a message of up to 100KB.
Max firmware input size for KMAC is around 392KB, but this is too large for a DV
simulation.
Average input size from firmware would be around 60-100KB, so we use 100KB as a max
input size for DV, but will enable easy extensibility for emulation testing where we can
enable much larger messages.
Allow output length to vary up to 1KB (for XOF functions).
If output length is greater than `keccak_rate` bytes, keccak rounds will be run manually to
squeeze extra output data.
Set function name as "KMAC" and enable full randomization of customization string (if
applicable).


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_long_msg_and_output">{name}_long_msg_and_output</a></td>
  <td><a href="01_feature_report.md#kmacendiannessdigest">KMAC.ENDIANNESS.DIGEST</a><br><a href="01_feature_report.md#kmacendiannessmessage">KMAC.ENDIANNESS.MESSAGE</a><br><a href="01_feature_report.md#kmacentropy_modes">KMAC.ENTROPY_MODES</a><br><a href="01_feature_report.md#kmackeysideload">KMAC.KEY.SIDELOAD</a><br><a href="01_feature_report.md#kmacmodecshake">KMAC.MODE.CSHAKE</a><br><a href="01_feature_report.md#kmacmodekmac">KMAC.MODE.KMAC</a><br><a href="01_feature_report.md#kmacmodesha3">KMAC.MODE.SHA3</a><br><a href="01_feature_report.md#kmacmodeshake">KMAC.MODE.SHAKE</a></td>
</tr>
  </tbody>
</table>

## sideload

Same as the smoke test, except we set cfg.sideload and provide a
valid sideloaded key as well as a valid SW-provided key.
KMAC should operate on the sideloaded key regardless of the cfg_shadowed.sideload field
value.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_sideload">{name}_sideload</a></td>
  <td><a href="01_feature_report.md#kmackeysideload">KMAC.KEY.SIDELOAD</a></td>
</tr>
  </tbody>
</table>

## sideload_invalid
 Test kmac responses correctly sideloaded key is invalidated.
**Stimulus**:

- Configure kmac and send keymgr request.
- Wait until random FSM app state is entered.
- Invalidate the sideloaded key by forcing the .valid signal to 0.
- Repeat the above sequence a few times to try different configurations.

**Check**:

- Check error related registers including `err_code`.
- Check keymgr interface have responses where all digests are zero and the error
  bit is set.
- Check kmac can resume normal functionalities after processing this error case.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_sideload_invalid">{name}_sideload_invalid</a></td>
  <td><a href="01_feature_report.md#kmackeysideload">KMAC.KEY.SIDELOAD</a></td>
</tr>
  </tbody>
</table>

## smoke

KMAC smoke test will contain a number of rounds, and acts as a base for many other tests.
In each round, we run a full KMAC hashing operation:

  - Randomly enable interrupts, operation mode (SHA3/SHAKE/CSHAKE/KMAC), key length (if
    applicable), constraining all settings to be legal.
  - Set function name to "KMAC" and set customization string as empty if applicable.
  - Randomly set endianness of input msg and internal keccak state.
  - Randomly provide a sideloaded key, do not set cfg.sideload.
  - Set output length between 1-`keccak_rate` bytes if applicable.
  - Randomly select either SW or EDN as the source of entropy
  - Trigger KMAC to start absorbing input message.
    - During absorption stage randomly read from STATE window, expect 0.
  - Write message to MSG_FIFO window, maximum length of 32 bytes.
  - Check SHA3 engine status.
  - Trigger KMAC to finish absorbing stage, check kmac_done is set and status.squeeze is
    set.
  - Read output digest, and compare against output from reference C++ model.
    - In masked configuration: both shares are XORed to get unmasked result digest.
    - In unmasked configuration: Share1 is the result digest, Share2 should be 0.
  - Signal cmd.done to tell KMAC to clear internal state.
  - Try reading output digest again, confirm that it is 0.

  This test, and all other tests in the testplan, will be checked for correctness
  in two different ways:

  - first, a DPI-C model is used to check that the correct digest value is produced
  - a cycle-accurate model is implemented in the scoreboard to provide constant checks
    during each hash operation and ensure that internal state is being updated
    correctly


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_smoke">{name}_smoke</a></td>
  <td><a href="01_feature_report.md#kmacendiannessdigest">KMAC.ENDIANNESS.DIGEST</a><br><a href="01_feature_report.md#kmacendiannessmessage">KMAC.ENDIANNESS.MESSAGE</a><br><a href="01_feature_report.md#kmacentropy_modes">KMAC.ENTROPY_MODES</a><br><a href="01_feature_report.md#kmackeysideload">KMAC.KEY.SIDELOAD</a><br><a href="01_feature_report.md#kmacmodecshake">KMAC.MODE.CSHAKE</a><br><a href="01_feature_report.md#kmacmodekmac">KMAC.MODE.KMAC</a><br><a href="01_feature_report.md#kmacmodesha3">KMAC.MODE.SHA3</a><br><a href="01_feature_report.md#kmacmodeshake">KMAC.MODE.SHAKE</a></td>
</tr>
  </tbody>
</table>

## stress_all


- Combine above sequences in one test to run sequentially, except csr sequence and
  some error tests that disabled scoreboard.
- Randomly add reset between each sequence


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#kmac_stress_all">kmac_stress_all</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## test_vectors

These tests drive NIST test vectors for SHA3/SHAKE/KMAC into the design and check
the output against the expected digest values.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_test_vectors_kmac">{name}_test_vectors_kmac</a><br><a href="03_test_report.md#name_test_vectors_kmac_xof">{name}_test_vectors_kmac_xof</a><br><a href="03_test_report.md#name_test_vectors_sha3_224">{name}_test_vectors_sha3_224</a><br><a href="03_test_report.md#name_test_vectors_sha3_256">{name}_test_vectors_sha3_256</a><br><a href="03_test_report.md#name_test_vectors_sha3_384">{name}_test_vectors_sha3_384</a><br><a href="03_test_report.md#name_test_vectors_sha3_512">{name}_test_vectors_sha3_512</a><br><a href="03_test_report.md#name_test_vectors_shake_128">{name}_test_vectors_shake_128</a><br><a href="03_test_report.md#name_test_vectors_shake_256">{name}_test_vectors_shake_256</a></td>
  <td><a href="01_feature_report.md#kmacmodecshake">KMAC.MODE.CSHAKE</a><br><a href="01_feature_report.md#kmacmodekmac">KMAC.MODE.KMAC</a><br><a href="01_feature_report.md#kmacmodesha3">KMAC.MODE.SHA3</a><br><a href="01_feature_report.md#kmacmodeshake">KMAC.MODE.SHAKE</a></td>
</tr>
  </tbody>
</table>

## throughput

Measure the throughput of the various hashing calculations and make sure they correspond
to the expected throughput range for the design.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_throughput">{name}_throughput</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>
