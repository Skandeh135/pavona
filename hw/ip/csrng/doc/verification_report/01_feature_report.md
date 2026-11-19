# csrng Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="csrnginterfacehardware0">
      <td>CSRNG.INTERFACE.HARDWARE0</td>
      <td>CSRNG has an application interface intended for hardware; this interface is labelled zero.</td>
    </tr>
    <tr id="csrnginterfacehardware1">
      <td>CSRNG.INTERFACE.HARDWARE1</td>
      <td>CSRNG has an application interface intended for hardware; this interface is labelled one.</td>
    </tr>
    <tr id="csrnginterfacesoftware">
      <td>CSRNG.INTERFACE.SOFTWARE</td>
      <td>CSRNG has an application interface for the software to interact with.Note that for software to actually retrieve random numbers from this interface, the otp_en_csrng_sw_app_read input from OTP needs to be `kMultiBitBool8True` and !!CTRL.SW_APP_ENABLE needs to be set to `kMultiBitBool4True`.Otherwise the !!GENBITS register always reads 0.</td>
    </tr>
    <tr id="csrnglifecycledebugenable">
      <td>CSRNG.LIFECYCLE.DEBUGENABLE</td>
      <td>CSRNG has a debug enable signal, which allows for seed diversification.Depending on this value it will use the non-production seed constant or the production seed constant.This state is controlled by the life-cycle controller and so debug is enabled only in test mode.</td>
    </tr>
    <tr id="csrngmodedeterministic">
      <td>CSRNG.MODE.DETERMINISTIC</td>
      <td>CSRNG can be set up to deterministically generate the same sequence of random values by using a fixed seed.</td>
    </tr>
    <tr id="csrngmodenondeterministic">
      <td>CSRNG.MODE.NONDETERMINISTIC</td>
      <td>CSRNG can be set up to generate non-deterministic random values by using a random seed from the entropy source.</td>
    </tr>
    <tr id="csrngread_int_state">
      <td>CSRNG.READ_INT_STATE</td>
      <td>CSRNG allows reading the internal state of the three CTR_DRBG instances corresponding to the three interfaces.This is useful for debugging and validation testing.Note that for this to work the `otp_en_csrng_sw_app_read` input from OTP needs to be `kMultiBitBool8True`.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>CSRNG.INTERFACE.SOFTWARE</th>
    <th>CSRNG.INTERFACE.HARDWARE0</th>
    <th>CSRNG.INTERFACE.HARDWARE1</th>
    <th>CSRNG.MODE.DETERMINISTIC</th>
    <th>CSRNG.MODE.NONDETERMINISTIC</th>
    <th>CSRNG.READ_INT_STATE</th>
    <th>CSRNG.LIFECYCLE.DEBUGENABLE</th>
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
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#block-diagram">Block Diagram</a></th>
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
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#non-blocking-commands">Non-blocking Commands</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#working-state-values">Working State Values</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#working-state-values">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#aes-cipher">AES Cipher</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#software-support">Software Support</a></th>
    <td><a href="../theory_of_operation.md#software-support">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#application-interface">Application Interface</a></th>
    <td><a href="../theory_of_operation.md#application-interface">X</a></td>
    <td><a href="../theory_of_operation.md#application-interface">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#general-command-format">General Command Format</a></th>
    <td><a href="../theory_of_operation.md#general-command-format">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#command-header">Command Header</a></th>
    <td><a href="../theory_of_operation.md#command-header">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#command-description">Command Description</a></th>
    <td><a href="../theory_of_operation.md#command-description">X</a></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#command-description">X</a></td>
    <td><a href="../theory_of_operation.md#command-description">X</a></td>
    <td></td>
    <td><a href="../theory_of_operation.md#command-description">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#command-response">Command Response</a></th>
    <td><a href="../theory_of_operation.md#command-response">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#generated-bits-genbits-interface">Generated Bits (`genbits`) Interface</a></th>
    <td><a href="../theory_of_operation.md#generated-bits-genbits-interface">X</a></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#generated-bits-genbits-interface">X</a></td>
    <td><a href="../theory_of_operation.md#generated-bits-genbits-interface">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#handshaking-signals">Handshaking signals</a></th>
    <td><a href="../theory_of_operation.md#handshaking-signals">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#waveforms">Waveforms</a></th>
    <td><a href="../theory_of_operation.md#waveforms">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#application-interface-instantiate-request">Application Interface: Instantiate Request</a></th>
    <td><a href="../theory_of_operation.md#application-interface-instantiate-request">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#application-interface--reseed-request">Application Interface:  Reseed Request</a></th>
    <td><a href="../theory_of_operation.md#application-interface--reseed-request">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#application-interface--generate-request">Application Interface:  Generate Request</a></th>
    <td><a href="../theory_of_operation.md#application-interface--generate-request">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#application-interface--update-request">Application Interface:  Update Request</a></th>
    <td><a href="../theory_of_operation.md#application-interface--update-request">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#application-interface--uninstantiate-request">Application Interface:  Uninstantiate Request</a></th>
    <td><a href="../theory_of_operation.md#application-interface--uninstantiate-request">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#entropy-source-hardware-interface">Entropy Source Hardware Interface</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#interrupts">Interrupts</a></th>
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
    <th>CSRNG.INTERFACE.SOFTWARE</th>
    <th>CSRNG.INTERFACE.HARDWARE0</th>
    <th>CSRNG.INTERFACE.HARDWARE1</th>
    <th>CSRNG.MODE.DETERMINISTIC</th>
    <th>CSRNG.MODE.NONDETERMINISTIC</th>
    <th>CSRNG.READ_INT_STATE</th>
    <th>CSRNG.LIFECYCLE.DEBUGENABLE</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
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
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#alerts">alerts</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#err">err</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#cmds">cmds</a></th>
    <td><a href="02_testpoint_report.md#cmds">X</a></td>
    <td><a href="02_testpoint_report.md#cmds">X</a></td>
    <td><a href="02_testpoint_report.md#cmds">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cmds">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#life-cycle">life cycle</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#life-cycle">X</a></td>
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
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_csrng_edn_cmd-dragonfly">chip_sw_csrng_edn_cmd (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_edn_cmd-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_edn_cmd-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_edn_cmd-dragonfly">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_csrng_fuse_en_sw_app_read-dragonfly">chip_sw_csrng_fuse_en_sw_app_read (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_fuse_en_sw_app_read-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_fuse_en_sw_app_read-dragonfly">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_csrng_lc_hw_debug_en-dragonfly">chip_sw_csrng_lc_hw_debug_en (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_lc_hw_debug_en-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_lc_hw_debug_en-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_lc_hw_debug_en-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_csrng_known_answer_tests-dragonfly">chip_sw_csrng_known_answer_tests (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_known_answer_tests-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_known_answer_tests-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_known_answer_tests-dragonfly">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_csrng_edn_cmd-egret">chip_sw_csrng_edn_cmd (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_edn_cmd-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_edn_cmd-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_edn_cmd-egret">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_csrng_fuse_en_sw_app_read-egret">chip_sw_csrng_fuse_en_sw_app_read (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_fuse_en_sw_app_read-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_fuse_en_sw_app_read-egret">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_csrng_lc_hw_debug_en-egret">chip_sw_csrng_lc_hw_debug_en (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_lc_hw_debug_en-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_lc_hw_debug_en-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_lc_hw_debug_en-egret">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_csrng_known_answer_tests-egret">chip_sw_csrng_known_answer_tests (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_known_answer_tests-egret">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_known_answer_tests-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_csrng_known_answer_tests-egret">X</a></td>
    <td></td>
  </tr>
</table>
</div>
</div>
