# rv_plic Testpoint Report

## IdChangeWithIrq_A
If `irq_id_o` signal is changed and the signal does not change to 0 (value 0 does
not represent any interrupt source ID). Then either of the two condition should have
happened:

- `irq_o` is triggered
- No interrupt triggered, `ip` is set and `ie` is enabled, interrupt source priority is the
  largest among the rest of the interrupt, but the interrupt source
  priority is smaller than the threshold


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_plic_assert">rv_plic_assert</a></td>
  <td><a href="01_feature_report.md#rv_plicenable">RV_PLIC.ENABLE</a><br><a href="01_feature_report.md#rv_plicpriority">RV_PLIC.PRIORITY</a></td>
</tr>
  </tbody>
</table>

## IpClearAfterClaim_A
Once `ip` is set and being claimed, its value is cleared to 0.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_plic_assert">rv_plic_assert</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## IpStableAfterClaimed_A
Once `ip` is cleared to 0, it stays stable until completed and being triggered
again.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_plic_assert">rv_plic_assert</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## IpStableAfterTriggered_A
Once `ip` is set, it stays stable until is being claimed.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_plic_assert">rv_plic_assert</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## LevelTriggeredIpWithClaim_A
If `intr_src_i` is set to 1, level indicator is set to level triggered, and claim
signal is not set, then at the next clock cycle `ip` will be triggered.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_plic_assert">rv_plic_assert</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## LevelTriggeredIp_A
If interrupt pending (`ip`) is triggered, and the level indicator is set to
level triggered (`le=0`), then in the prvious clock cycle, the interrupt source
(`intr_src_i) should be set to 1.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_plic_assert">rv_plic_assert</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## TriggerIrqBackwardCheck_A
If `irq_o` is set to 1, then in the previous clock cycle, the corresponding
`ip` should be set, `ie` should be enabled, and the interrupt source should above the
threshold and have the highest priority.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_plic_assert">rv_plic_assert</a></td>
  <td><a href="01_feature_report.md#rv_plicenable">RV_PLIC.ENABLE</a><br><a href="01_feature_report.md#rv_plicpriority">RV_PLIC.PRIORITY</a></td>
</tr>
  </tbody>
</table>

## TriggerIrqForwardCheck_A
If interrupt is enabled (`ie=1`), interrupt pending is set (`ip=1`), interrupt
input has the highest priority among the rest of the inputs, and its priority is
above the threshold. Then in the next clock clcye, the `irq_o` should be triggered,
and the `irq_id_o` will reflect the input ID.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rv_plic_assert">rv_plic_assert</a></td>
  <td><a href="01_feature_report.md#rv_plicenable">RV_PLIC.ENABLE</a><br><a href="01_feature_report.md#rv_plicpriority">RV_PLIC.PRIORITY</a></td>
</tr>
  </tbody>
</table>

## chip_sw_plic_alerts (egret)
Verify alerts from PLIC due to both, TL intg and reg WE onehot check faults.

- Since PLIC is not pre-verified in a DV environment, we need to ensure these are tested
  separately.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_all_escalation_resets-egret">chip_sw_all_escalation_resets (egret)</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## chip_sw_plic_all_irqs (egret)
Verify all interrupts from all peripherals aggregated at the PLIC.

The automated SW test enables all interrupts at the PLIC to interrupt the core. It uses
the `intr_test` CSR in each peripheral to mock assert an interrupt, looping through all
available interrupts in that peripheral. The ISR verifies that the right interrupt
occurred. This is used as a catch-all interrupt test for all peripheral integration
testing within which functionally asserting an interrupt is hard to achieve or not of
high value.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_plic_all_irqs_0-egret">chip_plic_all_irqs_0 (egret)</a><br><a href="03_test_report.md#chip_plic_all_irqs_10-egret">chip_plic_all_irqs_10 (egret)</a><br><a href="03_test_report.md#chip_plic_all_irqs_20-egret">chip_plic_all_irqs_20 (egret)</a></td>
  <td><a href="01_feature_report.md#rv_plicenable">RV_PLIC.ENABLE</a><br><a href="01_feature_report.md#rv_plicpriority">RV_PLIC.PRIORITY</a></td>
</tr>
  </tbody>
</table>

## chip_sw_plic_sw_irq (egret)
Verify the SW interrupt to the CPU.

Enable all peripheral interrupts at PLIC. Enable all types of interrupt at the CPU core.
Write to the MSIP CSR to generate a SW interrupt to the CPU. Verify that the only
interrupt that is seen is the SW interrupt.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_plic_sw_irq-egret">chip_sw_plic_sw_irq (egret)</a></td>
  <td><a href="01_feature_report.md#rv_plicenable">RV_PLIC.ENABLE</a><br><a href="01_feature_report.md#rv_plicpriority">RV_PLIC.PRIORITY</a></td>
</tr>
  </tbody>
</table>
