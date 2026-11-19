# spi_device Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="spi_devicehw3b4b_addressing">
      <td>SPI_DEVICE.HW.3B4B_ADDRESSING</td>
      <td>Support CSR control of 3B/4B operation, plus host control with EN4B/EX4B</td>
    </tr>
    <tr id="spi_devicehwcmdinfos">
      <td>SPI_DEVICE.HW.CMDINFOS</td>
      <td>Registers that can contain custom opcode + data for responding to SPI Flash Commands.</td>
    </tr>
    <tr id="spi_devicehwcommand_upload">
      <td>SPI_DEVICE.HW.COMMAND_UPLOAD</td>
      <td>HW can store the received command into the command/address FIFOs and payload buffer.MODES:FLASH_EMULATION,PASSTHROUGH- A received SPI Flash command can conditionally be written to the command,address and payload FIFOs.- SW can access data about the uploaded commands via CSR.UPLOAD_STATUS and CSR.UPLOAD_STATUS2.- SW can read CSR.UPLOAD_CMDFIFO to access the command FIFO.- SW can read CSR.UPLOAD_ADDRFIFO to access the address FIFO.- The payload FIFO can be read by accessing the DPSRAM window.</td>
    </tr>
    <tr id="spi_devicehwcsb_status">
      <td>SPI_DEVICE.HW.CSB_STATUS</td>
      <td>CSR.STATUS fields show the current status of the two CSB signals (.csb/.tpm_csb).</td>
    </tr>
    <tr id="spi_devicehwflash_emulation_blocks">
      <td>SPI_DEVICE.HW.FLASH_EMULATION_BLOCKS</td>
      <td>Hardware contains a number of submodules for handling certain commands.cmdparse, READ, EN4B/EX4B, SFDP, JEDEC, status/busy- CSR.FLASH_STATUS contains SW-writable bits that define the response to a Read Status Register command.- Some fields in CSR.FLASH_STATUS may also be modified by HW.  - WRDI/WREN commands modify the CSR.FLASH_STATUS.status.WEL bit.  - CSR.FLASH_STATUS.status.BUSY may be modified by HW depending on command upload configuration of the    CSR.CMDINFO[x].busy field.- CSR.JEDEC_CC and CSR.JEDEC_ID provide data for the JEDEC Read command.- The SFDP section of DPSRAM provides data for the Read SFDP command.</td>
    </tr>
    <tr id="spi_devicehwlanes">
      <td>SPI_DEVICE.HW.LANES</td>
      <td>1,2 or 4 lane operation is supported by the block.</td>
    </tr>
    <tr id="spi_devicehwlast_read_addr">
      <td>SPI_DEVICE.HW.LAST_READ_ADDR</td>
      <td>The register CSR.LAST_READ_ADDR shows the last address a SPI Flash Read command accessed before CSb de-assertion.MODES : FLASH_EMULATION,PASSTHROUGH</td>
    </tr>
    <tr id="spi_devicehwserdes_ordering">
      <td>SPI_DEVICE.HW.SERDES_ORDERING</td>
      <td>The block allows serialization ordering control for SDI/SDO that can be controlled at runtime.CSR.CFG.rx_order : "RX bit order on SDI. 0 for MSB first, 1 for LSB first."CSR.CFG.tx_order : "TX bit order on SDO. 0 for MSB first, 1 for LSB first.</td>
    </tr>
    <tr id="spi_devicejedec_cc">
      <td>SPI_DEVICE.JEDEC_CC</td>
      <td>The JEDEC module can be configued by software to return the proper number of continuation codes (CC) needed for identification for a particular manufacturer.</td>
    </tr>
    <tr id="spi_devicejedec_id">
      <td>SPI_DEVICE.JEDEC_ID</td>
      <td>The JEDEC module can return a device ID (one byte) and manufacturer ID (two bytes).</td>
    </tr>
    <tr id="spi_devicemodeflash_emulation">
      <td>SPI_DEVICE.MODE.FLASH_EMULATION</td>
      <td>Emulates the behaviour of a Serial Flash device when connected to an upstream SPI Host.In this mode, the block recognizes SPI Flash commands and can respond entirely in HW.</td>
    </tr>
    <tr id="spi_devicemodeflash_emulationcommands">
      <td>SPI_DEVICE.MODE.FLASH_EMULATION.COMMANDS</td>
      <td>Device should respond to all specified standard SPI Flash Commands.</td>
    </tr>
    <tr id="spi_devicemodeflash_emulationdummy_cycle">
      <td>SPI_DEVICE.MODE.FLASH_EMULATION.DUMMY_CYCLE</td>
      <td>Insertion of dummy cycles between SPI Flash opcode and data.</td>
    </tr>
    <tr id="spi_devicemodeflash_emulationread_command_processor">
      <td>SPI_DEVICE.MODE.FLASH_EMULATION.READ_COMMAND_PROCESSOR</td>
      <td>SPI Flash Read commands are provided with data from a DPSRAM section with a ping-pong buffering scheme, or a fixed mailbox region.- The readptr crossing the buffer boundary creates a readbuf_flip interrupt.- The readptr crossing the offset CSR.READ_THRESHOLD within a buffer creates a readbuf_watermark interrupt.</td>
    </tr>
    <tr id="spi_devicemodeflash_emulationwrite_enable_disable">
      <td>SPI_DEVICE.MODE.FLASH_EMULATION.WRITE_ENABLE_DISABLE</td>
      <td>The block supports SPI Flash WREN/WRDI commands from the external host.</td>
    </tr>
    <tr id="spi_devicemodepassthrough">
      <td>SPI_DEVICE.MODE.PASSTHROUGH</td>
      <td>The block acts as a proxy to a downstream external SPI Flash, with optional inline filtering and monitoring.In this mode, an upstream SPI Host communicates with a downstream external SPI Flash.Traffic received by this block is forwarded to a SPI_HOST instance, which thenrelays the traffic onto the downstream external SPI flash.Runtime-configurable filtering, payload interception, payload substitution and monitoring operationson the passthrough traffic are provided by the block.</td>
    </tr>
    <tr id="spi_devicemodepassthroughaddress_manipulation">
      <td>SPI_DEVICE.MODE.PASSTHROUGH.ADDRESS_MANIPULATION</td>
      <td>By configuring ADDR_SWAP_MASK and ADDR_SWAP_DATA CSRs, certain address bits of Flash Commands can be overwritten on passthrough.</td>
    </tr>
    <tr id="spi_devicemodepassthroughcmd_filter">
      <td>SPI_DEVICE.MODE.PASSTHROUGH.CMD_FILTER</td>
      <td>Passthrough logic filters the command based on the 256-bit value of the "CMD_FILTER_0" CSR.</td>
    </tr>
    <tr id="spi_devicemodepassthroughintercept_en">
      <td>SPI_DEVICE.MODE.PASSTHROUGH.INTERCEPT_EN</td>
      <td>Allow the block to reply to SPI Flash commands, taking precedence over the data returned by the passthrough device.</td>
    </tr>
    <tr id="spi_devicemodepassthroughmailbox">
      <td>SPI_DEVICE.MODE.PASSTHROUGH.MAILBOX</td>
      <td>Return data from the 1kB Mailbox read/write buffer if the command address falls in the range (MAILBOX_ADDR:MAILBOX_ADDR+1kB).</td>
    </tr>
    <tr id="spi_devicemodepassthroughoutput_enable_control">
      <td>SPI_DEVICE.MODE.PASSTHROUGH.OUTPUT_ENABLE_CONTROL</td>
      <td>Passthrough module can control the output enable signals on both host and downstream side.</td>
    </tr>
    <tr id="spi_devicemodepassthroughstatus_manipulation">
      <td>SPI_DEVICE.MODE.PASSTHROUGH.STATUS_MANIPULATION</td>
      <td>By configuring PAYLOAD_SWAP_MASK and PAYLOAD_SWAP_DATA CSRs, certain bits of the first 4 payload bytes may be overwritten on passthrough.</td>
    </tr>
    <tr id="spi_devicemodetpm">
      <td>SPI_DEVICE.MODE.TPM</td>
      <td>Acts as a device-side endpoint in compliance with TPM PC Client Platform over SPI.</td>
    </tr>
    <tr id="spi_devicemodetpmauto_wait">
      <td>SPI_DEVICE.MODE.TPM.AUTO_WAIT</td>
      <td>If the address of a command does not fall into a pre-configured range, the block automatically returns a WAIT on the bus.</td>
    </tr>
    <tr id="spi_devicemodetpmcapability">
      <td>SPI_DEVICE.MODE.TPM.CAPABILITY</td>
      <td>TPM-mode can advertise the capabilities it supports to the upstream Host by setting CSR.TPM_CAP.</td>
    </tr>
    <tr id="spi_devicemodetpmread_fifo_mode">
      <td>SPI_DEVICE.MODE.TPM.READ_FIFO_MODE</td>
      <td>If not activating the RETURN-BY-HW mode, the block responds to a Host TPM commands when the TPM_READ_FIFO has data >= requested transfer size.</td>
    </tr>
    <tr id="spi_devicemodetpmreturn-by-hw_regs">
      <td>SPI_DEVICE.MODE.TPM.RETURN-BY-HW_REGS</td>
      <td>Block can auto-respond to a TPM host when the address falls within a configured range using the RETURN-BY-HW registers.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>SPI_DEVICE.MODE.FLASH_EMULATION</th>
    <th>SPI_DEVICE.MODE.PASSTHROUGH</th>
    <th>SPI_DEVICE.MODE.TPM</th>
    <th>SPI_DEVICE.HW.LANES</th>
    <th>SPI_DEVICE.HW.SERDES_ORDERING</th>
    <th>SPI_DEVICE.HW.CSB_STATUS</th>
    <th>SPI_DEVICE.MODE.FLASH_EMULATION.COMMANDS</th>
    <th>SPI_DEVICE.HW.FLASH_EMULATION_BLOCKS</th>
    <th>SPI_DEVICE.MODE.FLASH_EMULATION.READ_COMMAND_PROCESSOR</th>
    <th>SPI_DEVICE.MODE.FLASH_EMULATION.DUMMY_CYCLE</th>
    <th>SPI_DEVICE.MODE.FLASH_EMULATION.WRITE_ENABLE_DISABLE</th>
    <th>SPI_DEVICE.HW.LAST_READ_ADDR</th>
    <th>SPI_DEVICE.HW.CMDINFOS</th>
    <th>SPI_DEVICE.HW.COMMAND_UPLOAD</th>
    <th>SPI_DEVICE.HW.3B4B_ADDRESSING</th>
    <th>SPI_DEVICE.MODE.PASSTHROUGH.CMD_FILTER</th>
    <th>SPI_DEVICE.MODE.PASSTHROUGH.ADDRESS_MANIPULATION</th>
    <th>SPI_DEVICE.MODE.PASSTHROUGH.STATUS_MANIPULATION</th>
    <th>SPI_DEVICE.MODE.PASSTHROUGH.OUTPUT_ENABLE_CONTROL</th>
    <th>SPI_DEVICE.MODE.PASSTHROUGH.INTERCEPT_EN</th>
    <th>SPI_DEVICE.MODE.PASSTHROUGH.MAILBOX</th>
    <th>SPI_DEVICE.MODE.TPM.RETURN-BY-HW_REGS</th>
    <th>SPI_DEVICE.MODE.TPM.AUTO_WAIT</th>
    <th>SPI_DEVICE.MODE.TPM.READ_FIFO_MODE</th>
    <th>SPI_DEVICE.MODE.TPM.CAPABILITY</th>
    <th>SPI_DEVICE.JEDEC_CC</th>
    <th>SPI_DEVICE.JEDEC_ID</th>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#theory-of-operation">Theory of Operation</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#block-diagram">Block Diagram</a></th>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
    <td><a href="../theory_of_operation.md#block-diagram">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#spi-flash-and-passthrough-modes">SPI Flash and Passthrough Modes</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#spi-flash-and-passthrough-modes">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#command-information-list">Command Information List</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#command-information-list">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#command-information-list">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#command-information-list">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#command-information-list">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#command-parser">Command Parser</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#command-parser">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#status-control">Status Control</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#status-control">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#status-control">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#jedec-id-control">JEDEC ID Control</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#jedec-id-control">X</a></td>
    <td><a href="../theory_of_operation.md#jedec-id-control">X</a></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#serial-flash-discoverable-parameters-sfdp-control">Serial Flash Discoverable Parameters (SFDP) Control</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#serial-flash-discoverable-parameters-sfdp-control">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#read-command-processor">Read Command Processor</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#read-command-processor">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#address-handling">Address Handling</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#address-handling">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#address-handling">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#dummy-cycle">Dummy Cycle</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#dummy-cycle">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#pipelined-reads">Pipelined Reads</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#buffer-management">Buffer Management</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#buffer-management">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#4b-address-management-en4b-ex4b">4B Address Management (EN4B/ EX4B)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#4b-address-management-en4b-ex4b">X</a></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#command-upload">Command Upload</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#command-upload">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#passthrough">Passthrough</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#passthrough">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#command-filtering">Command Filtering</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#command-filtering">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#command-filtering">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#address-manipulation">Address Manipulation</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#address-manipulation">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#address-manipulation">X</a></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#write-status-data-manipulation">Write Status Data Manipulation</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#write-status-data-manipulation">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#write-status-data-manipulation">X</a></td>
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
    <th><a href="../theory_of_operation.md#output-enable-control">Output Enable Control</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#output-enable-control">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#output-enable-control">X</a></td>
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
    <th><a href="../theory_of_operation.md#internally-processed-commands">Internally processed Commands</a></th>
    <td></td>
    <td><a href="../theory_of_operation.md#internally-processed-commands">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#internally-processed-commands">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#internally-processed-commands">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#tpm-over-spi">TPM over SPI</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#tpm-over-spi">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#tpm-over-spi">X</a></td>
    <td><a href="../theory_of_operation.md#tpm-over-spi">X</a></td>
    <td><a href="../theory_of_operation.md#tpm-over-spi">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#configuring-return-by-hw-registers">Configuring Return-by-HW registers</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#configuring-return-by-hw-registers">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#detecting-reliability-errors">Detecting Reliability Errors</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="../theory_of_operation.md#clock-and-phase">Clock and Phase</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th>SPI_DEVICE.MODE.FLASH_EMULATION</th>
    <th>SPI_DEVICE.MODE.PASSTHROUGH</th>
    <th>SPI_DEVICE.MODE.TPM</th>
    <th>SPI_DEVICE.HW.LANES</th>
    <th>SPI_DEVICE.HW.SERDES_ORDERING</th>
    <th>SPI_DEVICE.HW.CSB_STATUS</th>
    <th>SPI_DEVICE.MODE.FLASH_EMULATION.COMMANDS</th>
    <th>SPI_DEVICE.HW.FLASH_EMULATION_BLOCKS</th>
    <th>SPI_DEVICE.MODE.FLASH_EMULATION.READ_COMMAND_PROCESSOR</th>
    <th>SPI_DEVICE.MODE.FLASH_EMULATION.DUMMY_CYCLE</th>
    <th>SPI_DEVICE.MODE.FLASH_EMULATION.WRITE_ENABLE_DISABLE</th>
    <th>SPI_DEVICE.HW.LAST_READ_ADDR</th>
    <th>SPI_DEVICE.HW.CMDINFOS</th>
    <th>SPI_DEVICE.HW.COMMAND_UPLOAD</th>
    <th>SPI_DEVICE.HW.3B4B_ADDRESSING</th>
    <th>SPI_DEVICE.MODE.PASSTHROUGH.CMD_FILTER</th>
    <th>SPI_DEVICE.MODE.PASSTHROUGH.ADDRESS_MANIPULATION</th>
    <th>SPI_DEVICE.MODE.PASSTHROUGH.STATUS_MANIPULATION</th>
    <th>SPI_DEVICE.MODE.PASSTHROUGH.OUTPUT_ENABLE_CONTROL</th>
    <th>SPI_DEVICE.MODE.PASSTHROUGH.INTERCEPT_EN</th>
    <th>SPI_DEVICE.MODE.PASSTHROUGH.MAILBOX</th>
    <th>SPI_DEVICE.MODE.TPM.RETURN-BY-HW_REGS</th>
    <th>SPI_DEVICE.MODE.TPM.AUTO_WAIT</th>
    <th>SPI_DEVICE.MODE.TPM.READ_FIFO_MODE</th>
    <th>SPI_DEVICE.MODE.TPM.CAPABILITY</th>
    <th>SPI_DEVICE.JEDEC_CC</th>
    <th>SPI_DEVICE.JEDEC_ID</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#csb_read">csb_read</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#csb_read">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#mem_parity">mem_parity</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#mem_cfg">mem_cfg</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#tpm_read">tpm_read</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#tpm_read">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#tpm_read">X</a></td>
    <td><a href="02_testpoint_report.md#tpm_read">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#tpm_write">tpm_write</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#tpm_write">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#tpm_write">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#tpm_hw_reg">tpm_hw_reg</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#tpm_hw_reg">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#tpm_hw_reg">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#tpm_fully_random_case">tpm_fully_random_case</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#tpm_fully_random_case">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#tpm_fully_random_case">X</a></td>
    <td><a href="02_testpoint_report.md#tpm_fully_random_case">X</a></td>
    <td><a href="02_testpoint_report.md#tpm_fully_random_case">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#pass_cmd_filtering">pass_cmd_filtering</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#pass_cmd_filtering">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#pass_cmd_filtering">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#pass_cmd_filtering">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#pass_addr_translation">pass_addr_translation</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#pass_addr_translation">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#pass_addr_translation">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#pass_addr_translation">X</a></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#pass_payload_translation">pass_payload_translation</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#pass_payload_translation">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#pass_payload_translation">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#pass_payload_translation">X</a></td>
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
    <th><a href="02_testpoint_report.md#cmd_info_slots">cmd_info_slots</a></th>
    <td><a href="02_testpoint_report.md#cmd_info_slots">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cmd_info_slots">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#cmd_read_status">cmd_read_status</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cmd_read_status">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cmd_read_status">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#cmd_read_jedec">cmd_read_jedec</a></th>
    <td><a href="02_testpoint_report.md#cmd_read_jedec">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cmd_read_jedec">X</a></td>
    <td><a href="02_testpoint_report.md#cmd_read_jedec">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cmd_read_jedec">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cmd_read_jedec">X</a></td>
    <td><a href="02_testpoint_report.md#cmd_read_jedec">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#cmd_read_sfdp">cmd_read_sfdp</a></th>
    <td><a href="02_testpoint_report.md#cmd_read_sfdp">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cmd_read_sfdp">X</a></td>
    <td><a href="02_testpoint_report.md#cmd_read_sfdp">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cmd_read_sfdp">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#cmd_fast_read">cmd_fast_read</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cmd_fast_read">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#cmd_read_pipeline">cmd_read_pipeline</a></th>
    <td><a href="02_testpoint_report.md#cmd_read_pipeline">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cmd_read_pipeline">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cmd_read_pipeline">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#flash_cmd_upload">flash_cmd_upload</a></th>
    <td><a href="02_testpoint_report.md#flash_cmd_upload">X</a></td>
    <td><a href="02_testpoint_report.md#flash_cmd_upload">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#flash_cmd_upload">X</a></td>
    <td><a href="02_testpoint_report.md#flash_cmd_upload">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#mailbox_command">mailbox_command</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#mailbox_command">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#mailbox_command">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#mailbox_cross_outside_command">mailbox_cross_outside_command</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#mailbox_cross_outside_command">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#mailbox_cross_outside_command">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#mailbox_cross_outside_command">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#mailbox_cross_inside_command">mailbox_cross_inside_command</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#mailbox_cross_inside_command">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#mailbox_cross_inside_command">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#mailbox_cross_inside_command">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#cmd_read_buffer">cmd_read_buffer</a></th>
    <td><a href="02_testpoint_report.md#cmd_read_buffer">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cmd_read_buffer">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cmd_read_buffer">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#cmd_dummy_cycle">cmd_dummy_cycle</a></th>
    <td><a href="02_testpoint_report.md#cmd_dummy_cycle">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cmd_dummy_cycle">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#cmd_dummy_cycle">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#quad_spi">quad_spi</a></th>
    <td><a href="02_testpoint_report.md#quad_spi">X</a></td>
    <td><a href="02_testpoint_report.md#quad_spi">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#quad_spi">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#quad_spi">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#dual_spi">dual_spi</a></th>
    <td><a href="02_testpoint_report.md#dual_spi">X</a></td>
    <td><a href="02_testpoint_report.md#dual_spi">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dual_spi">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#dual_spi">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#4b_3b_feature">4b_3b_feature</a></th>
    <td><a href="02_testpoint_report.md#4b_3b_feature">X</a></td>
    <td><a href="02_testpoint_report.md#4b_3b_feature">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#4b_3b_feature">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#4b_3b_feature">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#4b_3b_feature">X</a></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#write_enable_disable">write_enable_disable</a></th>
    <td><a href="02_testpoint_report.md#write_enable_disable">X</a></td>
    <td><a href="02_testpoint_report.md#write_enable_disable">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#write_enable_disable">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#write_enable_disable">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#write_enable_disable">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#tpm_with_flash_or_passthrough_mode">TPM_with_flash_or_passthrough_mode</a></th>
    <td><a href="02_testpoint_report.md#tpm_with_flash_or_passthrough_mode">X</a></td>
    <td><a href="02_testpoint_report.md#tpm_with_flash_or_passthrough_mode">X</a></td>
    <td><a href="02_testpoint_report.md#tpm_with_flash_or_passthrough_mode">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#tpm_with_flash_or_passthrough_mode">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#tpm_and_flash_trans_with_min_inactive_time">tpm_and_flash_trans_with_min_inactive_time</a></th>
    <td><a href="02_testpoint_report.md#tpm_and_flash_trans_with_min_inactive_time">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#tpm_and_flash_trans_with_min_inactive_time">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#tpm_and_flash_trans_with_min_inactive_time">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#stress_all">stress_all</a></th>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td><a href="02_testpoint_report.md#stress_all">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_spi_device_flash_mode-dragonfly">chip_sw_spi_device_flash_mode (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_flash_mode-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_flash_mode-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_flash_mode-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_flash_mode-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_flash_mode-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through-dragonfly">chip_sw_spi_device_pass_through (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through-dragonfly">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through-dragonfly">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through_collision-dragonfly">chip_sw_spi_device_pass_through_collision (dragonfly)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through_collision-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through_collision-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through_collision-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through_collision-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through_collision-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_spi_device_tpm-dragonfly">chip_sw_spi_device_tpm (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_tpm-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_tpm-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_spi_device_output_when_disabled_or_sleeping-dragonfly">chip_sw_spi_device_output_when_disabled_or_sleeping (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_output_when_disabled_or_sleeping-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_output_when_disabled_or_sleeping-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_output_when_disabled_or_sleeping-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_output_when_disabled_or_sleeping-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_output_when_disabled_or_sleeping-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_spi_device_flash_mode-egret">chip_sw_spi_device_flash_mode (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_flash_mode-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_flash_mode-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_flash_mode-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_flash_mode-egret">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_flash_mode-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through-egret">chip_sw_spi_device_pass_through (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through-egret">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through_flash_model-egret">chip_sw_spi_device_pass_through_flash_model (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through_flash_model-egret">X</a></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through_flash_model-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through_flash_model-egret">X</a></td>
    <td></td>
    <td></td>
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
    <th><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through_collision-egret">chip_sw_spi_device_pass_through_collision (egret)</a></th>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through_collision-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through_collision-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through_collision-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through_collision-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_pass_through_collision-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_spi_device_tpm-egret">chip_sw_spi_device_tpm (egret)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_tpm-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_tpm-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_spi_device_output_when_disabled_or_sleeping-egret">chip_sw_spi_device_output_when_disabled_or_sleeping (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_output_when_disabled_or_sleeping-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_output_when_disabled_or_sleeping-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_spi_device_output_when_disabled_or_sleeping-egret">X</a></td>
  </tr>
</table>
</div>
</div>
