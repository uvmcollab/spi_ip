## IP UVM Verification

```bash
ln -sf $GIT_ROOT/verification/uvm/scripts/makefiles/Makefile.xilinx Makefile
ln -sf $GIT_ROOT/verification/uvm/scripts/setup/setup_vivado_eda.sh
source setup_vivado_eda.tcsh
make
```
# Comandos para compilar elaborar y simular

```bash
make compile
make elaborate
make sim
# Enable Debug messages
make sim VERBOSITY=UVM_DEBUG
# With GUI
make sim VERBOSITY=UVM_DEBUG GUI_MODE=true
```
