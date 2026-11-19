# rom_ctrl Testpoint Report

## chip_sw_rom_access (dragonfly)
Verify that the CPU can access the rom contents.

- Verify that the CPU can fetch instructions from the ROM.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rom_ctrl_integrity_check-dragonfly">chip_sw_rom_ctrl_integrity_check (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rom_ctrlscrambled">ROM_CTRL.SCRAMBLED</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rom_access (egret)
Verify that the CPU can access the rom contents.

- Verify that the CPU can fetch instructions from the ROM.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rom_ctrl_integrity_check-egret">chip_sw_rom_ctrl_integrity_check (egret)</a></td>
  <td><a href="01_feature_report.md#rom_ctrlscrambled">ROM_CTRL.SCRAMBLED</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rom_ctrl_digests (egret)


Check that the (real and expected) ROM digests are accessible
through CSRs.

- Read the DIGEST_* and EXP_DIGEST_* CSRs and check they match
  (if they differed, we wouldn't be running!)
- Check that they also match the digest words that we expect.


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
  <td><a href="01_feature_report.md#rom_ctrldigests">ROM_CTRL.DIGESTS</a><br><a href="01_feature_report.md#rom_ctrlexp_digests">ROM_CTRL.EXP_DIGESTS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rom_ctrl_integrity_check (dragonfly)
Verify that the ROM ctrl performs the integrity check of the ROM on power up.

- In non-PROD LC state, the computed digest does not have to match the top 8 words in
  the ROM. Verify that we can successfully power up the chip in this case.
- In PROD LC state, verify that the pwrmgr does not fully power up if the computed
  digest does not match the top 8 words of the ROM.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rom_ctrl_integrity_check-dragonfly">chip_sw_rom_ctrl_integrity_check (dragonfly)</a></td>
  <td><a href="01_feature_report.md#rom_ctrldigests">ROM_CTRL.DIGESTS</a><br><a href="01_feature_report.md#rom_ctrlexp_digests">ROM_CTRL.EXP_DIGESTS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rom_ctrl_integrity_check (egret)
Verify that the ROM ctrl performs the integrity check of the ROM on power up.

- In non-PROD LC state, the computed digest does not have to match the top 8 words in
  the ROM. Verify that we can successfully power up the chip in this case.
- In PROD LC state, verify that the pwrmgr does not fully power up if the computed
  digest does not match the top 8 words of the ROM.

Notes for silicon targets:

- The only thing that this test can do at the SiVal stage
  is to ensure that the expected and measured digests are
  readable and have the values we expect.

- That (simpler) check is done in the separate
  chip_sw_rom_ctrl_digests test, so this test doesn't have
  any SiVal stage.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_rom_ctrl_integrity_check-egret">chip_sw_rom_ctrl_integrity_check (egret)</a></td>
  <td><a href="01_feature_report.md#rom_ctrldigests">ROM_CTRL.DIGESTS</a><br><a href="01_feature_report.md#rom_ctrlexp_digests">ROM_CTRL.EXP_DIGESTS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rom_ctrl_kmac_error (dragonfly)

Verify the effect of KMAC reporting an error during ROM digest computation.

- Backdoor load a valid test ROM image and bring the DUT out of reset.
- During the ROM checker pwrmgr FSM state, while the ROM controller is actively sending
  data to KMAC for the digest computation, glitch the KMAC app sparse FSM to trigger a
  fault.
- Verify that KMAC returns an error signal to the ROM controller.
- Verify that the ROM controller itself transitions to invalid state and the chip is
  effectively dead.

SiVal: Creating a glitch is not feasible, so this is not a sival test.


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
  <td><a href="01_feature_report.md#rom_ctrldigests">ROM_CTRL.DIGESTS</a><br><a href="01_feature_report.md#rom_ctrlfi_hardening">ROM_CTRL.FI_HARDENING</a></td>
</tr>
  </tbody>
</table>

## chip_sw_rom_ctrl_kmac_error (egret)

Verify the effect of KMAC reporting an error during ROM digest computation.

- Backdoor load a valid test ROM image and bring the DUT out of reset.
- During the ROM checker pwrmgr FSM state, while the ROM controller is actively sending
  data to KMAC for the digest computation, glitch the KMAC app sparse FSM to trigger a
  fault.
- Verify that KMAC returns an error signal to the ROM controller.
- Verify that the ROM controller itself transitions to invalid state and the chip is
  effectively dead.

SiVal: Creating a glitch is not feasible, so this is not a sival test.


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
  <td><a href="01_feature_report.md#rom_ctrldigests">ROM_CTRL.DIGESTS</a><br><a href="01_feature_report.md#rom_ctrlfi_hardening">ROM_CTRL.FI_HARDENING</a></td>
</tr>
  </tbody>
</table>

## corrupt_sig_fatal_chk

Corrupt integrity of signals like the select signal to addr mux.

**Checks**:

- Check that fatal error is flagged.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rom_ctrl_corrupt_sig_fatal_chk">rom_ctrl_corrupt_sig_fatal_chk</a></td>
  <td><a href="01_feature_report.md#rom_ctrlfi_hardening">ROM_CTRL.FI_HARDENING</a></td>
</tr>
  </tbody>
</table>

## kmac_err_chk


- Generate error from KMAC when it responds with KMAC digest image.
- Check that ROM controller goes into invalid state


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rom_ctrl_kmac_err_chk">rom_ctrl_kmac_err_chk</a></td>
  <td><a href="01_feature_report.md#rom_ctrldigests">ROM_CTRL.DIGESTS</a></td>
</tr>
  </tbody>
</table>

## max_throughput_chk

This test is intended to test the max throughput of ROM controller.
It takes N+1 cycles to finish N ROM read accesses.

**Checks**:

- Check if N read accesses finish in N+1 cycles.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rom_ctrl_max_throughput_chk">rom_ctrl_max_throughput_chk</a></td>
  <td><a href="01_feature_report.md#rom_ctrlscrambled">ROM_CTRL.SCRAMBLED</a></td>
</tr>
  </tbody>
</table>

## smoke

Smoke test exercising the main features of rom_ctrl.

**Stimulus**:

- Create a random valid ROM where expected digest doesn't match with the KMAC digest
  image and load into memory model
- Allow the rom check to complete
- Perform some random memory accesses
- Create a random valid ROM where expected digest matches with the KMAC digest
- Repeat steps 2 and 3.

**Checks**:

- Check that all data supplied to kmac is correct
- Check that the rom checking sequence gives the expected result
- Check that the memory accesses return expected data
- Check that pwrmgr_data_o.good is not asserted in first iteration.
- Check that pwrmgr_data_o.good is asserted in second iteration.
- Check that tile link accesses are blocked till pwrmgr_data_o.done is asserted.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rom_ctrl_smoke">rom_ctrl_smoke</a></td>
  <td><a href="01_feature_report.md#rom_ctrldigests">ROM_CTRL.DIGESTS</a><br><a href="01_feature_report.md#rom_ctrlexp_digests">ROM_CTRL.EXP_DIGESTS</a><br><a href="01_feature_report.md#rom_ctrlscrambled">ROM_CTRL.SCRAMBLED</a></td>
</tr>
  </tbody>
</table>

## stress_all


- Combine above sequences in one test to run sequentially.
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
  <td><a href="03_test_report.md#rom_ctrl_stress_all">rom_ctrl_stress_all</a></td>
  <td><a href="01_feature_report.md#rom_ctrldigests">ROM_CTRL.DIGESTS</a><br><a href="01_feature_report.md#rom_ctrlexp_digests">ROM_CTRL.EXP_DIGESTS</a><br><a href="01_feature_report.md#rom_ctrlscrambled">ROM_CTRL.SCRAMBLED</a></td>
</tr>
  </tbody>
</table>
