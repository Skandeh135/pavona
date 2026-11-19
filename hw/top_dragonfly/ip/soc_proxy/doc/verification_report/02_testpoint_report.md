# soc_proxy Testpoint Report

## chip_sw_soc_proxy_external_reset_requests (dragonfly)
Verify that external reset requests reset (parts of) OT.

- In DV env, trigger the external reset request.
- In DV env, ensure that the desired parts of OT get reset and the others don't.
- In SW, ensure that the reset request shows up in Reset Manager's RESET_INFO register.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_soc_proxy_smoketest-dragonfly">chip_sw_soc_proxy_smoketest (dragonfly)</a></td>
  <td><a href="01_feature_report.md#soc_proxyexternal_reset">SOC_PROXY.EXTERNAL_RESET</a></td>
</tr>
  </tbody>
</table>

## chip_sw_soc_proxy_external_wakeup_requests (dragonfly)
Verify that external wakeup requests are forwarded to Power Manager.

- In SW, enable the wakeup in Power Manager.
- In DV env, trigger the wakeup request.
- In SW, ensure that the wakeup request shows up in Power Manager's `WAKE_STATUS` register.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_soc_proxy_external_wakeup-dragonfly">chip_sw_soc_proxy_external_wakeup (dragonfly)</a></td>
  <td><a href="01_feature_report.md#soc_proxyexternal_wakeup">SOC_PROXY.EXTERNAL_WAKEUP</a></td>
</tr>
  </tbody>
</table>

## chip_sw_soc_proxy_gpios (dragonfly)
Verify that GPI/Os of the SoC into/from OT are correctly connected to multiplexed I/Os.

For each of the general-purpose outputs of the SoC into OT

- In SW, configure Pinmux MIO such that the pin is externally observable.
- In DV env, toggle the pin.
- In DV env, ensure that the pattern shows up on the configured pin.

For each of the general-purpose inputs of the SoC from OT

- In SW, configure Pinmux MIO such that the pin is externally controllable.
- In DV env, toggle the pin.
- In DV env, ensure that the pattern shows up on the SoC input.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_soc_proxy_gpios-dragonfly">chip_sw_soc_proxy_gpios (dragonfly)</a></td>
  <td><a href="01_feature_report.md#soc_proxygpio">SOC_PROXY.GPIO</a></td>
</tr>
  </tbody>
</table>
