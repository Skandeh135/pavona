# otp_ctrl Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="otp_ctrlbackground_checkcheck_timeout">
      <td>OTP_CTRL.BACKGROUND_CHECK.CHECK_TIMEOUT</td>
      <td>Timeout value for the integrity and consistency checks.</td>
    </tr>
    <tr id="otp_ctrlbackground_checkconsistency_check_period">
      <td>OTP_CTRL.BACKGROUND_CHECK.CONSISTENCY_CHECK_PERIOD</td>
      <td>Re-read period of the buffer registers to ensure data is matched with the associated OTP partition.</td>
    </tr>
    <tr id="otp_ctrlbackground_checkintegrity_check_period">
      <td>OTP_CTRL.BACKGROUND_CHECK.INTEGRITY_CHECK_PERIOD</td>
      <td>The interval which the digest of the partition is recomputed to check integrity of locked partition.</td>
    </tr>
    <tr id="otp_ctrlentropy_read">
      <td>OTP_CTRL.ENTROPY_READ</td>
      <td>Firmware can read entropy from ENTROPY_SRC block by configuring following field of HW_CFG* partition.- EN_CSRNG_SW_APP_READ</td>
    </tr>
    <tr id="otp_ctrlerror_handlingfatal">
      <td>OTP_CTRL.ERROR_HANDLING.FATAL</td>
      <td>Unrecoverable errors are created for uncorrectable ecc error, otp macro malfunction and unauthorized access via lc_ctrl.</td>
    </tr>
    <tr id="otp_ctrlerror_handlingrecoverable">
      <td>OTP_CTRL.ERROR_HANDLING.RECOVERABLE</td>
      <td>Recoverable error is created when unauthorized access attempt are detected via dai interface.</td>
    </tr>
    <tr id="otp_ctrlinit">
      <td>OTP_CTRL.INIT</td>
      <td>When power is up, OTP controller reads devices status.After all reads complete, the controller performs integrity check on the HW_CFG* and SECRET partitions.Once all integrity checks are complete, the controller marks outputs as valid.</td>
    </tr>
    <tr id="otp_ctrlkey_derivation">
      <td>OTP_CTRL.KEY_DERIVATION</td>
      <td>OTP controller participates in the key derivation process by providing scramble key seed to SRAM_CTRL.</td>
    </tr>
    <tr id="otp_ctrlpartitioncreator_sw_cfg">
      <td>OTP_CTRL.PARTITION.CREATOR_SW_CFG</td>
      <td>During calibration stage, various parameters (clock, voltage, and timing sources) are calibrated and recorded to CREATOR_SW_CFG partition.</td>
    </tr>
    <tr id="otp_ctrlpartitionlife_cycle">
      <td>OTP_CTRL.PARTITION.LIFE_CYCLE</td>
      <td>LC state, LC transition count.This feature is owned by the LC_CTRL and cannot be tested well through the OTP_CTRL CSR interface.</td>
    </tr>
    <tr id="otp_ctrlpartitionowner_sw_cfg">
      <td>OTP_CTRL.PARTITION.OWNER_SW_CFG</td>
      <td>Define attributes for rom code execution.Most tests for this partition described insw/device/silicon_creator/rom/data/rom_e2e_testplan.hjson.</td>
    </tr>
    <tr id="otp_ctrlpartitionsecret0">
      <td>OTP_CTRL.PARTITION.SECRET0</td>
      <td>Test unlock tokens, Test exit token</td>
    </tr>
    <tr id="otp_ctrlpartitionsecret1">
      <td>OTP_CTRL.PARTITION.SECRET1</td>
      <td>SRAM scrambling key</td>
    </tr>
    <tr id="otp_ctrlpartitionsecret2">
      <td>OTP_CTRL.PARTITION.SECRET2</td>
      <td>RMA unlock token and creator root key</td>
    </tr>
    <tr id="otp_ctrlpartitionvendor_test">
      <td>OTP_CTRL.PARTITION.VENDOR_TEST</td>
      <td>Vendor test partition is used for OTP programming smoke check during manufacturing flow.In this partition, ECC uncorrectable errors will not lead to fatal errors and alerts.Instead the error will be reported as correctable ECC error.</td>
    </tr>
    <tr id="otp_ctrlpartitions_featureread_lock">
      <td>OTP_CTRL.PARTITIONS_FEATURE.READ_LOCK</td>
      <td>Following partitions can be read lockable by CSR.     - VENDOR_TEST     - CREATOR_SW_CFG     - OWNER_SW_CFG   Following partitions can be read lockable by writing digest.     - SECRET0     - SECRET1     - RECRET2All read attempt to these partitions after read is locked will trigger AccessError (recoverable).</td>
    </tr>
    <tr id="otp_ctrlpartitions_featurewrite_lock">
      <td>OTP_CTRL.PARTITIONS_FEATURE.WRITE_LOCK</td>
      <td>All partitions except LIFE_CYCLE can be write lockable by writing digest.</td>
    </tr>
    <tr id="otp_ctrlprogram">
      <td>OTP_CTRL.PROGRAM</td>
      <td>All other partitions except life cycle partition are programmed through DAI interface.And once non-zero digest is programmed to these partition, no further write access is allowed.Life cycle partition is programmed by LC_CTRL.</td>
    </tr>
    <tr id="otp_ctrlzeroization">
      <td>OTP_CTRL.ZEROIZATION</td>
      <td>Perform zeroization of selected partitions for FIPS compliance.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>OTP_CTRL.PARTITION.VENDOR_TEST</th>
    <th>OTP_CTRL.PARTITION.CREATOR_SW_CFG</th>
    <th>OTP_CTRL.PARTITION.OWNER_SW_CFG</th>
    <th>OTP_CTRL.INIT</th>
    <th>OTP_CTRL.ENTROPY_READ</th>
    <th>OTP_CTRL.KEY_DERIVATION</th>
    <th>OTP_CTRL.PROGRAM</th>
    <th>OTP_CTRL.PARTITION.SECRET0</th>
    <th>OTP_CTRL.PARTITION.SECRET1</th>
    <th>OTP_CTRL.PARTITION.SECRET2</th>
    <th>OTP_CTRL.PARTITION.LIFE_CYCLE</th>
    <th>OTP_CTRL.PARTITIONS_FEATURE.READ_LOCK</th>
    <th>OTP_CTRL.PARTITIONS_FEATURE.WRITE_LOCK</th>
    <th>OTP_CTRL.ERROR_HANDLING.RECOVERABLE</th>
    <th>OTP_CTRL.ERROR_HANDLING.FATAL</th>
    <th>OTP_CTRL.BACKGROUND_CHECK.CHECK_TIMEOUT</th>
    <th>OTP_CTRL.BACKGROUND_CHECK.INTEGRITY_CHECK_PERIOD</th>
    <th>OTP_CTRL.BACKGROUND_CHECK.CONSISTENCY_CHECK_PERIOD</th>
    <th>OTP_CTRL.ZEROIZATION</th>
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
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#logical-partitions">Logical Partitions</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#logical-partitions">X</a></td>
    <td><a href="../theory_of_operation.md#logical-partitions">X</a></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#logical-partitions">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#partition-listing-and-description">Partition Listing and Description</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#calibration-and-test">Calibration and Test</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#calibration-and-test">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#provisioning">Provisioning</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#life-cycle-partition">Life Cycle Partition</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#locking-a-partition">Locking a Partition</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#locking-a-partition">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#locking-a-partition">X</a></td>
    <td><a href="../theory_of_operation.md#locking-a-partition">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#vendor-test-partition">Vendor Test Partition</a></th>
    <td><a href="../theory_of_operation.md#vendor-test-partition">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#software-configuration-partitions">Software Configuration Partitions</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#software-configuration-partitions">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#hardware-configuration-and-secret-partitions">Hardware Configuration and Secret Partitions</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#life-cycle-partition-access">Life Cycle Partition Access</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#life-cycle-partition-access">X</a></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#zeroizing-a-partition">Zeroizing a Partition</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#zeroizing-a-partition">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#zeroization-detection">Zeroization Detection</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#zeroization-detection">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#secret-vs-non-secret-partitions">Secret vs Non-Secret Partitions</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#secret-vs-non-secret-partitions">X</a></td>
    <td><a href="../theory_of_operation.md#secret-vs-non-secret-partitions">X</a></td>
    <td><a href="../theory_of_operation.md#secret-vs-non-secret-partitions">X</a></td>
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
    <th><a href="../theory_of_operation.md#partition-checks">Partition Checks</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#integrity">Integrity</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#integrity">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#integrity">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#storage-consistency">Storage Consistency</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#storage-consistency">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#storage-consistency">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#secret-partition-integrity-checks">Secret Partition Integrity Checks</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#secret-partition-integrity-checks">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#checks-on-zeroized-partitions">Checks on Zeroized Partitions</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#checks-on-zeroized-partitions">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#power-up-and-sense">Power-up and Sense</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#power-up-and-sense">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#partition-defaults">Partition Defaults</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#program-and-read-ports">Program and Read Ports</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#programming-the-otp">Programming the OTP</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#programming-the-otp">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#programming-the-otp">X</a></td>
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
    <th><a href="../theory_of_operation.md#zeroizing-the-otp">Zeroizing the OTP</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#enabling-zeroization">Enabling Zeroization</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#zeroizing-a-partition-procedure">Zeroizing a Partition Procedure</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#the-zeroization-command">The Zeroization Command</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#data-allocation-and-packing">Data Allocation and Packing</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#software-view">Software View</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#life-cycle-view">Life Cycle View</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#partition-controllers">Partition Controllers</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#unbuffered-partition">Unbuffered Partition</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#unbuffered-partition">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#buffered-partition">Buffered Partition</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#buffered-partition">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#direct-access-interface-control">Direct Access Interface Control</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#direct-access-interface-control">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#direct-access-interface-control">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#life-cycle-interface-control">Life Cycle Interface Control</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#key-derivation-interface">Key Derivation Interface</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#key-derivation-interface">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#scrambling-datapath">Scrambling Datapath</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#scrambling">Scrambling</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#digest-calculation">Digest Calculation</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#scrambling-key-derivation">Scrambling Key Derivation</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#scrambling-key-derivation">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#access-arbitration">Access Arbitration</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#primitive-wrapper-and-fpga-emulation">Primitive Wrapper and FPGA Emulation</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#generalized-open-source-interface">Generalized Open-source Interface</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#generic-simulation-and-fpga-emulation-model">Generic Simulation and FPGA Emulation Model</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th>OTP_CTRL.PARTITION.VENDOR_TEST</th>
    <th>OTP_CTRL.PARTITION.CREATOR_SW_CFG</th>
    <th>OTP_CTRL.PARTITION.OWNER_SW_CFG</th>
    <th>OTP_CTRL.INIT</th>
    <th>OTP_CTRL.ENTROPY_READ</th>
    <th>OTP_CTRL.KEY_DERIVATION</th>
    <th>OTP_CTRL.PROGRAM</th>
    <th>OTP_CTRL.PARTITION.SECRET0</th>
    <th>OTP_CTRL.PARTITION.SECRET1</th>
    <th>OTP_CTRL.PARTITION.SECRET2</th>
    <th>OTP_CTRL.PARTITION.LIFE_CYCLE</th>
    <th>OTP_CTRL.PARTITIONS_FEATURE.READ_LOCK</th>
    <th>OTP_CTRL.PARTITIONS_FEATURE.WRITE_LOCK</th>
    <th>OTP_CTRL.ERROR_HANDLING.RECOVERABLE</th>
    <th>OTP_CTRL.ERROR_HANDLING.FATAL</th>
    <th>OTP_CTRL.BACKGROUND_CHECK.CHECK_TIMEOUT</th>
    <th>OTP_CTRL.BACKGROUND_CHECK.INTEGRITY_CHECK_PERIOD</th>
    <th>OTP_CTRL.BACKGROUND_CHECK.CONSISTENCY_CHECK_PERIOD</th>
    <th>OTP_CTRL.ZEROIZATION</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#wake_up">wake_up</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#wake_up">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#wake_up">X</a></td>
    <td><a href="02_testpoint_report.md#wake_up">X</a></td>
    <td><a href="02_testpoint_report.md#wake_up">X</a></td>
    <td><a href="02_testpoint_report.md#wake_up">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#wake_up">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#dai_access_partition_walk">dai_access_partition_walk</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dai_access_partition_walk">X</a></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#init_fail">init_fail</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#init_fail">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#init_fail">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#init_fail">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#partition_check">partition_check</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#partition_check">X</a></td>
    <td><a href="02_testpoint_report.md#partition_check">X</a></td>
    <td><a href="02_testpoint_report.md#partition_check">X</a></td>
    <td><a href="02_testpoint_report.md#partition_check">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#regwen_during_otp_init">regwen_during_otp_init</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#regwen_during_otp_init">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#partition_lock">partition_lock</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#partition_lock">X</a></td>
    <td><a href="02_testpoint_report.md#partition_lock">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#interface_key_check">interface_key_check</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#interface_key_check">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#lc_interactions">lc_interactions</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#lc_interactions">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#lc_interactions">X</a></td>
    <td><a href="02_testpoint_report.md#lc_interactions">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#otp_dai_errors">otp_dai_errors</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#otp_dai_errors">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#otp_macro_errors">otp_macro_errors</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#otp_macro_errors">X</a></td>
    <td><a href="02_testpoint_report.md#otp_macro_errors">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#test_access">test_access</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#zeroization">zeroization</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#zeroization">X</a></td>
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
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#sec_cm_additional_check">sec_cm_additional_check</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#sec_cm_additional_check">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#otp_ctrl_low_freq_read">otp_ctrl_low_freq_read</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_otp_ctrl_init-dragonfly">chip_otp_ctrl_init (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_otp_ctrl_init-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_otp_ctrl_keys-dragonfly">chip_sw_otp_ctrl_keys (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_otp_ctrl_keys-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_otp_ctrl_keys-dragonfly">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_otp_ctrl_entropy-dragonfly">chip_sw_otp_ctrl_entropy (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_otp_ctrl_entropy-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_otp_ctrl_program-dragonfly">chip_sw_otp_ctrl_program (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_otp_ctrl_program-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_otp_ctrl_program-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_otp_ctrl_program-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_otp_ctrl_program-dragonfly">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_otp_ctrl_program_error-dragonfly">chip_sw_otp_ctrl_program_error (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_otp_ctrl_program_error-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_otp_ctrl_hw_cfg0-dragonfly">chip_sw_otp_ctrl_hw_cfg0 (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_otp_ctrl_hw_cfg0-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_otp_ctrl_lc_signals-dragonfly">chip_sw_otp_ctrl_lc_signals (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_otp_ctrl_lc_signals-dragonfly">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_otp_prim_tl_access-dragonfly">chip_sw_otp_prim_tl_access (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_otp_ctrl_vendor_test_csr_access-dragonfly">chip_sw_otp_ctrl_vendor_test_csr_access (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_otp_ctrl_vendor_test_csr_access-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_otp_ctrl_vendor_test_csr_access-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_otp_ctrl_vendor_test_csr_access-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_otp_ctrl_escalation-dragonfly">chip_sw_otp_ctrl_escalation (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_otp_ctrl_escalation-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#otp_ctrl_calibration-dragonfly">otp_ctrl_calibration (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#otp_ctrl_calibration-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#otp_ctrl_partition_access_locked-dragonfly">otp_ctrl_partition_access_locked (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#otp_ctrl_partition_access_locked-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#otp_ctrl_partition_access_locked-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#otp_ctrl_partition_access_locked-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_otp_ctrl_dai_lock-dragonfly">chip_sw_otp_ctrl_dai_lock (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_otp_ctrl_dai_lock-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_otp_ctrl_dai_lock-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_otp_ctrl_dai_lock-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#otp_ctrl_check_timeout-dragonfly">otp_ctrl_check_timeout (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#otp_ctrl_check_timeout-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>
</div>
</div>
