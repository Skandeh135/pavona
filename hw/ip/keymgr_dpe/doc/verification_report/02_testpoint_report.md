# keymgr_dpe Testpoint Report

## chip_sw_keymgr_dpe_key_derivation (dragonfly)
Verify the keymgr_dpe advances to all states and generate identity / SW output.

- Start keymgr_dpe, letting it derive the boot stage 0 key into slot 1.
- Generate outputs (ACC, SW, KMAC, AES) from the boot stage 0 key.
- Derive a boot stage 1 key from the boot stage 0 key.
- Generate outputs and derive boot stage 2 key from the boot stage 1 key.
- Generate outputs and derive boot stage 3 key from the boot stage 2 key.
- Generate outputs from previous boot stage (1 and 2) keys.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_keymgr_dpe_key_derivation-dragonfly">chip_sw_keymgr_dpe_key_derivation (dragonfly)</a><br><a href="03_test_report.md#chip_sw_keymgr_dpe_key_derivation_jitter_en-dragonfly">chip_sw_keymgr_dpe_key_derivation_jitter_en (dragonfly)</a></td>
  <td><a href="01_feature_report.md#keymgr_dpederiveattestation">KEYMGR_DPE.DERIVE.ATTESTATION</a><br><a href="01_feature_report.md#keymgr_dpedpeadvance">KEYMGR_DPE.DPE.ADVANCE</a><br><a href="01_feature_report.md#keymgr_dpegenerateoutput">KEYMGR_DPE.GENERATE.OUTPUT</a><br><a href="01_feature_report.md#keymgr_dpesideloadacc">KEYMGR_DPE.SIDELOAD.ACC</a><br><a href="01_feature_report.md#keymgr_dpesideloadaes">KEYMGR_DPE.SIDELOAD.AES</a><br><a href="01_feature_report.md#keymgr_dpesideloadkmac">KEYMGR_DPE.SIDELOAD.KMAC</a></td>
</tr>
  </tbody>
</table>

## smoke

Smoke test accessing a major datapath within the keymgr_dpe.
Test operations (advance, gen-sw-out, gen-hw-out) at every stage.

Stimulus:

- Randomly select a destination slot x and issue advance call
  (which should latch the root key into slot x).
- At each stage, issue gen-hw-out and gen-sw-out by using the previously loaded key slot.
- At each stage, advance to the next stage by randomly picking a new destination slot y,
  and advancing to it from slot x (x = y is also allowed).
- Use fixed values for max_key_version = 0 and policy.allow_child = 1, during advance calls.
- Use default/fixed values for HW/SW inputs. Use key_version = 0 during key generation.

Checks:

- Check STATUS reg for each operation.
- Check interrupts `op_done` is triggered when operation is done.
- Check `err` and alert `recov_operation_err` are triggered after invalid operation.
- Check that valid bit is set to 1 in the destination slot.
- Check that policy field is correctly updated from POLICY_SLOT CSR.
- Check KMAC key, KMAC data and output SW data for correctness.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#keymgr_dpe_smoke">keymgr_dpe_smoke</a></td>
  <td><a href="01_feature_report.md#keymgr_dpedpeadvance">KEYMGR_DPE.DPE.ADVANCE</a><br><a href="01_feature_report.md#keymgr_dpegenerateoutput">KEYMGR_DPE.GENERATE.OUTPUT</a></td>
</tr>
  </tbody>
</table>
