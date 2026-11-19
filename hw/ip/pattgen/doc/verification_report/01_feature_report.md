# pattgen Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="pattgenchannelone">
      <td>PATTGEN.CHANNEL.ONE</td>
      <td>Pattern generator can generate patterns on two separate channels, this is the first one.</td>
    </tr>
    <tr id="pattgenchanneltwo">
      <td>PATTGEN.CHANNEL.TWO</td>
      <td>Pattern generator can generate patterns on two separate channels, this is the second one.</td>
    </tr>
    <tr id="pattgencomplete">
      <td>PATTGEN.COMPLETE</td>
      <td>Once a pattern is finished, an interrupt is raised.</td>
    </tr>
    <tr id="pattgenconfigdivider">
      <td>PATTGEN.CONFIG.DIVIDER</td>
      <td>Each channel has an independent clock divider.</td>
    </tr>
    <tr id="pattgenconfiginactive_level">
      <td>PATTGEN.CONFIG.INACTIVE_LEVEL</td>
      <td>The inactive level of clock and data output of each channel can be configured separately.</td>
    </tr>
    <tr id="pattgenconfigpattern">
      <td>PATTGEN.CONFIG.PATTERN</td>
      <td>Each channel can be programmed with a pattern with a length of between 1 and 64 bits, inclusive.</td>
    </tr>
    <tr id="pattgenconfigpolarity">
      <td>PATTGEN.CONFIG.POLARITY</td>
      <td>Each channel's clock can be inverted.</td>
    </tr>
    <tr id="pattgenconfigrepeat">
      <td>PATTGEN.CONFIG.REPEAT</td>
      <td>Each channel can be configured to repeat the pattern up to 1024 times.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
IP pattgen currently contains no **Feature → Specification** mapping

## Feature -> Testpoint Matrix
IP pattgen currently contains no **Feature → Testpoint** mapping
