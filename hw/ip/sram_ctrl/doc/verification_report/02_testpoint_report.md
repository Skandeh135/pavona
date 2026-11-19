# sram_ctrl Testpoint Report

## access_during_key_req

This test is the same as the multiple_keys test, except we make sure to sequence some
memory transactions while a key request to OTP is still pending.
Verify that these transactions are completely ignored by the memory.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_access_during_key_req">{name}_access_during_key_req</a></td>
  <td><a href="01_feature_report.md#sram_ctrlmemset">SRAM_CTRL.MEMSET</a><br><a href="01_feature_report.md#sram_ctrlscrambled">SRAM_CTRL.SCRAMBLED</a></td>
</tr>
  </tbody>
</table>

## bijection

In this test we iterate through each address in the SRAM memory.
For each address write the current address to the SRAM.

After this is done, read every address and check that the stored data is equivalent to
the current address.

This will verify that the SRAM encryption mechanism is actually bijective, and will not
cause any address collisions.

e.g. if the encryption scheme causes addresses 0x1 and 0x2 to collide and we write 0x1
     and 0x2 respectively, we will see a return value of 0x2 when we read from 0x1,
     instead of the expected 0x1.

This process will be repeated for a number of new key seeds.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_bijection">{name}_bijection</a></td>
  <td><a href="01_feature_report.md#sram_ctrlmemset">SRAM_CTRL.MEMSET</a><br><a href="01_feature_report.md#sram_ctrlscrambled">SRAM_CTRL.SCRAMBLED</a></td>
</tr>
  </tbody>
</table>

## chip_sw_sleep_sram_ret_contents (dragonfly)
Verify that the data within the retention SRAM survives low power entry-exit and reset.

Ensure that the data within the retention SRAM survives as described in this table.
  |             Mode             | Scrambled | Data Preserved |
  |:----------------------------:|:---------:|:--------------:|
  |          Normal sleep        |    No     |       Yes      |
  |           Deep sleep         |    No     |       Yes      |
  | Reset due to a reset request |    No     |       Yes      |
  |          Normal sleep        |    Yes    |       Yes      |
  |           Deep sleep         |    Yes    |       Yes      |
  | Reset due to a reset request |    Yes    |       No       |

Notes for silicon targets:

- This test has an empty list of associated "features" because those list block-level
  features and this is really testing a chip-level property.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_sleep_sram_ret_contents_no_scramble-dragonfly">chip_sw_sleep_sram_ret_contents_no_scramble (dragonfly)</a><br><a href="03_test_report.md#chip_sw_sleep_sram_ret_contents_scramble-dragonfly">chip_sw_sleep_sram_ret_contents_scramble (dragonfly)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_sleep_sram_ret_contents (egret)
Verify that the data within the retention SRAM survives low power entry-exit and reset.

Ensure that the data within the retention SRAM survives as described in this table.
  |             Mode             | Scrambled | Data Preserved |
  |:----------------------------:|:---------:|:--------------:|
  |          Normal sleep        |    No     |       Yes      |
  |           Deep sleep         |    No     |       Yes      |
  | Reset due to a reset request |    No     |       Yes      |
  |          Normal sleep        |    Yes    |       Yes      |
  |           Deep sleep         |    Yes    |       Yes      |
  | Reset due to a reset request |    Yes    |       No       |

Notes for silicon targets:

- This test has an empty list of associated "features" because those list block-level
  features and this is really testing a chip-level property.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_sleep_sram_ret_contents_no_scramble-egret">chip_sw_sleep_sram_ret_contents_no_scramble (egret)</a><br><a href="03_test_report.md#chip_sw_sleep_sram_ret_contents_scramble-egret">chip_sw_sleep_sram_ret_contents_scramble (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_sram_execution (dragonfly)
Verify that CPU can fetch instructions from SRAM if enabled.

- Create the following combinations of 8 scenarios:
  - The fetch enable bit in the HW_CFG1 partition of OTP controller set and not set.
  - A life cycle state that enables (TEST_UNLOCKED, DEV or RMA) and disables (PROD)
    hardware debug.
  - The execution CSR programmed to be enabled and disabled.

- For both, main and the retention SRAM in each of these 8 scenarios:
  - Load instruction data into the SRAMs.
  - If the instruction execution is enabled, verify that the CPU can fetch and execute
    the instruction from the SRAM correctly.
  - If the instruction execution is not enabled, verify that the SRAM throws an error
    response via an exception handler.

The following table indicates in which of these scenarios should the instruction
execution be enabled, for both, main and the retention SRAM instances.

  | OTP HW_CFG1[IFETCH] | HW_DEBUG_EN via LC state | EXEC CSR | MAIN SRAM | RET SRAM |
  |:------------------:|:------------------------:|:--------:|:---------:|:--------:|
  |          0         |             0            |     0    |  disabled | disabled |
  |          0         |             0            |     1    |  disabled | disabled |
  |          0         |             1            |     0    |  enabled  | disabled |
  |          0         |             1            |     1    |  enabled  | disabled |
  |          1         |             0            |     0    |  disabled | disabled |
  |          1         |             0            |     1    |  enabled  | disabled |
  |          1         |             1            |     0    |  disabled | disabled |
  |          1         |             1            |     1    |  enabled  | disabled |

For the retention SRAM, instruction fetch is completely disabled via design parameter.

Notes for silicon targets:

- This test will be reasonably trivial for silicon validation, because the behaviour
  depends on lifecycle state and we're expecting to do these tests on PROD silicon,
  where execution from SRAM is disallowed.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_sram_ctrl_execution_main-dragonfly">chip_sw_sram_ctrl_execution_main (dragonfly)</a></td>
  <td><a href="01_feature_report.md#sram_ctrlfetch_allow">SRAM_CTRL.FETCH_ALLOW</a></td>
</tr>
  </tbody>
</table>

## chip_sw_sram_execution (egret)
Verify that CPU can fetch instructions from SRAM if enabled.

- Create the following combinations of 8 scenarios:
  - The fetch enable bit in the HW_CFG1 partition of OTP controller set and not set.
  - A life cycle state that enables (TEST_UNLOCKED, DEV or RMA) and disables (PROD)
    hardware debug.
  - The execution CSR programmed to be enabled and disabled.

- For both, main and the retention SRAM in each of these 8 scenarios:
  - Load instruction data into the SRAMs.
  - If the instruction execution is enabled, verify that the CPU can fetch and execute
    the instruction from the SRAM correctly.
  - If the instruction execution is not enabled, verify that the SRAM throws an error
    response via an exception handler.

The following table indicates in which of these scenarios should the instruction
execution be enabled, for both, main and the retention SRAM instances.

  | OTP HW_CFG1[IFETCH] | HW_DEBUG_EN via LC state | EXEC CSR | MAIN SRAM | RET SRAM |
  |:------------------:|:------------------------:|:--------:|:---------:|:--------:|
  |          0         |             0            |     0    |  disabled | disabled |
  |          0         |             0            |     1    |  disabled | disabled |
  |          0         |             1            |     0    |  enabled  | disabled |
  |          0         |             1            |     1    |  enabled  | disabled |
  |          1         |             0            |     0    |  disabled | disabled |
  |          1         |             0            |     1    |  enabled  | disabled |
  |          1         |             1            |     0    |  disabled | disabled |
  |          1         |             1            |     1    |  enabled  | disabled |

For the retention SRAM, instruction fetch is completely disabled via design parameter.

Notes for silicon targets:

- This test will be reasonably trivial for silicon validation, because the behaviour
  depends on lifecycle state and we're expecting to do these tests on PROD silicon,
  where execution from SRAM is disallowed.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_sram_ctrl_execution_main-egret">chip_sw_sram_ctrl_execution_main (egret)</a></td>
  <td><a href="01_feature_report.md#sram_ctrlfetch_allow">SRAM_CTRL.FETCH_ALLOW</a></td>
</tr>
  </tbody>
</table>

## chip_sw_sram_lc_escalation (dragonfly)
Verify the LC escalation path to the SRAMs.

- Configure the LC_CTRL to trigger an escalation request to the SRAMs.
- Verify that the SRAMs stop accepting and responding to new memory requests.
- Reset the system to exit the terminal escalation state.
- Re-initialize the SRAMs and verify that they can now respond correctly to
  any further memory requests.

X-ref with chip_sw_all_escalation_resets and chip_sw_data_integrity.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_all_escalation_resets-dragonfly">chip_sw_all_escalation_resets (dragonfly)</a><br><a href="03_test_report.md#chip_sw_data_integrity_escalation-dragonfly">chip_sw_data_integrity_escalation (dragonfly)</a></td>
  <td><a href="01_feature_report.md#sram_ctrllock_on_error">SRAM_CTRL.LOCK_ON_ERROR</a></td>
</tr>
  </tbody>
</table>

## chip_sw_sram_lc_escalation (egret)
Verify the LC escalation path to the SRAMs.

- Configure the LC_CTRL to trigger an escalation request to the SRAMs.
- Verify that the SRAMs stop accepting and responding to new memory requests.
- Reset the system to exit the terminal escalation state.
- Re-initialize the SRAMs and verify that they can now respond correctly to
  any further memory requests.

X-ref with chip_sw_all_escalation_resets and chip_sw_data_integrity.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_all_escalation_resets-egret">chip_sw_all_escalation_resets (egret)</a><br><a href="03_test_report.md#chip_sw_data_integrity_escalation-egret">chip_sw_data_integrity_escalation (egret)</a></td>
  <td><a href="01_feature_report.md#sram_ctrllock_on_error">SRAM_CTRL.LOCK_ON_ERROR</a></td>
</tr>
  </tbody>
</table>

## chip_sw_sram_memset (dragonfly)
Use the LFSR-based initialisation mechanism to wipe the contents of SRAM.

- Write some known data to the main SRAM and read it back to make sure the write worked
  as expected.
- Use the INIT CSR for the relevant sram_ctrl to request that the memory is filled with
  pseudo-random data.
- Read the location from the SRAM and check that the data has been wiped.
- Repeat the steps above for the retention SRAM.


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
  <td><a href="01_feature_report.md#sram_ctrlmemset">SRAM_CTRL.MEMSET</a></td>
</tr>
  </tbody>
</table>

## chip_sw_sram_memset (egret)
Use the LFSR-based initialisation mechanism to wipe the contents of SRAM.

- Write some known data to the main SRAM and read it back to make sure the write worked
  as expected.
- Use the INIT CSR for the relevant sram_ctrl to request that the memory is filled with
  pseudo-random data.
- Read the location from the SRAM and check that the data has been wiped.
- Repeat the steps above for the retention SRAM.


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
  <td><a href="01_feature_report.md#sram_ctrlmemset">SRAM_CTRL.MEMSET</a></td>
</tr>
  </tbody>
</table>

## chip_sw_sram_readback (dragonfly)
Enable the SRAM readback feature and write and read data from and to the SRAM.

- Enable the SRAM readback feature.
- Write some known data to the ret. SRAM and read it back to make sure the write worked
  as expected.
- Use the INIT CSR for the relevant sram_ctrl to request that the memory is filled with
  pseudo-random data.
- Read the location from the SRAM and check that the data has been wiped.
- Repeat the steps above with the disabled SRAM readback feature.
- Lock the SRAM readback configuration register and try to set it.


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
  <td><a href="01_feature_report.md#sram_ctrlreadback">SRAM_CTRL.READBACK</a></td>
</tr>
  </tbody>
</table>

## chip_sw_sram_readback (egret)
Enable the SRAM readback feature and write and read data from and to the SRAM.

- Enable the SRAM readback feature.
- Write some known data to the ret. SRAM and read it back to make sure the write worked
  as expected.
- Use the INIT CSR for the relevant sram_ctrl to request that the memory is filled with
  pseudo-random data.
- Read the location from the SRAM and check that the data has been wiped.
- Repeat the steps above with the disabled SRAM readback feature.
- Lock the SRAM readback configuration register and try to set it.


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
  <td><a href="01_feature_report.md#sram_ctrlreadback">SRAM_CTRL.READBACK</a></td>
</tr>
  </tbody>
</table>

## chip_sw_sram_scrambled_access (dragonfly)
Verify scrambled memory accesses to both main and retention SRAMs.

- Initialize the entropy_src subsystem to enable OTP_CTRL fetch random data (already
  done by the test_rom startup code).
- Trigger both SRAMs to fetch a new key and nonce from the OTP_CTRL
- Drive the CPU to perform random accesses to both RAMs and verify these operations
  complete successfully by using the backdoor interface
- Fetch a new key from the OTP_CTRL and ensure that the previous contents cannot be
  read anymore.
- Verify the validity of EDN's output to OTP_CTRL via assertions
  (unique, non-zero data).

Note: In simulation, this uses a backdoor interface. However, most of the test should be
      possible on a silicon target (with no EDN assertions, and no backdoor accesses to
      check operations).


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_sram_ctrl_scrambled_access-dragonfly">chip_sw_sram_ctrl_scrambled_access (dragonfly)</a><br><a href="03_test_report.md#chip_sw_sram_ctrl_scrambled_access_jitter_en-dragonfly">chip_sw_sram_ctrl_scrambled_access_jitter_en (dragonfly)</a></td>
  <td><a href="01_feature_report.md#sram_ctrlscrambled">SRAM_CTRL.SCRAMBLED</a></td>
</tr>
  </tbody>
</table>

## chip_sw_sram_scrambled_access (egret)
Verify scrambled memory accesses to both main and retention SRAMs.

- Initialize the entropy_src subsystem to enable OTP_CTRL fetch random data (already
  done by the test_rom startup code).
- Trigger both SRAMs to fetch a new key and nonce from the OTP_CTRL
- Drive the CPU to perform random accesses to both RAMs and verify these operations
  complete successfully by using the backdoor interface
- Fetch a new key from the OTP_CTRL and ensure that the previous contents cannot be
  read anymore.
- Verify the validity of EDN's output to OTP_CTRL via assertions
  (unique, non-zero data).

Note: In simulation, this uses a backdoor interface. However, most of the test should be
      possible on a silicon target (with no EDN assertions, and no backdoor accesses to
      check operations).


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_sram_ctrl_scrambled_access-egret">chip_sw_sram_ctrl_scrambled_access (egret)</a><br><a href="03_test_report.md#chip_sw_sram_ctrl_scrambled_access_jitter_en-egret">chip_sw_sram_ctrl_scrambled_access_jitter_en (egret)</a></td>
  <td><a href="01_feature_report.md#sram_ctrlscrambled">SRAM_CTRL.SCRAMBLED</a></td>
</tr>
  </tbody>
</table>

## chip_sw_sram_subword_access (dragonfly)
Check that subword access works for each SRAM.

- Initialise a region of the SRAM with known patterns.
- Read subwords (each length from one byte upwards; each address modulo 8) and check
  they have the expected values.
- Write subwords (same list as above) and read back the whole word that we touch in
  each case. Check that only the expected bytes have been changed.


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
  <td><a href="01_feature_report.md#sram_ctrlsubword_access">SRAM_CTRL.SUBWORD_ACCESS</a></td>
</tr>
  </tbody>
</table>

## chip_sw_sram_subword_access (egret)
Check that subword access works for each SRAM.

- Initialise a region of the SRAM with known patterns.
- Read subwords (each length from one byte upwards; each address modulo 8) and check
  they have the expected values.
- Write subwords (same list as above) and read back the whole word that we touch in
  each case. Check that only the expected bytes have been changed.


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
  <td><a href="01_feature_report.md#sram_ctrlsubword_access">SRAM_CTRL.SUBWORD_ACCESS</a></td>
</tr>
  </tbody>
</table>

## executable

This test is intended to test the "execute from SRAM" feature, in which TLUL memory
transactions tagged with the `InstrType` value in the user bits are allowed to be
handled by the SRAM memory.

This behavior is enabled by either setting the `exec` CSR to 1 or by driving a second
lifecycle input to `On` - both of these are muxed between with a `otp_en_sram_ifetch_i`
input from the OTP controller.

If this functionality is disabled, any memory transaction NOT tagged as `DataType` should
error out, however `DataType` transactions should be successful when the SRAM is
configured to be executable.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_executable">{name}_executable</a></td>
  <td><a href="01_feature_report.md#sram_ctrlfetch_allow">SRAM_CTRL.FETCH_ALLOW</a></td>
</tr>
  </tbody>
</table>

## lc_escalation

This test is the same as the multiple_keys test, except we now randomly assert the
lifecycle escalation signal.
Upon sending an escalation request, we verify that the DUT has properly latched it,
and all scrambling state has been reset.
In this state, we perform some memory accesses, they should all be blocked and not go
through.
We then issue a reset to the SRAM to get it out of the terminal state, and issue a
couple of memory accesses just to make sure everything is still in working order.


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
  <td><a href="01_feature_report.md#sram_ctrllock_on_error">SRAM_CTRL.LOCK_ON_ERROR</a><br><a href="01_feature_report.md#sram_ctrlmemset">SRAM_CTRL.MEMSET</a><br><a href="01_feature_report.md#sram_ctrlscrambled">SRAM_CTRL.SCRAMBLED</a></td>
</tr>
  </tbody>
</table>

## max_throughput

This test is intended to test the max throughput of the SRAM.

Without partial write, if driver doesn't introduce any delay, it takes N+1 cycles to
finish N SRAM read/write accesses.
With partial write, it needs 2 extra cycles per partial write.
With readback enabled, each read needs 2 cycles and each write 3 cycles.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_max_throughput">{name}_max_throughput</a><br><a href="03_test_report.md#name_throughput_w_partial_write">{name}_throughput_w_partial_write</a><br><a href="03_test_report.md#name_throughput_w_readback">{name}_throughput_w_readback</a></td>
  <td><a href="01_feature_report.md#sram_ctrlreadback">SRAM_CTRL.READBACK</a></td>
</tr>
  </tbody>
</table>

## multiple_keys

In this test we request multiple scrambling keys from OTP and verify that the memory
scrambling is performed correctly even with multiple seeds.
Perform the following steps:

  - Initialize the memory to zero
  - Perform some random memory operations, verify that they succeed with an
    all-zero key and nonce
  - Repeat the following steps a number of times:
    - Get a scrambling key from the OTP interface
    - Perform a number of random memory accesses to the SRAM
  - Verify that all memory access succeed even if the scrambling key changes at arbitrary
    intervals


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_multiple_keys">{name}_multiple_keys</a></td>
  <td><a href="01_feature_report.md#sram_ctrlmemset">SRAM_CTRL.MEMSET</a><br><a href="01_feature_report.md#sram_ctrlscrambled">SRAM_CTRL.SCRAMBLED</a></td>
</tr>
  </tbody>
</table>

## partial_access

This test is intended to test a lot of partial accesses with random addresses or
back-to-back accesses.

Reuse the `smoke` and `stress_pipeline` by setting `partial_access_pct` = 90%


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_partial_access">{name}_partial_access</a><br><a href="03_test_report.md#name_partial_access_b2b">{name}_partial_access_b2b</a></td>
  <td><a href="01_feature_report.md#sram_ctrlsubword_access">SRAM_CTRL.SUBWORD_ACCESS</a></td>
</tr>
  </tbody>
</table>

## ram_cfg
Test `cfg_i` connectivity between sram_ctrl and prim_ram_1p.

Randomly set `dut.cfg_i` and check its value is propagated to `prim_mem_1p`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_ram_cfg">{name}_ram_cfg</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## regwen

This test is intended to test `exec_regwen`, `ctrl_regwen`, and `readback_regwen` as
well as their related CSRs.

`ctrl_regwen` related CSRs (renew_scr_key and init) are excluded from CSR tests as they
affects other CSRs.
`readback_regwen` related CSRs are excluded from CSR tests as they affect other CSRs.
`exec_regwen` and its related CSRs are tested in CSR tests, but this `exec` relates to
other sram inputs (en_sram_ifetch and hw_debug_en), so also test it in this test.

Both `exec_regwen` and `ctrl_regwen` as well as their related CSRs will be programmed
at the beginning of each iteration. So when regwen is cleared, the related CSRs will be
locked.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_regwen">{name}_regwen</a></td>
  <td><a href="01_feature_report.md#sram_ctrlregwen">SRAM_CTRL.REGWEN</a></td>
</tr>
  </tbody>
</table>

## smoke

This test performs basic SRAM initialization procedure and tests basic memory function:

  - Initialize SRAM memory to zero
  - Perform some random memory operations, verify that they all succeed with an
    all-zero key and nonce
  - Request a new scrambling key from the OTP interface and verify that:
    - A valid key is received
    - The key seed used by OTP is valid
  - Perform a number of random memory accesses to the SRAM, verify that all accesses
    were executed correctly using the `mem_bkdr_util`


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
  <td><a href="01_feature_report.md#sram_ctrlmemset">SRAM_CTRL.MEMSET</a><br><a href="01_feature_report.md#sram_ctrlscrambled">SRAM_CTRL.SCRAMBLED</a></td>
</tr>
  </tbody>
</table>

## stress_all


- Combine above sequences in one test to run sequentially, except csr sequence and
  sequences that require zero_delays or invoke reset (such as lc_escalation).
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
  <td><a href="03_test_report.md#name_stress_all">{name}_stress_all</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## stress_pipeline

This test is the same as the multiple_keys_test but we now do a series of back-to-back
memory accesses at each random address in order to create read/write conflicts and
stress the encryption pipeline.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#name_stress_pipeline">{name}_stress_pipeline</a></td>
  <td><a href="01_feature_report.md#sram_ctrlmemset">SRAM_CTRL.MEMSET</a><br><a href="01_feature_report.md#sram_ctrlscrambled">SRAM_CTRL.SCRAMBLED</a></td>
</tr>
  </tbody>
</table>
