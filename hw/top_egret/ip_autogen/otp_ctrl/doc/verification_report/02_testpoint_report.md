# otp_ctrl Testpoint Report

## chip_otp_ctrl_init (egret)
Verify the OTP ctrl initialization on chip power up.

Verify that the chip powers up correctly on POR.

- The pwrmgr initiates a handshake with OTP ctrl and later, with LC ctrl in subsequent
  FSM states. Ensure that the whole power up sequence does not hang.
- Verify with connectivity assertion checks, the handshake signals are connected.
- Ensure that no interrupts or alerts are triggered.


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
  <td><a href="01_feature_report.md#otp_ctrlinit">OTP_CTRL.INIT</a></td>
</tr>
  </tbody>
</table>

## chip_sw_otp_ctrl_dai_lock (egret)
Verify DAI lock functionality.

- Try write/read through DAI accessible partitions.
- Disable DAI by clearing the DIRECT_ACCESS_REGWEN register.
- OTP data must not be accessible to software through DAI when it is disabled.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_otp_ctrl_dai_lock-egret">chip_sw_otp_ctrl_dai_lock (egret)</a></td>
  <td><a href="01_feature_report.md#otp_ctrlerror_handlingrecoverable">OTP_CTRL.ERROR_HANDLING.RECOVERABLE</a><br><a href="01_feature_report.md#otp_ctrlpartitions_featureread_lock">OTP_CTRL.PARTITIONS_FEATURE.READ_LOCK</a><br><a href="01_feature_report.md#otp_ctrlpartitions_featurewrite_lock">OTP_CTRL.PARTITIONS_FEATURE.WRITE_LOCK</a></td>
</tr>
  </tbody>
</table>

## chip_sw_otp_ctrl_entropy (egret)
Verify the entropy interface from OTP ctrl to EDN.

This is X-ref'ed with the chip_otp_ctrl_keys test, which needs to handshake with the EDN
to receive some entropy bits before the keys for SRAM ctrl and ACC are computed.
For sival, this test can be done by

- manuf_ft_sku_individualization
- manuf_ft_provision_rma_token_and_personalization


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_acc_mem_scramble-egret">chip_sw_acc_mem_scramble (egret)</a><br><a href="03_test_report.md#chip_sw_flash_init-egret">chip_sw_flash_init (egret)</a><br><a href="03_test_report.md#chip_sw_keymgr_key_derivation-egret">chip_sw_keymgr_key_derivation (egret)</a><br><a href="03_test_report.md#chip_sw_rv_core_ibex_icache_invalidate-egret">chip_sw_rv_core_ibex_icache_invalidate (egret)</a><br><a href="03_test_report.md#chip_sw_sram_ctrl_scrambled_access-egret">chip_sw_sram_ctrl_scrambled_access (egret)</a></td>
  <td><a href="01_feature_report.md#otp_ctrlentropy_read">OTP_CTRL.ENTROPY_READ</a></td>
</tr>
  </tbody>
</table>

## chip_sw_otp_ctrl_escalation (egret)
Verify escalation from otp_ctrl macro fatal error.

- Inject ECC fatal error into OTP macro's HW cfg partition, and read back this macro
  via DAI interface.
- Because this fatal error will immediately turn off CPU, so the DV sequence will probe
  the alert interface to make sure alert and escalation is triggered.

X'ref with chip_sw_all_escalation_resets.
SiVal: It is not feasible to inject ECC fatal errors in OTP macro.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_otp_ctrl_escalation-egret">chip_sw_otp_ctrl_escalation (egret)</a></td>
  <td><a href="01_feature_report.md#otp_ctrlerror_handlingfatal">OTP_CTRL.ERROR_HANDLING.FATAL</a></td>
</tr>
  </tbody>
</table>

## chip_sw_otp_ctrl_hw_cfg0 (egret)
Verify the correctness of otp_hw_cfg0 bus in all peripherals that receive it.

Preload the OTP ctrl's `hw_cfg0` partition with random data and verify that all
consumers of the hardware configuration bits are receiving the correct values.

Xref'ed with corresponding IP tests that receive these bits.
For sival, this test can be done by

- manuf_ft_sku_individualization_preop


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_lc_ctrl_otp_hw_cfg0-egret">chip_sw_lc_ctrl_otp_hw_cfg0 (egret)</a></td>
  <td><a href="01_feature_report.md#otp_ctrlentropy_read">OTP_CTRL.ENTROPY_READ</a></td>
</tr>
  </tbody>
</table>

## chip_sw_otp_ctrl_keys (egret)
Verify the proliferation of keys to security peripherals.

- Verify the correctness of keys provided to SRAM ctrl (main & ret), flash ctrl, keymgr,
  (note that keymgr does not have handshake).
- Ensure that the test requests a new key and verifies the previously written
  data to an address now returns a garbage value.

X-ref'ed with the following IP tests that consume these signals:

- chip_sw_sram_scrambled_access
- chip_sw_flash_scramble
- chip_sw_keymgr_key_derivation
- chip_sw_acc_mem_scramble

For sival, this test can be done by

- manuf_ft_sku_individualization
- manuf_ft_provision_rma_token_and_personalization


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_acc_mem_scramble-egret">chip_sw_acc_mem_scramble (egret)</a><br><a href="03_test_report.md#chip_sw_flash_init-egret">chip_sw_flash_init (egret)</a><br><a href="03_test_report.md#chip_sw_keymgr_key_derivation-egret">chip_sw_keymgr_key_derivation (egret)</a><br><a href="03_test_report.md#chip_sw_rv_core_ibex_icache_invalidate-egret">chip_sw_rv_core_ibex_icache_invalidate (egret)</a><br><a href="03_test_report.md#chip_sw_sram_ctrl_scrambled_access-egret">chip_sw_sram_ctrl_scrambled_access (egret)</a></td>
  <td><a href="01_feature_report.md#otp_ctrlkey_derivation">OTP_CTRL.KEY_DERIVATION</a><br><a href="01_feature_report.md#otp_ctrlpartitionsecret1">OTP_CTRL.PARTITION.SECRET1</a></td>
</tr>
  </tbody>
</table>

## chip_sw_otp_ctrl_lc_signals (egret)
Verify the broadcast signals from LC ctrl.

- `lc_creator_seed_sw_rw_en_i`: verify that the SECRET2 partition is locked.
- `lc_seed_hw_rd_en_i`: verify that the keymgr outputs a default value when enabled.
- `lc_dft_en_i`: verify that the test interface within OTP ctrl is accessible.
- `lc_check_byp_en_i`: verify that the background check during LC ctrl state
  programming passes when enabled.

Note that `lc_escalate_en_i` is verified via a connectivity test.

The `lc_seed_hw_rd_en_i` signal can be tested by attempting a keymgr advance operation
into the CreatorRootKey state, which should fail since the root key will be tied off to
all-zero when the SECRET2 partition is not locked in OTP.

X-ref'ed with chip_sw_lc_ctrl_broadcast test, which verifies the connectivity of the LC
decoded outputs to other IPs.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_prim_tl_access-egret">chip_prim_tl_access (egret)</a><br><a href="03_test_report.md#chip_sw_lc_ctrl_transition-egret">chip_sw_lc_ctrl_transition (egret)</a><br><a href="03_test_report.md#chip_sw_otp_ctrl_lc_signals_dev-egret">chip_sw_otp_ctrl_lc_signals_dev (egret)</a><br><a href="03_test_report.md#chip_sw_otp_ctrl_lc_signals_prod-egret">chip_sw_otp_ctrl_lc_signals_prod (egret)</a><br><a href="03_test_report.md#chip_sw_otp_ctrl_lc_signals_rma-egret">chip_sw_otp_ctrl_lc_signals_rma (egret)</a><br><a href="03_test_report.md#chip_sw_otp_ctrl_lc_signals_test_unlocked0-egret">chip_sw_otp_ctrl_lc_signals_test_unlocked0 (egret)</a></td>
  <td><a href="01_feature_report.md#otp_ctrlpartitionsecret2">OTP_CTRL.PARTITION.SECRET2</a></td>
</tr>
  </tbody>
</table>

## chip_sw_otp_ctrl_program (egret)
Verify the program request from lc_ctrl.

- Verify that upon an LC state transition request, LC ctrl signals the OTP ctrl with a
  program request.
- Verify that the OTP ctrl generates the LC data output correctly and is sent to the LC
  ctrl before it is reset.
- Verify that the `lc_check_byp_en_i` from LC ctrl is set.
- Ensure that the whole operation does not raise any interrupts or alerts or errors.
- After reset, verify that the LC state transition completed successfully by reading the
  LC state and LC count CSRs.

For sival, this test can be done by

- manuf_ft_sku_individualization_preop


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
  <td><a href="01_feature_report.md#otp_ctrlpartitionlife_cycle">OTP_CTRL.PARTITION.LIFE_CYCLE</a><br><a href="01_feature_report.md#otp_ctrlpartitionsecret0">OTP_CTRL.PARTITION.SECRET0</a><br><a href="01_feature_report.md#otp_ctrlpartitionsecret2">OTP_CTRL.PARTITION.SECRET2</a><br><a href="01_feature_report.md#otp_ctrlprogram">OTP_CTRL.PROGRAM</a></td>
</tr>
  </tbody>
</table>

## chip_sw_otp_ctrl_program_error (egret)
Verify the otp program error.

- Initiate an illegal program request from LC ctrl to OTP ctrl by forcing the
  `lc_otp_program_i`.
- Verify that the LC ctrl triggers an alert and escalation when the OTP ctrl responds back with the correct
  fatal program error as expected.
- Allow escalation to go through reset.
- Use the rstmgr alert info and the fault CSRs to check the alert cause is right.
- Keep state across resets in flash to check that no NMI or regular ISR interrupt run
  for kTopEgretAlertIdLcCtrlFatalProgError.
- Verify that, after escalation reset, the alert handler cause and the fault register are cleared.
- Verify after the escalation reset that the alert info captured the correct alert.

SiVal: Forcing this illegal condition is not feasible in sival.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_lc_ctrl_program_error-egret">chip_sw_lc_ctrl_program_error (egret)</a></td>
  <td><a href="01_feature_report.md#otp_ctrlerror_handlingfatal">OTP_CTRL.ERROR_HANDLING.FATAL</a></td>
</tr>
  </tbody>
</table>

## chip_sw_otp_ctrl_vendor_test_csr_access (egret)

Verify the vendor test control access in raw, test_*, dev, prod, and rma LC states.

- Boot the chip successively in raw, test_*, dev, prod and rma LC states.
- Verify that the SW is able to access the vendor test control and status registers in
  raw, test_* and rma LC states.
  In open source environment, this check is implemented by probing the OTP_CTRL's
  `lc_otp_vendor_test_i` port.
- Verify that in dev / prod LC states, the vendor status always reads back 0s regardless
  of what is programmed into the vendor test control register.
- Once VENDOR_TEST_READ_LOCK is 0, Try to read / write to see it triggered access error.
- For sival, real vendor test will be done by a silicon vendor and nothing need to be done
  in the open source side.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_otp_ctrl_vendor_test_csr_access-egret">chip_sw_otp_ctrl_vendor_test_csr_access (egret)</a></td>
  <td><a href="01_feature_report.md#otp_ctrlpartitionvendor_test">OTP_CTRL.PARTITION.VENDOR_TEST</a><br><a href="01_feature_report.md#otp_ctrlpartitions_featureread_lock">OTP_CTRL.PARTITIONS_FEATURE.READ_LOCK</a><br><a href="01_feature_report.md#otp_ctrlpartitions_featurewrite_lock">OTP_CTRL.PARTITIONS_FEATURE.WRITE_LOCK</a></td>
</tr>
  </tbody>
</table>

## chip_sw_otp_prim_tl_access (egret)
Verify that the SW can read / write the prim tlul interface.

- The prim tlul interface is a open source placeholder for the closed source CSRs that
  will be implemented in a translation 'shim'.
- Verify that when `lc_dft_en_i` is On, this region can be read / written to by the SW.
  When `lc_dft_en_i` is Off, accessing this region will result in a TLUL error.
- For sival, this test can only run on open-source RTL in test_unlocked or rma state.
  Do random csr write and read back for RW type registers.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_prim_tl_access-egret">chip_prim_tl_access (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## dai_access_partition_walk

Similar to UVM's memory walk test, this test ensures every address in each partition
can be accessed successfully via DAI and TLUL interfaces according to its access policy.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#otp_ctrl_partition_walk">otp_ctrl_partition_walk</a></td>
  <td><a href="01_feature_report.md#otp_ctrlprogram">OTP_CTRL.PROGRAM</a></td>
</tr>
  </tbody>
</table>

## init_fail

Based on OTP_CTRL smoke test, this test creates OTP_CTRL's initialization failure:

- write and read OTP memory via DAI interface
- randomly issue DAI digest command to lock HW partitions
- keep writing to OTP memory via DAI interface without asserting reset
- if digests are not locked, backdoor inject ECC correctable or uncorrectable errors
- issue reset and power initialization
- if the injected errors are all correctable errors, disable the `lc_bypass_chk_en`
  after LC program request to create an LC partition check failure

If fatal error is triggered, this test will check:

- OTP initialization failure triggers fatal alert
- `status`, `intr_state`, `err_code` CSRs reflect correct fatal error

If OTP initialization finished without any fatal error, this test will check:

- OTP initialization finishes with power init output goes to 1
- `status`, `intr_state`, `err_code` CSRs reflect ECC correctable error


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#otp_ctrl_init_fail">otp_ctrl_init_fail</a></td>
  <td><a href="01_feature_report.md#otp_ctrlerror_handlingfatal">OTP_CTRL.ERROR_HANDLING.FATAL</a><br><a href="01_feature_report.md#otp_ctrlinit">OTP_CTRL.INIT</a><br><a href="01_feature_report.md#otp_ctrlprogram">OTP_CTRL.PROGRAM</a></td>
</tr>
  </tbody>
</table>

## interface_key_check

OTP_CTRL will generate keys to `flash`, `sram`, and `acc` upon their requests.
Based on the DAI access sequence, this test will run key requests sequence in
parallel, and check if correct keys are generated.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#otp_ctrl_parallel_key_req">otp_ctrl_parallel_key_req</a></td>
  <td><a href="01_feature_report.md#otp_ctrlkey_derivation">OTP_CTRL.KEY_DERIVATION</a></td>
</tr>
  </tbody>
</table>

## lc_interactions

Verify the protocols between OTP_CTRL and LC_CTRL. Based on the DAI access sequence,
run the following sequences in parallel:

- request a LC state transition via the programming interface
- enable the `lc_escalation_en` signal

**Checks**:

- if the LC program request has `AccessError`, check the LC program response sets
  the `error` bit to 1
- if `lc_escalation_en` is enabled, verify that alert is triggered and OTP_CTRL entered
  terminal state


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#otp_ctrl_parallel_lc_esc">otp_ctrl_parallel_lc_esc</a><br><a href="03_test_report.md#otp_ctrl_parallel_lc_req">otp_ctrl_parallel_lc_req</a></td>
  <td><a href="01_feature_report.md#otp_ctrlerror_handlingfatal">OTP_CTRL.ERROR_HANDLING.FATAL</a><br><a href="01_feature_report.md#otp_ctrlerror_handlingrecoverable">OTP_CTRL.ERROR_HANDLING.RECOVERABLE</a><br><a href="01_feature_report.md#otp_ctrlpartitionlife_cycle">OTP_CTRL.PARTITION.LIFE_CYCLE</a></td>
</tr>
  </tbody>
</table>

## otp_ctrl_calibration (egret)
Verify all calibrated parameters are programmed during manufacturing stage calibration test phase.
For sival this test can be done by

- manuf_cp_ast_test_execution


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
  <td><a href="01_feature_report.md#otp_ctrlpartitioncreator_sw_cfg">OTP_CTRL.PARTITION.CREATOR_SW_CFG</a></td>
</tr>
  </tbody>
</table>

## otp_ctrl_check_timeout (egret)
Verify check_timeout feature.

- Program otp_ctrl.check_timeout value small value (e.g. 1000 cycles).
- Write 1 to otp_ctrl.check_trigger.integrity.
- After timeout cycle, check otp_ctrl.status.timeout_error = 1.
- Write 1 to otp_ctrl.check_trigger.consistency.
- After timeout cycle, check otp_ctrl.status.timeout_error = 1.


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
  <td><a href="01_feature_report.md#otp_ctrlbackground_checkcheck_timeout">OTP_CTRL.BACKGROUND_CHECK.CHECK_TIMEOUT</a></td>
</tr>
  </tbody>
</table>

## otp_ctrl_low_freq_read

This test checks if OTP's read operation can operate successfully in a low clock
frequency before the clock is calibrated.

**Stimulus and Checks**:

- Configure OTP_CTRL's clock to 6MHz low frequency.
- Backdoor write OTP memory.
- Use DAI access to read each memory address and compare if the value is correct.
- If DAI address is in a SW partition, read and check again via TLUL interface.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#otp_ctrl_low_freq_read">otp_ctrl_low_freq_read</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## otp_ctrl_partition_access_locked (egret)
Verify accessibility of all partitions except life_cycle partition.

- Without locking state, try random write and read back test over all sw accessible partitions.
- Per each partition, enable write lock and try to do subsequent write then readback.
- Dut should generate recoverable error (access error) and 2nd write won't go through.
- Per each partition, enable read lock and try to read.
- Dut should generate recoverable error (access error).


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
  <td><a href="01_feature_report.md#otp_ctrlerror_handlingrecoverable">OTP_CTRL.ERROR_HANDLING.RECOVERABLE</a><br><a href="01_feature_report.md#otp_ctrlpartitions_featureread_lock">OTP_CTRL.PARTITIONS_FEATURE.READ_LOCK</a><br><a href="01_feature_report.md#otp_ctrlpartitions_featurewrite_lock">OTP_CTRL.PARTITIONS_FEATURE.WRITE_LOCK</a></td>
</tr>
  </tbody>
</table>

## otp_dai_errors

Based on the otp_dai_lock test, this test will randomly run the following OTP errors:

- DAI interface writes non-blank OTP address
- DAI interface accesses LC partition
- DAI interface writes HW digests
- DAI interface writes non-empty memory

**Checks**:

- `err_code` and `status` CSRs
- `otp_error` interrupt


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#otp_ctrl_dai_errs">otp_ctrl_dai_errs</a></td>
  <td><a href="01_feature_report.md#otp_ctrlerror_handlingfatal">OTP_CTRL.ERROR_HANDLING.FATAL</a></td>
</tr>
  </tbody>
</table>

## otp_macro_errors

Randomly run the following OTP errors:

- MacroError
- MacroEccCorrError
- MacroEccUncorrError

**Checks**:

- `err_code` and `status` CSRs
- `otp_error` interrupt
- if the error is unrecoverable, verify that alert is triggered and OTP_CTRL entered
  terminal state


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#otp_ctrl_macro_errs">otp_ctrl_macro_errs</a></td>
  <td><a href="01_feature_report.md#otp_ctrlerror_handlingfatal">OTP_CTRL.ERROR_HANDLING.FATAL</a><br><a href="01_feature_report.md#otp_ctrlerror_handlingrecoverable">OTP_CTRL.ERROR_HANDLING.RECOVERABLE</a></td>
</tr>
  </tbody>
</table>

## partition_check

Randomly program the partition check related CSRs including:

- `check_timeout`
- `integrity_check_period`
- `consistency_check_period`
- `check_trigger`

Create a failure scenario by randomly picking one of these three methods:

- inject ECC errors into the OTP macro via backdoor
- set the `check_timeout` CSR with a very small value
- write to a random OTP partition after digest is issued but before reset is asserted

**Checks**:

- the corresponding alerts are triggered
- the error_code register is set correctly

Note that due to limited simulation time, for background checks, this test only writes
random values that are less than 20 to the check period.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#otp_ctrl_background_chks">otp_ctrl_background_chks</a><br><a href="03_test_report.md#otp_ctrl_check_fail">otp_ctrl_check_fail</a></td>
  <td><a href="01_feature_report.md#otp_ctrlbackground_checkcheck_timeout">OTP_CTRL.BACKGROUND_CHECK.CHECK_TIMEOUT</a><br><a href="01_feature_report.md#otp_ctrlbackground_checkconsistency_check_period">OTP_CTRL.BACKGROUND_CHECK.CONSISTENCY_CHECK_PERIOD</a><br><a href="01_feature_report.md#otp_ctrlbackground_checkintegrity_check_period">OTP_CTRL.BACKGROUND_CHECK.INTEGRITY_CHECK_PERIOD</a><br><a href="01_feature_report.md#otp_ctrlerror_handlingfatal">OTP_CTRL.ERROR_HANDLING.FATAL</a></td>
</tr>
  </tbody>
</table>

## partition_lock

This test will cover two methods of locking read and write: digest calculation and CSR
write. After locking the partitions, issue read or program sequences and check if the
operations are locked correctly, and check if the `AccessError` is set.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#otp_ctrl_dai_lock">otp_ctrl_dai_lock</a></td>
  <td><a href="01_feature_report.md#otp_ctrlpartitions_featureread_lock">OTP_CTRL.PARTITIONS_FEATURE.READ_LOCK</a><br><a href="01_feature_report.md#otp_ctrlpartitions_featurewrite_lock">OTP_CTRL.PARTITIONS_FEATURE.WRITE_LOCK</a></td>
</tr>
  </tbody>
</table>

## regwen_during_otp_init

The `direct_access_regwen` is a RO register which controls the write-enable of other
registers. It is not verified by the common CSR tests. HW sets it to 0 when the DAI
interface is busy.

Stimulus and checks:

- randomly read `direct_access_regwen` and verify that it returns 0 during OTP
  initialization
- verify that the writes to the registers controlled by it do not go through during OTP
  initialization


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#otp_ctrl_regwen">otp_ctrl_regwen</a></td>
  <td><a href="01_feature_report.md#otp_ctrlinit">OTP_CTRL.INIT</a></td>
</tr>
  </tbody>
</table>

## sec_cm_additional_check

Verify the outcome of injecting faults to security countermeasures.

Stimulus:
As mentioned in `prim_count_check`, `prim_fsm_check` and `prim_double_lfsr_check`.

Checks:

- Check the value of status register according to where the fault is injected.
- Check OTP_CTRL is locked after the fatal fault injection by trying to access OTP_CTRL
  via dai, kdi, and lci interfaces.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#otp_ctrl_sec_cm">otp_ctrl_sec_cm</a></td>
  <td><a href="01_feature_report.md#otp_ctrlerror_handlingfatal">OTP_CTRL.ERROR_HANDLING.FATAL</a></td>
</tr>
  </tbody>
</table>

## smoke

OTP_CTRL smoke test provisions and locks partitions.

- drive pwrmgr's request pin to trigger OTP initialization after reset, check status
  after OTP initialization
- randomly read out keys pertaining to `key_manager`, `flash`, `sram`, `acc`
- randomly issue LC program request
- write random values to random addresses within each OTP partition
- read out the random selected write addresses, check if the readout values are expected
- during read and write operations, check if direct_access_regwen is correctly set by HW
- perform a system-level reset and check corresponding CSRs are set correctly
- lock all partitions except life_cycle by triggering digest calculations
- read back and verify the digest
- perform a system-level reset to verify the corresponding CSRs exposing the digests
  have been populated

**Checks**:

- Assertion checks to ensure vendor specific I/Os: `otp_vendor_test_status_o`,
  `otp_vendor_test_ctrl_i`, `cio_test_o`, and `cio_test_en_o` are connected currently
  with `lc_dft_en_i` On and Off.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#otp_ctrl_smoke">otp_ctrl_smoke</a></td>
  <td><a href="01_feature_report.md#otp_ctrlinit">OTP_CTRL.INIT</a><br><a href="01_feature_report.md#otp_ctrlpartitionlife_cycle">OTP_CTRL.PARTITION.LIFE_CYCLE</a><br><a href="01_feature_report.md#otp_ctrlpartitionsecret1">OTP_CTRL.PARTITION.SECRET1</a><br><a href="01_feature_report.md#otp_ctrlpartitionvendor_test">OTP_CTRL.PARTITION.VENDOR_TEST</a><br><a href="01_feature_report.md#otp_ctrlpartitions_featurewrite_lock">OTP_CTRL.PARTITIONS_FEATURE.WRITE_LOCK</a><br><a href="01_feature_report.md#otp_ctrlprogram">OTP_CTRL.PROGRAM</a></td>
</tr>
  </tbody>
</table>

## stress_all


- combine above sequences in one test to run sequentially, except csr sequence
- randomly add reset between each sequence


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

## test_access

This test checks if the test access to OTP macro is connected correctly.

**Stimulus and Checks**:

- Write and check read results from the prim_tl_i/o.
- Ensure no error or alert occurs from DUT.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#otp_ctrl_test_access">otp_ctrl_test_access</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## wake_up

Wake_up test walks through otp_ctrl's power-on initialization, read, program, and
digest functionalities.

- drive pwrmgr's request pin to trigger OTP initialization after reset, check status
  after OTP initialization
- write all-ones to a random address within OTP partition 0, wait until this operation
  completes
- read out the random selected write address, check if the readout value is all-ones
- trigger a digest calculation for a Software partition, check if the OtpError
  interrupt is set
- trigger a digest calculation for a non-software partition, expect operation completes
  without the OtpError interrupt
- read out secrets through the hardware interfaces


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#otp_ctrl_wake_up">otp_ctrl_wake_up</a></td>
  <td><a href="01_feature_report.md#otp_ctrlinit">OTP_CTRL.INIT</a><br><a href="01_feature_report.md#otp_ctrlpartitionsecret0">OTP_CTRL.PARTITION.SECRET0</a><br><a href="01_feature_report.md#otp_ctrlpartitionsecret1">OTP_CTRL.PARTITION.SECRET1</a><br><a href="01_feature_report.md#otp_ctrlpartitionsecret2">OTP_CTRL.PARTITION.SECRET2</a><br><a href="01_feature_report.md#otp_ctrlpartitions_featurewrite_lock">OTP_CTRL.PARTITIONS_FEATURE.WRITE_LOCK</a><br><a href="01_feature_report.md#otp_ctrlprogram">OTP_CTRL.PROGRAM</a></td>
</tr>
  </tbody>
</table>

## zeroization
Randomly zeroize partitions.

**Stimulus and Checks**:

- Use the zeroize command for the zeroization marker and other fields.
- Optionally perform consistency and integrity checks.
- Check for failures for non-zeroizable partitions to flag a DaiError.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#otp_ctrl_zeroization">otp_ctrl_zeroization</a><br><a href="03_test_report.md#otp_ctrl_zeroization_with_checks">otp_ctrl_zeroization_with_checks</a></td>
  <td><a href="01_feature_report.md#otp_ctrlzeroization">OTP_CTRL.ZEROIZATION</a></td>
</tr>
  </tbody>
</table>
