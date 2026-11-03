# [Environment variables](#environment-variables)

ty defines and respects the following environment variables:

### [`TY_CONFIG_FILE`](#ty_config_file)

Path to a `ty.toml` configuration file to use.

When set, ty will use this file for configuration instead of discovering configuration files automatically.

Equivalent to the `--config-file` command-line argument.

### [`TY_LOG`](#ty_log)

If set, ty will use this value as the log level for its `--verbose` output. Accepts any filter compatible with the `tracing_subscriber` crate.

For example:

- `TY_LOG=ty=debug` is the equivalent of `-vv` to the command line
- `TY_LOG=trace` will enable all trace-level logging.

See the [tracing documentation](https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#example-syntax) for more.

### [`TY_LOG_PROFILE`](#ty_log_profile)

If set to `"1"` or `"true"`, ty will enable flamegraph profiling. This creates a `tracing.folded` file that can be used to generate flame graphs for performance analysis.

### [`TY_MAX_PARALLELISM`](#ty_max_parallelism)

Specifies an upper limit for the number of tasks ty is allowed to run in parallel.

For example, how many files should be checked in parallel. This isn't the same as a thread limit. ty may spawn additional threads when necessary, e.g. to watch for file system changes or a dedicated UI thread.

### [`TY_OUTPUT_FORMAT`](#ty_output_format)

The format to use for printing diagnostic messages.

When set, ty will use this format for output instead of the default.

Accepts the same values as the `--output-format` command-line argument.

## [Externally-defined variables](#externally-defined-variables)

ty also reads the following externally defined environment variables:

### [`CLICOLOR`](#clicolor)

Enables color in `ty check` diagnostics when stdout is a terminal, even if `TERM=dumb`.

Setting this environment variable to any non-empty value (including `0`) enables this behavior. An empty value has the same effect as leaving the variable unset. All of the following have higher precedence: setting the `NO_COLOR` environment variable to any non-empty value, passing `--color=always`, or passing `--color=never`.

### [`CLICOLOR_FORCE`](#clicolor_force)

Alias for [`FORCE_COLOR`](#force_color).

### [`CONDA_DEFAULT_ENV`](#conda_default_env)

Used to determine the name of the active Conda environment.

### [`CONDA_PREFIX`](#conda_prefix)

Used to detect the path of an active Conda environment. If both `VIRTUAL_ENV` and `CONDA_PREFIX` are present, `VIRTUAL_ENV` will be preferred.

### [`FORCE_COLOR`](#force_color)

Controls color in `ty check` diagnostics, including when piped.

Setting this to any non-empty value (including `0`) forces color. An empty value has the same effect as leaving the variable unset. All of the following have higher precedence: setting the `NO_COLOR` environment variable to a non-empty value, passing `--color=always`, or passing `--color=never`.

### [`NO_COLOR`](#no_color)

Controls color in `ty check` diagnostics, including when piped.

Setting this to any non-empty value (including `0`) disables color in diagnostics. Setting it to an empty value causes ty to defer to other environment variables and heuristics such as whether stdout is a tty.

Passing `--color always` or `--color never` takes precedence over this environment variable.

### [`PYTHONPATH`](#pythonpath)

Adds additional directories to ty's search paths. The format is the same as the shell’s PATH: one or more directory pathnames separated by os appropriate pathsep (e.g. colons on Unix or semicolons on Windows).

### [`RAYON_NUM_THREADS`](#rayon_num_threads)

Specifies an upper limit for the number of threads ty uses when performing work in parallel. Equivalent to `TY_MAX_PARALLELISM`.

This is a standard Rayon environment variable.

### [`TERM`](#term)

In automatic mode, `ty check` uses color when stdout is a terminal unless `TERM` is exactly `dumb`. An empty or unset `TERM` allows color on a terminal. An explicit `--color=always` or `--color=never` takes precedence, as does a non-empty `NO_COLOR`, `FORCE_COLOR`, `CLICOLOR_FORCE`, or `CLICOLOR` environment variable.

### [`VIRTUAL_ENV`](#virtual_env)

Used to detect an activated virtual environment.

### [`XDG_CONFIG_HOME`](#xdg_config_home)

Path to user-level configuration directory on Unix systems.

### [`_CONDA_ROOT`](#_conda_root)

Used to determine the root install path of Conda.
