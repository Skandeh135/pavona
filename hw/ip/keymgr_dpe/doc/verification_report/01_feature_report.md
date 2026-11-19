# keymgr_dpe Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="keymgr_dpederiveattestation">
      <td>KEYMGR_DPE.DERIVE.ATTESTATION</td>
      <td>DICE compliant key derivation. Used to generate attestation keys. Derived keys canbe directed to registers exposed to software, or sideloaded to ACC(KEYMGR_DPE.SIDELOAD.ACC). 256Bit measurements can be provided to the key derivationfunction using a dedicated set of registers.</td>
    </tr>
    <tr id="keymgr_dpedpeadvance">
      <td>KEYMGR_DPE.DPE.ADVANCE</td>
      <td>Advancing state derives a destination slot from source. The destination slot creationonly occurs when the creation of such a destination slot is compatible with the sourceslot's data.</td>
    </tr>
    <tr id="keymgr_dpedpedisable">
      <td>KEYMGR_DPE.DPE.DISABLE</td>
      <td>Disabling operation clears all DICE contexts and prevents further use until reset.</td>
    </tr>
    <tr id="keymgr_dpedpeerase">
      <td>KEYMGR_DPE.DPE.ERASE</td>
      <td>Erasing operation clears DICE context from a destination slot.</td>
    </tr>
    <tr id="keymgr_dpegenerateoutput">
      <td>KEYMGR_DPE.GENERATE.OUTPUT</td>
      <td>Derivation of output keys with additional salt and version. Software providedsalt and version values are used as inputs in the key derivation function along withthe internal key manager state. The derived keys can be directed to software registers,or sideloaded to hardware security blocks.</td>
    </tr>
    <tr id="keymgr_dpekey_versioning">
      <td>KEYMGR_DPE.KEY_VERSIONING</td>
      <td>The maximum version value supported by KEYMGR_DPE.GENERATE.OUTPUT is configurable via aset of write-lockable registers. KEYMGR_DPE.GENERATE.OUTPUT will fail to derive a key witha version greater than the version set in the write lockable register for any givenkey manager internal state.</td>
    </tr>
    <tr id="keymgr_dpesideloadacc">
      <td>KEYMGR_DPE.SIDELOAD.ACC</td>
      <td>Generation of keys for ACC. The key is only visible to hardware and ACC code.</td>
    </tr>
    <tr id="keymgr_dpesideloadaes">
      <td>KEYMGR_DPE.SIDELOAD.AES</td>
      <td>Generation of keys for AES. The key is only visible to hardware.</td>
    </tr>
    <tr id="keymgr_dpesideloadkmac">
      <td>KEYMGR_DPE.SIDELOAD.KMAC</td>
      <td>Generation of keys for KMAC. The key is only visible to hardware. This is tracked inKMAC as KMAC.KEY.SIDELOAD.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>KEYMGR_DPE.SIDELOAD.KMAC</th>
    <th>KEYMGR_DPE.SIDELOAD.AES</th>
    <th>KEYMGR_DPE.SIDELOAD.ACC</th>
    <th>KEYMGR_DPE.DERIVE.ATTESTATION</th>
    <th>KEYMGR_DPE.GENERATE.OUTPUT</th>
    <th>KEYMGR_DPE.KEY_VERSIONING</th>
    <th>KEYMGR_DPE.DPE.ADVANCE</th>
    <th>KEYMGR_DPE.DPE.ERASE</th>
    <th>KEYMGR_DPE.DPE.DISABLE</th>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#theory-of-operation">Theory of Operation</a></th>
    <td><a href="../theory_of_operation.md#theory-of-operation">X</a></td>
    <td><a href="../theory_of_operation.md#theory-of-operation">X</a></td>
    <td><a href="../theory_of_operation.md#theory-of-operation">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#key-manager-slots">Key Manager Slots</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#key-manager-slots">X</a></td>
    <td><a href="../theory_of_operation.md#key-manager-slots">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#key-manager-state">Key Manager State</a></th>
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
    <th><a href="../theory_of_operation.md#reset">Reset</a></th>
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
    <th><a href="../theory_of_operation.md#available">Available</a></th>
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
    <th><a href="../theory_of_operation.md#disabled">Disabled</a></th>
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
    <th><a href="../theory_of_operation.md#invalid">Invalid</a></th>
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
    <th><a href="../theory_of_operation.md#invalid-and-disabled-state">Invalid and Disabled State</a></th>
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
    <th><a href="../theory_of_operation.md#accepted-commands">Accepted Commands</a></th>
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
    <th><a href="../theory_of_operation.md#advance">Advance</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#advance">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#versioned-key-generation">Versioned Key Generation</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#versioned-key-generation">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#erase-slot">Erase slot</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#erase-slot">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#disable">Disable</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#disable">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#peripheral-connections">Peripheral Connections</a></th>
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
    <th><a href="../theory_of_operation.md#kdf-details">KDF Details</a></th>
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
    <th><a href="../theory_of_operation.md#life-cycle-connection">Life Cycle Connection</a></th>
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
    <th>KEYMGR_DPE.SIDELOAD.KMAC</th>
    <th>KEYMGR_DPE.SIDELOAD.AES</th>
    <th>KEYMGR_DPE.SIDELOAD.ACC</th>
    <th>KEYMGR_DPE.DERIVE.ATTESTATION</th>
    <th>KEYMGR_DPE.GENERATE.OUTPUT</th>
    <th>KEYMGR_DPE.KEY_VERSIONING</th>
    <th>KEYMGR_DPE.DPE.ADVANCE</th>
    <th>KEYMGR_DPE.DPE.ERASE</th>
    <th>KEYMGR_DPE.DPE.DISABLE</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_keymgr_dpe_key_derivation-dragonfly">chip_sw_keymgr_dpe_key_derivation (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_keymgr_dpe_key_derivation-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_keymgr_dpe_key_derivation-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_keymgr_dpe_key_derivation-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_keymgr_dpe_key_derivation-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_keymgr_dpe_key_derivation-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_keymgr_dpe_key_derivation-dragonfly">X</a></td>
    <td></td>
    <td></td>
  </tr>
</table>
</div>
</div>
