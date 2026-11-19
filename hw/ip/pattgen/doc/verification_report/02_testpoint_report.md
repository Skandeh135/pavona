# pattgen Testpoint Report

## cnt_rollover

Checking ip operation with random counter values

Stimulus:

  - Program the pre-divider and size registers to unconstrained random values
  - Program the clk_cnt, bit_cnt and rep_cnt to values less than but close to
    predivider and size registers, so that counting would take a reasonable
    number of clock cycles
  - include programming for corner cases
    repeat programming a random number of times
  - Start and stop channels quickly
  - Clear interrupts quickly

Checking:

  - Include functional cover point that rollover value is reached and counter is re-enabled:
  - Ensure patterns are correctly generated
  - Ensure interrupts are robust asserted and cleared (e.g. at the high data rate)


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#cnt_rollover">cnt_rollover</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## error

Reset then re-start the output channel on the fly.

Stimulus:

  - Program the configuration registers of the output channels
  - Randomly re-enable the in progress output channels
  - Re-program the configuration registers of the output channels

Checking:

  - Ensure patterns are dropped when re-enabled
  - Ensure the output channels get back normal after re-enable


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pattgen_error">pattgen_error</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## perf

Checking ip operation at min/max bandwidth

Stimulus:

  - Program the pre-divider registers to high/low values (slow/fast data rate).
  - Program the pattern data registers, the pattern length per output, and
    repeat counter registers to high/low values.
  - Start and stop channels quickly.
  - Clear interrupts quickly.

Checking:

  - Ensure patterns are correctly generated.
  - Ensure interrupts are robust asserted and cleared (e.g. at the high data rate).


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pattgen_perf">pattgen_perf</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## smoke

Smoke test for pattgen ip in which dut is randomly programmed
to generate random patterns on output channels.

Stimulus:

  - Program the configuration registers of the output channels.
  - Randomly activate the output channels.
  - Re-program the configuration registers of the output channels once
    completion interrupts are asserted.

Checking:

  - Check divided clock rate for the active channels
    matching with the values of pre-divider registers.
  - Check generated pattern matching on the active channels
    matching with the values of pattern data registers.
  - Check completion interrupts are asserted once a pattern
    is completely generated on the active channels.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pattgen_smoke">pattgen_smoke</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## stress_all

Stress_all test is a random mix of all the test above except csr tests.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#pattgen_stress_all">pattgen_stress_all</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>
