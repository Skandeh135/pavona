# keymgr Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="keymgrderiveattestation">
      <td>KEYMGR.DERIVE.ATTESTATION</td>
      <td>DICE compliant key derivation. Used to generate attestation keys. Derived keys canbe directed to registers exposed to software, or sideloaded to ACC(KEYMGR.SIDELOAD.ACC). 256Bit measurements can be provided to the key derivationfunction using a dedicated set of registers.</td>
    </tr>
    <tr id="keymgrderivesealing">
      <td>KEYMGR.DERIVE.SEALING</td>
      <td>Derivation of sealing keys. Derived keys can be directed to software registers, orsideloaded to hardware security blocks. 256Bit binding words can be provided to the thekey derivation function using a dedicated set of registers.</td>
    </tr>
    <tr id="keymgrgenerateidentity">
      <td>KEYMGR.GENERATE.IDENTITY</td>
      <td>Derivation of output keys to software registers. Unlike KEYMGR.GENERATE.OUTPUT, thekey derivation function does not support salt or version inputs.</td>
    </tr>
    <tr id="keymgrgenerateoutput">
      <td>KEYMGR.GENERATE.OUTPUT</td>
      <td>Derivation of output keys with additional salt and version. Software providedsalt and version values are used as inputs in the key derivation function along withthe internal key manager state. The derived keys can be directed to software registers,or sideloaded to hardware security blocks.</td>
    </tr>
    <tr id="keymgrkey_versioning">
      <td>KEYMGR.KEY_VERSIONING</td>
      <td>The maximum version value supported by KEYMGR.GENERATE.OUTPUT is configurable via aset of write-lockable registers. KEYMGR.GENERATE.OUTPUT will fail to derive a key witha version greater than the version set in the write lockable register for any givenkey manager internal state.</td>
    </tr>
    <tr id="keymgrsideloadacc">
      <td>KEYMGR.SIDELOAD.ACC</td>
      <td>Generation of keys for KMAC. The key is only visible to hardware and ACC code.</td>
    </tr>
    <tr id="keymgrsideloadaes">
      <td>KEYMGR.SIDELOAD.AES</td>
      <td>Generation of keys for AES. The key is only visible to hardware.</td>
    </tr>
    <tr id="keymgrsideloadkmac">
      <td>KEYMGR.SIDELOAD.KMAC</td>
      <td>Generation of keys for KMAC. The key is only visible to hardware. This is tracked inKMAC as KMAC.KEY.SIDELOAD.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
IP keymgr currently contains no **Feature → Specification** mapping

## Feature -> Testpoint Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Testpoints↓ : Features→</th>
    <th>KEYMGR.SIDELOAD.KMAC</th>
    <th>KEYMGR.SIDELOAD.AES</th>
    <th>KEYMGR.SIDELOAD.ACC</th>
    <th>KEYMGR.DERIVE.ATTESTATION</th>
    <th>KEYMGR.DERIVE.SEALING</th>
    <th>KEYMGR.GENERATE.OUTPUT</th>
    <th>KEYMGR.GENERATE.IDENTITY</th>
    <th>KEYMGR.KEY_VERSIONING</th>
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
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#random">random</a></th>
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
    <th><a href="02_testpoint_report.md#cfgen_during_op">cfgen_during_op</a></th>
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
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#direct_to_disabled_state">direct_to_disabled_state</a></th>
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
    <th><a href="02_testpoint_report.md#lc_disable">lc_disable</a></th>
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
    <th><a href="02_testpoint_report.md#kmac_error_response">kmac_error_response</a></th>
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
    <th><a href="02_testpoint_report.md#invalid_sw_input">invalid_sw_input</a></th>
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
    <th><a href="02_testpoint_report.md#invalid_hw_input">invalid_hw_input</a></th>
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
    <th><a href="02_testpoint_report.md#sync_async_fault_cross">sync_async_fault_cross</a></th>
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
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_keymgr_key_derivation-egret">chip_sw_keymgr_key_derivation (egret)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_keymgr_sideload_kmac_error-egret">chip_sw_keymgr_sideload_kmac_error (egret)</a></th>
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
    <th><a href="02_testpoint_report.md#chip_sw_keymgr_sideload_kmac-egret">chip_sw_keymgr_sideload_kmac (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_keymgr_sideload_kmac-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_keymgr_sideload_aes-egret">chip_sw_keymgr_sideload_aes (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_keymgr_sideload_aes-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_keymgr_sideload_acc-egret">chip_sw_keymgr_sideload_acc (egret)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_keymgr_sideload_acc-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_keymgr_derive_attestation-egret">chip_sw_keymgr_derive_attestation (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_keymgr_derive_attestation-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_keymgr_derive_attestation-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_keymgr_derive_attestation-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_keymgr_derive_sealing-egret">chip_sw_keymgr_derive_sealing (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_keymgr_derive_sealing-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_keymgr_derive_sealing-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_keymgr_derive_sealing-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_keymgr_derive_sealing-egret">X</a></td>
  </tr>
</table>
</div>
</div>
