# Setup Environment

## Initial setup

```bash
export GIT_ROOT=$(git rev-parse --show-toplevel)
export UVM_WORK="${GIT_ROOT}/work/uvm"
export UVM_ROOT="${GIT_ROOT}/verification/uvm"
mkdir -p "${UVM_WORK}" && cd "${UVM_WORK}"

# Style utility Makefile
ln -sf "${GIT_ROOT}/scripts/style/Makefile.fmt" 

# Filter utility Makefile
ln -sf "${GIT_ROOT}/scripts/filter/Makefile.filter" 

# Vivado setup
ln -sf ${UVM_ROOT}/scripts/makefiles/Makefile.xilinx Makefile
ln -sf ${UVM_ROOT}/scripts/setup/setup_vivado_eda.sh
```

> [!IMPORTANT]  
> You must run this commands just one time

## Commands

```bash
# Setup environment variables
source setup_vivado_eda.sh

# Basic flow
make compile elaborate sim

# Enable debug messages
make sim VERBOSITY=UVM_DEBUG

# Open GUI
make sim VERBOSITY=UVM_DEBUG GUI_MODE=true
```

> [!IMPORTANT]  
> Make sure that `settings64.sh` is in your `~/.bashrc` or source it manually

## Utility

```bash
make -f Makefile.fmt
make -f Makefile.filter
```
