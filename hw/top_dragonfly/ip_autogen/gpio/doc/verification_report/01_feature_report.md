# gpio Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="gpioinfilter">
      <td>GPIO.IN.FILTER</td>
      <td>GPIO module provides noise filter control.It can be enabled with programing GPIO.CTRL_EN_INPUT_FILTER.Once it enables, input value must be stable for 16cycles before transitioning</td>
    </tr>
    <tr id="gpioinintr_ctrl">
      <td>GPIO.IN.INTR_CTRL</td>
      <td>Input interrupts can be triggered identified by detecting either level or edge.There are four detection modes available: rising edge, falling edge, high-level, and low-level.</td>
    </tr>
    <tr id="gpiooutmask">
      <td>GPIO.OUT.MASK</td>
      <td>Masked output access enables to modify either upper or lower 16bits of output register  without a Read-Modify-Write.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>GPIO.IN.INTR_CTRL</th>
    <th>GPIO.IN.FILTER</th>
    <th>GPIO.OUT.MASK</th>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#theory-of-operation">Theory of Operation</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#block-diagram">Block Diagram</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#design-details">Design Details</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#gpio-output-logic">GPIO Output logic</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#gpio-output-logic">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#gpio-input">GPIO Input</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#gpio-input">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#gpio-inputs-as-hw-straps">GPIO Inputs as HW Straps</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#interrupts">Interrupts</a></th>
    <td><a href="../theory_of_operation.md#interrupts">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#input-period-counters">Input Period Counters</a></th>
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
    <th>GPIO.IN.INTR_CTRL</th>
    <th>GPIO.IN.FILTER</th>
    <th>GPIO.OUT.MASK</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#direct_and_masked_out">direct_and_masked_out</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#direct_and_masked_out">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#out_in_regs_read_write">out_in_regs_read_write</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#gpio_interrupt_programming">gpio_interrupt_programming</a></th>
    <td><a href="02_testpoint_report.md#gpio_interrupt_programming">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#random_interrupt_trigger">random_interrupt_trigger</a></th>
    <td><a href="02_testpoint_report.md#random_interrupt_trigger">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#interrupt_and_noise_filter">interrupt_and_noise_filter</a></th>
    <td><a href="02_testpoint_report.md#interrupt_and_noise_filter">X</a></td>
    <td><a href="02_testpoint_report.md#interrupt_and_noise_filter">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#noise_filter_stress">noise_filter_stress</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#noise_filter_stress">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#regs_long_reads_and_writes">regs_long_reads_and_writes</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#full_random">full_random</a></th>
    <td><a href="02_testpoint_report.md#full_random">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#full_random">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#stress_all">stress_all</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#straps_data">straps_data</a></th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_gpio_out-dragonfly">chip_sw_gpio_out (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_gpio_out-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_gpio_in-dragonfly">chip_sw_gpio_in (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_gpio_in-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_gpio_in-dragonfly">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_gpio_irq-dragonfly">chip_sw_gpio_irq (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_gpio_irq-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_gpio_irq-dragonfly">X</a></td>
    <td></td>
  </tr>
</table>
</div>
</div>
