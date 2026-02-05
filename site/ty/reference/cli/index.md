# [CLI Reference](#cli-reference)

## [ty](#ty)

An extremely fast Python type checker.

### Usage

```
ty <COMMAND>

```

### Commands

[`ty check`](#ty-check) : Check a project for type errors

[`ty server`](#ty-server) : Start the language server

[`ty version`](#ty-version) : Display ty's version

[`ty help`](#ty-help) : Print this message or the help of the given subcommand(s)

## [ty check](#ty-check)

Check a project for type errors

### Usage

```
ty check [OPTIONS] [PATH]...

```

### Arguments

[`PATHS`](#ty-check--paths) : List of files or directories to check [default: the project root]

### Options

[`--add-ignore`](#ty-check--add-ignore) : Adds `ty: ignore` comments to suppress all rule diagnostics

[`--color`](#ty-check--color) *when* : Control when colored output is used

```
Possible values:

- `auto`: Display colors if the output goes to an interactive terminal
- `always`: Always display colors
- `never`: Never display colors
```

[`--config`](#ty-check--config), `-c` *config-option* : A TOML `<KEY> = <VALUE>` pair (such as you might find in a `ty.toml` configuration file) overriding a specific configuration option.

```
Overrides of individual settings using this option always take precedence
over all configuration files.
```

[`--config-file`](#ty-check--config-file) *path* : The path to a `ty.toml` file to use for configuration.

```
While ty configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `TY_CONFIG_FILE` environment variable.
```

[`--error`](#ty-check--error) *rule* : Treat the given rule as having severity 'error'. Can be specified multiple times. Use 'all' to apply to all rules.

[`--error-on-warning`](#ty-check--error-on-warning) : Use exit code 1 if there are any warning-level diagnostics

[`--exclude`](#ty-check--exclude) *exclude* : Glob patterns for files to exclude from type checking.

```
Uses gitignore-style syntax to exclude files and directories from type checking. Supports patterns like `tests/`, `*.tmp`, `**/__pycache__/**`.
```

[`--exit-zero`](#ty-check--exit-zero) : Always use exit code 0, even when there are error-level diagnostics

[`--extra-search-path`](#ty-check--extra-search-path) *path* : Additional path to use as a module-resolution source (can be passed multiple times).

```
This is an advanced option that should usually only be used for first-party or third-party modules that are not installed into your Python environment in a conventional way. Use `--python` to point ty to your Python environment if it is in an unusual location.
```

[`--force-exclude`](#ty-check--force-exclude) : Enforce exclusions, even for paths passed to ty directly on the command-line. Use `--no-force-exclude` to disable

[`--help`](#ty-check--help), `-h` : Print help (see a summary with '-h')

[`--ignore`](#ty-check--ignore) *rule* : Disables the rule. Can be specified multiple times. Use 'all' to apply to all rules.

[`--no-progress`](#ty-check--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.
```

[`--output-format`](#ty-check--output-format) *output-format* : The format to use for printing diagnostic messages

```
Possible values:

- `full`: Print diagnostics verbosely, with context and helpful hints (default)
- `concise`: Print diagnostics concisely, one per line
- `gitlab`: Print diagnostics in the JSON format expected by GitLab Code Quality reports
- `github`: Print diagnostics in the format used by GitHub Actions workflow error annotations
```

[`--project`](#ty-check--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml` files will be discovered by walking up the directory tree from the given project directory, as will the project's virtual environment (`.venv`) unless the `venv-path` option is set.

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.
```

[`--python`](#ty-check--python), `--venv` *path* : Path to your project's Python environment or interpreter.

```
ty uses your Python environment to resolve third-party imports in your code.

If you're using a project management tool such as uv or you have an activated Conda or virtual environment, you should not generally need to specify this option.

This option can be used to point to virtual or system Python environments.
```

[`--python-platform`](#ty-check--python-platform), `--platform` *platform* : Target platform to assume when resolving types.

```
This is used to specialize the type of `sys.platform` and will affect the visibility of platform-specific functions and attributes. If the value is set to `all`, no assumptions are made about the target platform. If unspecified, the current system's platform will be used.
```

[`--python-version`](#ty-check--python-version), `--target-version` *version* : Python version to assume when resolving types.

```
The Python version affects allowed syntax, type definitions of the standard library, and type definitions of first- and third-party modules that are conditional on the Python version.

If a version is not specified on the command line or in a configuration file, ty will try the following techniques in order of preference to determine a value: 1. Check for the `project.requires-python` setting in a `pyproject.toml` file and use the minimum version from the specified range 2. Check for an activated or configured Python environment and attempt to infer the Python version of that environment 3. Fall back to the latest stable Python version supported by ty (see `ty check --help` output)

Possible values:

- `3.7`
- `3.8`
- `3.9`
- `3.10`
- `3.11`
- `3.12`
- `3.13`
- `3.14`
```

[`--quiet`](#ty-check--quiet), `-q` : Use quiet output (or `-qq` for silent output)

[`--respect-ignore-files`](#ty-check--respect-ignore-files) : Respect file exclusions via `.gitignore` and other standard ignore files. Use `--no-respect-ignore-files` to disable

[`--typeshed`](#ty-check--typeshed), `--custom-typeshed-dir` *path* : Custom directory to use for stdlib typeshed stubs

[`--verbose`](#ty-check--verbose), `-v` : Use verbose output (or `-vv` and `-vvv` for more verbose output)

[`--warn`](#ty-check--warn) *rule* : Treat the given rule as having severity 'warn'. Can be specified multiple times. Use 'all' to apply to all rules.

[`--watch`](#ty-check--watch), `-W` : Watch files for changes and recheck files related to the changed files

## [ty server](#ty-server)

Start the language server

### Usage

```
ty server

```

### Options

[`--help`](#ty-server--help), `-h` : Print help

## [ty version](#ty-version)

Display ty's version

### Usage

```
ty version

```

### Options

[`--help`](#ty-version--help), `-h` : Print help

## [ty generate-shell-completion](#ty-generate-shell-completion)

Generate shell completion

### Usage

```
ty generate-shell-completion <SHELL>

```

### Arguments

[`SHELL`](#ty-generate-shell-completion--shell)

### Options

[`--help`](#ty-generate-shell-completion--help), `-h` : Print help

## [ty help](#ty-help)

Print this message or the help of the given subcommand(s)

### Usage

```
ty help [COMMAND]

```
