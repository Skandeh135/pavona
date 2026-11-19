# mbx Testpoint Report

## chip_sw_mbx_smoke (dragonfly)
Verify the mailbox integrations with a basic smoketest

- Random-cyclically select a mailbox to perform a req-rsp transaction with
- TB(requester) writes a message into the imbx, then awaits a response
- sw(responder) awaits the request, reads it then replies with a modified version
  of the original message
- TB checks if the received response is as-expected
- Requester randomly selects between an irq or polling-based handler
- Responder polls the peripheral to await transaction completed
- Repeat process for all mailboxes in the system


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_mbx_smoke-dragonfly">chip_sw_mbx_smoke (dragonfly)</a></td>
  <td><a href="01_feature_report.md#mbxinbound">MBX.INBOUND</a><br><a href="01_feature_report.md#mbxoutbound">MBX.OUTBOUND</a></td>
</tr>
  </tbody>
</table>

## mbx_doe_intr_msg

Exercise the DOE_INTR_MSG_ADDR and DOE_INTR_MSG_DATA registers on the RoT- and SoC sides.
These two registers simply convey read only data from the SoC to the RoT.

- Supply a stream of randomized data to SOC_DOE_INTR_MSG_ADDR/DATA at a sufficiently
  low rate that they may be reliably sampled on the RoT side.
- Read and check the randomized data on the RoT side.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#mbx_doe_intr_msg">mbx_doe_intr_msg</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## mbx_imbx_oob

Test accesses that are out of bounds for the inbound mailbox.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#mbx_imbx_oob">mbx_imbx_oob</a></td>
  <td><a href="01_feature_report.md#mbxaddress_range">MBX.ADDRESS_RANGE</a><br><a href="01_feature_report.md#mbxinbound">MBX.INBOUND</a></td>
</tr>
  </tbody>
</table>

## mbx_max_activity

Stress test as per `mbx_stress` but with all access and response delays to be configured to zero cycles.
Additionally, combinational responses shall be enabled on the mailbox SRAM model.
This testpoint aims to check the correct operation of the DUT logic at maximum throughput, minimum latency.
This may be important in ensuring that there are no race hazards.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#mbx_stress_zero_delays">mbx_stress_zero_delays</a></td>
  <td><a href="01_feature_report.md#mbxabort">MBX.ABORT</a><br><a href="01_feature_report.md#mbxinbound">MBX.INBOUND</a><br><a href="01_feature_report.md#mbxoutbound">MBX.OUTBOUND</a></td>
</tr>
  </tbody>
</table>

## mbx_range_lock

Attempt to modify the Inbound and Outbound memory limits whilst the DUT should have locked the memory ranges to prevent changes.
Also attempt to unlock the memory range whilst the DUT is operating.

- Set up memory ranges for the Inbound and Outbound message boxes, and mark them as valid.
- Randomly choose whether to lock the memory ranges.
- Attempt to change one or more of the memory range registers and/or the lock itself.
- Check that the registers value(s) change iff the memory range is unlocked.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td>No tests</td>
  <td><a href="01_feature_report.md#mbxaddress_range">MBX.ADDRESS_RANGE</a></td>
</tr>
  </tbody>
</table>

## mbx_smoke

Smoke test that sends a request from the SoC to the ROT and retrieves the response.

Repeat the following sequence of steps a number of times:

- Send a randomized request message to the RoT.
- Await the receipt of the message on the RoT side, and then check the contents of the
  Inbound mailbox against the request that was sent.
- Present a randomized response message in the Outbound mailbox of the RoT.
- Wait for the availability of the response message to be signaled to the SoC.
- Collect and check the response message.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#mbx_smoke">mbx_smoke</a></td>
  <td><a href="01_feature_report.md#mbxinbound">MBX.INBOUND</a><br><a href="01_feature_report.md#mbxoutbound">MBX.OUTBOUND</a></td>
</tr>
  </tbody>
</table>

## mbx_stress

Stress test that repeatedly sends requests and responses to/from the RoT side as per `mbx_smoke` testpoint.
Additionally, the following abnormal stimuli shall be randomly generated during the test.

- Error reported by the RoT side.
- Abort request from the SoC side.
- Panic (abort clearing) from the RoT side.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#mbx_stress">mbx_stress</a></td>
  <td><a href="01_feature_report.md#mbxabort">MBX.ABORT</a><br><a href="01_feature_report.md#mbxinbound">MBX.INBOUND</a><br><a href="01_feature_report.md#mbxoutbound">MBX.OUTBOUND</a></td>
</tr>
  </tbody>
</table>

## mbx_stress_all

Run the other tests in random order while injecting TL errors and running automated CSR tests in parallel.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#mbx_stress_all">mbx_stress_all</a></td>
  <td><a href="01_feature_report.md#mbxabort">MBX.ABORT</a><br><a href="01_feature_report.md#mbxinbound">MBX.INBOUND</a><br><a href="01_feature_report.md#mbxoutbound">MBX.OUTBOUND</a></td>
</tr>
  </tbody>
</table>
