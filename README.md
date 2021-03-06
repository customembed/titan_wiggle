# titan_wiggle

This is a simple Verilog project to validate the Titan PCI Express development card for the Lattice ECP5 FPGA

# Features
* Toggles GPIO pins on P3 and P5 expansion header (slow enough for LEDs)
* Enumerates the PCIe express interface in x1 mode
  * Device ID is beef
  * Vendor ID is dead

# Dependencies
* Lattice Diamond 3.5.1
* PCI Express x1/x2/x4 Endpoint - Optimized for ECP5UM (pci_express_endpoint_v6.1)
* DDR3 SDRAM Controller - v3.0

# Build Instructions
* Open the project (titan_wiggle.ldf)
* Open Clarity Designer by double-clicking on **claritycores.sbx** in the file list
  * Download and install the IP cores (if not installed)
    * Click on the **Catalog** tab (in the top set of tabs)
    * Click on the **Lattice IP** tab (in the bottom set of tabs)
    * Locate the **PCI Express Endpoint** core and verify that the description is **PCI Express x1/x2/x4 Endpoint - Optimized for LatticeECP3 and ECP5UM** and the version is 6.1
	   * If not installed, click on the **Lattice IP Server** tab, locate the appropriate core and version, and install
    * Locate the **DDR3 SDRAM Controller** core and verify that the version is 3.0
	   * If not installed, click on the **Lattice IP Server** tab, locate the appropriate core and version, and install
  * Click on **Builder** (in the top set of tabs)
    * Re-configure the refclk core
      * Right-click on refclk, then select **Config**
      * In the new dialog, click **Configure** and then **Close** when the process completes
    * Re-configure the pcie_x1 core
      * Right-click on pcie_x1, then select **Config**
      * In the new dialog, click **Configure** and then **Close** when the process completes
    * Re-configure the ddr3_x16 core
      * Right-click on ddr3_x16, then select **Config**
      * In the new dialog, click **Configure** and then **Close** when the process completes
  * Click on the **Generate** button at the top of the Clarity Designer window
  * Close Clarity Designer
* Build the FPGA bitstream
  * Click on the **Process** tab
  * Right-click on **Bitstream File** and select **Rerun All**

# Simulation Instructions
* After building the project in Diamond (see above), open Aldec-HDL
  * In the console, set the current directory to the root of your titan_wiggle checkout (ie. **cd c:\titan_wiggle**)
  * Run the simulation script: **do titan.do**
