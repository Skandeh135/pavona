# soc_proxy Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="soc_proxyctn_egressbat">
      <td>SOC_PROXY.CTN_EGRESS.BAT</td>
      <td>Base address translation of CTN-bound requests: a request addressing the [1G, 2G)   window is downlifted into the [0, 1G) window before it leaves the block, and its   command integrity is regenerated for the modified address.</td>
    </tr>
    <tr id="soc_proxyctn_egressmux">
      <td>SOC_PROXY.CTN_EGRESS.MUX</td>
      <td>The CTN device port, the DMA host port and the MISC host port are multiplexed onto   the single TL-UL host port which egresses into the CTN.</td>
    </tr>
    <tr id="soc_proxyexternal_reset">
      <td>SOC_PROXY.EXTERNAL_RESET</td>
      <td>An asynchronous, level-encoded reset request from the SoC is synchronized onto the   always-on domain and glitch-filtered before being presented as a reset request.</td>
    </tr>
    <tr id="soc_proxyexternal_wakeup">
      <td>SOC_PROXY.EXTERNAL_WAKEUP</td>
      <td>An asynchronous, level-encoded wakeup request from the SoC is synchronized onto the   always-on domain and presented to the power manager as a wakeup request.</td>
    </tr>
    <tr id="soc_proxygpio">
      <td>SOC_PROXY.GPIO</td>
      <td>Sixteen general-purpose inputs from the SoC and sixteen general-purpose outputs to   the SoC are fed through between the chip IOs and the SoC-facing ports.</td>
    </tr>
    <tr id="soc_proxylsio_trigger">
      <td>SOC_PROXY.LSIO_TRIGGER</td>
      <td>LSIO trigger signals from I2C, SPI Host and UART are synchronized onto the fast clock   domain and collated with the SoC-provided triggers into the trigger vector for the   DMA.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>SOC_PROXY.CTN_EGRESS.MUX</th>
    <th>SOC_PROXY.CTN_EGRESS.BAT</th>
    <th>SOC_PROXY.EXTERNAL_WAKEUP</th>
    <th>SOC_PROXY.EXTERNAL_RESET</th>
    <th>SOC_PROXY.GPIO</th>
    <th>SOC_PROXY.LSIO_TRIGGER</th>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#theory-of-operation">Theory of Operation</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#ctn-egress-multiplexing">CTN Egress Multiplexing</a></th>
    <td><a href="../theory_of_operation.md#ctn-egress-multiplexing">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#base-address-translation">Base Address Translation</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#base-address-translation">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#external-wakeup-requests">External Wakeup Requests</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#external-wakeup-requests">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#external-reset-requests">External Reset Requests</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#external-reset-requests">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#general-purpose-io-feed-through">General-Purpose IO Feed-Through</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#general-purpose-io-feed-through">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#lsio-trigger-collation">LSIO Trigger Collation</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#lsio-trigger-collation">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#bus-integrity">Bus Integrity</a></th>
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
    <th>SOC_PROXY.CTN_EGRESS.MUX</th>
    <th>SOC_PROXY.CTN_EGRESS.BAT</th>
    <th>SOC_PROXY.EXTERNAL_WAKEUP</th>
    <th>SOC_PROXY.EXTERNAL_RESET</th>
    <th>SOC_PROXY.GPIO</th>
    <th>SOC_PROXY.LSIO_TRIGGER</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_soc_proxy_external_reset_requests-dragonfly">chip_sw_soc_proxy_external_reset_requests (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_soc_proxy_external_reset_requests-dragonfly">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_soc_proxy_external_wakeup_requests-dragonfly">chip_sw_soc_proxy_external_wakeup_requests (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_soc_proxy_external_wakeup_requests-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_soc_proxy_gpios-dragonfly">chip_sw_soc_proxy_gpios (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_soc_proxy_gpios-dragonfly">X</a></td>
    <td></td>
  </tr>
</table>
</div>
</div>
