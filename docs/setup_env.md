# Setup Environment 

```bash
export GIT_ROOT=$(git rev-parse --show-toplevel)
export UVM_WORK="${GIT_ROOT}/work/uvm"
mkdir -p "${UVM_WORK}" && cd "${UVM_WORK}"

# Style utility Makefile
ln -sf "${GIT_ROOT}/scripts/style/Makefile.fmt" Makefile
```
