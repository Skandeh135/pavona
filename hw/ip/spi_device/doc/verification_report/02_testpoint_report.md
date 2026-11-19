# spi_device Testpoint Report

## 4b_3b_feature


- Configure passthrough or flash mode.
- Configure command info slots.
- Configure different values for 4B/3B.
- Randomize configuration of EN4B and EX4B register fields.
- Issue supported command with required address.
- Check proper address propagation.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_cfg_cmd">spi_device_cfg_cmd</a></td>
  <td><a href="01_feature_report.md#spi_devicehw3b4b_addressing">SPI_DEVICE.HW.3B4B_ADDRESSING</a><br><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a><br><a href="01_feature_report.md#spi_devicehwflash_emulation_blocks">SPI_DEVICE.HW.FLASH_EMULATION_BLOCKS</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulation">SPI_DEVICE.MODE.FLASH_EMULATION</a><br><a href="01_feature_report.md#spi_devicemodepassthrough">SPI_DEVICE.MODE.PASSTHROUGH</a></td>
</tr>
  </tbody>
</table>

## TPM_with_flash_or_passthrough_mode


- Enable TPM mode.
- Configure passthrough or flash mode.
- Issue TPM read/write interleaving with flash transactions.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_flash_and_tpm">spi_device_flash_and_tpm</a></td>
  <td><a href="01_feature_report.md#spi_devicemodeflash_emulation">SPI_DEVICE.MODE.FLASH_EMULATION</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulationcommands">SPI_DEVICE.MODE.FLASH_EMULATION.COMMANDS</a><br><a href="01_feature_report.md#spi_devicemodepassthrough">SPI_DEVICE.MODE.PASSTHROUGH</a><br><a href="01_feature_report.md#spi_devicemodetpm">SPI_DEVICE.MODE.TPM</a></td>
</tr>
  </tbody>
</table>

## chip_sw_spi_device_flash_mode (dragonfly)
Verify the SPI device in flash mode.

- SW puts the SPI device in flash mode.
- Load a firmware image (bootstrap) through flash commands to the spi_device memory.
- SW verifies the integrity of the image upon reception by reading the spi_device memory.
- Ensure the image is executed correctly.
- Verify the LAST_READ_ADDR.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rom_e2e_smoke-dragonfly">rom_e2e_smoke (dragonfly)</a></td>
  <td><a href="01_feature_report.md#spi_devicehwflash_emulation_blocks">SPI_DEVICE.HW.FLASH_EMULATION_BLOCKS</a><br><a href="01_feature_report.md#spi_devicehwlast_read_addr">SPI_DEVICE.HW.LAST_READ_ADDR</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulation">SPI_DEVICE.MODE.FLASH_EMULATION</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulationcommands">SPI_DEVICE.MODE.FLASH_EMULATION.COMMANDS</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulationread_command_processor">SPI_DEVICE.MODE.FLASH_EMULATION.READ_COMMAND_PROCESSOR</a></td>
</tr>
  </tbody>
</table>

## chip_sw_spi_device_flash_mode (egret)
Verify the SPI device in flash mode.

- SW puts the SPI device in flash mode.
- Load a firmware image (bootstrap) through flash commands to the spi_device memory.
- SW verifies the integrity of the image upon reception by reading the spi_device memory.
- Ensure the image is executed correctly.
- Verify the LAST_READ_ADDR.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#rom_e2e_smoke-egret">rom_e2e_smoke (egret)</a></td>
  <td><a href="01_feature_report.md#spi_devicehwflash_emulation_blocks">SPI_DEVICE.HW.FLASH_EMULATION_BLOCKS</a><br><a href="01_feature_report.md#spi_devicehwlast_read_addr">SPI_DEVICE.HW.LAST_READ_ADDR</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulation">SPI_DEVICE.MODE.FLASH_EMULATION</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulationcommands">SPI_DEVICE.MODE.FLASH_EMULATION.COMMANDS</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulationread_command_processor">SPI_DEVICE.MODE.FLASH_EMULATION.READ_COMMAND_PROCESSOR</a></td>
</tr>
  </tbody>
</table>

## chip_sw_spi_device_output_when_disabled_or_sleeping (dragonfly)
Verify spi_device output values when spi_device is disabled or the chip is sleeping.

SW needs to be able to set the SPI output value when spi_device is disabled or the
chip is sleeping, to either all-zeros or all-ones, depending on integration
requirements.  The following scenarios have to be verified:

After power-on reset:

- SW to configure pinmux retention logic so that the chip pins connected to
  spi_device outputs are (a) always zero or (b) always one (SW needs to be able to
  choose between a and b).
- DV environment to check that SPI outputs match configuration by SW.

Going to sleep:

- SW to disable spi_device, wait until CSb is high, configure pinmux retention logic
  as it would after POR, and put chip to sleep.
- DV environment to check that SPI outputs match configuration by SW.

Wake up from sleep:

- DV environment to wake chip from sleep.
- SW to enable spi_device and disable retention logic.
- DV environment to check that SPI transactions work as usual.

Notes for silicon targets:
This test currently does not exercise any features of the spi_device block itself,
which is why the "features" list is empty. It may be reclassified in the future.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_spi_device_pinmux_sleep_retention-dragonfly">chip_sw_spi_device_pinmux_sleep_retention (dragonfly)</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a><br><a href="01_feature_report.md#spi_devicehwlanes">SPI_DEVICE.HW.LANES</a><br><a href="01_feature_report.md#spi_devicejedec_cc">SPI_DEVICE.JEDEC_CC</a><br><a href="01_feature_report.md#spi_devicejedec_id">SPI_DEVICE.JEDEC_ID</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulation">SPI_DEVICE.MODE.FLASH_EMULATION</a></td>
</tr>
  </tbody>
</table>

## chip_sw_spi_device_output_when_disabled_or_sleeping (egret)
Verify spi_device output values when spi_device is disabled or the chip is sleeping.

SW needs to be able to set the SPI output value when spi_device is disabled or the
chip is sleeping, to either all-zeros or all-ones, depending on integration
requirements.  The following scenarios have to be verified:

After power-on reset:

- SW to configure pinmux retention logic so that the chip pins connected to
  spi_device outputs are (a) always zero or (b) always one (SW needs to be able to
  choose between a and b).
- DV environment to check that SPI outputs match configuration by SW.

Going to sleep:

- SW to disable spi_device, wait until CSb is high, configure pinmux retention logic
  as it would after POR, and put chip to sleep.
- DV environment to check that SPI outputs match configuration by SW.

Wake up from sleep:

- DV environment to wake chip from sleep.
- SW to enable spi_device and disable retention logic.
- DV environment to check that SPI transactions work as usual.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_spi_device_pinmux_sleep_retention-egret">chip_sw_spi_device_pinmux_sleep_retention (egret)</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a><br><a href="01_feature_report.md#spi_devicejedec_cc">SPI_DEVICE.JEDEC_CC</a><br><a href="01_feature_report.md#spi_devicejedec_id">SPI_DEVICE.JEDEC_ID</a></td>
</tr>
  </tbody>
</table>

## chip_sw_spi_device_pass_through (dragonfly)
Verify the passthrough mode from an end-to-end perspective.

- Configure the SPI device and host in passthrough mode.
- Program the cmd_filter_* CSRs to filter out random commands.
- Configure and enable both spi_host0 and spi_host1.
- Send random flash commands over the SPI device interface (chip IOs) from the
  testbench.
- Verify the flash commands which pass through spi_host0 are received on chip IOs.
- Verify that only the payloads that are not filtered show up on the SPI host interface
  at chip IOs.
- Verify spi_host1 doesn't send out any data from spi_device.
- Run with min (6MHz), typical (24Mhz) and max (30MHz) SPI clk frequencies.
- Run with single, dual and quad SPI modes.
- Testbench should test the following commands:
  - Read Normal
  - Fast Read
  - Fast Dual
  - Fast Quad
  - Chip Erase
  - Program


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_spi_device_pass_through-dragonfly">chip_sw_spi_device_pass_through (dragonfly)</a></td>
  <td><a href="01_feature_report.md#spi_devicehwlanes">SPI_DEVICE.HW.LANES</a><br><a href="01_feature_report.md#spi_devicemodepassthrough">SPI_DEVICE.MODE.PASSTHROUGH</a><br><a href="01_feature_report.md#spi_devicemodepassthroughcmd_filter">SPI_DEVICE.MODE.PASSTHROUGH.CMD_FILTER</a></td>
</tr>
  </tbody>
</table>

## chip_sw_spi_device_pass_through (egret)
Verify the passthrough mode from an end-to-end perspective.

- Configure the SPI device and host in passthrough mode.
- Program the cmd_filter_* CSRs to filter out random commands.
- Configure and enable both spi_host0 and spi_host1.
- Send random flash commands over the SPI device interface (chip IOs) from the
  testbench.
- Verify the flash commands which pass through spi_host0 are received on chip IOs.
- Verify that only the payloads that are not filtered show up on the SPI host interface
  at chip IOs.
- Verify spi_host1 doesn't send out any data from spi_device.
- Run with min (6MHz), typical (24Mhz) and max (30MHz) SPI clk frequencies.
- Run with single, dual and quad SPI modes.
- Testbench should test the following commands:
  - Read Normal
  - Fast Read
  - Fast Dual
  - Fast Quad
  - Chip Erase
  - Program


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_spi_device_pass_through-egret">chip_sw_spi_device_pass_through (egret)</a></td>
  <td><a href="01_feature_report.md#spi_devicehwlanes">SPI_DEVICE.HW.LANES</a><br><a href="01_feature_report.md#spi_devicemodepassthrough">SPI_DEVICE.MODE.PASSTHROUGH</a><br><a href="01_feature_report.md#spi_devicemodepassthroughcmd_filter">SPI_DEVICE.MODE.PASSTHROUGH.CMD_FILTER</a></td>
</tr>
  </tbody>
</table>

## chip_sw_spi_device_pass_through_collision (dragonfly)
Verify the collisions on driving spi_host is handled properly.

- Enable upload-related interrupts and configure the spi_device in passthrough mode.
- Configure a command slot to enable upload for a flash program/erase command.
- Execute two parallel threads:
  1. Upstream SPI host agent.
    - Send a flash program/erase, then keep sending read_status to poll the busy bit.
    - When the busy bit is low, issue a read command to read data from the downstream
      SPI port, and check data correctness.
  2. A SW process.
    - Receives an upload interrupt, then reads the command in the upload fifo to check.
    - Configures the SPI host that shows the same downstream port to send the
      uploaded command to the downstream SPI port.
    - Clears the busy bit to allow the upstream SPI host to proceed to the next command.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_spi_device_pass_through_collision-dragonfly">chip_sw_spi_device_pass_through_collision (dragonfly)</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a><br><a href="01_feature_report.md#spi_devicehwcommand_upload">SPI_DEVICE.HW.COMMAND_UPLOAD</a><br><a href="01_feature_report.md#spi_devicehwflash_emulation_blocks">SPI_DEVICE.HW.FLASH_EMULATION_BLOCKS</a><br><a href="01_feature_report.md#spi_devicemodepassthrough">SPI_DEVICE.MODE.PASSTHROUGH</a><br><a href="01_feature_report.md#spi_devicemodepassthroughintercept_en">SPI_DEVICE.MODE.PASSTHROUGH.INTERCEPT_EN</a></td>
</tr>
  </tbody>
</table>

## chip_sw_spi_device_pass_through_collision (egret)
Verify the collisions on driving spi_host is handled properly.

- Enable upload-related interrupts and configure the spi_device in passthrough mode.
- Configure a command slot to enable upload for a flash program/erase command.
- Execute two parallel threads:
  1. Upstream SPI host agent.
    - Send a flash program/erase, then keep sending read_status to poll the busy bit.
    - When the busy bit is low, issue a read command to read data from the downstream
      SPI port, and check data correctness.
  2. A SW process.
    - Receives an upload interrupt, then reads the command in the upload fifo to check.
    - Configures the SPI host that shows the same downstream port to send the
      uploaded command to the downstream SPI port.
    - Clears the busy bit to allow the upstream SPI host to proceed to the next command.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_spi_device_pass_through_collision-egret">chip_sw_spi_device_pass_through_collision (egret)</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a><br><a href="01_feature_report.md#spi_devicehwcommand_upload">SPI_DEVICE.HW.COMMAND_UPLOAD</a><br><a href="01_feature_report.md#spi_devicehwflash_emulation_blocks">SPI_DEVICE.HW.FLASH_EMULATION_BLOCKS</a><br><a href="01_feature_report.md#spi_devicemodepassthrough">SPI_DEVICE.MODE.PASSTHROUGH</a><br><a href="01_feature_report.md#spi_devicemodepassthroughintercept_en">SPI_DEVICE.MODE.PASSTHROUGH.INTERCEPT_EN</a></td>
</tr>
  </tbody>
</table>

## chip_sw_spi_device_pass_through_flash_model (egret)
Verify the command filtering mechanism in passthrough mode.

- Extend the chip_spi_device_pass_through test.
- Connect with a real flash model on spi_host.
- Verify that the flash commands are received and interpreted correctly in the flash
  model.


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
  <td><a href="01_feature_report.md#spi_devicehwlanes">SPI_DEVICE.HW.LANES</a><br><a href="01_feature_report.md#spi_devicemodepassthrough">SPI_DEVICE.MODE.PASSTHROUGH</a><br><a href="01_feature_report.md#spi_devicemodepassthroughcmd_filter">SPI_DEVICE.MODE.PASSTHROUGH.CMD_FILTER</a></td>
</tr>
  </tbody>
</table>

## chip_sw_spi_device_tpm (dragonfly)
Verify the basic operation of the spi_device in TPM mode.

- The testbench sends a known payload to the spi_device TPM input port.
- The testbench sends a read command.
- The software test should playback the data received in the write command as the read
  response.
- The testbench should check if the written and read data match.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_spi_device_tpm-dragonfly">chip_sw_spi_device_tpm (dragonfly)</a></td>
  <td><a href="01_feature_report.md#spi_devicemodetpm">SPI_DEVICE.MODE.TPM</a><br><a href="01_feature_report.md#spi_devicemodetpmread_fifo_mode">SPI_DEVICE.MODE.TPM.READ_FIFO_MODE</a></td>
</tr>
  </tbody>
</table>

## chip_sw_spi_device_tpm (egret)
Verify the basic operation of the spi_device in TPM mode.

- The testbench sends a known payload to the spi_device TPM input port.
- The testbench sends a read command.
- The software test should playback the data received in the write command as the read
  response.
- The testbench should check if the written and read data match.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#chip_sw_spi_device_tpm-egret">chip_sw_spi_device_tpm (egret)</a></td>
  <td><a href="01_feature_report.md#spi_devicemodetpm">SPI_DEVICE.MODE.TPM</a><br><a href="01_feature_report.md#spi_devicemodetpmread_fifo_mode">SPI_DEVICE.MODE.TPM.READ_FIFO_MODE</a></td>
</tr>
  </tbody>
</table>

## cmd_dummy_cycle


- Configure cmd info slots.
- Configure dummy cycle of read commands to non default value.
- For single mode allowed dummy cycle is 0 or more.
- For dual/quad mode allowed dummy cycle is 2 or more.
- Check return data timing for configured commands.
- Check proper read data.
- Issue new read command that crosses read maibox boundary.
- Check internal buffer index bit.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_flash_all">spi_device_flash_all</a><br><a href="03_test_report.md#spi_device_mailbox">spi_device_mailbox</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulation">SPI_DEVICE.MODE.FLASH_EMULATION</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulationdummy_cycle">SPI_DEVICE.MODE.FLASH_EMULATION.DUMMY_CYCLE</a></td>
</tr>
  </tbody>
</table>

## cmd_fast_read


- Configure proper fast read command info slot.
- Issue fast read command.
- Check propagation of fast read command.
- Initiate response to the fast read.
- Check proper reception of response.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_flash_all">spi_device_flash_all</a><br><a href="03_test_report.md#spi_device_intercept">spi_device_intercept</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a></td>
</tr>
  </tbody>
</table>

## cmd_info_slots


- Configure first 5 slots according to required configuration.
- Configure next 6 slots for read commands
- Randomize configuration of the remaining 13 cmd info slots.
- Issue commands with various opcodes enabled in info slots.
- Check proper command propagation.
- Disable some cmd info slots.
- Check no propagation of disabled commands.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_flash_all">spi_device_flash_all</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulation">SPI_DEVICE.MODE.FLASH_EMULATION</a></td>
</tr>
  </tbody>
</table>

## cmd_read_buffer


- Configure device in flash mode.
- Issue read commands.
- Create another parallel thread that SW updates read buffer contents after a watermark
  or buffer flip event occurs.
- Check proper read data.
- Randomly issue read command that crosses read buffer boundary and switches back to
  index 0.
- Check correctness of `last_read_addr`, `readbuf_watermark` and `readbuf_flip`.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_flash_mode">spi_device_flash_mode</a><br><a href="03_test_report.md#spi_device_read_buffer_direct">spi_device_read_buffer_direct</a></td>
  <td><a href="01_feature_report.md#spi_devicehwlast_read_addr">SPI_DEVICE.HW.LAST_READ_ADDR</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulation">SPI_DEVICE.MODE.FLASH_EMULATION</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulationread_command_processor">SPI_DEVICE.MODE.FLASH_EMULATION.READ_COMMAND_PROCESSOR</a></td>
</tr>
  </tbody>
</table>

## cmd_read_jedec


- Configure proper read JEDEC command info slot.
- Issue read JEDEC command.
- Check propagation of read JEDEC command.
- Initiate response to the read JEDEC.
- Check proper reception of response.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_flash_all">spi_device_flash_all</a><br><a href="03_test_report.md#spi_device_intercept">spi_device_intercept</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a><br><a href="01_feature_report.md#spi_devicehwflash_emulation_blocks">SPI_DEVICE.HW.FLASH_EMULATION_BLOCKS</a><br><a href="01_feature_report.md#spi_devicejedec_cc">SPI_DEVICE.JEDEC_CC</a><br><a href="01_feature_report.md#spi_devicejedec_id">SPI_DEVICE.JEDEC_ID</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulation">SPI_DEVICE.MODE.FLASH_EMULATION</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulationcommands">SPI_DEVICE.MODE.FLASH_EMULATION.COMMANDS</a></td>
</tr>
  </tbody>
</table>

## cmd_read_pipeline


- Configure proper fast read command info slot with the read data pipeline feature.
- Issue fast read command.
- Check propagation of fast read command, including dummy cycles for read data pipeline.
- Initiate response to the fast read.
- Check proper reception of response.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_flash_all">spi_device_flash_all</a><br><a href="03_test_report.md#spi_device_intercept">spi_device_intercept</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulation">SPI_DEVICE.MODE.FLASH_EMULATION</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulationdummy_cycle">SPI_DEVICE.MODE.FLASH_EMULATION.DUMMY_CYCLE</a></td>
</tr>
  </tbody>
</table>

## cmd_read_sfdp


- Configure proper read SFDP command info slot.
- Issue read SFDP command.
- Check propagation of read SFDP command.
- Initiate response to the read SFDP.
- Check proper reception of response.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_flash_all">spi_device_flash_all</a><br><a href="03_test_report.md#spi_device_intercept">spi_device_intercept</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a><br><a href="01_feature_report.md#spi_devicehwflash_emulation_blocks">SPI_DEVICE.HW.FLASH_EMULATION_BLOCKS</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulation">SPI_DEVICE.MODE.FLASH_EMULATION</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulationcommands">SPI_DEVICE.MODE.FLASH_EMULATION.COMMANDS</a></td>
</tr>
  </tbody>
</table>

## cmd_read_status


- Configure proper read status command info slot.
- Issue read status command.
- Check propagation of read status command.
- Initiate response to the read status.
- Check proper reception of response.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_flash_all">spi_device_flash_all</a><br><a href="03_test_report.md#spi_device_intercept">spi_device_intercept</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a><br><a href="01_feature_report.md#spi_devicemodepassthroughintercept_en">SPI_DEVICE.MODE.PASSTHROUGH.INTERCEPT_EN</a></td>
</tr>
  </tbody>
</table>

## csb_read
Read `CSb` value from CSR and check the correctness

This feature is for debug only, so it's sufficient to verify with this direct sequence:

- Assign both `CSb` pins with random values and read the `CSb` CSRs to check the values


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_csb_read">spi_device_csb_read</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcsb_status">SPI_DEVICE.HW.CSB_STATUS</a></td>
</tr>
  </tbody>
</table>

## dual_spi


- Configure passthrough or flash mode.
- Configure cmd info slots.
- Configure dual mode.
- Issue supported command.
- Check data on both lines.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_flash_all">spi_device_flash_all</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a><br><a href="01_feature_report.md#spi_devicehwlanes">SPI_DEVICE.HW.LANES</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulation">SPI_DEVICE.MODE.FLASH_EMULATION</a><br><a href="01_feature_report.md#spi_devicemodepassthrough">SPI_DEVICE.MODE.PASSTHROUGH</a></td>
</tr>
  </tbody>
</table>

## flash_cmd_upload


- Configure `spi_device` on flash or passthrough mode.
- Configure cmd info slots.
- Set upload to 1 for some of 13 non fixed cmd info slots.
- Host should poll busy field status to check if command is done.
- Issue next command upload and poll busy status again.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_upload">spi_device_upload</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a><br><a href="01_feature_report.md#spi_devicehwcommand_upload">SPI_DEVICE.HW.COMMAND_UPLOAD</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulation">SPI_DEVICE.MODE.FLASH_EMULATION</a><br><a href="01_feature_report.md#spi_devicemodepassthrough">SPI_DEVICE.MODE.PASSTHROUGH</a></td>
</tr>
  </tbody>
</table>

## mailbox_command


- Configure cmd info slots.
- Issue one of predefined read command targeting mailbox space.
- Check response to read command.
- Check if command is processed internally.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_mailbox">spi_device_mailbox</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a><br><a href="01_feature_report.md#spi_devicemodepassthroughmailbox">SPI_DEVICE.MODE.PASSTHROUGH.MAILBOX</a></td>
</tr>
  </tbody>
</table>

## mailbox_cross_inside_command


- Similar to `mailbox_cross_outside_command`, except that start address is inside the
  mailbox.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_mailbox">spi_device_mailbox</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a><br><a href="01_feature_report.md#spi_devicemodepassthrough">SPI_DEVICE.MODE.PASSTHROUGH</a><br><a href="01_feature_report.md#spi_devicemodepassthroughmailbox">SPI_DEVICE.MODE.PASSTHROUGH.MAILBOX</a></td>
</tr>
  </tbody>
</table>

## mailbox_cross_outside_command


- Configure `spi_device` on passthrough mode. Mailbox boundary crossing is not expected to
  be used on flash mode, so that testing this on flash mode isn't needed.
- Configure cmd info slots.
- Issue one of predefined read command targeting mailbox space.
- Command should start inside mailbox space and cross into read space.
- When the address falls in the mailbox region, data returns from the mailbox. when the
  address is outside the mailbox, data returns as follows
    - Returns high-z if the read command is filtered.
    - Returns from downstream port if read command is passed through.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_mailbox">spi_device_mailbox</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a><br><a href="01_feature_report.md#spi_devicemodepassthrough">SPI_DEVICE.MODE.PASSTHROUGH</a><br><a href="01_feature_report.md#spi_devicemodepassthroughmailbox">SPI_DEVICE.MODE.PASSTHROUGH.MAILBOX</a></td>
</tr>
  </tbody>
</table>

## mem_cfg
Test `cfg_i` connectivity between `spi_device` and the backing RAM.


Randomly set `dut.ram_cfg_i` and check this value is propagated to the memory itself.
For the `1r1w` implementation, where the RAM is split into ingress and egress portions,
check that the configuration makes it to both sides.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_ram_cfg">spi_device_ram_cfg</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## mem_parity
Test memory parity error

Pick a random memory address to inject parity errors and read it back,
then check it returns `d_error` with all 1s as data.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_mem_parity">spi_device_mem_parity</a></td>
  <td>No features</td>
</tr>
  </tbody>
</table>

## pass_addr_translation


- Randomize command opcode.
- Configure unused `CMD_INFO` reg with new opcode and set it to valid.
- Enable address translation for given command.
- Configure address translation bits.
- Check proper address translation is applied.
- Disable address translation for given command.
- Check address is now passing unchanged.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_flash_all">spi_device_flash_all</a><br><a href="03_test_report.md#spi_device_pass_addr_payload_swap">spi_device_pass_addr_payload_swap</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a><br><a href="01_feature_report.md#spi_devicemodepassthrough">SPI_DEVICE.MODE.PASSTHROUGH</a><br><a href="01_feature_report.md#spi_devicemodepassthroughaddress_manipulation">SPI_DEVICE.MODE.PASSTHROUGH.ADDRESS_MANIPULATION</a></td>
</tr>
  </tbody>
</table>

## pass_cmd_filtering


- Randomize command opcode.
- Configure unused `CMD_INFO` reg with new opcode and set it to valid.
- Check opcode, address and payload are passing through.
- Configure filter bit corresponding to opcode to 1.
- Check the entire command is filtered.
- Set filter bit back to 0.
- Check opcode and address are passing through again.
- Invalid opcode is also filtered


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_flash_all">spi_device_flash_all</a><br><a href="03_test_report.md#spi_device_pass_cmd_filtering">spi_device_pass_cmd_filtering</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a><br><a href="01_feature_report.md#spi_devicemodepassthrough">SPI_DEVICE.MODE.PASSTHROUGH</a><br><a href="01_feature_report.md#spi_devicemodepassthroughcmd_filter">SPI_DEVICE.MODE.PASSTHROUGH.CMD_FILTER</a></td>
</tr>
  </tbody>
</table>

## pass_payload_translation


- Configure program or write_status command.
- Enable payload translation for given command.
- Configure payload translation bits.
- Check proper payload translation is applied.
- Disable payload translation for given command.
- Check payload is now passing unchanged.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_flash_all">spi_device_flash_all</a><br><a href="03_test_report.md#spi_device_pass_addr_payload_swap">spi_device_pass_addr_payload_swap</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a><br><a href="01_feature_report.md#spi_devicemodepassthrough">SPI_DEVICE.MODE.PASSTHROUGH</a><br><a href="01_feature_report.md#spi_devicemodepassthroughstatus_manipulation">SPI_DEVICE.MODE.PASSTHROUGH.STATUS_MANIPULATION</a></td>
</tr>
  </tbody>
</table>

## quad_spi


- Configure passthrough or flash mode.
- Configure cmd info slots.
- Configure quad mode.
- Issue supported command.
- Check data on all four lines.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_flash_all">spi_device_flash_all</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a><br><a href="01_feature_report.md#spi_devicehwlanes">SPI_DEVICE.HW.LANES</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulation">SPI_DEVICE.MODE.FLASH_EMULATION</a><br><a href="01_feature_report.md#spi_devicemodepassthrough">SPI_DEVICE.MODE.PASSTHROUGH</a></td>
</tr>
  </tbody>
</table>

## smoke

Configures Flash/Passthrough modes as well as TPM and drive reads/writes
through SPI alternating between TPM and SPI commands.
Sequences `spi_device_flash_all_vseq` and `spi_device_tpm_all_vseq` are
launched in parallel.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_flash_and_tpm">spi_device_flash_and_tpm</a></td>
  <td><a href="01_feature_report.md#spi_devicemodeflash_emulation">SPI_DEVICE.MODE.FLASH_EMULATION</a><br><a href="01_feature_report.md#spi_devicemodepassthrough">SPI_DEVICE.MODE.PASSTHROUGH</a><br><a href="01_feature_report.md#spi_devicemodetpm">SPI_DEVICE.MODE.TPM</a></td>
</tr>
  </tbody>
</table>

## stress_all


- Combine above sequences in one test to run sequentially, except CSR sequences.
- Test modes switch among FW, flash, passthrough and tpm.
- Randomly add reset between each sequence


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_stress_all">spi_device_stress_all</a></td>
  <td><a href="01_feature_report.md#spi_devicemodeflash_emulation">SPI_DEVICE.MODE.FLASH_EMULATION</a><br><a href="01_feature_report.md#spi_devicemodepassthrough">SPI_DEVICE.MODE.PASSTHROUGH</a><br><a href="01_feature_report.md#spi_devicemodetpm">SPI_DEVICE.MODE.TPM</a></td>
</tr>
  </tbody>
</table>

## tpm_and_flash_trans_with_min_inactive_time

Issue these transactions with 2 `sys_clk` inactive time in between.

- 2 tpm transactions.
- 2 flash transactions.
- A TPM transaction and a Flash transaction.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_flash_and_tpm_min_idle">spi_device_flash_and_tpm_min_idle</a></td>
  <td><a href="01_feature_report.md#spi_devicemodeflash_emulation">SPI_DEVICE.MODE.FLASH_EMULATION</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulationcommands">SPI_DEVICE.MODE.FLASH_EMULATION.COMMANDS</a><br><a href="01_feature_report.md#spi_devicemodetpm">SPI_DEVICE.MODE.TPM</a></td>
</tr>
  </tbody>
</table>

## tpm_fully_random_case


- Configure `TPM_CFG.EN` to On and fully randomize other TPM configuration.
- Run these 3 threads to randomly access TPM HW registers and other addresses.
  - Host issues random TPM reads/writes to spi_device.
  - SW polls the TPM interrupt `tpm_header_not_empty`, then read command/address and
    the corresponding FIFO.
  - SW randomly updates TPM HW registers.
- Ensure all the data is correct in the scoreboard.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_tpm_all">spi_device_tpm_all</a></td>
  <td><a href="01_feature_report.md#spi_devicemodetpm">SPI_DEVICE.MODE.TPM</a><br><a href="01_feature_report.md#spi_devicemodetpmauto_wait">SPI_DEVICE.MODE.TPM.AUTO_WAIT</a><br><a href="01_feature_report.md#spi_devicemodetpmread_fifo_mode">SPI_DEVICE.MODE.TPM.READ_FIFO_MODE</a><br><a href="01_feature_report.md#spi_devicemodetpmreturn-by-hw_regs">SPI_DEVICE.MODE.TPM.RETURN-BY-HW_REGS</a></td>
</tr>
  </tbody>
</table>

## tpm_hw_reg


- Configure `TPM_CFG` as follows to have DUT directly respond for the access to the HW
  registers.
  - Set `tpm_mode` to fifo mode.
  - Set `hw_reg_dis` to 0.
  - Set `tpm_reg_chk_dis` to 0.
  - Set `invalid_locality` to 1.
- Send SPI transactions of varying HW registers. In the meanwhile, SW updates the HW
  registers.
- Ensure that the data returned is correct for the given address and active locality.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_tpm_read_hw_reg">spi_device_tpm_read_hw_reg</a><br><a href="03_test_report.md#spi_device_tpm_sts_read">spi_device_tpm_sts_read</a></td>
  <td><a href="01_feature_report.md#spi_devicemodetpm">SPI_DEVICE.MODE.TPM</a><br><a href="01_feature_report.md#spi_devicemodetpmread_fifo_mode">SPI_DEVICE.MODE.TPM.READ_FIFO_MODE</a></td>
</tr>
  </tbody>
</table>

## tpm_read


- Set `TPM_CFG.TPM_MODE` to CRB mode and set TPM_CFG.EN.
- Randomise other fields in `TPM_CFG`.
- Assert the `tpm_csb`.
- Send TPM read command over the SPI bus with a randomised address.
- Check `TPM_CMD_ADDR`.
- Confirm FIFO behaviour dictated by `TPM_CFG.tpm``_mode.
- Check `TPM_STATUS.cmdaddr_notempty` and `INTR_STATE.tpm_header_notempty`, they should be asserted if `hw_reg_dis == 0`.
- If `hw_reg_dis == 0`, the data is returned to the host via return-by-HW register, else the data is returned via read TPM FIFO in SRAM.
- Confirm that the TPM submodule sends WAIT until the read FIFO is available.
- Check the read FIFO.
- When available, confirm that the TPM submodule sends START followed by the register value.
- Compare this value with the expected value.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_tpm_rw">spi_device_tpm_rw</a></td>
  <td><a href="01_feature_report.md#spi_devicemodetpm">SPI_DEVICE.MODE.TPM</a><br><a href="01_feature_report.md#spi_devicemodetpmauto_wait">SPI_DEVICE.MODE.TPM.AUTO_WAIT</a><br><a href="01_feature_report.md#spi_devicemodetpmreturn-by-hw_regs">SPI_DEVICE.MODE.TPM.RETURN-BY-HW_REGS</a></td>
</tr>
  </tbody>
</table>

## tpm_write


- Set `TPM_CFG.TPM_MODE` to CRB mode and set `TPM_CFG.EN`.
- Randomise other fields in `TPM_CFG`.
- Assert the `tpm_csb`.
- Send TPM write command with a randomised address.
- Check `TPM_CMD_ADDR` and write FIFO.
- Check `TPM_STATUS.cmdaddr_notempty` and `INTR_STATE.tpm_header_notempty`.
- Based on FIFO status, check SPI bus to confirm WAIT or START sent.
- Check that the TPM submodule accepts write data without the WAIT state if the write FIFO is empty.
- Otherwise, check WAIT until the write FIFO becomes available (empty).


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_tpm_rw">spi_device_tpm_rw</a></td>
  <td><a href="01_feature_report.md#spi_devicemodetpm">SPI_DEVICE.MODE.TPM</a><br><a href="01_feature_report.md#spi_devicemodetpmauto_wait">SPI_DEVICE.MODE.TPM.AUTO_WAIT</a></td>
</tr>
  </tbody>
</table>

## write_enable_disable


- Configure passthrough or flash mode.
- Randomize WREN and WRDI command info slots.
- Issue WREN and WRDI commands along with read_status command and others.
- Read flash status via TL interface.
- Check WREN/WRDI sets/clears flash status correctly.


<table class="verification_report_table">
  <thead>
    <tr>
      <th>Tests</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>

<tr>
  <td><a href="03_test_report.md#spi_device_cfg_cmd">spi_device_cfg_cmd</a></td>
  <td><a href="01_feature_report.md#spi_devicehwcmdinfos">SPI_DEVICE.HW.CMDINFOS</a><br><a href="01_feature_report.md#spi_devicehwflash_emulation_blocks">SPI_DEVICE.HW.FLASH_EMULATION_BLOCKS</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulation">SPI_DEVICE.MODE.FLASH_EMULATION</a><br><a href="01_feature_report.md#spi_devicemodeflash_emulationwrite_enable_disable">SPI_DEVICE.MODE.FLASH_EMULATION.WRITE_ENABLE_DISABLE</a><br><a href="01_feature_report.md#spi_devicemodepassthrough">SPI_DEVICE.MODE.PASSTHROUGH</a></td>
</tr>
  </tbody>
</table>
