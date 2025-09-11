# Vivado installation

Download `FPGAs_AdaptiveSoCs_Unified_2024.2_1113_1001_Lin64.bin`

Run the following commands:

```bash
sudo apt-get install libtinfo5
sudo apt install libncurses5
chmod +x FPGAs_AdaptiveSoCs_Unified_2024.2_1113_1001_Lin64.bin
sudo ./FPGAs_AdaptiveSoCs_Unified_2024.2_1113_1001_Lin64.bin
```

Select the free version of Vivado and leave everything as default.
You can uncheck some options to save some space but for simplicity
leave as it is.

Add to your `~/.bashrc` the following:

```bash
# Vivado
source /tools/Xilinx/Vivado/2024.2/settings64.sh
```

be aware of the version you are installing.

Install the cable drivers

```bash
sudo chmod +x /tools/Xilinx/Vivado/2024.2/data/xicom/cable_drivers/lin64/install_script/install_drivers/install_drivers
sudo ./tools/Xilinx/Vivado/2024.2/data/xicom/cable_drivers/lin64/install_script/install_drivers/install_drivers
```

