# Style Utility

This utility provides a `Makefile.fmt`to streamline the installation and use of [Verible](https://chipsalliance.github.io/verible/) for **SystemVerilog linting and formatting**.

## Overview

- **Verible** is an open-source suite of tools for checking and formatting SystemVerilog code.
- `Makefile.fmt` wraps Verible with simple `make` targets for installation, linting, and formatting.

## Features


- **Installation**: Download and install Verible automatically
- **Linting**: Run coding-style and best-practice checks
- **Formatting**: Reformat code to follow style guidelines
- **Safe backups**: Create backups before formatting (in certain modes)

## Usage

Make sure `make` is installed on your system. You can then invoke the following targets:

1. **Install Verible**

```plain
make -f Makefile.fmt install-verible
```

2. **Lint code**

```plain
make -f Makefile.fmt lint
```

3. **Format code**

```plain
make -f Makefile.fmt format
```

- `MODE=check`: writes results into fmt_log/ without modifying files (default)
- `MODE=inplace`: reformats files in place (backups are created)

> [!TIP]
> Create a symlink to call it as the default Makefile:


```bash
ln -sf Makefile.fmt Makefile 
```

## Customization

You can adjust linting and formatting rules using the configuration files:

- `.rules.verible_lint`
- `.rules.verible_format`

### Linting

Check a single file:

```bash
verible-verilog-lint filename.sv 
```

Use a custom rules file:

```bash
verible-verilog-lint --rules_config .rules.verible_lint filename.sv
```

See the full list of rules in the [Verible Lint Rules](https://chipsalliance.github.io/verible/verilog_lint.html#lint-rules).

### Formatting

Format a file and write to a new one:

```bash
verible-verilog-format filename.sv > filename_formated.sv
```

Format in place:

```bash
verible-verilog-format --inplace filename.sv
```

Apply custom formatting rules:

```bash
verible-verilog-format --flagfile=.rules.verible_format
```

See configuration details in the [Verible Format Rules](https://chipsalliance.github.io/verible/verilog_format.html).
