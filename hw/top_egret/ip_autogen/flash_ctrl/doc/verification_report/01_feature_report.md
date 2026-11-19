# flash_ctrl Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="flash_ctrlescalation">
      <td>FLASH_CTRL.ESCALATION</td>
      <td>Flash controller has two sources of escalation.1. Global escalation : This is initiated by the Lifecycle Controller through lc_escalate_en.2. Local escalation : This is activated in response to standard faults detected within the flash.                 These faults are monitored through flash_ctrl.STD_FAULT_STATUS.</td>
    </tr>
    <tr id="flash_ctrlfetch_code">
      <td>FLASH_CTRL.FETCH_CODE</td>
      <td>If SW programs flash_ctrl.EXEC to 0xA26A38F7, code fetch from flash device is allowed.All top-level tests that make use of the tests uses this features. No dedicated test is required.</td>
    </tr>
    <tr id="flash_ctrlinfocreator_partition">
      <td>FLASH_CTRL.INFO.CREATOR_PARTITION</td>
      <td>This partition stores creator root seed.It is accessed by the flash controller after scramble key is received.SW can read or program the contents when both of the following conditions are satisfied:  1. Life cycle state is one of DEV, PROD, PROD_END, or RMA.  2. OTP SECRET2_DIGEST partition has not been written and locked.</td>
    </tr>
    <tr id="flash_ctrlinfoisolated_partition">
      <td>FLASH_CTRL.INFO.ISOLATED_PARTITION</td>
      <td>This partition can hold extra manufacturing details (e.g., the wafer authentication secret).SW can read or program the contents when life cycle state is one of PROD, PROD_END, or RMA.SW can only program the contents when life cycle state is TEST_UNLOCKED* or DEV.</td>
    </tr>
    <tr id="flash_ctrlinfoowner_partition">
      <td>FLASH_CTRL.INFO.OWNER_PARTITION</td>
      <td>This partition stores owner root seed.It is accessed by the flash controller after scramble key is received.SW can read or program the contents when life cycle state is one of DEV, PROD, PROD_END, or RMA.</td>
    </tr>
    <tr id="flash_ctrlinitroot_seeds">
      <td>FLASH_CTRL.INIT.ROOT_SEEDS</td>
      <td>After the scrambling keys are requested, the flash controller reads root seeds from secret partitions and provides them to the key manager.</td>
    </tr>
    <tr id="flash_ctrlinitscrambling_keys">
      <td>FLASH_CTRL.INIT.SCRAMBLING_KEYS</td>
      <td>When flash_ctrl.INIT is set, flash controller requests scrambling keys from otp controller.</td>
    </tr>
    <tr id="flash_ctrlmem_protection">
      <td>FLASH_CTRL.MEM_PROTECTION</td>
      <td>For data partitions, SW can designate a memory region of up to 8 regions.Each of these regions can contain more than one page, up to a maximum limit (which is 512 in egret).For each region, SW can establish the access policy by programming flash_ctrl.MP_REGION_CFG.In the case of information partitions, the access policy can be configured on a per page basis.To achieve this, SW must configure flash_ctrl.BANK*_INFO*_PAGE_CFG.</td>
    </tr>
    <tr id="flash_ctrlophost_read">
      <td>FLASH_CTRL.OP.HOST_READ</td>
      <td>Host can read any data partition by providing a valid physical address.</td>
    </tr>
    <tr id="flash_ctrlopprotocol_ctrl">
      <td>FLASH_CTRL.OP.PROTOCOL_CTRL</td>
      <td>As opposed to the host, the protocol controller can read, write and erase both data and info partitions.It has lower priority than host requests.While an operation is in progress, other hw initiated request i.e. RMA, will be held until the operation is finished.</td>
    </tr>
    <tr id="flash_ctrlrma">
      <td>FLASH_CTRL.RMA</td>
      <td>Upon receiving an RMA request from the LC (Lifecycle Controller), the flash controller ensures the completion of all ongoing processes.Subsequently, it proceeds to perform the following actions:1. Erase the following partitions:- Creator partition- Owner partition- Isolated partition- Data partition2. After erasing each page within these partitions, the flash controller systematically writes random data to them.This procedure is implemented to guarantee that any sensitive information previously stored in these partitions remains unrecoverable.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
IP flash_ctrl currently contains no **Feature → Specification** mapping

## Feature -> Testpoint Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Testpoints↓ : Features→</th>
    <th>FLASH_CTRL.ESCALATION</th>
    <th>FLASH_CTRL.FETCH_CODE</th>
    <th>FLASH_CTRL.INFO.CREATOR_PARTITION</th>
    <th>FLASH_CTRL.INFO.ISOLATED_PARTITION</th>
    <th>FLASH_CTRL.INFO.OWNER_PARTITION</th>
    <th>FLASH_CTRL.INIT.ROOT_SEEDS</th>
    <th>FLASH_CTRL.INIT.SCRAMBLING_KEYS</th>
    <th>FLASH_CTRL.MEM_PROTECTION</th>
    <th>FLASH_CTRL.OP.HOST_READ</th>
    <th>FLASH_CTRL.OP.PROTOCOL_CTRL</th>
    <th>FLASH_CTRL.RMA</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#smoke_hw">smoke_hw</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#sw_op">sw_op</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#host_read_direct">host_read_direct</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#rma_hw_if">rma_hw_if</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#host_controller_arb">host_controller_arb</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#erase_suspend">erase_suspend</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#program_reset">program_reset</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#full_memory_access">full_memory_access</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#rd_buff_eviction">rd_buff_eviction</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#rd_buff_eviction_w_ecc">rd_buff_eviction_w_ecc</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#host_arb">host_arb</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#host_interleave">host_interleave</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#memory_protection">memory_protection</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#fetch_code">fetch_code</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#all_partitions">all_partitions</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#error_mp">error_mp</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#error_prog_win">error_prog_win</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#error_prog_type">error_prog_type</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#error_read_seed">error_read_seed</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#read_write_overflow">read_write_overflow</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#flash_ctrl_disable">flash_ctrl_disable</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#flash_ctrl_connect">flash_ctrl_connect</a></th>
    <td></td>
    <td></td>
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
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#secret_partition">secret_partition</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#isolation_partition">isolation_partition</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#interrupts">interrupts</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#invalid_op">invalid_op</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#mid_op_rst">mid_op_rst</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#double_bit_err">double_bit_err</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#single_bit_err">single_bit_err</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#singlebit_err_counter">singlebit_err_counter</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#singlebit_err_address">singlebit_err_address</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#scramble">scramble</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#filesystem_support">filesystem_support</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#rma_write_process_error">rma_write_process_error</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#asymmetric_read_path">asymmetric_read_path</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_flash_init-egret">chip_sw_flash_init (egret)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_flash_init-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_flash_init-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_flash_init-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_flash_init-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_flash_host_access-egret">chip_sw_flash_host_access (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_flash_host_access-egret">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_flash_ctrl_ops-egret">chip_sw_flash_ctrl_ops (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_flash_ctrl_ops-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_flash_memory_protection-egret">chip_sw_flash_memory_protection (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_flash_memory_protection-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_flash_rma_unlocked-egret">chip_sw_flash_rma_unlocked (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_flash_rma_unlocked-egret">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_flash_scramble-egret">chip_sw_flash_scramble (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_flash_scramble-egret">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_flash_scramble-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_flash_idle_low_power-egret">chip_sw_flash_idle_low_power (egret)</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_flash_keymgr_seeds-egret">chip_sw_flash_keymgr_seeds (egret)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_flash_keymgr_seeds-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_flash_keymgr_seeds-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_flash_keymgr_seeds-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_flash_lc_creator_seed_sw_rw_en-egret">chip_sw_flash_lc_creator_seed_sw_rw_en (egret)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_flash_lc_creator_seed_sw_rw_en-egret">X</a></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_flash_creator_seed_wipe_on_rma-egret">chip_sw_flash_creator_seed_wipe_on_rma (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_flash_creator_seed_wipe_on_rma-egret">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_flash_lc_owner_seed_sw_rw_en-egret">chip_sw_flash_lc_owner_seed_sw_rw_en (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_flash_lc_owner_seed_sw_rw_en-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_flash_lc_iso_part_sw_rd_en-egret">chip_sw_flash_lc_iso_part_sw_rd_en (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_flash_lc_iso_part_sw_rd_en-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_flash_lc_iso_part_sw_wr_en-egret">chip_sw_flash_lc_iso_part_sw_wr_en (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_flash_lc_iso_part_sw_wr_en-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_flash_lc_seed_hw_rd_en-egret">chip_sw_flash_lc_seed_hw_rd_en (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_flash_lc_seed_hw_rd_en-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_flash_lc_escalate_en-egret">chip_sw_flash_lc_escalate_en (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_flash_lc_escalate_en-egret">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_flash_prim_tl_access-egret">chip_sw_flash_prim_tl_access (egret)</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_flash_ctrl_clock_freqs-egret">chip_sw_flash_ctrl_clock_freqs (egret)</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_flash_ctrl_escalation_reset-egret">chip_sw_flash_ctrl_escalation_reset (egret)</a></th>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_flash_ctrl_write_clear-egret">chip_sw_flash_ctrl_write_clear (egret)</a></th>
    <td></td>
    <td></td>
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
