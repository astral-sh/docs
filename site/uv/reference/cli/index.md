# [CLI Reference](#cli-reference)

## [uv](#uv)

An extremely fast Python package manager.

### Usage

```
uv [OPTIONS] <COMMAND>

```

### Commands

[`uv auth`](#uv-auth) : Manage authentication

[`uv run`](#uv-run) : Run a command or script

[`uv init`](#uv-init) : Create a new project

[`uv add`](#uv-add) : Add dependencies to the project

[`uv remove`](#uv-remove) : Remove dependencies from the project

[`uv version`](#uv-version) : Read or update the project's version

[`uv sync`](#uv-sync) : Update the project's environment

[`uv lock`](#uv-lock) : Update the project's lockfile

[`uv export`](#uv-export) : Export the project's lockfile to an alternate format

[`uv tree`](#uv-tree) : Display the project's dependency tree

[`uv format`](#uv-format) : Format Python code in the project

[`uv tool`](#uv-tool) : Run and install commands provided by Python packages

[`uv python`](#uv-python) : Manage Python versions and installations

[`uv pip`](#uv-pip) : Manage Python packages with a pip-compatible interface

[`uv venv`](#uv-venv) : Create a virtual environment

[`uv build`](#uv-build) : Build Python packages into source distributions and wheels

[`uv publish`](#uv-publish) : Upload distributions to an index

[`uv cache`](#uv-cache) : Manage uv's cache

[`uv self`](#uv-self) : Manage the uv executable

[`uv help`](#uv-help) : Display documentation for a command

## [uv auth](#uv-auth)

Manage authentication

### Usage

```
uv auth [OPTIONS] <COMMAND>

```

### Commands

[`uv auth login`](#uv-auth-login) : Login to a service

[`uv auth logout`](#uv-auth-logout) : Logout of a service

[`uv auth token`](#uv-auth-token) : Show the authentication token for a service

[`uv auth dir`](#uv-auth-dir) : Show the path to the uv credentials directory

### [uv auth login](#uv-auth-login)

Login to a service

### Usage

```
uv auth login [OPTIONS] <SERVICE>

```

### Arguments

[SERVICE](#uv-auth-login--service) : The domain or URL of the service to log into

### Options

[`--allow-insecure-host`](#uv-auth-login--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-auth-login--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-auth-login--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-auth-login--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-auth-login--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--help`](#uv-auth-login--help), `-h` : Display the concise help for this command

[`--keyring-provider`](#uv-auth-login--keyring-provider) *keyring-provider* : The keyring provider to use for storage of credentials.

```
Only `--keyring-provider native` is supported for `login`, which uses the system keyring via an integration built into uv.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--managed-python`](#uv-auth-login--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-auth-login--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-auth-login--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-auth-login--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-auth-login--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-auth-login--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-auth-login--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-auth-login--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--password`](#uv-auth-login--password) *password* : The password to use for the service.

```
Use `-` to read the password from stdin.
```

[`--project`](#uv-auth-login--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--quiet`](#uv-auth-login--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--token`](#uv-auth-login--token), `-t` *token* : The token to use for the service.

```
The username will be set to `__token__`.

Use `-` to read the token from stdin.
```

[`--username`](#uv-auth-login--username), `-u` *username* : The username to use for the service

[`--verbose`](#uv-auth-login--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv auth logout](#uv-auth-logout)

Logout of a service

### Usage

```
uv auth logout [OPTIONS] <SERVICE>

```

### Arguments

[SERVICE](#uv-auth-logout--service) : The domain or URL of the service to logout from

### Options

[`--allow-insecure-host`](#uv-auth-logout--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-auth-logout--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-auth-logout--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-auth-logout--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-auth-logout--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--help`](#uv-auth-logout--help), `-h` : Display the concise help for this command

[`--keyring-provider`](#uv-auth-logout--keyring-provider) *keyring-provider* : The keyring provider to use for storage of credentials.

```
Only `--keyring-provider native` is supported for `logout`, which uses the system keyring via an integration built into uv.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--managed-python`](#uv-auth-logout--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-auth-logout--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-auth-logout--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-auth-logout--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-auth-logout--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-auth-logout--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-auth-logout--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-auth-logout--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-auth-logout--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--quiet`](#uv-auth-logout--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--username`](#uv-auth-logout--username), `-u` *username* : The username to logout

[`--verbose`](#uv-auth-logout--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv auth token](#uv-auth-token)

Show the authentication token for a service

### Usage

```
uv auth token [OPTIONS] <SERVICE>

```

### Arguments

[SERVICE](#uv-auth-token--service) : The domain or URL of the service to lookup

### Options

[`--allow-insecure-host`](#uv-auth-token--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-auth-token--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-auth-token--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-auth-token--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-auth-token--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--help`](#uv-auth-token--help), `-h` : Display the concise help for this command

[`--keyring-provider`](#uv-auth-token--keyring-provider) *keyring-provider* : The keyring provider to use for reading credentials

```
May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--managed-python`](#uv-auth-token--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-auth-token--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-auth-token--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-auth-token--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-auth-token--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-auth-token--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-auth-token--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-auth-token--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-auth-token--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--quiet`](#uv-auth-token--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--username`](#uv-auth-token--username), `-u` *username* : The username to lookup

[`--verbose`](#uv-auth-token--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv auth dir](#uv-auth-dir)

Show the path to the uv credentials directory.

By default, credentials are stored in the uv data directory at `$XDG_DATA_HOME/uv/credentials` or `$HOME/.local/share/uv/credentials` on Unix and `%APPDATA%\uv\data\credentials` on Windows.

The credentials directory may be overridden with `$UV_CREDENTIALS_DIR`.

Credentials are only stored in this directory when the plaintext backend is used, as opposed to the native backend, which uses the system keyring.

### Usage

```
uv auth dir [OPTIONS] [SERVICE]

```

### Arguments

[SERVICE](#uv-auth-dir--service) : The domain or URL of the service to lookup

### Options

[`--allow-insecure-host`](#uv-auth-dir--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-auth-dir--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-auth-dir--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-auth-dir--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-auth-dir--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--help`](#uv-auth-dir--help), `-h` : Display the concise help for this command

[`--managed-python`](#uv-auth-dir--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-auth-dir--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-auth-dir--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-auth-dir--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-auth-dir--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-auth-dir--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-auth-dir--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-auth-dir--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-auth-dir--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--quiet`](#uv-auth-dir--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--verbose`](#uv-auth-dir--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

## [uv run](#uv-run)

Run a command or script.

Ensures that the command runs in a Python environment.

When used with a file ending in `.py` or an HTTP(S) URL, the file will be treated as a script and run with a Python interpreter, i.e., `uv run file.py` is equivalent to `uv run python file.py`. For URLs, the script is temporarily downloaded before execution. If the script contains inline dependency metadata, it will be installed into an isolated, ephemeral environment. When used with `-`, the input will be read from stdin, and treated as a Python script.

When used in a project, the project environment will be created and updated before invoking the command.

When used outside a project, if a virtual environment can be found in the current directory or a parent directory, the command will be run in that environment. Otherwise, the command will be run in the environment of the discovered interpreter.

Arguments following the command (or script) are not interpreted as arguments to uv. All options to uv must be provided before the command, e.g., `uv run --verbose foo`. A `--` can be used to separate the command from uv options for clarity, e.g., `uv run --python 3.12 -- python`.

### Usage

```
uv run [OPTIONS] [COMMAND]

```

### Options

[`--active`](#uv-run--active) : Prefer the active virtual environment over the project's virtual environment.

```
If the project virtual environment is active or no virtual environment is active, this has no effect.
```

[`--all-extras`](#uv-run--all-extras) : Include all optional dependencies.

```
Optional dependencies are defined via `project.optional-dependencies` in a `pyproject.toml`.

This option is only available when running in a project.
```

[`--all-groups`](#uv-run--all-groups) : Include dependencies from all dependency groups.

```
`--no-group` can be used to exclude specific groups.
```

[`--all-packages`](#uv-run--all-packages) : Run the command with all workspace members installed.

```
The workspace's environment (`.venv`) is updated to include all workspace members.

Any extras or groups specified via `--extra`, `--group`, or related options will be applied to all workspace members.
```

[`--allow-insecure-host`](#uv-run--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-run--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-run--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--compile-bytecode`](#uv-run--compile-bytecode), `--compile` : Compile Python files to bytecode after installation.

```
By default, uv does not compile Python (`.py`) files to bytecode (`__pycache__/*.pyc`); instead, compilation is performed lazily the first time a module is imported. For use-cases in which start time is critical, such as CLI applications and Docker containers, this option can be enabled to trade longer installation times for faster start times.

When enabled, uv will process the entire site-packages directory (including packages that are not being modified by the current operation) for consistency. Like pip, it will also ignore errors.

May also be set with the `UV_COMPILE_BYTECODE` environment variable.
```

[`--config-file`](#uv-run--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--config-setting`](#uv-run--config-setting), `--config-settings`, `-C` *config-setting* : Settings to pass to the PEP 517 build backend, specified as `KEY=VALUE` pairs

[`--config-settings-package`](#uv-run--config-settings-package), `--config-settings-package` *config-settings-package* : Settings to pass to the PEP 517 build backend for a specific package, specified as `PACKAGE:KEY=VALUE` pairs

[`--default-index`](#uv-run--default-index) *default-index* : The URL of the default package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--index` flag.

May also be set with the `UV_DEFAULT_INDEX` environment variable.
```

[`--directory`](#uv-run--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--env-file`](#uv-run--env-file) *env-file* : Load environment variables from a `.env` file.

```
Can be provided multiple times, with subsequent files overriding values defined in previous files.

May also be set with the `UV_ENV_FILE` environment variable.
```

[`--exact`](#uv-run--exact) : Perform an exact sync, removing extraneous packages.

```
When enabled, uv will remove any extraneous packages from the environment. By default, `uv run` will make the minimum necessary changes to satisfy the requirements.
```

[`--exclude-newer`](#uv-run--exclude-newer) *exclude-newer* : Limit candidate packages to those that were uploaded prior to the given date.

```
Accepts both RFC 3339 timestamps (e.g., `2006-12-02T02:07:43Z`) and local dates in the same format (e.g., `2006-12-02`) in your system's configured time zone.

May also be set with the `UV_EXCLUDE_NEWER` environment variable.
```

[`--exclude-newer-package`](#uv-run--exclude-newer-package) *exclude-newer-package* : Limit candidate packages for specific packages to those that were uploaded prior to the given date.

```
Accepts package-date pairs in the format `PACKAGE=DATE`, where `DATE` is an RFC 3339 timestamp (e.g., `2006-12-02T02:07:43Z`) or local date (e.g., `2006-12-02`) in your system's configured time zone.

Can be provided multiple times for different packages.
```

[`--extra`](#uv-run--extra) *extra* : Include optional dependencies from the specified extra name.

```
May be provided more than once.

Optional dependencies are defined via `project.optional-dependencies` in a `pyproject.toml`.

This option is only available when running in a project.
```

[`--extra-index-url`](#uv-run--extra-index-url) *extra-index-url* : (Deprecated: use `--index` instead) Extra URLs of package indexes to use, in addition to `--index-url`.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--index-url` (which defaults to PyPI). When multiple `--extra-index-url` flags are provided, earlier values take priority.

May also be set with the `UV_EXTRA_INDEX_URL` environment variable.
```

[`--find-links`](#uv-run--find-links), `-f` *find-links* : Locations to search for candidate distributions, in addition to those found in the registry indexes.

```
If a path, the target must be a directory that contains packages as wheel files (`.whl`) or source distributions (e.g., `.tar.gz` or `.zip`) at the top level.

If a URL, the page must contain a flat list of links to package files adhering to the formats described above.

May also be set with the `UV_FIND_LINKS` environment variable.
```

[`--fork-strategy`](#uv-run--fork-strategy) *fork-strategy* : The strategy to use when selecting multiple versions of a given package across Python versions and platforms.

```
By default, uv will optimize for selecting the latest version of each package for each supported Python version (`requires-python`), while minimizing the number of selected versions across platforms.

Under `fewest`, uv will minimize the number of selected versions for each package, preferring older versions that are compatible with a wider range of supported Python versions or platforms.

May also be set with the `UV_FORK_STRATEGY` environment variable.

Possible values:

- `fewest`: Optimize for selecting the fewest number of versions for each package. Older versions may be preferred if they are compatible with a wider range of supported Python versions or platforms
- `requires-python`: Optimize for selecting latest supported version of each package, for each supported Python version
```

[`--frozen`](#uv-run--frozen) : Run without updating the `uv.lock` file.

```
Instead of checking if the lockfile is up-to-date, uses the versions in the lockfile as the source of truth. If the lockfile is missing, uv will exit with an error. If the `pyproject.toml` includes changes to dependencies that have not been included in the lockfile yet, they will not be present in the environment.

May also be set with the `UV_FROZEN` environment variable.
```

[`--group`](#uv-run--group) *group* : Include dependencies from the specified dependency group.

```
May be provided multiple times.
```

[`--gui-script`](#uv-run--gui-script) : Run the given path as a Python GUI script.

```
Using `--gui-script` will attempt to parse the path as a PEP 723 script and run it with `pythonw.exe`, irrespective of its extension. Only available on Windows.
```

[`--help`](#uv-run--help), `-h` : Display the concise help for this command

[`--index`](#uv-run--index) *index* : The URLs to use when resolving dependencies, in addition to the default index.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--default-index` (which defaults to PyPI). When multiple `--index` flags are provided, earlier values take priority.

Index names are not supported as values. Relative paths must be disambiguated from index names with `./` or `../` on Unix or `.\\`, `..\\`, `./` or `../` on Windows.

May also be set with the `UV_INDEX` environment variable.
```

[`--index-strategy`](#uv-run--index-strategy) *index-strategy* : The strategy to use when resolving against multiple index URLs.

```
By default, uv will stop at the first index on which a given package is available, and limit resolutions to those present on that first index (`first-index`). This prevents "dependency confusion" attacks, whereby an attacker can upload a malicious package under the same name to an alternate index.

May also be set with the `UV_INDEX_STRATEGY` environment variable.

Possible values:

- `first-index`: Only use results from the first index that returns a match for a given package name
- `unsafe-first-match`: Search for every package name across all indexes, exhausting the versions from the first index before moving on to the next
- `unsafe-best-match`: Search for every package name across all indexes, preferring the "best" version found. If a package version is in multiple indexes, only look at the entry for the first index
```

[`--index-url`](#uv-run--index-url), `-i` *index-url* : (Deprecated: use `--default-index` instead) The URL of the Python package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--extra-index-url` flag.

May also be set with the `UV_INDEX_URL` environment variable.
```

[`--isolated`](#uv-run--isolated) : Run the command in an isolated virtual environment.

```
Usually, the project environment is reused for performance. This option forces a fresh environment to be used for the project, enforcing strict isolation between dependencies and declaration of requirements.

An editable installation is still used for the project.

When used with `--with` or `--with-requirements`, the additional dependencies will still be layered in a second environment.

May also be set with the `UV_ISOLATED` environment variable.
```

[`--keyring-provider`](#uv-run--keyring-provider) *keyring-provider* : Attempt to use `keyring` for authentication for index URLs.

```
At present, only `--keyring-provider subprocess` is supported, which configures uv to use the `keyring` CLI to handle authentication.

Defaults to `disabled`.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--link-mode`](#uv-run--link-mode) *link-mode* : The method to use when installing packages from the global cache.

```
Defaults to `clone` (also known as Copy-on-Write) on macOS, and `hardlink` on Linux and Windows.

WARNING: The use of symlink link mode is discouraged, as they create tight coupling between the cache and the target environment. For example, clearing the cache (`uv cache clean`) will break all installed packages by way of removing the underlying source files. Use symlinks with caution.

May also be set with the `UV_LINK_MODE` environment variable.

Possible values:

- `clone`: Clone (i.e., copy-on-write) packages from the wheel into the `site-packages` directory
- `copy`: Copy packages from the wheel into the `site-packages` directory
- `hardlink`: Hard link packages from the wheel into the `site-packages` directory
- `symlink`: Symbolically link packages from the wheel into the `site-packages` directory
```

[`--locked`](#uv-run--locked) : Assert that the `uv.lock` will remain unchanged.

```
Requires that the lockfile is up-to-date. If the lockfile is missing or needs to be updated, uv will exit with an error.

May also be set with the `UV_LOCKED` environment variable.
```

[`--managed-python`](#uv-run--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--module`](#uv-run--module), `-m` : Run a Python module.

```
Equivalent to `python -m <module>`.
```

[`--native-tls`](#uv-run--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-binary`](#uv-run--no-binary) : Don't install pre-built wheels.

```
The given packages will be built and installed from source. The resolver will still use pre-built wheels to extract package metadata, if available.

May also be set with the `UV_NO_BINARY` environment variable.
```

[`--no-binary-package`](#uv-run--no-binary-package) *no-binary-package* : Don't install pre-built wheels for a specific package

```
May also be set with the `UV_NO_BINARY_PACKAGE` environment variable.
```

[`--no-build`](#uv-run--no-build) : Don't build source distributions.

```
When enabled, resolving will not run arbitrary Python code. The cached wheels of already-built source distributions will be reused, but operations that require building distributions will exit with an error.

May also be set with the `UV_NO_BUILD` environment variable.
```

[`--no-build-isolation`](#uv-run--no-build-isolation) : Disable isolation when building source distributions.

```
Assumes that build dependencies specified by PEP 518 are already installed.

May also be set with the `UV_NO_BUILD_ISOLATION` environment variable.
```

[`--no-build-isolation-package`](#uv-run--no-build-isolation-package) *no-build-isolation-package* : Disable isolation when building source distributions for a specific package.

```
Assumes that the packages' build dependencies specified by PEP 518 are already installed.
```

[`--no-build-package`](#uv-run--no-build-package) *no-build-package* : Don't build source distributions for a specific package

```
May also be set with the `UV_NO_BUILD_PACKAGE` environment variable.
```

[`--no-cache`](#uv-run--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-run--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-default-groups`](#uv-run--no-default-groups) : Ignore the default dependency groups.

```
uv includes the groups defined in `tool.uv.default-groups` by default. This disables that option, however, specific groups can still be included with `--group`.
```

[`--no-dev`](#uv-run--no-dev) : Disable the development dependency group.

```
This option is an alias of `--no-group dev`. See `--no-default-groups` to disable all default groups instead.

This option is only available when running in a project.

May also be set with the `UV_NO_DEV` environment variable.
```

[`--no-editable`](#uv-run--no-editable) : Install any editable dependencies, including the project and any workspace members, as non-editable

```
May also be set with the `UV_NO_EDITABLE` environment variable.
```

[`--no-env-file`](#uv-run--no-env-file) : Avoid reading environment variables from a `.env` file

```
May also be set with the `UV_NO_ENV_FILE` environment variable.
```

[`--no-extra`](#uv-run--no-extra) *no-extra* : Exclude the specified optional dependencies, if `--all-extras` is supplied.

```
May be provided multiple times.
```

[`--no-group`](#uv-run--no-group) *no-group* : Disable the specified dependency group.

```
This option always takes precedence over default groups, `--all-groups`, and `--group`.

May be provided multiple times.
```

[`--no-index`](#uv-run--no-index) : Ignore the registry index (e.g., PyPI), instead relying on direct URL dependencies and those provided via `--find-links`

[`--no-managed-python`](#uv-run--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-run--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-project`](#uv-run--no-project), `--no_workspace` : Avoid discovering the project or workspace.

```
Instead of searching for projects in the current directory and parent directories, run in an isolated, ephemeral environment populated by the `--with` requirements.

If a virtual environment is active or found in a current or parent directory, it will be used as if there was no project or workspace.
```

[`--no-python-downloads`](#uv-run--no-python-downloads) : Disable automatic downloads of Python.

[`--no-sources`](#uv-run--no-sources) : Ignore the `tool.uv.sources` table when resolving dependencies. Used to lock against the standards-compliant, publishable package metadata, as opposed to using any workspace, Git, URL, or local path sources

[`--no-sync`](#uv-run--no-sync) : Avoid syncing the virtual environment.

```
Implies `--frozen`, as the project dependencies will be ignored (i.e., the lockfile will not be updated, since the environment will not be synced regardless).

May also be set with the `UV_NO_SYNC` environment variable.
```

[`--offline`](#uv-run--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--only-dev`](#uv-run--only-dev) : Only include the development dependency group.

```
The project and its dependencies will be omitted.

This option is an alias for `--only-group dev`. Implies `--no-default-groups`.
```

[`--only-group`](#uv-run--only-group) *only-group* : Only include dependencies from the specified dependency group.

```
The project and its dependencies will be omitted.

May be provided multiple times. Implies `--no-default-groups`.
```

[`--package`](#uv-run--package) *package* : Run the command in a specific package in the workspace.

```
If the workspace member does not exist, uv will exit with an error.
```

[`--prerelease`](#uv-run--prerelease) *prerelease* : The strategy to use when considering pre-release versions.

```
By default, uv will accept pre-releases for packages that *only* publish pre-releases, along with first-party requirements that contain an explicit pre-release marker in the declared specifiers (`if-necessary-or-explicit`).

May also be set with the `UV_PRERELEASE` environment variable.

Possible values:

- `disallow`: Disallow all pre-release versions
- `allow`: Allow all pre-release versions
- `if-necessary`: Allow pre-release versions if all versions of a package are pre-release
- `explicit`: Allow pre-release versions for first-party packages with explicit pre-release markers in their version requirements
- `if-necessary-or-explicit`: Allow pre-release versions if all versions of a package are pre-release, or if the package has an explicit pre-release marker in its version requirements
```

[`--project`](#uv-run--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--python`](#uv-run--python), `-p` *python* : The Python interpreter to use for the run environment.

```
If the interpreter request is satisfied by a discovered environment, the environment will be
used.

See [uv python](#uv-python) to view supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--python-platform`](#uv-run--python-platform) *python-platform* : The platform for which requirements should be installed.

```
Represented as a "target triple", a string that describes the target platform in terms of its CPU, vendor, and operating system name, like `x86_64-unknown-linux-gnu` or `aarch64-apple-darwin`.

When targeting macOS (Darwin), the default minimum version is `13.0`. Use `MACOSX_DEPLOYMENT_TARGET` to specify a different minimum version, e.g., `14.0`.

When targeting iOS, the default minimum version is `13.0`. Use `IPHONEOS_DEPLOYMENT_TARGET` to specify a different minimum version, e.g., `14.0`.

When targeting Android, the default minimum Android API level is `24`. Use `ANDROID_API_LEVEL` to specify a different minimum version, e.g., `26`.

WARNING: When specified, uv will select wheels that are compatible with the *target* platform; as a result, the installed distributions may not be compatible with the *current* platform. Conversely, any distributions that are built from source may be incompatible with the *target* platform, as they will be built for the *current* platform. The `--python-platform` option is intended for advanced use cases.

Possible values:

- `windows`: An alias for `x86_64-pc-windows-msvc`, the default target for Windows
- `linux`: An alias for `x86_64-unknown-linux-gnu`, the default target for Linux
- `macos`: An alias for `aarch64-apple-darwin`, the default target for macOS
- `x86_64-pc-windows-msvc`: A 64-bit x86 Windows target
- `aarch64-pc-windows-msvc`: An ARM64 Windows target
- `i686-pc-windows-msvc`: A 32-bit x86 Windows target
- `x86_64-unknown-linux-gnu`: An x86 Linux target. Equivalent to `x86_64-manylinux_2_28`
- `aarch64-apple-darwin`: An ARM-based macOS target, as seen on Apple Silicon devices
- `x86_64-apple-darwin`: An x86 macOS target
- `aarch64-unknown-linux-gnu`: An ARM64 Linux target. Equivalent to `aarch64-manylinux_2_28`
- `aarch64-unknown-linux-musl`: An ARM64 Linux target
- `x86_64-unknown-linux-musl`: An `x86_64` Linux target
- `riscv64-unknown-linux`: A RISCV64 Linux target
- `x86_64-manylinux2014`: An `x86_64` target for the `manylinux2014` platform. Equivalent to `x86_64-manylinux_2_17`
- `x86_64-manylinux_2_17`: An `x86_64` target for the `manylinux_2_17` platform
- `x86_64-manylinux_2_28`: An `x86_64` target for the `manylinux_2_28` platform
- `x86_64-manylinux_2_31`: An `x86_64` target for the `manylinux_2_31` platform
- `x86_64-manylinux_2_32`: An `x86_64` target for the `manylinux_2_32` platform
- `x86_64-manylinux_2_33`: An `x86_64` target for the `manylinux_2_33` platform
- `x86_64-manylinux_2_34`: An `x86_64` target for the `manylinux_2_34` platform
- `x86_64-manylinux_2_35`: An `x86_64` target for the `manylinux_2_35` platform
- `x86_64-manylinux_2_36`: An `x86_64` target for the `manylinux_2_36` platform
- `x86_64-manylinux_2_37`: An `x86_64` target for the `manylinux_2_37` platform
- `x86_64-manylinux_2_38`: An `x86_64` target for the `manylinux_2_38` platform
- `x86_64-manylinux_2_39`: An `x86_64` target for the `manylinux_2_39` platform
- `x86_64-manylinux_2_40`: An `x86_64` target for the `manylinux_2_40` platform
- `aarch64-manylinux2014`: An ARM64 target for the `manylinux2014` platform. Equivalent to `aarch64-manylinux_2_17`
- `aarch64-manylinux_2_17`: An ARM64 target for the `manylinux_2_17` platform
- `aarch64-manylinux_2_28`: An ARM64 target for the `manylinux_2_28` platform
- `aarch64-manylinux_2_31`: An ARM64 target for the `manylinux_2_31` platform
- `aarch64-manylinux_2_32`: An ARM64 target for the `manylinux_2_32` platform
- `aarch64-manylinux_2_33`: An ARM64 target for the `manylinux_2_33` platform
- `aarch64-manylinux_2_34`: An ARM64 target for the `manylinux_2_34` platform
- `aarch64-manylinux_2_35`: An ARM64 target for the `manylinux_2_35` platform
- `aarch64-manylinux_2_36`: An ARM64 target for the `manylinux_2_36` platform
- `aarch64-manylinux_2_37`: An ARM64 target for the `manylinux_2_37` platform
- `aarch64-manylinux_2_38`: An ARM64 target for the `manylinux_2_38` platform
- `aarch64-manylinux_2_39`: An ARM64 target for the `manylinux_2_39` platform
- `aarch64-manylinux_2_40`: An ARM64 target for the `manylinux_2_40` platform
- `aarch64-linux-android`: An ARM64 Android target
- `x86_64-linux-android`: An `x86_64` Android target
- `wasm32-pyodide2024`: A wasm32 target using the Pyodide 2024 platform. Meant for use with Python 3.12
- `arm64-apple-ios`: An ARM64 target for iOS device
- `arm64-apple-ios-simulator`: An ARM64 target for iOS simulator
- `x86_64-apple-ios-simulator`: An `x86_64` target for iOS simulator
```

[`--quiet`](#uv-run--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--refresh`](#uv-run--refresh) : Refresh all cached data

[`--refresh-package`](#uv-run--refresh-package) *refresh-package* : Refresh cached data for a specific package

[`--reinstall`](#uv-run--reinstall), `--force-reinstall` : Reinstall all packages, regardless of whether they're already installed. Implies `--refresh`

[`--reinstall-package`](#uv-run--reinstall-package) *reinstall-package* : Reinstall a specific package, regardless of whether it's already installed. Implies `--refresh-package`

[`--resolution`](#uv-run--resolution) *resolution* : The strategy to use when selecting between the different compatible versions for a given package requirement.

```
By default, uv will use the latest compatible version of each package (`highest`).

May also be set with the `UV_RESOLUTION` environment variable.

Possible values:

- `highest`: Resolve the highest compatible version of each package
- `lowest`: Resolve the lowest compatible version of each package
- `lowest-direct`: Resolve the lowest compatible version of any direct dependencies, and the highest compatible version of any transitive dependencies
```

[`--script`](#uv-run--script), `-s` : Run the given path as a Python script.

```
Using `--script` will attempt to parse the path as a PEP 723 script, irrespective of its extension.
```

[`--upgrade`](#uv-run--upgrade), `-U` : Allow package upgrades, ignoring pinned versions in any existing output file. Implies `--refresh`

[`--upgrade-package`](#uv-run--upgrade-package), `-P` *upgrade-package* : Allow upgrades for a specific package, ignoring pinned versions in any existing output file. Implies `--refresh-package`

[`--verbose`](#uv-run--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

[`--with`](#uv-run--with), `-w` *with* : Run with the given packages installed.

```
When used in a project, these dependencies will be layered on top of the project environment in a separate, ephemeral environment. These dependencies are allowed to conflict with those specified by the project.
```

[`--with-editable`](#uv-run--with-editable) *with-editable* : Run with the given packages installed in editable mode.

```
When used in a project, these dependencies will be layered on top of the project environment in a separate, ephemeral environment. These dependencies are allowed to conflict with those specified by the project.
```

[`--with-requirements`](#uv-run--with-requirements) *with-requirements* : Run with the packages listed in the given files.

```
The following formats are supported: `requirements.txt`, `.py` files with inline metadata, and `pylock.toml`.

The same environment semantics as `--with` apply.

Using `pyproject.toml`, `setup.py`, or `setup.cfg` files is not allowed.
```

## [uv init](#uv-init)

Create a new project.

Follows the `pyproject.toml` specification.

If a `pyproject.toml` already exists at the target, uv will exit with an error.

If a `pyproject.toml` is found in any of the parent directories of the target path, the project will be added as a workspace member of the parent.

Some project state is not created until needed, e.g., the project virtual environment (`.venv`) and lockfile (`uv.lock`) are lazily created during the first sync.

### Usage

```
uv init [OPTIONS] [PATH]

```

### Arguments

[PATH](#uv-init--path) : The path to use for the project/script.

```
Defaults to the current working directory when initializing an app or library; required when initializing a script. Accepts relative and absolute paths.

If a `pyproject.toml` is found in any of the parent directories of the target path, the project will be added as a workspace member of the parent, unless `--no-workspace` is provided.
```

### Options

[`--allow-insecure-host`](#uv-init--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--app`](#uv-init--app), `--application` : Create a project for an application.

```
This is the default behavior if `--lib` is not requested.

This project kind is for web servers, scripts, and command-line interfaces.

By default, an application is not intended to be built and distributed as a Python package. The `--package` option can be used to create an application that is distributable, e.g., if you want to distribute a command-line interface via PyPI.
```

[`--author-from`](#uv-init--author-from) *author-from* : Fill in the `authors` field in the `pyproject.toml`.

```
By default, uv will attempt to infer the author information from some sources (e.g., Git) (`auto`). Use `--author-from git` to only infer from Git configuration. Use `--author-from none` to avoid inferring the author information.

Possible values:

- `auto`: Fetch the author information from some sources (e.g., Git) automatically
- `git`: Fetch the author information from Git configuration only
- `none`: Do not infer the author information
```

[`--bare`](#uv-init--bare) : Only create a `pyproject.toml`.

```
Disables creating extra files like `README.md`, the `src/` tree, `.python-version` files, etc.
```

[`--build-backend`](#uv-init--build-backend) *build-backend* : Initialize a build-backend of choice for the project.

```
Implicitly sets `--package`.

May also be set with the `UV_INIT_BUILD_BACKEND` environment variable.

Possible values:

- `uv`: Use uv as the project build backend
- `hatch`: Use [hatchling](https://pypi.org/project/hatchling) as the project build backend
- `flit`: Use [flit-core](https://pypi.org/project/flit-core) as the project build backend
- `pdm`: Use [pdm-backend](https://pypi.org/project/pdm-backend) as the project build backend
- `poetry`: Use [poetry-core](https://pypi.org/project/poetry-core) as the project build backend
- `setuptools`: Use [setuptools](https://pypi.org/project/setuptools) as the project build backend
- `maturin`: Use [maturin](https://pypi.org/project/maturin) as the project build backend
- `scikit`: Use [scikit-build-core](https://pypi.org/project/scikit-build-core) as the project build backend
```

[`--cache-dir`](#uv-init--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-init--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-init--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--description`](#uv-init--description) *description* : Set the project description

[`--directory`](#uv-init--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--help`](#uv-init--help), `-h` : Display the concise help for this command

[`--lib`](#uv-init--lib), `--library` : Create a project for a library.

```
A library is a project that is intended to be built and distributed as a Python package.
```

[`--managed-python`](#uv-init--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--name`](#uv-init--name) *name* : The name of the project.

```
Defaults to the name of the directory.
```

[`--native-tls`](#uv-init--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-init--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-init--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-description`](#uv-init--no-description) : Disable the description for the project

[`--no-managed-python`](#uv-init--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-package`](#uv-init--no-package) : Do not set up the project to be built as a Python package.

```
Does not include a `[build-system]` for the project.

This is the default behavior when using `--app`.
```

[`--no-pin-python`](#uv-init--no-pin-python) : Do not create a `.python-version` file for the project.

```
By default, uv will create a `.python-version` file containing the minor version of the discovered Python interpreter, which will cause subsequent uv commands to use that version.
```

[`--no-progress`](#uv-init--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-init--no-python-downloads) : Disable automatic downloads of Python.

[`--no-readme`](#uv-init--no-readme) : Do not create a `README.md` file

[`--no-workspace`](#uv-init--no-workspace), `--no-project` : Avoid discovering a workspace and create a standalone project.

```
By default, uv searches for workspaces in the current directory or any parent directory.
```

[`--offline`](#uv-init--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--package`](#uv-init--package) : Set up the project to be built as a Python package.

```
Defines a `[build-system]` for the project.

This is the default behavior when using `--lib` or `--build-backend`.

When using `--app`, this will include a `[project.scripts]` entrypoint and use a `src/` project structure.
```

[`--project`](#uv-init--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--python`](#uv-init--python), `-p` *python* : The Python interpreter to use to determine the minimum supported Python version.

```
See [uv python](#uv-python) to view supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--quiet`](#uv-init--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--script`](#uv-init--script) : Create a script.

```
A script is a standalone file with embedded metadata enumerating its dependencies, along with any Python version requirements, as defined in the PEP 723 specification.

PEP 723 scripts can be executed directly with `uv run`.

By default, adds a requirement on the system Python version; use `--python` to specify an alternative Python version requirement.
```

[`--vcs`](#uv-init--vcs) *vcs* : Initialize a version control system for the project.

```
By default, uv will initialize a Git repository (`git`). Use `--vcs none` to explicitly avoid initializing a version control system.

Possible values:

- `git`: Use Git for version control
- `none`: Do not use any version control system
```

[`--verbose`](#uv-init--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

## [uv add](#uv-add)

Add dependencies to the project.

Dependencies are added to the project's `pyproject.toml` file.

If a given dependency exists already, it will be updated to the new version specifier unless it includes markers that differ from the existing specifier in which case another entry for the dependency will be added.

The lockfile and project environment will be updated to reflect the added dependencies. To skip updating the lockfile, use `--frozen`. To skip updating the environment, use `--no-sync`.

If any of the requested dependencies cannot be found, uv will exit with an error, unless the `--frozen` flag is provided, in which case uv will add the dependencies verbatim without checking that they exist or are compatible with the project.

uv will search for a project in the current directory or any parent directory. If a project cannot be found, uv will exit with an error.

### Usage

```
uv add [OPTIONS] <PACKAGES|--requirements <REQUIREMENTS>>

```

### Arguments

[PACKAGES](#uv-add--packages) : The packages to add, as PEP 508 requirements (e.g., `ruff==0.5.0`)

### Options

[`--active`](#uv-add--active) : Prefer the active virtual environment over the project's virtual environment.

```
If the project virtual environment is active or no virtual environment is active, this has no effect.
```

[`--allow-insecure-host`](#uv-add--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--bounds`](#uv-add--bounds) *bounds* : The kind of version specifier to use when adding dependencies.

```
When adding a dependency to the project, if no constraint or URL is provided, a constraint is added based on the latest compatible version of the package. By default, a lower bound constraint is used, e.g., `>=1.2.3`.

When `--frozen` is provided, no resolution is performed, and dependencies are always added without constraints.

This option is in preview and may change in any future release.

Possible values:

- `lower`: Only a lower bound, e.g., `>=1.2.3`
- `major`: Allow the same major version, similar to the semver caret, e.g., `>=1.2.3, <2.0.0`
- `minor`: Allow the same minor version, similar to the semver tilde, e.g., `>=1.2.3, <1.3.0`
- `exact`: Pin the exact version, e.g., `==1.2.3`
```

[`--branch`](#uv-add--branch) *branch* : Branch to use when adding a dependency from Git

[`--cache-dir`](#uv-add--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-add--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--compile-bytecode`](#uv-add--compile-bytecode), `--compile` : Compile Python files to bytecode after installation.

```
By default, uv does not compile Python (`.py`) files to bytecode (`__pycache__/*.pyc`); instead, compilation is performed lazily the first time a module is imported. For use-cases in which start time is critical, such as CLI applications and Docker containers, this option can be enabled to trade longer installation times for faster start times.

When enabled, uv will process the entire site-packages directory (including packages that are not being modified by the current operation) for consistency. Like pip, it will also ignore errors.

May also be set with the `UV_COMPILE_BYTECODE` environment variable.
```

[`--config-file`](#uv-add--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--config-setting`](#uv-add--config-setting), `--config-settings`, `-C` *config-setting* : Settings to pass to the PEP 517 build backend, specified as `KEY=VALUE` pairs

[`--config-settings-package`](#uv-add--config-settings-package), `--config-settings-package` *config-settings-package* : Settings to pass to the PEP 517 build backend for a specific package, specified as `PACKAGE:KEY=VALUE` pairs

[`--constraints`](#uv-add--constraints), `--constraint`, `-c` *constraints* : Constrain versions using the given requirements files.

```
Constraints files are `requirements.txt`-like files that only control the *version* of a requirement that's installed. The constraints will *not* be added to the project's `pyproject.toml` file, but *will* be respected during dependency resolution.

This is equivalent to pip's `--constraint` option.

May also be set with the `UV_CONSTRAINT` environment variable.
```

[`--default-index`](#uv-add--default-index) *default-index* : The URL of the default package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--index` flag.

May also be set with the `UV_DEFAULT_INDEX` environment variable.
```

[`--dev`](#uv-add--dev) : Add the requirements to the development dependency group.

```
This option is an alias for `--group dev`.

May also be set with the `UV_DEV` environment variable.
```

[`--directory`](#uv-add--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--editable`](#uv-add--editable) : Add the requirements as editable

[`--exclude-newer`](#uv-add--exclude-newer) *exclude-newer* : Limit candidate packages to those that were uploaded prior to the given date.

```
Accepts both RFC 3339 timestamps (e.g., `2006-12-02T02:07:43Z`) and local dates in the same format (e.g., `2006-12-02`) in your system's configured time zone.

May also be set with the `UV_EXCLUDE_NEWER` environment variable.
```

[`--exclude-newer-package`](#uv-add--exclude-newer-package) *exclude-newer-package* : Limit candidate packages for specific packages to those that were uploaded prior to the given date.

```
Accepts package-date pairs in the format `PACKAGE=DATE`, where `DATE` is an RFC 3339 timestamp (e.g., `2006-12-02T02:07:43Z`) or local date (e.g., `2006-12-02`) in your system's configured time zone.

Can be provided multiple times for different packages.
```

[`--extra`](#uv-add--extra) *extra* : Extras to enable for the dependency.

```
May be provided more than once.

To add this dependency to an optional extra instead, see `--optional`.
```

[`--extra-index-url`](#uv-add--extra-index-url) *extra-index-url* : (Deprecated: use `--index` instead) Extra URLs of package indexes to use, in addition to `--index-url`.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--index-url` (which defaults to PyPI). When multiple `--extra-index-url` flags are provided, earlier values take priority.

May also be set with the `UV_EXTRA_INDEX_URL` environment variable.
```

[`--find-links`](#uv-add--find-links), `-f` *find-links* : Locations to search for candidate distributions, in addition to those found in the registry indexes.

```
If a path, the target must be a directory that contains packages as wheel files (`.whl`) or source distributions (e.g., `.tar.gz` or `.zip`) at the top level.

If a URL, the page must contain a flat list of links to package files adhering to the formats described above.

May also be set with the `UV_FIND_LINKS` environment variable.
```

[`--fork-strategy`](#uv-add--fork-strategy) *fork-strategy* : The strategy to use when selecting multiple versions of a given package across Python versions and platforms.

```
By default, uv will optimize for selecting the latest version of each package for each supported Python version (`requires-python`), while minimizing the number of selected versions across platforms.

Under `fewest`, uv will minimize the number of selected versions for each package, preferring older versions that are compatible with a wider range of supported Python versions or platforms.

May also be set with the `UV_FORK_STRATEGY` environment variable.

Possible values:

- `fewest`: Optimize for selecting the fewest number of versions for each package. Older versions may be preferred if they are compatible with a wider range of supported Python versions or platforms
- `requires-python`: Optimize for selecting latest supported version of each package, for each supported Python version
```

[`--frozen`](#uv-add--frozen) : Add dependencies without re-locking the project.

```
The project environment will not be synced.

May also be set with the `UV_FROZEN` environment variable.
```

[`--group`](#uv-add--group) *group* : Add the requirements to the specified dependency group.

```
These requirements will not be included in the published metadata for the project.
```

[`--help`](#uv-add--help), `-h` : Display the concise help for this command

[`--index`](#uv-add--index) *index* : The URLs to use when resolving dependencies, in addition to the default index.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--default-index` (which defaults to PyPI). When multiple `--index` flags are provided, earlier values take priority.

Index names are not supported as values. Relative paths must be disambiguated from index names with `./` or `../` on Unix or `.\\`, `..\\`, `./` or `../` on Windows.

May also be set with the `UV_INDEX` environment variable.
```

[`--index-strategy`](#uv-add--index-strategy) *index-strategy* : The strategy to use when resolving against multiple index URLs.

```
By default, uv will stop at the first index on which a given package is available, and limit resolutions to those present on that first index (`first-index`). This prevents "dependency confusion" attacks, whereby an attacker can upload a malicious package under the same name to an alternate index.

May also be set with the `UV_INDEX_STRATEGY` environment variable.

Possible values:

- `first-index`: Only use results from the first index that returns a match for a given package name
- `unsafe-first-match`: Search for every package name across all indexes, exhausting the versions from the first index before moving on to the next
- `unsafe-best-match`: Search for every package name across all indexes, preferring the "best" version found. If a package version is in multiple indexes, only look at the entry for the first index
```

[`--index-url`](#uv-add--index-url), `-i` *index-url* : (Deprecated: use `--default-index` instead) The URL of the Python package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--extra-index-url` flag.

May also be set with the `UV_INDEX_URL` environment variable.
```

[`--keyring-provider`](#uv-add--keyring-provider) *keyring-provider* : Attempt to use `keyring` for authentication for index URLs.

```
At present, only `--keyring-provider subprocess` is supported, which configures uv to use the `keyring` CLI to handle authentication.

Defaults to `disabled`.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--link-mode`](#uv-add--link-mode) *link-mode* : The method to use when installing packages from the global cache.

```
Defaults to `clone` (also known as Copy-on-Write) on macOS, and `hardlink` on Linux and Windows.

WARNING: The use of symlink link mode is discouraged, as they create tight coupling between the cache and the target environment. For example, clearing the cache (`uv cache clean`) will break all installed packages by way of removing the underlying source files. Use symlinks with caution.

May also be set with the `UV_LINK_MODE` environment variable.

Possible values:

- `clone`: Clone (i.e., copy-on-write) packages from the wheel into the `site-packages` directory
- `copy`: Copy packages from the wheel into the `site-packages` directory
- `hardlink`: Hard link packages from the wheel into the `site-packages` directory
- `symlink`: Symbolically link packages from the wheel into the `site-packages` directory
```

[`--locked`](#uv-add--locked) : Assert that the `uv.lock` will remain unchanged.

```
Requires that the lockfile is up-to-date. If the lockfile is missing or needs to be updated, uv will exit with an error.

May also be set with the `UV_LOCKED` environment variable.
```

[`--managed-python`](#uv-add--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--marker`](#uv-add--marker), `-m` *marker* : Apply this marker to all added packages

[`--native-tls`](#uv-add--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-binary`](#uv-add--no-binary) : Don't install pre-built wheels.

```
The given packages will be built and installed from source. The resolver will still use pre-built wheels to extract package metadata, if available.

May also be set with the `UV_NO_BINARY` environment variable.
```

[`--no-binary-package`](#uv-add--no-binary-package) *no-binary-package* : Don't install pre-built wheels for a specific package

```
May also be set with the `UV_NO_BINARY_PACKAGE` environment variable.
```

[`--no-build`](#uv-add--no-build) : Don't build source distributions.

```
When enabled, resolving will not run arbitrary Python code. The cached wheels of already-built source distributions will be reused, but operations that require building distributions will exit with an error.

May also be set with the `UV_NO_BUILD` environment variable.
```

[`--no-build-isolation`](#uv-add--no-build-isolation) : Disable isolation when building source distributions.

```
Assumes that build dependencies specified by PEP 518 are already installed.

May also be set with the `UV_NO_BUILD_ISOLATION` environment variable.
```

[`--no-build-isolation-package`](#uv-add--no-build-isolation-package) *no-build-isolation-package* : Disable isolation when building source distributions for a specific package.

```
Assumes that the packages' build dependencies specified by PEP 518 are already installed.
```

[`--no-build-package`](#uv-add--no-build-package) *no-build-package* : Don't build source distributions for a specific package

```
May also be set with the `UV_NO_BUILD_PACKAGE` environment variable.
```

[`--no-cache`](#uv-add--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-add--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-index`](#uv-add--no-index) : Ignore the registry index (e.g., PyPI), instead relying on direct URL dependencies and those provided via `--find-links`

[`--no-install-local`](#uv-add--no-install-local) : Do not install local path dependencies

```
Skips the current project, workspace members, and any other local (path or editable) packages. Only remote/indexed dependencies are installed. Useful in Docker builds to cache heavy third-party dependencies first and layer local packages separately.
```

[`--no-install-project`](#uv-add--no-install-project) : Do not install the current project.

```
By default, the current project is installed into the environment with all of its dependencies. The `--no-install-project` option allows the project to be excluded, but all of its dependencies are still installed. This is particularly useful in situations like building Docker images where installing the project separately from its dependencies allows optimal layer caching.
```

[`--no-install-workspace`](#uv-add--no-install-workspace) : Do not install any workspace members, including the current project.

```
By default, all of the workspace members and their dependencies are installed into the environment. The `--no-install-workspace` option allows exclusion of all the workspace members while retaining their dependencies. This is particularly useful in situations like building Docker images where installing the workspace separately from its dependencies allows optimal layer caching.
```

[`--no-managed-python`](#uv-add--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-add--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-add--no-python-downloads) : Disable automatic downloads of Python.

[`--no-sources`](#uv-add--no-sources) : Ignore the `tool.uv.sources` table when resolving dependencies. Used to lock against the standards-compliant, publishable package metadata, as opposed to using any workspace, Git, URL, or local path sources

[`--no-sync`](#uv-add--no-sync) : Avoid syncing the virtual environment

```
May also be set with the `UV_NO_SYNC` environment variable.
```

[`--no-workspace`](#uv-add--no-workspace) : Don't add the dependency as a workspace member.

```
By default, when adding a dependency that's a local path and is within the workspace directory, uv will add it as a workspace member; pass `--no-workspace` to add the package as direct path dependency instead.
```

[`--offline`](#uv-add--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--optional`](#uv-add--optional) *optional* : Add the requirements to the package's optional dependencies for the specified extra.

```
The group may then be activated when installing the project with the `--extra` flag.

To enable an optional extra for this requirement instead, see `--extra`.
```

[`--package`](#uv-add--package) *package* : Add the dependency to a specific package in the workspace

[`--prerelease`](#uv-add--prerelease) *prerelease* : The strategy to use when considering pre-release versions.

```
By default, uv will accept pre-releases for packages that *only* publish pre-releases, along with first-party requirements that contain an explicit pre-release marker in the declared specifiers (`if-necessary-or-explicit`).

May also be set with the `UV_PRERELEASE` environment variable.

Possible values:

- `disallow`: Disallow all pre-release versions
- `allow`: Allow all pre-release versions
- `if-necessary`: Allow pre-release versions if all versions of a package are pre-release
- `explicit`: Allow pre-release versions for first-party packages with explicit pre-release markers in their version requirements
- `if-necessary-or-explicit`: Allow pre-release versions if all versions of a package are pre-release, or if the package has an explicit pre-release marker in its version requirements
```

[`--project`](#uv-add--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--python`](#uv-add--python), `-p` *python* : The Python interpreter to use for resolving and syncing.

```
See [uv python](#uv-python) for details on Python discovery and supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--quiet`](#uv-add--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--raw`](#uv-add--raw), `--raw-sources` : Add a dependency as provided.

```
By default, uv will use the `tool.uv.sources` section to record source information for Git, local, editable, and direct URL requirements. When `--raw` is provided, uv will add source requirements to `project.dependencies`, rather than `tool.uv.sources`.

Additionally, by default, uv will add bounds to your dependency, e.g., `foo>=1.0.0`. When `--raw` is provided, uv will add the dependency without bounds.
```

[`--refresh`](#uv-add--refresh) : Refresh all cached data

[`--refresh-package`](#uv-add--refresh-package) *refresh-package* : Refresh cached data for a specific package

[`--reinstall`](#uv-add--reinstall), `--force-reinstall` : Reinstall all packages, regardless of whether they're already installed. Implies `--refresh`

[`--reinstall-package`](#uv-add--reinstall-package) *reinstall-package* : Reinstall a specific package, regardless of whether it's already installed. Implies `--refresh-package`

[`--requirements`](#uv-add--requirements), `--requirement`, `-r` *requirements* : Add the packages listed in the given files.

```
The following formats are supported: `requirements.txt`, `.py` files with inline metadata, `pylock.toml`, `pyproject.toml`, `setup.py`, and `setup.cfg`.
```

[`--resolution`](#uv-add--resolution) *resolution* : The strategy to use when selecting between the different compatible versions for a given package requirement.

```
By default, uv will use the latest compatible version of each package (`highest`).

May also be set with the `UV_RESOLUTION` environment variable.

Possible values:

- `highest`: Resolve the highest compatible version of each package
- `lowest`: Resolve the lowest compatible version of each package
- `lowest-direct`: Resolve the lowest compatible version of any direct dependencies, and the highest compatible version of any transitive dependencies
```

[`--rev`](#uv-add--rev) *rev* : Commit to use when adding a dependency from Git

[`--script`](#uv-add--script) *script* : Add the dependency to the specified Python script, rather than to a project.

```
If provided, uv will add the dependency to the script's inline metadata table, in adherence with PEP 723. If no such inline metadata table is present, a new one will be created and added to the script. When executed via `uv run`, uv will create a temporary environment for the script with all inline dependencies installed.
```

[`--tag`](#uv-add--tag) *tag* : Tag to use when adding a dependency from Git

[`--upgrade`](#uv-add--upgrade), `-U` : Allow package upgrades, ignoring pinned versions in any existing output file. Implies `--refresh`

[`--upgrade-package`](#uv-add--upgrade-package), `-P` *upgrade-package* : Allow upgrades for a specific package, ignoring pinned versions in any existing output file. Implies `--refresh-package`

[`--verbose`](#uv-add--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

[`--workspace`](#uv-add--workspace) : Add the dependency as a workspace member.

```
By default, uv will add path dependencies that are within the workspace directory as workspace members. When used with a path dependency, the package will be added to the workspace's `members` list in the root `pyproject.toml` file.
```

## [uv remove](#uv-remove)

Remove dependencies from the project.

Dependencies are removed from the project's `pyproject.toml` file.

If multiple entries exist for a given dependency, i.e., each with different markers, all of the entries will be removed.

The lockfile and project environment will be updated to reflect the removed dependencies. To skip updating the lockfile, use `--frozen`. To skip updating the environment, use `--no-sync`.

If any of the requested dependencies are not present in the project, uv will exit with an error.

If a package has been manually installed in the environment, i.e., with `uv pip install`, it will not be removed by `uv remove`.

uv will search for a project in the current directory or any parent directory. If a project cannot be found, uv will exit with an error.

### Usage

```
uv remove [OPTIONS] <PACKAGES>...

```

### Arguments

[PACKAGES](#uv-remove--packages) : The names of the dependencies to remove (e.g., `ruff`)

### Options

[`--active`](#uv-remove--active) : Prefer the active virtual environment over the project's virtual environment.

```
If the project virtual environment is active or no virtual environment is active, this has no effect.
```

[`--allow-insecure-host`](#uv-remove--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-remove--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-remove--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--compile-bytecode`](#uv-remove--compile-bytecode), `--compile` : Compile Python files to bytecode after installation.

```
By default, uv does not compile Python (`.py`) files to bytecode (`__pycache__/*.pyc`); instead, compilation is performed lazily the first time a module is imported. For use-cases in which start time is critical, such as CLI applications and Docker containers, this option can be enabled to trade longer installation times for faster start times.

When enabled, uv will process the entire site-packages directory (including packages that are not being modified by the current operation) for consistency. Like pip, it will also ignore errors.

May also be set with the `UV_COMPILE_BYTECODE` environment variable.
```

[`--config-file`](#uv-remove--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--config-setting`](#uv-remove--config-setting), `--config-settings`, `-C` *config-setting* : Settings to pass to the PEP 517 build backend, specified as `KEY=VALUE` pairs

[`--config-settings-package`](#uv-remove--config-settings-package), `--config-settings-package` *config-settings-package* : Settings to pass to the PEP 517 build backend for a specific package, specified as `PACKAGE:KEY=VALUE` pairs

[`--default-index`](#uv-remove--default-index) *default-index* : The URL of the default package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--index` flag.

May also be set with the `UV_DEFAULT_INDEX` environment variable.
```

[`--dev`](#uv-remove--dev) : Remove the packages from the development dependency group.

```
This option is an alias for `--group dev`.

May also be set with the `UV_DEV` environment variable.
```

[`--directory`](#uv-remove--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--exclude-newer`](#uv-remove--exclude-newer) *exclude-newer* : Limit candidate packages to those that were uploaded prior to the given date.

```
Accepts both RFC 3339 timestamps (e.g., `2006-12-02T02:07:43Z`) and local dates in the same format (e.g., `2006-12-02`) in your system's configured time zone.

May also be set with the `UV_EXCLUDE_NEWER` environment variable.
```

[`--exclude-newer-package`](#uv-remove--exclude-newer-package) *exclude-newer-package* : Limit candidate packages for specific packages to those that were uploaded prior to the given date.

```
Accepts package-date pairs in the format `PACKAGE=DATE`, where `DATE` is an RFC 3339 timestamp (e.g., `2006-12-02T02:07:43Z`) or local date (e.g., `2006-12-02`) in your system's configured time zone.

Can be provided multiple times for different packages.
```

[`--extra-index-url`](#uv-remove--extra-index-url) *extra-index-url* : (Deprecated: use `--index` instead) Extra URLs of package indexes to use, in addition to `--index-url`.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--index-url` (which defaults to PyPI). When multiple `--extra-index-url` flags are provided, earlier values take priority.

May also be set with the `UV_EXTRA_INDEX_URL` environment variable.
```

[`--find-links`](#uv-remove--find-links), `-f` *find-links* : Locations to search for candidate distributions, in addition to those found in the registry indexes.

```
If a path, the target must be a directory that contains packages as wheel files (`.whl`) or source distributions (e.g., `.tar.gz` or `.zip`) at the top level.

If a URL, the page must contain a flat list of links to package files adhering to the formats described above.

May also be set with the `UV_FIND_LINKS` environment variable.
```

[`--fork-strategy`](#uv-remove--fork-strategy) *fork-strategy* : The strategy to use when selecting multiple versions of a given package across Python versions and platforms.

```
By default, uv will optimize for selecting the latest version of each package for each supported Python version (`requires-python`), while minimizing the number of selected versions across platforms.

Under `fewest`, uv will minimize the number of selected versions for each package, preferring older versions that are compatible with a wider range of supported Python versions or platforms.

May also be set with the `UV_FORK_STRATEGY` environment variable.

Possible values:

- `fewest`: Optimize for selecting the fewest number of versions for each package. Older versions may be preferred if they are compatible with a wider range of supported Python versions or platforms
- `requires-python`: Optimize for selecting latest supported version of each package, for each supported Python version
```

[`--frozen`](#uv-remove--frozen) : Remove dependencies without re-locking the project.

```
The project environment will not be synced.

May also be set with the `UV_FROZEN` environment variable.
```

[`--group`](#uv-remove--group) *group* : Remove the packages from the specified dependency group

[`--help`](#uv-remove--help), `-h` : Display the concise help for this command

[`--index`](#uv-remove--index) *index* : The URLs to use when resolving dependencies, in addition to the default index.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--default-index` (which defaults to PyPI). When multiple `--index` flags are provided, earlier values take priority.

Index names are not supported as values. Relative paths must be disambiguated from index names with `./` or `../` on Unix or `.\\`, `..\\`, `./` or `../` on Windows.

May also be set with the `UV_INDEX` environment variable.
```

[`--index-strategy`](#uv-remove--index-strategy) *index-strategy* : The strategy to use when resolving against multiple index URLs.

```
By default, uv will stop at the first index on which a given package is available, and limit resolutions to those present on that first index (`first-index`). This prevents "dependency confusion" attacks, whereby an attacker can upload a malicious package under the same name to an alternate index.

May also be set with the `UV_INDEX_STRATEGY` environment variable.

Possible values:

- `first-index`: Only use results from the first index that returns a match for a given package name
- `unsafe-first-match`: Search for every package name across all indexes, exhausting the versions from the first index before moving on to the next
- `unsafe-best-match`: Search for every package name across all indexes, preferring the "best" version found. If a package version is in multiple indexes, only look at the entry for the first index
```

[`--index-url`](#uv-remove--index-url), `-i` *index-url* : (Deprecated: use `--default-index` instead) The URL of the Python package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--extra-index-url` flag.

May also be set with the `UV_INDEX_URL` environment variable.
```

[`--keyring-provider`](#uv-remove--keyring-provider) *keyring-provider* : Attempt to use `keyring` for authentication for index URLs.

```
At present, only `--keyring-provider subprocess` is supported, which configures uv to use the `keyring` CLI to handle authentication.

Defaults to `disabled`.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--link-mode`](#uv-remove--link-mode) *link-mode* : The method to use when installing packages from the global cache.

```
Defaults to `clone` (also known as Copy-on-Write) on macOS, and `hardlink` on Linux and Windows.

WARNING: The use of symlink link mode is discouraged, as they create tight coupling between the cache and the target environment. For example, clearing the cache (`uv cache clean`) will break all installed packages by way of removing the underlying source files. Use symlinks with caution.

May also be set with the `UV_LINK_MODE` environment variable.

Possible values:

- `clone`: Clone (i.e., copy-on-write) packages from the wheel into the `site-packages` directory
- `copy`: Copy packages from the wheel into the `site-packages` directory
- `hardlink`: Hard link packages from the wheel into the `site-packages` directory
- `symlink`: Symbolically link packages from the wheel into the `site-packages` directory
```

[`--locked`](#uv-remove--locked) : Assert that the `uv.lock` will remain unchanged.

```
Requires that the lockfile is up-to-date. If the lockfile is missing or needs to be updated, uv will exit with an error.

May also be set with the `UV_LOCKED` environment variable.
```

[`--managed-python`](#uv-remove--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-remove--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-binary`](#uv-remove--no-binary) : Don't install pre-built wheels.

```
The given packages will be built and installed from source. The resolver will still use pre-built wheels to extract package metadata, if available.

May also be set with the `UV_NO_BINARY` environment variable.
```

[`--no-binary-package`](#uv-remove--no-binary-package) *no-binary-package* : Don't install pre-built wheels for a specific package

```
May also be set with the `UV_NO_BINARY_PACKAGE` environment variable.
```

[`--no-build`](#uv-remove--no-build) : Don't build source distributions.

```
When enabled, resolving will not run arbitrary Python code. The cached wheels of already-built source distributions will be reused, but operations that require building distributions will exit with an error.

May also be set with the `UV_NO_BUILD` environment variable.
```

[`--no-build-isolation`](#uv-remove--no-build-isolation) : Disable isolation when building source distributions.

```
Assumes that build dependencies specified by PEP 518 are already installed.

May also be set with the `UV_NO_BUILD_ISOLATION` environment variable.
```

[`--no-build-isolation-package`](#uv-remove--no-build-isolation-package) *no-build-isolation-package* : Disable isolation when building source distributions for a specific package.

```
Assumes that the packages' build dependencies specified by PEP 518 are already installed.
```

[`--no-build-package`](#uv-remove--no-build-package) *no-build-package* : Don't build source distributions for a specific package

```
May also be set with the `UV_NO_BUILD_PACKAGE` environment variable.
```

[`--no-cache`](#uv-remove--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-remove--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-index`](#uv-remove--no-index) : Ignore the registry index (e.g., PyPI), instead relying on direct URL dependencies and those provided via `--find-links`

[`--no-managed-python`](#uv-remove--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-remove--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-remove--no-python-downloads) : Disable automatic downloads of Python.

[`--no-sources`](#uv-remove--no-sources) : Ignore the `tool.uv.sources` table when resolving dependencies. Used to lock against the standards-compliant, publishable package metadata, as opposed to using any workspace, Git, URL, or local path sources

[`--no-sync`](#uv-remove--no-sync) : Avoid syncing the virtual environment after re-locking the project

```
May also be set with the `UV_NO_SYNC` environment variable.
```

[`--offline`](#uv-remove--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--optional`](#uv-remove--optional) *optional* : Remove the packages from the project's optional dependencies for the specified extra

[`--package`](#uv-remove--package) *package* : Remove the dependencies from a specific package in the workspace

[`--prerelease`](#uv-remove--prerelease) *prerelease* : The strategy to use when considering pre-release versions.

```
By default, uv will accept pre-releases for packages that *only* publish pre-releases, along with first-party requirements that contain an explicit pre-release marker in the declared specifiers (`if-necessary-or-explicit`).

May also be set with the `UV_PRERELEASE` environment variable.

Possible values:

- `disallow`: Disallow all pre-release versions
- `allow`: Allow all pre-release versions
- `if-necessary`: Allow pre-release versions if all versions of a package are pre-release
- `explicit`: Allow pre-release versions for first-party packages with explicit pre-release markers in their version requirements
- `if-necessary-or-explicit`: Allow pre-release versions if all versions of a package are pre-release, or if the package has an explicit pre-release marker in its version requirements
```

[`--project`](#uv-remove--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--python`](#uv-remove--python), `-p` *python* : The Python interpreter to use for resolving and syncing.

```
See [uv python](#uv-python) for details on Python discovery and supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--quiet`](#uv-remove--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--refresh`](#uv-remove--refresh) : Refresh all cached data

[`--refresh-package`](#uv-remove--refresh-package) *refresh-package* : Refresh cached data for a specific package

[`--reinstall`](#uv-remove--reinstall), `--force-reinstall` : Reinstall all packages, regardless of whether they're already installed. Implies `--refresh`

[`--reinstall-package`](#uv-remove--reinstall-package) *reinstall-package* : Reinstall a specific package, regardless of whether it's already installed. Implies `--refresh-package`

[`--resolution`](#uv-remove--resolution) *resolution* : The strategy to use when selecting between the different compatible versions for a given package requirement.

```
By default, uv will use the latest compatible version of each package (`highest`).

May also be set with the `UV_RESOLUTION` environment variable.

Possible values:

- `highest`: Resolve the highest compatible version of each package
- `lowest`: Resolve the lowest compatible version of each package
- `lowest-direct`: Resolve the lowest compatible version of any direct dependencies, and the highest compatible version of any transitive dependencies
```

[`--script`](#uv-remove--script) *script* : Remove the dependency from the specified Python script, rather than from a project.

```
If provided, uv will remove the dependency from the script's inline metadata table, in adherence with PEP 723.
```

[`--upgrade`](#uv-remove--upgrade), `-U` : Allow package upgrades, ignoring pinned versions in any existing output file. Implies `--refresh`

[`--upgrade-package`](#uv-remove--upgrade-package), `-P` *upgrade-package* : Allow upgrades for a specific package, ignoring pinned versions in any existing output file. Implies `--refresh-package`

[`--verbose`](#uv-remove--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

## [uv version](#uv-version)

Read or update the project's version

### Usage

```
uv version [OPTIONS] [VALUE]

```

### Arguments

[VALUE](#uv-version--value) : Set the project version to this value

```
To update the project using semantic versioning components instead, use `--bump`.
```

### Options

[`--active`](#uv-version--active) : Prefer the active virtual environment over the project's virtual environment.

```
If the project virtual environment is active or no virtual environment is active, this has no effect.
```

[`--allow-insecure-host`](#uv-version--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--bump`](#uv-version--bump) *bump* : Update the project version using the given semantics

```
This flag can be passed multiple times.

Possible values:

- `major`: Increase the major version (e.g., 1.2.3 => 2.0.0)
- `minor`: Increase the minor version (e.g., 1.2.3 => 1.3.0)
- `patch`: Increase the patch version (e.g., 1.2.3 => 1.2.4)
- `stable`: Move from a pre-release to stable version (e.g., 1.2.3b4.post5.dev6 => 1.2.3)
- `alpha`: Increase the alpha version (e.g., 1.2.3a4 => 1.2.3a5)
- `beta`: Increase the beta version (e.g., 1.2.3b4 => 1.2.3b5)
- `rc`: Increase the rc version (e.g., 1.2.3rc4 => 1.2.3rc5)
- `post`: Increase the post version (e.g., 1.2.3.post5 => 1.2.3.post6)
- `dev`: Increase the dev version (e.g., 1.2.3a4.dev6 => 1.2.3.dev7)
```

[`--cache-dir`](#uv-version--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-version--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--compile-bytecode`](#uv-version--compile-bytecode), `--compile` : Compile Python files to bytecode after installation.

```
By default, uv does not compile Python (`.py`) files to bytecode (`__pycache__/*.pyc`); instead, compilation is performed lazily the first time a module is imported. For use-cases in which start time is critical, such as CLI applications and Docker containers, this option can be enabled to trade longer installation times for faster start times.

When enabled, uv will process the entire site-packages directory (including packages that are not being modified by the current operation) for consistency. Like pip, it will also ignore errors.

May also be set with the `UV_COMPILE_BYTECODE` environment variable.
```

[`--config-file`](#uv-version--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--config-setting`](#uv-version--config-setting), `--config-settings`, `-C` *config-setting* : Settings to pass to the PEP 517 build backend, specified as `KEY=VALUE` pairs

[`--config-settings-package`](#uv-version--config-settings-package), `--config-settings-package` *config-settings-package* : Settings to pass to the PEP 517 build backend for a specific package, specified as `PACKAGE:KEY=VALUE` pairs

[`--default-index`](#uv-version--default-index) *default-index* : The URL of the default package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--index` flag.

May also be set with the `UV_DEFAULT_INDEX` environment variable.
```

[`--directory`](#uv-version--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--dry-run`](#uv-version--dry-run) : Don't write a new version to the `pyproject.toml`

```
Instead, the version will be displayed.
```

[`--exclude-newer`](#uv-version--exclude-newer) *exclude-newer* : Limit candidate packages to those that were uploaded prior to the given date.

```
Accepts both RFC 3339 timestamps (e.g., `2006-12-02T02:07:43Z`) and local dates in the same format (e.g., `2006-12-02`) in your system's configured time zone.

May also be set with the `UV_EXCLUDE_NEWER` environment variable.
```

[`--exclude-newer-package`](#uv-version--exclude-newer-package) *exclude-newer-package* : Limit candidate packages for specific packages to those that were uploaded prior to the given date.

```
Accepts package-date pairs in the format `PACKAGE=DATE`, where `DATE` is an RFC 3339 timestamp (e.g., `2006-12-02T02:07:43Z`) or local date (e.g., `2006-12-02`) in your system's configured time zone.

Can be provided multiple times for different packages.
```

[`--extra-index-url`](#uv-version--extra-index-url) *extra-index-url* : (Deprecated: use `--index` instead) Extra URLs of package indexes to use, in addition to `--index-url`.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--index-url` (which defaults to PyPI). When multiple `--extra-index-url` flags are provided, earlier values take priority.

May also be set with the `UV_EXTRA_INDEX_URL` environment variable.
```

[`--find-links`](#uv-version--find-links), `-f` *find-links* : Locations to search for candidate distributions, in addition to those found in the registry indexes.

```
If a path, the target must be a directory that contains packages as wheel files (`.whl`) or source distributions (e.g., `.tar.gz` or `.zip`) at the top level.

If a URL, the page must contain a flat list of links to package files adhering to the formats described above.

May also be set with the `UV_FIND_LINKS` environment variable.
```

[`--fork-strategy`](#uv-version--fork-strategy) *fork-strategy* : The strategy to use when selecting multiple versions of a given package across Python versions and platforms.

```
By default, uv will optimize for selecting the latest version of each package for each supported Python version (`requires-python`), while minimizing the number of selected versions across platforms.

Under `fewest`, uv will minimize the number of selected versions for each package, preferring older versions that are compatible with a wider range of supported Python versions or platforms.

May also be set with the `UV_FORK_STRATEGY` environment variable.

Possible values:

- `fewest`: Optimize for selecting the fewest number of versions for each package. Older versions may be preferred if they are compatible with a wider range of supported Python versions or platforms
- `requires-python`: Optimize for selecting latest supported version of each package, for each supported Python version
```

[`--frozen`](#uv-version--frozen) : Update the version without re-locking the project.

```
The project environment will not be synced.

May also be set with the `UV_FROZEN` environment variable.
```

[`--help`](#uv-version--help), `-h` : Display the concise help for this command

[`--index`](#uv-version--index) *index* : The URLs to use when resolving dependencies, in addition to the default index.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--default-index` (which defaults to PyPI). When multiple `--index` flags are provided, earlier values take priority.

Index names are not supported as values. Relative paths must be disambiguated from index names with `./` or `../` on Unix or `.\\`, `..\\`, `./` or `../` on Windows.

May also be set with the `UV_INDEX` environment variable.
```

[`--index-strategy`](#uv-version--index-strategy) *index-strategy* : The strategy to use when resolving against multiple index URLs.

```
By default, uv will stop at the first index on which a given package is available, and limit resolutions to those present on that first index (`first-index`). This prevents "dependency confusion" attacks, whereby an attacker can upload a malicious package under the same name to an alternate index.

May also be set with the `UV_INDEX_STRATEGY` environment variable.

Possible values:

- `first-index`: Only use results from the first index that returns a match for a given package name
- `unsafe-first-match`: Search for every package name across all indexes, exhausting the versions from the first index before moving on to the next
- `unsafe-best-match`: Search for every package name across all indexes, preferring the "best" version found. If a package version is in multiple indexes, only look at the entry for the first index
```

[`--index-url`](#uv-version--index-url), `-i` *index-url* : (Deprecated: use `--default-index` instead) The URL of the Python package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--extra-index-url` flag.

May also be set with the `UV_INDEX_URL` environment variable.
```

[`--keyring-provider`](#uv-version--keyring-provider) *keyring-provider* : Attempt to use `keyring` for authentication for index URLs.

```
At present, only `--keyring-provider subprocess` is supported, which configures uv to use the `keyring` CLI to handle authentication.

Defaults to `disabled`.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--link-mode`](#uv-version--link-mode) *link-mode* : The method to use when installing packages from the global cache.

```
Defaults to `clone` (also known as Copy-on-Write) on macOS, and `hardlink` on Linux and Windows.

WARNING: The use of symlink link mode is discouraged, as they create tight coupling between the cache and the target environment. For example, clearing the cache (`uv cache clean`) will break all installed packages by way of removing the underlying source files. Use symlinks with caution.

May also be set with the `UV_LINK_MODE` environment variable.

Possible values:

- `clone`: Clone (i.e., copy-on-write) packages from the wheel into the `site-packages` directory
- `copy`: Copy packages from the wheel into the `site-packages` directory
- `hardlink`: Hard link packages from the wheel into the `site-packages` directory
- `symlink`: Symbolically link packages from the wheel into the `site-packages` directory
```

[`--locked`](#uv-version--locked) : Assert that the `uv.lock` will remain unchanged.

```
Requires that the lockfile is up-to-date. If the lockfile is missing or needs to be updated, uv will exit with an error.

May also be set with the `UV_LOCKED` environment variable.
```

[`--managed-python`](#uv-version--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-version--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-binary`](#uv-version--no-binary) : Don't install pre-built wheels.

```
The given packages will be built and installed from source. The resolver will still use pre-built wheels to extract package metadata, if available.

May also be set with the `UV_NO_BINARY` environment variable.
```

[`--no-binary-package`](#uv-version--no-binary-package) *no-binary-package* : Don't install pre-built wheels for a specific package

```
May also be set with the `UV_NO_BINARY_PACKAGE` environment variable.
```

[`--no-build`](#uv-version--no-build) : Don't build source distributions.

```
When enabled, resolving will not run arbitrary Python code. The cached wheels of already-built source distributions will be reused, but operations that require building distributions will exit with an error.

May also be set with the `UV_NO_BUILD` environment variable.
```

[`--no-build-isolation`](#uv-version--no-build-isolation) : Disable isolation when building source distributions.

```
Assumes that build dependencies specified by PEP 518 are already installed.

May also be set with the `UV_NO_BUILD_ISOLATION` environment variable.
```

[`--no-build-isolation-package`](#uv-version--no-build-isolation-package) *no-build-isolation-package* : Disable isolation when building source distributions for a specific package.

```
Assumes that the packages' build dependencies specified by PEP 518 are already installed.
```

[`--no-build-package`](#uv-version--no-build-package) *no-build-package* : Don't build source distributions for a specific package

```
May also be set with the `UV_NO_BUILD_PACKAGE` environment variable.
```

[`--no-cache`](#uv-version--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-version--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-index`](#uv-version--no-index) : Ignore the registry index (e.g., PyPI), instead relying on direct URL dependencies and those provided via `--find-links`

[`--no-managed-python`](#uv-version--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-version--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-version--no-python-downloads) : Disable automatic downloads of Python.

[`--no-sources`](#uv-version--no-sources) : Ignore the `tool.uv.sources` table when resolving dependencies. Used to lock against the standards-compliant, publishable package metadata, as opposed to using any workspace, Git, URL, or local path sources

[`--no-sync`](#uv-version--no-sync) : Avoid syncing the virtual environment after re-locking the project

```
May also be set with the `UV_NO_SYNC` environment variable.
```

[`--offline`](#uv-version--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--output-format`](#uv-version--output-format) *output-format* : The format of the output

```
[default: text]

Possible values:

- `text`: Display the version as plain text
- `json`: Display the version as JSON
```

[`--package`](#uv-version--package) *package* : Update the version of a specific package in the workspace

[`--prerelease`](#uv-version--prerelease) *prerelease* : The strategy to use when considering pre-release versions.

```
By default, uv will accept pre-releases for packages that *only* publish pre-releases, along with first-party requirements that contain an explicit pre-release marker in the declared specifiers (`if-necessary-or-explicit`).

May also be set with the `UV_PRERELEASE` environment variable.

Possible values:

- `disallow`: Disallow all pre-release versions
- `allow`: Allow all pre-release versions
- `if-necessary`: Allow pre-release versions if all versions of a package are pre-release
- `explicit`: Allow pre-release versions for first-party packages with explicit pre-release markers in their version requirements
- `if-necessary-or-explicit`: Allow pre-release versions if all versions of a package are pre-release, or if the package has an explicit pre-release marker in its version requirements
```

[`--project`](#uv-version--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--python`](#uv-version--python), `-p` *python* : The Python interpreter to use for resolving and syncing.

```
See [uv python](#uv-python) for details on Python discovery and supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--quiet`](#uv-version--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--refresh`](#uv-version--refresh) : Refresh all cached data

[`--refresh-package`](#uv-version--refresh-package) *refresh-package* : Refresh cached data for a specific package

[`--reinstall`](#uv-version--reinstall), `--force-reinstall` : Reinstall all packages, regardless of whether they're already installed. Implies `--refresh`

[`--reinstall-package`](#uv-version--reinstall-package) *reinstall-package* : Reinstall a specific package, regardless of whether it's already installed. Implies `--refresh-package`

[`--resolution`](#uv-version--resolution) *resolution* : The strategy to use when selecting between the different compatible versions for a given package requirement.

```
By default, uv will use the latest compatible version of each package (`highest`).

May also be set with the `UV_RESOLUTION` environment variable.

Possible values:

- `highest`: Resolve the highest compatible version of each package
- `lowest`: Resolve the lowest compatible version of each package
- `lowest-direct`: Resolve the lowest compatible version of any direct dependencies, and the highest compatible version of any transitive dependencies
```

[`--short`](#uv-version--short) : Only show the version

```
By default, uv will show the project name before the version.
```

[`--upgrade`](#uv-version--upgrade), `-U` : Allow package upgrades, ignoring pinned versions in any existing output file. Implies `--refresh`

[`--upgrade-package`](#uv-version--upgrade-package), `-P` *upgrade-package* : Allow upgrades for a specific package, ignoring pinned versions in any existing output file. Implies `--refresh-package`

[`--verbose`](#uv-version--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

## [uv sync](#uv-sync)

Update the project's environment.

Syncing ensures that all project dependencies are installed and up-to-date with the lockfile.

By default, an exact sync is performed: uv removes packages that are not declared as dependencies of the project. Use the `--inexact` flag to keep extraneous packages. Note that if an extraneous package conflicts with a project dependency, it will still be removed. Additionally, if `--no-build-isolation` is used, uv will not remove extraneous packages to avoid removing possible build dependencies.

If the project virtual environment (`.venv`) does not exist, it will be created.

The project is re-locked before syncing unless the `--locked` or `--frozen` flag is provided.

uv will search for a project in the current directory or any parent directory. If a project cannot be found, uv will exit with an error.

Note that, when installing from a lockfile, uv will not provide warnings for yanked package versions.

### Usage

```
uv sync [OPTIONS]

```

### Options

[`--active`](#uv-sync--active) : Sync dependencies to the active virtual environment.

```
Instead of creating or updating the virtual environment for the project or script, the active virtual environment will be preferred, if the `VIRTUAL_ENV` environment variable is set.
```

[`--all-extras`](#uv-sync--all-extras) : Include all optional dependencies.

```
When two or more extras are declared as conflicting in `tool.uv.conflicts`, using this flag will always result in an error.

Note that all optional dependencies are always included in the resolution; this option only affects the selection of packages to install.
```

[`--all-groups`](#uv-sync--all-groups) : Include dependencies from all dependency groups.

```
`--no-group` can be used to exclude specific groups.
```

[`--all-packages`](#uv-sync--all-packages) : Sync all packages in the workspace.

```
The workspace's environment (`.venv`) is updated to include all workspace members.

Any extras or groups specified via `--extra`, `--group`, or related options will be applied to all workspace members.
```

[`--allow-insecure-host`](#uv-sync--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-sync--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--check`](#uv-sync--check) : Check if the Python environment is synchronized with the project.

```
If the environment is not up to date, uv will exit with an error.
```

[`--color`](#uv-sync--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--compile-bytecode`](#uv-sync--compile-bytecode), `--compile` : Compile Python files to bytecode after installation.

```
By default, uv does not compile Python (`.py`) files to bytecode (`__pycache__/*.pyc`); instead, compilation is performed lazily the first time a module is imported. For use-cases in which start time is critical, such as CLI applications and Docker containers, this option can be enabled to trade longer installation times for faster start times.

When enabled, uv will process the entire site-packages directory (including packages that are not being modified by the current operation) for consistency. Like pip, it will also ignore errors.

May also be set with the `UV_COMPILE_BYTECODE` environment variable.
```

[`--config-file`](#uv-sync--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--config-setting`](#uv-sync--config-setting), `--config-settings`, `-C` *config-setting* : Settings to pass to the PEP 517 build backend, specified as `KEY=VALUE` pairs

[`--config-settings-package`](#uv-sync--config-settings-package), `--config-settings-package` *config-settings-package* : Settings to pass to the PEP 517 build backend for a specific package, specified as `PACKAGE:KEY=VALUE` pairs

[`--default-index`](#uv-sync--default-index) *default-index* : The URL of the default package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--index` flag.

May also be set with the `UV_DEFAULT_INDEX` environment variable.
```

[`--directory`](#uv-sync--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--dry-run`](#uv-sync--dry-run) : Perform a dry run, without writing the lockfile or modifying the project environment.

```
In dry-run mode, uv will resolve the project's dependencies and report on the resulting changes to both the lockfile and the project environment, but will not modify either.
```

[`--exclude-newer`](#uv-sync--exclude-newer) *exclude-newer* : Limit candidate packages to those that were uploaded prior to the given date.

```
Accepts both RFC 3339 timestamps (e.g., `2006-12-02T02:07:43Z`) and local dates in the same format (e.g., `2006-12-02`) in your system's configured time zone.

May also be set with the `UV_EXCLUDE_NEWER` environment variable.
```

[`--exclude-newer-package`](#uv-sync--exclude-newer-package) *exclude-newer-package* : Limit candidate packages for specific packages to those that were uploaded prior to the given date.

```
Accepts package-date pairs in the format `PACKAGE=DATE`, where `DATE` is an RFC 3339 timestamp (e.g., `2006-12-02T02:07:43Z`) or local date (e.g., `2006-12-02`) in your system's configured time zone.

Can be provided multiple times for different packages.
```

[`--extra`](#uv-sync--extra) *extra* : Include optional dependencies from the specified extra name.

```
May be provided more than once.

When multiple extras or groups are specified that appear in `tool.uv.conflicts`, uv will report an error.

Note that all optional dependencies are always included in the resolution; this option only affects the selection of packages to install.
```

[`--extra-index-url`](#uv-sync--extra-index-url) *extra-index-url* : (Deprecated: use `--index` instead) Extra URLs of package indexes to use, in addition to `--index-url`.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--index-url` (which defaults to PyPI). When multiple `--extra-index-url` flags are provided, earlier values take priority.

May also be set with the `UV_EXTRA_INDEX_URL` environment variable.
```

[`--find-links`](#uv-sync--find-links), `-f` *find-links* : Locations to search for candidate distributions, in addition to those found in the registry indexes.

```
If a path, the target must be a directory that contains packages as wheel files (`.whl`) or source distributions (e.g., `.tar.gz` or `.zip`) at the top level.

If a URL, the page must contain a flat list of links to package files adhering to the formats described above.

May also be set with the `UV_FIND_LINKS` environment variable.
```

[`--fork-strategy`](#uv-sync--fork-strategy) *fork-strategy* : The strategy to use when selecting multiple versions of a given package across Python versions and platforms.

```
By default, uv will optimize for selecting the latest version of each package for each supported Python version (`requires-python`), while minimizing the number of selected versions across platforms.

Under `fewest`, uv will minimize the number of selected versions for each package, preferring older versions that are compatible with a wider range of supported Python versions or platforms.

May also be set with the `UV_FORK_STRATEGY` environment variable.

Possible values:

- `fewest`: Optimize for selecting the fewest number of versions for each package. Older versions may be preferred if they are compatible with a wider range of supported Python versions or platforms
- `requires-python`: Optimize for selecting latest supported version of each package, for each supported Python version
```

[`--frozen`](#uv-sync--frozen) : Sync without updating the `uv.lock` file.

```
Instead of checking if the lockfile is up-to-date, uses the versions in the lockfile as the source of truth. If the lockfile is missing, uv will exit with an error. If the `pyproject.toml` includes changes to dependencies that have not been included in the lockfile yet, they will not be present in the environment.

May also be set with the `UV_FROZEN` environment variable.
```

[`--group`](#uv-sync--group) *group* : Include dependencies from the specified dependency group.

```
When multiple extras or groups are specified that appear in `tool.uv.conflicts`, uv will report an error.

May be provided multiple times.
```

[`--help`](#uv-sync--help), `-h` : Display the concise help for this command

[`--index`](#uv-sync--index) *index* : The URLs to use when resolving dependencies, in addition to the default index.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--default-index` (which defaults to PyPI). When multiple `--index` flags are provided, earlier values take priority.

Index names are not supported as values. Relative paths must be disambiguated from index names with `./` or `../` on Unix or `.\\`, `..\\`, `./` or `../` on Windows.

May also be set with the `UV_INDEX` environment variable.
```

[`--index-strategy`](#uv-sync--index-strategy) *index-strategy* : The strategy to use when resolving against multiple index URLs.

```
By default, uv will stop at the first index on which a given package is available, and limit resolutions to those present on that first index (`first-index`). This prevents "dependency confusion" attacks, whereby an attacker can upload a malicious package under the same name to an alternate index.

May also be set with the `UV_INDEX_STRATEGY` environment variable.

Possible values:

- `first-index`: Only use results from the first index that returns a match for a given package name
- `unsafe-first-match`: Search for every package name across all indexes, exhausting the versions from the first index before moving on to the next
- `unsafe-best-match`: Search for every package name across all indexes, preferring the "best" version found. If a package version is in multiple indexes, only look at the entry for the first index
```

[`--index-url`](#uv-sync--index-url), `-i` *index-url* : (Deprecated: use `--default-index` instead) The URL of the Python package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--extra-index-url` flag.

May also be set with the `UV_INDEX_URL` environment variable.
```

[`--inexact`](#uv-sync--inexact), `--no-exact` : Do not remove extraneous packages present in the environment.

```
When enabled, uv will make the minimum necessary changes to satisfy the requirements. By default, syncing will remove any extraneous packages from the environment
```

[`--keyring-provider`](#uv-sync--keyring-provider) *keyring-provider* : Attempt to use `keyring` for authentication for index URLs.

```
At present, only `--keyring-provider subprocess` is supported, which configures uv to use the `keyring` CLI to handle authentication.

Defaults to `disabled`.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--link-mode`](#uv-sync--link-mode) *link-mode* : The method to use when installing packages from the global cache.

```
Defaults to `clone` (also known as Copy-on-Write) on macOS, and `hardlink` on Linux and Windows.

WARNING: The use of symlink link mode is discouraged, as they create tight coupling between the cache and the target environment. For example, clearing the cache (`uv cache clean`) will break all installed packages by way of removing the underlying source files. Use symlinks with caution.

May also be set with the `UV_LINK_MODE` environment variable.

Possible values:

- `clone`: Clone (i.e., copy-on-write) packages from the wheel into the `site-packages` directory
- `copy`: Copy packages from the wheel into the `site-packages` directory
- `hardlink`: Hard link packages from the wheel into the `site-packages` directory
- `symlink`: Symbolically link packages from the wheel into the `site-packages` directory
```

[`--locked`](#uv-sync--locked) : Assert that the `uv.lock` will remain unchanged.

```
Requires that the lockfile is up-to-date. If the lockfile is missing or needs to be updated, uv will exit with an error.

May also be set with the `UV_LOCKED` environment variable.
```

[`--managed-python`](#uv-sync--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-sync--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-binary`](#uv-sync--no-binary) : Don't install pre-built wheels.

```
The given packages will be built and installed from source. The resolver will still use pre-built wheels to extract package metadata, if available.

May also be set with the `UV_NO_BINARY` environment variable.
```

[`--no-binary-package`](#uv-sync--no-binary-package) *no-binary-package* : Don't install pre-built wheels for a specific package

```
May also be set with the `UV_NO_BINARY_PACKAGE` environment variable.
```

[`--no-build`](#uv-sync--no-build) : Don't build source distributions.

```
When enabled, resolving will not run arbitrary Python code. The cached wheels of already-built source distributions will be reused, but operations that require building distributions will exit with an error.

May also be set with the `UV_NO_BUILD` environment variable.
```

[`--no-build-isolation`](#uv-sync--no-build-isolation) : Disable isolation when building source distributions.

```
Assumes that build dependencies specified by PEP 518 are already installed.

May also be set with the `UV_NO_BUILD_ISOLATION` environment variable.
```

[`--no-build-isolation-package`](#uv-sync--no-build-isolation-package) *no-build-isolation-package* : Disable isolation when building source distributions for a specific package.

```
Assumes that the packages' build dependencies specified by PEP 518 are already installed.
```

[`--no-build-package`](#uv-sync--no-build-package) *no-build-package* : Don't build source distributions for a specific package

```
May also be set with the `UV_NO_BUILD_PACKAGE` environment variable.
```

[`--no-cache`](#uv-sync--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-sync--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-default-groups`](#uv-sync--no-default-groups) : Ignore the default dependency groups.

```
uv includes the groups defined in `tool.uv.default-groups` by default. This disables that option, however, specific groups can still be included with `--group`.
```

[`--no-dev`](#uv-sync--no-dev) : Disable the development dependency group.

```
This option is an alias of `--no-group dev`. See `--no-default-groups` to disable all default groups instead.

May also be set with the `UV_NO_DEV` environment variable.
```

[`--no-editable`](#uv-sync--no-editable) : Install any editable dependencies, including the project and any workspace members, as non-editable

```
May also be set with the `UV_NO_EDITABLE` environment variable.
```

[`--no-extra`](#uv-sync--no-extra) *no-extra* : Exclude the specified optional dependencies, if `--all-extras` is supplied.

```
May be provided multiple times.
```

[`--no-group`](#uv-sync--no-group) *no-group* : Disable the specified dependency group.

```
This option always takes precedence over default groups, `--all-groups`, and `--group`.

May be provided multiple times.
```

[`--no-index`](#uv-sync--no-index) : Ignore the registry index (e.g., PyPI), instead relying on direct URL dependencies and those provided via `--find-links`

[`--no-install-local`](#uv-sync--no-install-local) : Do not install local path dependencies

```
Skips the current project, workspace members, and any other local (path or editable) packages. Only remote/indexed dependencies are installed. Useful in Docker builds to cache heavy third-party dependencies first and layer local packages separately.
```

[`--no-install-package`](#uv-sync--no-install-package) *no-install-package* : Do not install the given package(s).

```
By default, all of the project's dependencies are installed into the environment. The `--no-install-package` option allows exclusion of specific packages. Note this can result in a broken environment, and should be used with caution.
```

[`--no-install-project`](#uv-sync--no-install-project) : Do not install the current project.

```
By default, the current project is installed into the environment with all of its dependencies. The `--no-install-project` option allows the project to be excluded, but all of its dependencies are still installed. This is particularly useful in situations like building Docker images where installing the project separately from its dependencies allows optimal layer caching.
```

[`--no-install-workspace`](#uv-sync--no-install-workspace) : Do not install any workspace members, including the root project.

```
By default, all of the workspace members and their dependencies are installed into the environment. The `--no-install-workspace` option allows exclusion of all the workspace members while retaining their dependencies. This is particularly useful in situations like building Docker images where installing the workspace separately from its dependencies allows optimal layer caching.
```

[`--no-managed-python`](#uv-sync--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-sync--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-sync--no-python-downloads) : Disable automatic downloads of Python.

[`--no-sources`](#uv-sync--no-sources) : Ignore the `tool.uv.sources` table when resolving dependencies. Used to lock against the standards-compliant, publishable package metadata, as opposed to using any workspace, Git, URL, or local path sources

[`--offline`](#uv-sync--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--only-dev`](#uv-sync--only-dev) : Only include the development dependency group.

```
The project and its dependencies will be omitted.

This option is an alias for `--only-group dev`. Implies `--no-default-groups`.
```

[`--only-group`](#uv-sync--only-group) *only-group* : Only include dependencies from the specified dependency group.

```
The project and its dependencies will be omitted.

May be provided multiple times. Implies `--no-default-groups`.
```

[`--output-format`](#uv-sync--output-format) *output-format* : Select the output format

```
[default: text]

Possible values:

- `text`: Display the result in a human-readable format
- `json`: Display the result in JSON format
```

[`--package`](#uv-sync--package) *package* : Sync for a specific package in the workspace.

```
The workspace's environment (`.venv`) is updated to reflect the subset of dependencies declared by the specified workspace member package.

If the workspace member does not exist, uv will exit with an error.
```

[`--prerelease`](#uv-sync--prerelease) *prerelease* : The strategy to use when considering pre-release versions.

```
By default, uv will accept pre-releases for packages that *only* publish pre-releases, along with first-party requirements that contain an explicit pre-release marker in the declared specifiers (`if-necessary-or-explicit`).

May also be set with the `UV_PRERELEASE` environment variable.

Possible values:

- `disallow`: Disallow all pre-release versions
- `allow`: Allow all pre-release versions
- `if-necessary`: Allow pre-release versions if all versions of a package are pre-release
- `explicit`: Allow pre-release versions for first-party packages with explicit pre-release markers in their version requirements
- `if-necessary-or-explicit`: Allow pre-release versions if all versions of a package are pre-release, or if the package has an explicit pre-release marker in its version requirements
```

[`--project`](#uv-sync--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--python`](#uv-sync--python), `-p` *python* : The Python interpreter to use for the project environment.

```
By default, the first interpreter that meets the project's `requires-python` constraint is
used.

If a Python interpreter in a virtual environment is provided, the packages will not be
synced to the given environment. The interpreter will be used to create a virtual
environment in the project.

See [uv python](#uv-python) for details on Python discovery and supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--python-platform`](#uv-sync--python-platform) *python-platform* : The platform for which requirements should be installed.

```
Represented as a "target triple", a string that describes the target platform in terms of its CPU, vendor, and operating system name, like `x86_64-unknown-linux-gnu` or `aarch64-apple-darwin`.

When targeting macOS (Darwin), the default minimum version is `13.0`. Use `MACOSX_DEPLOYMENT_TARGET` to specify a different minimum version, e.g., `14.0`.

When targeting iOS, the default minimum version is `13.0`. Use `IPHONEOS_DEPLOYMENT_TARGET` to specify a different minimum version, e.g., `14.0`.

When targeting Android, the default minimum Android API level is `24`. Use `ANDROID_API_LEVEL` to specify a different minimum version, e.g., `26`.

WARNING: When specified, uv will select wheels that are compatible with the *target* platform; as a result, the installed distributions may not be compatible with the *current* platform. Conversely, any distributions that are built from source may be incompatible with the *target* platform, as they will be built for the *current* platform. The `--python-platform` option is intended for advanced use cases.

Possible values:

- `windows`: An alias for `x86_64-pc-windows-msvc`, the default target for Windows
- `linux`: An alias for `x86_64-unknown-linux-gnu`, the default target for Linux
- `macos`: An alias for `aarch64-apple-darwin`, the default target for macOS
- `x86_64-pc-windows-msvc`: A 64-bit x86 Windows target
- `aarch64-pc-windows-msvc`: An ARM64 Windows target
- `i686-pc-windows-msvc`: A 32-bit x86 Windows target
- `x86_64-unknown-linux-gnu`: An x86 Linux target. Equivalent to `x86_64-manylinux_2_28`
- `aarch64-apple-darwin`: An ARM-based macOS target, as seen on Apple Silicon devices
- `x86_64-apple-darwin`: An x86 macOS target
- `aarch64-unknown-linux-gnu`: An ARM64 Linux target. Equivalent to `aarch64-manylinux_2_28`
- `aarch64-unknown-linux-musl`: An ARM64 Linux target
- `x86_64-unknown-linux-musl`: An `x86_64` Linux target
- `riscv64-unknown-linux`: A RISCV64 Linux target
- `x86_64-manylinux2014`: An `x86_64` target for the `manylinux2014` platform. Equivalent to `x86_64-manylinux_2_17`
- `x86_64-manylinux_2_17`: An `x86_64` target for the `manylinux_2_17` platform
- `x86_64-manylinux_2_28`: An `x86_64` target for the `manylinux_2_28` platform
- `x86_64-manylinux_2_31`: An `x86_64` target for the `manylinux_2_31` platform
- `x86_64-manylinux_2_32`: An `x86_64` target for the `manylinux_2_32` platform
- `x86_64-manylinux_2_33`: An `x86_64` target for the `manylinux_2_33` platform
- `x86_64-manylinux_2_34`: An `x86_64` target for the `manylinux_2_34` platform
- `x86_64-manylinux_2_35`: An `x86_64` target for the `manylinux_2_35` platform
- `x86_64-manylinux_2_36`: An `x86_64` target for the `manylinux_2_36` platform
- `x86_64-manylinux_2_37`: An `x86_64` target for the `manylinux_2_37` platform
- `x86_64-manylinux_2_38`: An `x86_64` target for the `manylinux_2_38` platform
- `x86_64-manylinux_2_39`: An `x86_64` target for the `manylinux_2_39` platform
- `x86_64-manylinux_2_40`: An `x86_64` target for the `manylinux_2_40` platform
- `aarch64-manylinux2014`: An ARM64 target for the `manylinux2014` platform. Equivalent to `aarch64-manylinux_2_17`
- `aarch64-manylinux_2_17`: An ARM64 target for the `manylinux_2_17` platform
- `aarch64-manylinux_2_28`: An ARM64 target for the `manylinux_2_28` platform
- `aarch64-manylinux_2_31`: An ARM64 target for the `manylinux_2_31` platform
- `aarch64-manylinux_2_32`: An ARM64 target for the `manylinux_2_32` platform
- `aarch64-manylinux_2_33`: An ARM64 target for the `manylinux_2_33` platform
- `aarch64-manylinux_2_34`: An ARM64 target for the `manylinux_2_34` platform
- `aarch64-manylinux_2_35`: An ARM64 target for the `manylinux_2_35` platform
- `aarch64-manylinux_2_36`: An ARM64 target for the `manylinux_2_36` platform
- `aarch64-manylinux_2_37`: An ARM64 target for the `manylinux_2_37` platform
- `aarch64-manylinux_2_38`: An ARM64 target for the `manylinux_2_38` platform
- `aarch64-manylinux_2_39`: An ARM64 target for the `manylinux_2_39` platform
- `aarch64-manylinux_2_40`: An ARM64 target for the `manylinux_2_40` platform
- `aarch64-linux-android`: An ARM64 Android target
- `x86_64-linux-android`: An `x86_64` Android target
- `wasm32-pyodide2024`: A wasm32 target using the Pyodide 2024 platform. Meant for use with Python 3.12
- `arm64-apple-ios`: An ARM64 target for iOS device
- `arm64-apple-ios-simulator`: An ARM64 target for iOS simulator
- `x86_64-apple-ios-simulator`: An `x86_64` target for iOS simulator
```

[`--quiet`](#uv-sync--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--refresh`](#uv-sync--refresh) : Refresh all cached data

[`--refresh-package`](#uv-sync--refresh-package) *refresh-package* : Refresh cached data for a specific package

[`--reinstall`](#uv-sync--reinstall), `--force-reinstall` : Reinstall all packages, regardless of whether they're already installed. Implies `--refresh`

[`--reinstall-package`](#uv-sync--reinstall-package) *reinstall-package* : Reinstall a specific package, regardless of whether it's already installed. Implies `--refresh-package`

[`--resolution`](#uv-sync--resolution) *resolution* : The strategy to use when selecting between the different compatible versions for a given package requirement.

```
By default, uv will use the latest compatible version of each package (`highest`).

May also be set with the `UV_RESOLUTION` environment variable.

Possible values:

- `highest`: Resolve the highest compatible version of each package
- `lowest`: Resolve the lowest compatible version of each package
- `lowest-direct`: Resolve the lowest compatible version of any direct dependencies, and the highest compatible version of any transitive dependencies
```

[`--script`](#uv-sync--script) *script* : Sync the environment for a Python script, rather than the current project.

```
If provided, uv will sync the dependencies based on the script's inline metadata table, in adherence with PEP 723.
```

[`--upgrade`](#uv-sync--upgrade), `-U` : Allow package upgrades, ignoring pinned versions in any existing output file. Implies `--refresh`

[`--upgrade-package`](#uv-sync--upgrade-package), `-P` *upgrade-package* : Allow upgrades for a specific package, ignoring pinned versions in any existing output file. Implies `--refresh-package`

[`--verbose`](#uv-sync--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

## [uv lock](#uv-lock)

Update the project's lockfile.

If the project lockfile (`uv.lock`) does not exist, it will be created. If a lockfile is present, its contents will be used as preferences for the resolution.

If there are no changes to the project's dependencies, locking will have no effect unless the `--upgrade` flag is provided.

### Usage

```
uv lock [OPTIONS]

```

### Options

[`--allow-insecure-host`](#uv-lock--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-lock--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--check`](#uv-lock--check), `--locked` : Check if the lockfile is up-to-date.

```
Asserts that the `uv.lock` would remain unchanged after a resolution. If the lockfile is missing or needs to be updated, uv will exit with an error.

Equivalent to `--locked`.

May also be set with the `UV_LOCKED` environment variable.
```

[`--check-exists`](#uv-lock--check-exists), `--frozen` : Assert that a `uv.lock` exists without checking if it is up-to-date.

```
Equivalent to `--frozen`.

May also be set with the `UV_FROZEN` environment variable.
```

[`--color`](#uv-lock--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-lock--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--config-setting`](#uv-lock--config-setting), `--config-settings`, `-C` *config-setting* : Settings to pass to the PEP 517 build backend, specified as `KEY=VALUE` pairs

[`--config-settings-package`](#uv-lock--config-settings-package), `--config-settings-package` *config-settings-package* : Settings to pass to the PEP 517 build backend for a specific package, specified as `PACKAGE:KEY=VALUE` pairs

[`--default-index`](#uv-lock--default-index) *default-index* : The URL of the default package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--index` flag.

May also be set with the `UV_DEFAULT_INDEX` environment variable.
```

[`--directory`](#uv-lock--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--dry-run`](#uv-lock--dry-run) : Perform a dry run, without writing the lockfile.

```
In dry-run mode, uv will resolve the project's dependencies and report on the resulting changes, but will not write the lockfile to disk.
```

[`--exclude-newer`](#uv-lock--exclude-newer) *exclude-newer* : Limit candidate packages to those that were uploaded prior to the given date.

```
Accepts both RFC 3339 timestamps (e.g., `2006-12-02T02:07:43Z`) and local dates in the same format (e.g., `2006-12-02`) in your system's configured time zone.

May also be set with the `UV_EXCLUDE_NEWER` environment variable.
```

[`--exclude-newer-package`](#uv-lock--exclude-newer-package) *exclude-newer-package* : Limit candidate packages for a specific package to those that were uploaded prior to the given date.

```
Accepts package-date pairs in the format `PACKAGE=DATE`, where `DATE` is an RFC 3339 timestamp (e.g., `2006-12-02T02:07:43Z`) or local date (e.g., `2006-12-02`) in your system's configured time zone.

Can be provided multiple times for different packages.
```

[`--extra-index-url`](#uv-lock--extra-index-url) *extra-index-url* : (Deprecated: use `--index` instead) Extra URLs of package indexes to use, in addition to `--index-url`.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--index-url` (which defaults to PyPI). When multiple `--extra-index-url` flags are provided, earlier values take priority.

May also be set with the `UV_EXTRA_INDEX_URL` environment variable.
```

[`--find-links`](#uv-lock--find-links), `-f` *find-links* : Locations to search for candidate distributions, in addition to those found in the registry indexes.

```
If a path, the target must be a directory that contains packages as wheel files (`.whl`) or source distributions (e.g., `.tar.gz` or `.zip`) at the top level.

If a URL, the page must contain a flat list of links to package files adhering to the formats described above.

May also be set with the `UV_FIND_LINKS` environment variable.
```

[`--fork-strategy`](#uv-lock--fork-strategy) *fork-strategy* : The strategy to use when selecting multiple versions of a given package across Python versions and platforms.

```
By default, uv will optimize for selecting the latest version of each package for each supported Python version (`requires-python`), while minimizing the number of selected versions across platforms.

Under `fewest`, uv will minimize the number of selected versions for each package, preferring older versions that are compatible with a wider range of supported Python versions or platforms.

May also be set with the `UV_FORK_STRATEGY` environment variable.

Possible values:

- `fewest`: Optimize for selecting the fewest number of versions for each package. Older versions may be preferred if they are compatible with a wider range of supported Python versions or platforms
- `requires-python`: Optimize for selecting latest supported version of each package, for each supported Python version
```

[`--help`](#uv-lock--help), `-h` : Display the concise help for this command

[`--index`](#uv-lock--index) *index* : The URLs to use when resolving dependencies, in addition to the default index.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--default-index` (which defaults to PyPI). When multiple `--index` flags are provided, earlier values take priority.

Index names are not supported as values. Relative paths must be disambiguated from index names with `./` or `../` on Unix or `.\\`, `..\\`, `./` or `../` on Windows.

May also be set with the `UV_INDEX` environment variable.
```

[`--index-strategy`](#uv-lock--index-strategy) *index-strategy* : The strategy to use when resolving against multiple index URLs.

```
By default, uv will stop at the first index on which a given package is available, and limit resolutions to those present on that first index (`first-index`). This prevents "dependency confusion" attacks, whereby an attacker can upload a malicious package under the same name to an alternate index.

May also be set with the `UV_INDEX_STRATEGY` environment variable.

Possible values:

- `first-index`: Only use results from the first index that returns a match for a given package name
- `unsafe-first-match`: Search for every package name across all indexes, exhausting the versions from the first index before moving on to the next
- `unsafe-best-match`: Search for every package name across all indexes, preferring the "best" version found. If a package version is in multiple indexes, only look at the entry for the first index
```

[`--index-url`](#uv-lock--index-url), `-i` *index-url* : (Deprecated: use `--default-index` instead) The URL of the Python package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--extra-index-url` flag.

May also be set with the `UV_INDEX_URL` environment variable.
```

[`--keyring-provider`](#uv-lock--keyring-provider) *keyring-provider* : Attempt to use `keyring` for authentication for index URLs.

```
At present, only `--keyring-provider subprocess` is supported, which configures uv to use the `keyring` CLI to handle authentication.

Defaults to `disabled`.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--link-mode`](#uv-lock--link-mode) *link-mode* : The method to use when installing packages from the global cache.

```
This option is only used when building source distributions.

Defaults to `clone` (also known as Copy-on-Write) on macOS, and `hardlink` on Linux and Windows.

WARNING: The use of symlink link mode is discouraged, as they create tight coupling between the cache and the target environment. For example, clearing the cache (`uv cache clean`) will break all installed packages by way of removing the underlying source files. Use symlinks with caution.

May also be set with the `UV_LINK_MODE` environment variable.

Possible values:

- `clone`: Clone (i.e., copy-on-write) packages from the wheel into the `site-packages` directory
- `copy`: Copy packages from the wheel into the `site-packages` directory
- `hardlink`: Hard link packages from the wheel into the `site-packages` directory
- `symlink`: Symbolically link packages from the wheel into the `site-packages` directory
```

[`--managed-python`](#uv-lock--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-lock--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-binary`](#uv-lock--no-binary) : Don't install pre-built wheels.

```
The given packages will be built and installed from source. The resolver will still use pre-built wheels to extract package metadata, if available.

May also be set with the `UV_NO_BINARY` environment variable.
```

[`--no-binary-package`](#uv-lock--no-binary-package) *no-binary-package* : Don't install pre-built wheels for a specific package

```
May also be set with the `UV_NO_BINARY_PACKAGE` environment variable.
```

[`--no-build`](#uv-lock--no-build) : Don't build source distributions.

```
When enabled, resolving will not run arbitrary Python code. The cached wheels of already-built source distributions will be reused, but operations that require building distributions will exit with an error.

May also be set with the `UV_NO_BUILD` environment variable.
```

[`--no-build-isolation`](#uv-lock--no-build-isolation) : Disable isolation when building source distributions.

```
Assumes that build dependencies specified by PEP 518 are already installed.

May also be set with the `UV_NO_BUILD_ISOLATION` environment variable.
```

[`--no-build-isolation-package`](#uv-lock--no-build-isolation-package) *no-build-isolation-package* : Disable isolation when building source distributions for a specific package.

```
Assumes that the packages' build dependencies specified by PEP 518 are already installed.
```

[`--no-build-package`](#uv-lock--no-build-package) *no-build-package* : Don't build source distributions for a specific package

```
May also be set with the `UV_NO_BUILD_PACKAGE` environment variable.
```

[`--no-cache`](#uv-lock--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-lock--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-index`](#uv-lock--no-index) : Ignore the registry index (e.g., PyPI), instead relying on direct URL dependencies and those provided via `--find-links`

[`--no-managed-python`](#uv-lock--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-lock--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-lock--no-python-downloads) : Disable automatic downloads of Python.

[`--no-sources`](#uv-lock--no-sources) : Ignore the `tool.uv.sources` table when resolving dependencies. Used to lock against the standards-compliant, publishable package metadata, as opposed to using any workspace, Git, URL, or local path sources

[`--offline`](#uv-lock--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--prerelease`](#uv-lock--prerelease) *prerelease* : The strategy to use when considering pre-release versions.

```
By default, uv will accept pre-releases for packages that *only* publish pre-releases, along with first-party requirements that contain an explicit pre-release marker in the declared specifiers (`if-necessary-or-explicit`).

May also be set with the `UV_PRERELEASE` environment variable.

Possible values:

- `disallow`: Disallow all pre-release versions
- `allow`: Allow all pre-release versions
- `if-necessary`: Allow pre-release versions if all versions of a package are pre-release
- `explicit`: Allow pre-release versions for first-party packages with explicit pre-release markers in their version requirements
- `if-necessary-or-explicit`: Allow pre-release versions if all versions of a package are pre-release, or if the package has an explicit pre-release marker in its version requirements
```

[`--project`](#uv-lock--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--python`](#uv-lock--python), `-p` *python* : The Python interpreter to use during resolution.

```
A Python interpreter is required for building source distributions to determine package
metadata when there are not wheels.

The interpreter is also used as the fallback value for the minimum Python version if
`requires-python` is not set.

See [uv python](#uv-python) for details on Python discovery and supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--quiet`](#uv-lock--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--refresh`](#uv-lock--refresh) : Refresh all cached data

[`--refresh-package`](#uv-lock--refresh-package) *refresh-package* : Refresh cached data for a specific package

[`--resolution`](#uv-lock--resolution) *resolution* : The strategy to use when selecting between the different compatible versions for a given package requirement.

```
By default, uv will use the latest compatible version of each package (`highest`).

May also be set with the `UV_RESOLUTION` environment variable.

Possible values:

- `highest`: Resolve the highest compatible version of each package
- `lowest`: Resolve the lowest compatible version of each package
- `lowest-direct`: Resolve the lowest compatible version of any direct dependencies, and the highest compatible version of any transitive dependencies
```

[`--script`](#uv-lock--script) *script* : Lock the specified Python script, rather than the current project.

```
If provided, uv will lock the script (based on its inline metadata table, in adherence with PEP 723) to a `.lock` file adjacent to the script itself.
```

[`--upgrade`](#uv-lock--upgrade), `-U` : Allow package upgrades, ignoring pinned versions in any existing output file. Implies `--refresh`

[`--upgrade-package`](#uv-lock--upgrade-package), `-P` *upgrade-package* : Allow upgrades for a specific package, ignoring pinned versions in any existing output file. Implies `--refresh-package`

[`--verbose`](#uv-lock--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

## [uv export](#uv-export)

Export the project's lockfile to an alternate format.

At present, both `requirements.txt` and `pylock.toml` (PEP 751) formats are supported.

The project is re-locked before exporting unless the `--locked` or `--frozen` flag is provided.

uv will search for a project in the current directory or any parent directory. If a project cannot be found, uv will exit with an error.

If operating in a workspace, the root will be exported by default; however, a specific member can be selected using the `--package` option.

### Usage

```
uv export [OPTIONS]

```

### Options

[`--all-extras`](#uv-export--all-extras) : Include all optional dependencies

[`--all-groups`](#uv-export--all-groups) : Include dependencies from all dependency groups.

```
`--no-group` can be used to exclude specific groups.
```

[`--all-packages`](#uv-export--all-packages) : Export the entire workspace.

```
The dependencies for all workspace members will be included in the exported requirements file.

Any extras or groups specified via `--extra`, `--group`, or related options will be applied to all workspace members.
```

[`--allow-insecure-host`](#uv-export--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-export--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-export--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-export--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--config-setting`](#uv-export--config-setting), `--config-settings`, `-C` *config-setting* : Settings to pass to the PEP 517 build backend, specified as `KEY=VALUE` pairs

[`--config-settings-package`](#uv-export--config-settings-package), `--config-settings-package` *config-settings-package* : Settings to pass to the PEP 517 build backend for a specific package, specified as `PACKAGE:KEY=VALUE` pairs

[`--default-index`](#uv-export--default-index) *default-index* : The URL of the default package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--index` flag.

May also be set with the `UV_DEFAULT_INDEX` environment variable.
```

[`--directory`](#uv-export--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--exclude-newer`](#uv-export--exclude-newer) *exclude-newer* : Limit candidate packages to those that were uploaded prior to the given date.

```
Accepts both RFC 3339 timestamps (e.g., `2006-12-02T02:07:43Z`) and local dates in the same format (e.g., `2006-12-02`) in your system's configured time zone.

May also be set with the `UV_EXCLUDE_NEWER` environment variable.
```

[`--exclude-newer-package`](#uv-export--exclude-newer-package) *exclude-newer-package* : Limit candidate packages for a specific package to those that were uploaded prior to the given date.

```
Accepts package-date pairs in the format `PACKAGE=DATE`, where `DATE` is an RFC 3339 timestamp (e.g., `2006-12-02T02:07:43Z`) or local date (e.g., `2006-12-02`) in your system's configured time zone.

Can be provided multiple times for different packages.
```

[`--extra`](#uv-export--extra) *extra* : Include optional dependencies from the specified extra name.

```
May be provided more than once.
```

[`--extra-index-url`](#uv-export--extra-index-url) *extra-index-url* : (Deprecated: use `--index` instead) Extra URLs of package indexes to use, in addition to `--index-url`.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--index-url` (which defaults to PyPI). When multiple `--extra-index-url` flags are provided, earlier values take priority.

May also be set with the `UV_EXTRA_INDEX_URL` environment variable.
```

[`--find-links`](#uv-export--find-links), `-f` *find-links* : Locations to search for candidate distributions, in addition to those found in the registry indexes.

```
If a path, the target must be a directory that contains packages as wheel files (`.whl`) or source distributions (e.g., `.tar.gz` or `.zip`) at the top level.

If a URL, the page must contain a flat list of links to package files adhering to the formats described above.

May also be set with the `UV_FIND_LINKS` environment variable.
```

[`--fork-strategy`](#uv-export--fork-strategy) *fork-strategy* : The strategy to use when selecting multiple versions of a given package across Python versions and platforms.

```
By default, uv will optimize for selecting the latest version of each package for each supported Python version (`requires-python`), while minimizing the number of selected versions across platforms.

Under `fewest`, uv will minimize the number of selected versions for each package, preferring older versions that are compatible with a wider range of supported Python versions or platforms.

May also be set with the `UV_FORK_STRATEGY` environment variable.

Possible values:

- `fewest`: Optimize for selecting the fewest number of versions for each package. Older versions may be preferred if they are compatible with a wider range of supported Python versions or platforms
- `requires-python`: Optimize for selecting latest supported version of each package, for each supported Python version
```

[`--format`](#uv-export--format) *format* : The format to which `uv.lock` should be exported.

```
Supports both `requirements.txt` and `pylock.toml` (PEP 751) output formats.

uv will infer the output format from the file extension of the output file, if provided. Otherwise, defaults to `requirements.txt`.

Possible values:

- `requirements.txt`: Export in `requirements.txt` format
- `pylock.toml`: Export in `pylock.toml` format
```

[`--frozen`](#uv-export--frozen) : Do not update the `uv.lock` before exporting.

```
If a `uv.lock` does not exist, uv will exit with an error.

May also be set with the `UV_FROZEN` environment variable.
```

[`--group`](#uv-export--group) *group* : Include dependencies from the specified dependency group.

```
May be provided multiple times.
```

[`--help`](#uv-export--help), `-h` : Display the concise help for this command

[`--index`](#uv-export--index) *index* : The URLs to use when resolving dependencies, in addition to the default index.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--default-index` (which defaults to PyPI). When multiple `--index` flags are provided, earlier values take priority.

Index names are not supported as values. Relative paths must be disambiguated from index names with `./` or `../` on Unix or `.\\`, `..\\`, `./` or `../` on Windows.

May also be set with the `UV_INDEX` environment variable.
```

[`--index-strategy`](#uv-export--index-strategy) *index-strategy* : The strategy to use when resolving against multiple index URLs.

```
By default, uv will stop at the first index on which a given package is available, and limit resolutions to those present on that first index (`first-index`). This prevents "dependency confusion" attacks, whereby an attacker can upload a malicious package under the same name to an alternate index.

May also be set with the `UV_INDEX_STRATEGY` environment variable.

Possible values:

- `first-index`: Only use results from the first index that returns a match for a given package name
- `unsafe-first-match`: Search for every package name across all indexes, exhausting the versions from the first index before moving on to the next
- `unsafe-best-match`: Search for every package name across all indexes, preferring the "best" version found. If a package version is in multiple indexes, only look at the entry for the first index
```

[`--index-url`](#uv-export--index-url), `-i` *index-url* : (Deprecated: use `--default-index` instead) The URL of the Python package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--extra-index-url` flag.

May also be set with the `UV_INDEX_URL` environment variable.
```

[`--keyring-provider`](#uv-export--keyring-provider) *keyring-provider* : Attempt to use `keyring` for authentication for index URLs.

```
At present, only `--keyring-provider subprocess` is supported, which configures uv to use the `keyring` CLI to handle authentication.

Defaults to `disabled`.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--link-mode`](#uv-export--link-mode) *link-mode* : The method to use when installing packages from the global cache.

```
This option is only used when building source distributions.

Defaults to `clone` (also known as Copy-on-Write) on macOS, and `hardlink` on Linux and Windows.

WARNING: The use of symlink link mode is discouraged, as they create tight coupling between the cache and the target environment. For example, clearing the cache (`uv cache clean`) will break all installed packages by way of removing the underlying source files. Use symlinks with caution.

May also be set with the `UV_LINK_MODE` environment variable.

Possible values:

- `clone`: Clone (i.e., copy-on-write) packages from the wheel into the `site-packages` directory
- `copy`: Copy packages from the wheel into the `site-packages` directory
- `hardlink`: Hard link packages from the wheel into the `site-packages` directory
- `symlink`: Symbolically link packages from the wheel into the `site-packages` directory
```

[`--locked`](#uv-export--locked) : Assert that the `uv.lock` will remain unchanged.

```
Requires that the lockfile is up-to-date. If the lockfile is missing or needs to be updated, uv will exit with an error.

May also be set with the `UV_LOCKED` environment variable.
```

[`--managed-python`](#uv-export--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-export--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-annotate`](#uv-export--no-annotate) : Exclude comment annotations indicating the source of each package

[`--no-binary`](#uv-export--no-binary) : Don't install pre-built wheels.

```
The given packages will be built and installed from source. The resolver will still use pre-built wheels to extract package metadata, if available.

May also be set with the `UV_NO_BINARY` environment variable.
```

[`--no-binary-package`](#uv-export--no-binary-package) *no-binary-package* : Don't install pre-built wheels for a specific package

```
May also be set with the `UV_NO_BINARY_PACKAGE` environment variable.
```

[`--no-build`](#uv-export--no-build) : Don't build source distributions.

```
When enabled, resolving will not run arbitrary Python code. The cached wheels of already-built source distributions will be reused, but operations that require building distributions will exit with an error.

May also be set with the `UV_NO_BUILD` environment variable.
```

[`--no-build-isolation`](#uv-export--no-build-isolation) : Disable isolation when building source distributions.

```
Assumes that build dependencies specified by PEP 518 are already installed.

May also be set with the `UV_NO_BUILD_ISOLATION` environment variable.
```

[`--no-build-isolation-package`](#uv-export--no-build-isolation-package) *no-build-isolation-package* : Disable isolation when building source distributions for a specific package.

```
Assumes that the packages' build dependencies specified by PEP 518 are already installed.
```

[`--no-build-package`](#uv-export--no-build-package) *no-build-package* : Don't build source distributions for a specific package

```
May also be set with the `UV_NO_BUILD_PACKAGE` environment variable.
```

[`--no-cache`](#uv-export--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-export--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-default-groups`](#uv-export--no-default-groups) : Ignore the default dependency groups.

```
uv includes the groups defined in `tool.uv.default-groups` by default. This disables that option, however, specific groups can still be included with `--group`.
```

[`--no-dev`](#uv-export--no-dev) : Disable the development dependency group.

```
This option is an alias of `--no-group dev`. See `--no-default-groups` to disable all default groups instead.

May also be set with the `UV_NO_DEV` environment variable.
```

[`--no-editable`](#uv-export--no-editable) : Export any editable dependencies, including the project and any workspace members, as non-editable

```
May also be set with the `UV_NO_EDITABLE` environment variable.
```

[`--no-emit-local`](#uv-export--no-emit-local), `--no-install-local` : Do not include local path dependencies in the exported requirements.

```
Omits the current project, workspace members, and any other local (path or editable) packages from the export. Only remote/indexed dependencies are written. Useful for Docker and CI flows that want to export and cache third-party dependencies first.
```

[`--no-emit-package`](#uv-export--no-emit-package), `--no-install-package` *no-emit-package* : Do not emit the given package(s).

```
By default, all of the project's dependencies are included in the exported requirements file. The `--no-emit-package` option allows exclusion of specific packages.
```

[`--no-emit-project`](#uv-export--no-emit-project), `--no-install-project` : Do not emit the current project.

```
By default, the current project is included in the exported requirements file with all of its dependencies. The `--no-emit-project` option allows the project to be excluded, but all of its dependencies to remain included.
```

[`--no-emit-workspace`](#uv-export--no-emit-workspace), `--no-install-workspace` : Do not emit any workspace members, including the root project.

```
By default, all workspace members and their dependencies are included in the exported requirements file, with all of their dependencies. The `--no-emit-workspace` option allows exclusion of all the workspace members while retaining their dependencies.
```

[`--no-extra`](#uv-export--no-extra) *no-extra* : Exclude the specified optional dependencies, if `--all-extras` is supplied.

```
May be provided multiple times.
```

[`--no-group`](#uv-export--no-group) *no-group* : Disable the specified dependency group.

```
This option always takes precedence over default groups, `--all-groups`, and `--group`.

May be provided multiple times.
```

[`--no-hashes`](#uv-export--no-hashes) : Omit hashes in the generated output

[`--no-header`](#uv-export--no-header) : Exclude the comment header at the top of the generated output file

[`--no-index`](#uv-export--no-index) : Ignore the registry index (e.g., PyPI), instead relying on direct URL dependencies and those provided via `--find-links`

[`--no-managed-python`](#uv-export--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-export--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-export--no-python-downloads) : Disable automatic downloads of Python.

[`--no-sources`](#uv-export--no-sources) : Ignore the `tool.uv.sources` table when resolving dependencies. Used to lock against the standards-compliant, publishable package metadata, as opposed to using any workspace, Git, URL, or local path sources

[`--offline`](#uv-export--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--only-dev`](#uv-export--only-dev) : Only include the development dependency group.

```
The project and its dependencies will be omitted.

This option is an alias for `--only-group dev`. Implies `--no-default-groups`.
```

[`--only-group`](#uv-export--only-group) *only-group* : Only include dependencies from the specified dependency group.

```
The project and its dependencies will be omitted.

May be provided multiple times. Implies `--no-default-groups`.
```

[`--output-file`](#uv-export--output-file), `-o` *output-file* : Write the exported requirements to the given file

[`--package`](#uv-export--package) *package* : Export the dependencies for a specific package in the workspace.

```
If the workspace member does not exist, uv will exit with an error.
```

[`--prerelease`](#uv-export--prerelease) *prerelease* : The strategy to use when considering pre-release versions.

```
By default, uv will accept pre-releases for packages that *only* publish pre-releases, along with first-party requirements that contain an explicit pre-release marker in the declared specifiers (`if-necessary-or-explicit`).

May also be set with the `UV_PRERELEASE` environment variable.

Possible values:

- `disallow`: Disallow all pre-release versions
- `allow`: Allow all pre-release versions
- `if-necessary`: Allow pre-release versions if all versions of a package are pre-release
- `explicit`: Allow pre-release versions for first-party packages with explicit pre-release markers in their version requirements
- `if-necessary-or-explicit`: Allow pre-release versions if all versions of a package are pre-release, or if the package has an explicit pre-release marker in its version requirements
```

[`--project`](#uv-export--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--prune`](#uv-export--prune) *package* : Prune the given package from the dependency tree.

```
Pruned packages will be excluded from the exported requirements file, as will any dependencies that are no longer required after the pruned package is removed.
```

[`--python`](#uv-export--python), `-p` *python* : The Python interpreter to use during resolution.

```
A Python interpreter is required for building source distributions to determine package
metadata when there are not wheels.

The interpreter is also used as the fallback value for the minimum Python version if
`requires-python` is not set.

See [uv python](#uv-python) for details on Python discovery and supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--quiet`](#uv-export--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--refresh`](#uv-export--refresh) : Refresh all cached data

[`--refresh-package`](#uv-export--refresh-package) *refresh-package* : Refresh cached data for a specific package

[`--resolution`](#uv-export--resolution) *resolution* : The strategy to use when selecting between the different compatible versions for a given package requirement.

```
By default, uv will use the latest compatible version of each package (`highest`).

May also be set with the `UV_RESOLUTION` environment variable.

Possible values:

- `highest`: Resolve the highest compatible version of each package
- `lowest`: Resolve the lowest compatible version of each package
- `lowest-direct`: Resolve the lowest compatible version of any direct dependencies, and the highest compatible version of any transitive dependencies
```

[`--script`](#uv-export--script) *script* : Export the dependencies for the specified PEP 723 Python script, rather than the current project.

```
If provided, uv will resolve the dependencies based on its inline metadata table, in adherence with PEP 723.
```

[`--upgrade`](#uv-export--upgrade), `-U` : Allow package upgrades, ignoring pinned versions in any existing output file. Implies `--refresh`

[`--upgrade-package`](#uv-export--upgrade-package), `-P` *upgrade-package* : Allow upgrades for a specific package, ignoring pinned versions in any existing output file. Implies `--refresh-package`

[`--verbose`](#uv-export--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

## [uv tree](#uv-tree)

Display the project's dependency tree

### Usage

```
uv tree [OPTIONS]

```

### Options

[`--all-groups`](#uv-tree--all-groups) : Include dependencies from all dependency groups.

```
`--no-group` can be used to exclude specific groups.
```

[`--allow-insecure-host`](#uv-tree--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-tree--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-tree--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-tree--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--config-setting`](#uv-tree--config-setting), `--config-settings`, `-C` *config-setting* : Settings to pass to the PEP 517 build backend, specified as `KEY=VALUE` pairs

[`--config-settings-package`](#uv-tree--config-settings-package), `--config-settings-package` *config-settings-package* : Settings to pass to the PEP 517 build backend for a specific package, specified as `PACKAGE:KEY=VALUE` pairs

[`--default-index`](#uv-tree--default-index) *default-index* : The URL of the default package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--index` flag.

May also be set with the `UV_DEFAULT_INDEX` environment variable.
```

[`--depth`](#uv-tree--depth), `-d` *depth* : Maximum display depth of the dependency tree

```
[default: 255]
```

[`--directory`](#uv-tree--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--exclude-newer`](#uv-tree--exclude-newer) *exclude-newer* : Limit candidate packages to those that were uploaded prior to the given date.

```
Accepts both RFC 3339 timestamps (e.g., `2006-12-02T02:07:43Z`) and local dates in the same format (e.g., `2006-12-02`) in your system's configured time zone.

May also be set with the `UV_EXCLUDE_NEWER` environment variable.
```

[`--exclude-newer-package`](#uv-tree--exclude-newer-package) *exclude-newer-package* : Limit candidate packages for a specific package to those that were uploaded prior to the given date.

```
Accepts package-date pairs in the format `PACKAGE=DATE`, where `DATE` is an RFC 3339 timestamp (e.g., `2006-12-02T02:07:43Z`) or local date (e.g., `2006-12-02`) in your system's configured time zone.

Can be provided multiple times for different packages.
```

[`--extra-index-url`](#uv-tree--extra-index-url) *extra-index-url* : (Deprecated: use `--index` instead) Extra URLs of package indexes to use, in addition to `--index-url`.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--index-url` (which defaults to PyPI). When multiple `--extra-index-url` flags are provided, earlier values take priority.

May also be set with the `UV_EXTRA_INDEX_URL` environment variable.
```

[`--find-links`](#uv-tree--find-links), `-f` *find-links* : Locations to search for candidate distributions, in addition to those found in the registry indexes.

```
If a path, the target must be a directory that contains packages as wheel files (`.whl`) or source distributions (e.g., `.tar.gz` or `.zip`) at the top level.

If a URL, the page must contain a flat list of links to package files adhering to the formats described above.

May also be set with the `UV_FIND_LINKS` environment variable.
```

[`--fork-strategy`](#uv-tree--fork-strategy) *fork-strategy* : The strategy to use when selecting multiple versions of a given package across Python versions and platforms.

```
By default, uv will optimize for selecting the latest version of each package for each supported Python version (`requires-python`), while minimizing the number of selected versions across platforms.

Under `fewest`, uv will minimize the number of selected versions for each package, preferring older versions that are compatible with a wider range of supported Python versions or platforms.

May also be set with the `UV_FORK_STRATEGY` environment variable.

Possible values:

- `fewest`: Optimize for selecting the fewest number of versions for each package. Older versions may be preferred if they are compatible with a wider range of supported Python versions or platforms
- `requires-python`: Optimize for selecting latest supported version of each package, for each supported Python version
```

[`--frozen`](#uv-tree--frozen) : Display the requirements without locking the project.

```
If the lockfile is missing, uv will exit with an error.

May also be set with the `UV_FROZEN` environment variable.
```

[`--group`](#uv-tree--group) *group* : Include dependencies from the specified dependency group.

```
May be provided multiple times.
```

[`--help`](#uv-tree--help), `-h` : Display the concise help for this command

[`--index`](#uv-tree--index) *index* : The URLs to use when resolving dependencies, in addition to the default index.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--default-index` (which defaults to PyPI). When multiple `--index` flags are provided, earlier values take priority.

Index names are not supported as values. Relative paths must be disambiguated from index names with `./` or `../` on Unix or `.\\`, `..\\`, `./` or `../` on Windows.

May also be set with the `UV_INDEX` environment variable.
```

[`--index-strategy`](#uv-tree--index-strategy) *index-strategy* : The strategy to use when resolving against multiple index URLs.

```
By default, uv will stop at the first index on which a given package is available, and limit resolutions to those present on that first index (`first-index`). This prevents "dependency confusion" attacks, whereby an attacker can upload a malicious package under the same name to an alternate index.

May also be set with the `UV_INDEX_STRATEGY` environment variable.

Possible values:

- `first-index`: Only use results from the first index that returns a match for a given package name
- `unsafe-first-match`: Search for every package name across all indexes, exhausting the versions from the first index before moving on to the next
- `unsafe-best-match`: Search for every package name across all indexes, preferring the "best" version found. If a package version is in multiple indexes, only look at the entry for the first index
```

[`--index-url`](#uv-tree--index-url), `-i` *index-url* : (Deprecated: use `--default-index` instead) The URL of the Python package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--extra-index-url` flag.

May also be set with the `UV_INDEX_URL` environment variable.
```

[`--invert`](#uv-tree--invert), `--reverse` : Show the reverse dependencies for the given package. This flag will invert the tree and display the packages that depend on the given package

[`--keyring-provider`](#uv-tree--keyring-provider) *keyring-provider* : Attempt to use `keyring` for authentication for index URLs.

```
At present, only `--keyring-provider subprocess` is supported, which configures uv to use the `keyring` CLI to handle authentication.

Defaults to `disabled`.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--link-mode`](#uv-tree--link-mode) *link-mode* : The method to use when installing packages from the global cache.

```
This option is only used when building source distributions.

Defaults to `clone` (also known as Copy-on-Write) on macOS, and `hardlink` on Linux and Windows.

WARNING: The use of symlink link mode is discouraged, as they create tight coupling between the cache and the target environment. For example, clearing the cache (`uv cache clean`) will break all installed packages by way of removing the underlying source files. Use symlinks with caution.

May also be set with the `UV_LINK_MODE` environment variable.

Possible values:

- `clone`: Clone (i.e., copy-on-write) packages from the wheel into the `site-packages` directory
- `copy`: Copy packages from the wheel into the `site-packages` directory
- `hardlink`: Hard link packages from the wheel into the `site-packages` directory
- `symlink`: Symbolically link packages from the wheel into the `site-packages` directory
```

[`--locked`](#uv-tree--locked) : Assert that the `uv.lock` will remain unchanged.

```
Requires that the lockfile is up-to-date. If the lockfile is missing or needs to be updated, uv will exit with an error.

May also be set with the `UV_LOCKED` environment variable.
```

[`--managed-python`](#uv-tree--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-tree--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-binary`](#uv-tree--no-binary) : Don't install pre-built wheels.

```
The given packages will be built and installed from source. The resolver will still use pre-built wheels to extract package metadata, if available.

May also be set with the `UV_NO_BINARY` environment variable.
```

[`--no-binary-package`](#uv-tree--no-binary-package) *no-binary-package* : Don't install pre-built wheels for a specific package

```
May also be set with the `UV_NO_BINARY_PACKAGE` environment variable.
```

[`--no-build`](#uv-tree--no-build) : Don't build source distributions.

```
When enabled, resolving will not run arbitrary Python code. The cached wheels of already-built source distributions will be reused, but operations that require building distributions will exit with an error.

May also be set with the `UV_NO_BUILD` environment variable.
```

[`--no-build-isolation`](#uv-tree--no-build-isolation) : Disable isolation when building source distributions.

```
Assumes that build dependencies specified by PEP 518 are already installed.

May also be set with the `UV_NO_BUILD_ISOLATION` environment variable.
```

[`--no-build-isolation-package`](#uv-tree--no-build-isolation-package) *no-build-isolation-package* : Disable isolation when building source distributions for a specific package.

```
Assumes that the packages' build dependencies specified by PEP 518 are already installed.
```

[`--no-build-package`](#uv-tree--no-build-package) *no-build-package* : Don't build source distributions for a specific package

```
May also be set with the `UV_NO_BUILD_PACKAGE` environment variable.
```

[`--no-cache`](#uv-tree--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-tree--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-dedupe`](#uv-tree--no-dedupe) : Do not de-duplicate repeated dependencies. Usually, when a package has already displayed its dependencies, further occurrences will not re-display its dependencies, and will include a (\*) to indicate it has already been shown. This flag will cause those duplicates to be repeated

[`--no-default-groups`](#uv-tree--no-default-groups) : Ignore the default dependency groups.

```
uv includes the groups defined in `tool.uv.default-groups` by default. This disables that option, however, specific groups can still be included with `--group`.
```

[`--no-dev`](#uv-tree--no-dev) : Disable the development dependency group.

```
This option is an alias of `--no-group dev`. See `--no-default-groups` to disable all default groups instead.

May also be set with the `UV_NO_DEV` environment variable.
```

[`--no-group`](#uv-tree--no-group) *no-group* : Disable the specified dependency group.

```
This option always takes precedence over default groups, `--all-groups`, and `--group`.

May be provided multiple times.
```

[`--no-index`](#uv-tree--no-index) : Ignore the registry index (e.g., PyPI), instead relying on direct URL dependencies and those provided via `--find-links`

[`--no-managed-python`](#uv-tree--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-tree--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-tree--no-python-downloads) : Disable automatic downloads of Python.

[`--no-sources`](#uv-tree--no-sources) : Ignore the `tool.uv.sources` table when resolving dependencies. Used to lock against the standards-compliant, publishable package metadata, as opposed to using any workspace, Git, URL, or local path sources

[`--offline`](#uv-tree--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--only-dev`](#uv-tree--only-dev) : Only include the development dependency group.

```
The project and its dependencies will be omitted.

This option is an alias for `--only-group dev`. Implies `--no-default-groups`.
```

[`--only-group`](#uv-tree--only-group) *only-group* : Only include dependencies from the specified dependency group.

```
The project and its dependencies will be omitted.

May be provided multiple times. Implies `--no-default-groups`.
```

[`--outdated`](#uv-tree--outdated) : Show the latest available version of each package in the tree

[`--package`](#uv-tree--package) *package* : Display only the specified packages

[`--prerelease`](#uv-tree--prerelease) *prerelease* : The strategy to use when considering pre-release versions.

```
By default, uv will accept pre-releases for packages that *only* publish pre-releases, along with first-party requirements that contain an explicit pre-release marker in the declared specifiers (`if-necessary-or-explicit`).

May also be set with the `UV_PRERELEASE` environment variable.

Possible values:

- `disallow`: Disallow all pre-release versions
- `allow`: Allow all pre-release versions
- `if-necessary`: Allow pre-release versions if all versions of a package are pre-release
- `explicit`: Allow pre-release versions for first-party packages with explicit pre-release markers in their version requirements
- `if-necessary-or-explicit`: Allow pre-release versions if all versions of a package are pre-release, or if the package has an explicit pre-release marker in its version requirements
```

[`--project`](#uv-tree--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--prune`](#uv-tree--prune) *prune* : Prune the given package from the display of the dependency tree

[`--python`](#uv-tree--python), `-p` *python* : The Python interpreter to use for locking and filtering.

```
By default, the tree is filtered to match the platform as reported by the Python
interpreter. Use `--universal` to display the tree for all platforms, or use
`--python-version` or `--python-platform` to override a subset of markers.

See [uv python](#uv-python) for details on Python discovery and supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--python-platform`](#uv-tree--python-platform) *python-platform* : The platform to use when filtering the tree.

```
For example, pass `--platform windows` to display the dependencies that would be included when installing on Windows.

Represented as a "target triple", a string that describes the target platform in terms of its CPU, vendor, and operating system name, like `x86_64-unknown-linux-gnu` or `aarch64-apple-darwin`.

Possible values:

- `windows`: An alias for `x86_64-pc-windows-msvc`, the default target for Windows
- `linux`: An alias for `x86_64-unknown-linux-gnu`, the default target for Linux
- `macos`: An alias for `aarch64-apple-darwin`, the default target for macOS
- `x86_64-pc-windows-msvc`: A 64-bit x86 Windows target
- `aarch64-pc-windows-msvc`: An ARM64 Windows target
- `i686-pc-windows-msvc`: A 32-bit x86 Windows target
- `x86_64-unknown-linux-gnu`: An x86 Linux target. Equivalent to `x86_64-manylinux_2_28`
- `aarch64-apple-darwin`: An ARM-based macOS target, as seen on Apple Silicon devices
- `x86_64-apple-darwin`: An x86 macOS target
- `aarch64-unknown-linux-gnu`: An ARM64 Linux target. Equivalent to `aarch64-manylinux_2_28`
- `aarch64-unknown-linux-musl`: An ARM64 Linux target
- `x86_64-unknown-linux-musl`: An `x86_64` Linux target
- `riscv64-unknown-linux`: A RISCV64 Linux target
- `x86_64-manylinux2014`: An `x86_64` target for the `manylinux2014` platform. Equivalent to `x86_64-manylinux_2_17`
- `x86_64-manylinux_2_17`: An `x86_64` target for the `manylinux_2_17` platform
- `x86_64-manylinux_2_28`: An `x86_64` target for the `manylinux_2_28` platform
- `x86_64-manylinux_2_31`: An `x86_64` target for the `manylinux_2_31` platform
- `x86_64-manylinux_2_32`: An `x86_64` target for the `manylinux_2_32` platform
- `x86_64-manylinux_2_33`: An `x86_64` target for the `manylinux_2_33` platform
- `x86_64-manylinux_2_34`: An `x86_64` target for the `manylinux_2_34` platform
- `x86_64-manylinux_2_35`: An `x86_64` target for the `manylinux_2_35` platform
- `x86_64-manylinux_2_36`: An `x86_64` target for the `manylinux_2_36` platform
- `x86_64-manylinux_2_37`: An `x86_64` target for the `manylinux_2_37` platform
- `x86_64-manylinux_2_38`: An `x86_64` target for the `manylinux_2_38` platform
- `x86_64-manylinux_2_39`: An `x86_64` target for the `manylinux_2_39` platform
- `x86_64-manylinux_2_40`: An `x86_64` target for the `manylinux_2_40` platform
- `aarch64-manylinux2014`: An ARM64 target for the `manylinux2014` platform. Equivalent to `aarch64-manylinux_2_17`
- `aarch64-manylinux_2_17`: An ARM64 target for the `manylinux_2_17` platform
- `aarch64-manylinux_2_28`: An ARM64 target for the `manylinux_2_28` platform
- `aarch64-manylinux_2_31`: An ARM64 target for the `manylinux_2_31` platform
- `aarch64-manylinux_2_32`: An ARM64 target for the `manylinux_2_32` platform
- `aarch64-manylinux_2_33`: An ARM64 target for the `manylinux_2_33` platform
- `aarch64-manylinux_2_34`: An ARM64 target for the `manylinux_2_34` platform
- `aarch64-manylinux_2_35`: An ARM64 target for the `manylinux_2_35` platform
- `aarch64-manylinux_2_36`: An ARM64 target for the `manylinux_2_36` platform
- `aarch64-manylinux_2_37`: An ARM64 target for the `manylinux_2_37` platform
- `aarch64-manylinux_2_38`: An ARM64 target for the `manylinux_2_38` platform
- `aarch64-manylinux_2_39`: An ARM64 target for the `manylinux_2_39` platform
- `aarch64-manylinux_2_40`: An ARM64 target for the `manylinux_2_40` platform
- `aarch64-linux-android`: An ARM64 Android target
- `x86_64-linux-android`: An `x86_64` Android target
- `wasm32-pyodide2024`: A wasm32 target using the Pyodide 2024 platform. Meant for use with Python 3.12
- `arm64-apple-ios`: An ARM64 target for iOS device
- `arm64-apple-ios-simulator`: An ARM64 target for iOS simulator
- `x86_64-apple-ios-simulator`: An `x86_64` target for iOS simulator
```

[`--python-version`](#uv-tree--python-version) *python-version* : The Python version to use when filtering the tree.

```
For example, pass `--python-version 3.10` to display the dependencies that would be included when installing on Python 3.10.

Defaults to the version of the discovered Python interpreter.
```

[`--quiet`](#uv-tree--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--resolution`](#uv-tree--resolution) *resolution* : The strategy to use when selecting between the different compatible versions for a given package requirement.

```
By default, uv will use the latest compatible version of each package (`highest`).

May also be set with the `UV_RESOLUTION` environment variable.

Possible values:

- `highest`: Resolve the highest compatible version of each package
- `lowest`: Resolve the lowest compatible version of each package
- `lowest-direct`: Resolve the lowest compatible version of any direct dependencies, and the highest compatible version of any transitive dependencies
```

[`--script`](#uv-tree--script) *script* : Show the dependency tree the specified PEP 723 Python script, rather than the current project.

```
If provided, uv will resolve the dependencies based on its inline metadata table, in adherence with PEP 723.
```

[`--show-sizes`](#uv-tree--show-sizes) : Show compressed wheel sizes for packages in the tree

[`--universal`](#uv-tree--universal) : Show a platform-independent dependency tree.

```
Shows resolved package versions for all Python versions and platforms, rather than filtering to those that are relevant for the current environment.

Multiple versions may be shown for a each package.
```

[`--upgrade`](#uv-tree--upgrade), `-U` : Allow package upgrades, ignoring pinned versions in any existing output file. Implies `--refresh`

[`--upgrade-package`](#uv-tree--upgrade-package), `-P` *upgrade-package* : Allow upgrades for a specific package, ignoring pinned versions in any existing output file. Implies `--refresh-package`

[`--verbose`](#uv-tree--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

## [uv format](#uv-format)

Format Python code in the project.

Formats Python code using the Ruff formatter. By default, all Python files in the project are formatted. This command has the same behavior as running `ruff format` in the project root.

To check if files are formatted without modifying them, use `--check`. To see a diff of formatting changes, use `--diff`.

Additional arguments can be passed to Ruff after `--`.

### Usage

```
uv format [OPTIONS] [-- <EXTRA_ARGS>...]

```

### Arguments

[EXTRA_ARGS](#uv-format--extra_args) : Additional arguments to pass to Ruff.

```
For example, use `uv format -- --line-length 100` to set the line length or `uv format -- src/module/foo.py` to format a specific file.
```

### Options

[`--allow-insecure-host`](#uv-format--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-format--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--check`](#uv-format--check) : Check if files are formatted without applying changes

[`--color`](#uv-format--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-format--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--diff`](#uv-format--diff) : Show a diff of formatting changes without applying them.

```
Implies `--check`.
```

[`--directory`](#uv-format--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--help`](#uv-format--help), `-h` : Display the concise help for this command

[`--managed-python`](#uv-format--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-format--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-format--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-format--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-format--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-format--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-project`](#uv-format--no-project) : Avoid discovering a project or workspace.

```
Instead of running the formatter in the context of the current project, run it in the context of the current directory. This is useful when the current directory is not a project.
```

[`--no-python-downloads`](#uv-format--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-format--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-format--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--quiet`](#uv-format--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--verbose`](#uv-format--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

[`--version`](#uv-format--version) *version* : The version of Ruff to use for formatting.

```
By default, a version of Ruff pinned by uv will be used.
```

## [uv tool](#uv-tool)

Run and install commands provided by Python packages

### Usage

```
uv tool [OPTIONS] <COMMAND>

```

### Commands

[`uv tool run`](#uv-tool-run) : Run a command provided by a Python package

[`uv tool install`](#uv-tool-install) : Install commands provided by a Python package

[`uv tool upgrade`](#uv-tool-upgrade) : Upgrade installed tools

[`uv tool list`](#uv-tool-list) : List installed tools

[`uv tool uninstall`](#uv-tool-uninstall) : Uninstall a tool

[`uv tool update-shell`](#uv-tool-update-shell) : Ensure that the tool executable directory is on the `PATH`

[`uv tool dir`](#uv-tool-dir) : Show the path to the uv tools directory

### [uv tool run](#uv-tool-run)

Run a command provided by a Python package.

By default, the package to install is assumed to match the command name.

The name of the command can include an exact version in the format `<package>@<version>`, e.g., `uv tool run ruff@0.3.0`. If more complex version specification is desired or if the command is provided by a different package, use `--from`.

`uvx` can be used to invoke Python, e.g., with `uvx python` or `uvx python@<version>`. A Python interpreter will be started in an isolated virtual environment.

If the tool was previously installed, i.e., via `uv tool install`, the installed version will be used unless a version is requested or the `--isolated` flag is used.

`uvx` is provided as a convenient alias for `uv tool run`, their behavior is identical.

If no command is provided, the installed tools are displayed.

Packages are installed into an ephemeral virtual environment in the uv cache directory.

### Usage

```
uv tool run [OPTIONS] [COMMAND]

```

### Options

[`--allow-insecure-host`](#uv-tool-run--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--build-constraints`](#uv-tool-run--build-constraints), `--build-constraint`, `-b` *build-constraints* : Constrain build dependencies using the given requirements files when building source distributions.

```
Constraints files are `requirements.txt`-like files that only control the *version* of a requirement that's installed. However, including a package in a constraints file will *not* trigger the installation of that package.

May also be set with the `UV_BUILD_CONSTRAINT` environment variable.
```

[`--cache-dir`](#uv-tool-run--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-tool-run--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--compile-bytecode`](#uv-tool-run--compile-bytecode), `--compile` : Compile Python files to bytecode after installation.

```
By default, uv does not compile Python (`.py`) files to bytecode (`__pycache__/*.pyc`); instead, compilation is performed lazily the first time a module is imported. For use-cases in which start time is critical, such as CLI applications and Docker containers, this option can be enabled to trade longer installation times for faster start times.

When enabled, uv will process the entire site-packages directory (including packages that are not being modified by the current operation) for consistency. Like pip, it will also ignore errors.

May also be set with the `UV_COMPILE_BYTECODE` environment variable.
```

[`--config-file`](#uv-tool-run--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--config-setting`](#uv-tool-run--config-setting), `--config-settings`, `-C` *config-setting* : Settings to pass to the PEP 517 build backend, specified as `KEY=VALUE` pairs

[`--config-settings-package`](#uv-tool-run--config-settings-package), `--config-settings-package` *config-settings-package* : Settings to pass to the PEP 517 build backend for a specific package, specified as `PACKAGE:KEY=VALUE` pairs

[`--constraints`](#uv-tool-run--constraints), `--constraint`, `-c` *constraints* : Constrain versions using the given requirements files.

```
Constraints files are `requirements.txt`-like files that only control the *version* of a requirement that's installed. However, including a package in a constraints file will *not* trigger the installation of that package.

This is equivalent to pip's `--constraint` option.

May also be set with the `UV_CONSTRAINT` environment variable.
```

[`--default-index`](#uv-tool-run--default-index) *default-index* : The URL of the default package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--index` flag.

May also be set with the `UV_DEFAULT_INDEX` environment variable.
```

[`--directory`](#uv-tool-run--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--env-file`](#uv-tool-run--env-file) *env-file* : Load environment variables from a `.env` file.

```
Can be provided multiple times, with subsequent files overriding values defined in previous files.

May also be set with the `UV_ENV_FILE` environment variable.
```

[`--exclude-newer`](#uv-tool-run--exclude-newer) *exclude-newer* : Limit candidate packages to those that were uploaded prior to the given date.

```
Accepts both RFC 3339 timestamps (e.g., `2006-12-02T02:07:43Z`) and local dates in the same format (e.g., `2006-12-02`) in your system's configured time zone.

May also be set with the `UV_EXCLUDE_NEWER` environment variable.
```

[`--exclude-newer-package`](#uv-tool-run--exclude-newer-package) *exclude-newer-package* : Limit candidate packages for specific packages to those that were uploaded prior to the given date.

```
Accepts package-date pairs in the format `PACKAGE=DATE`, where `DATE` is an RFC 3339 timestamp (e.g., `2006-12-02T02:07:43Z`) or local date (e.g., `2006-12-02`) in your system's configured time zone.

Can be provided multiple times for different packages.
```

[`--extra-index-url`](#uv-tool-run--extra-index-url) *extra-index-url* : (Deprecated: use `--index` instead) Extra URLs of package indexes to use, in addition to `--index-url`.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--index-url` (which defaults to PyPI). When multiple `--extra-index-url` flags are provided, earlier values take priority.

May also be set with the `UV_EXTRA_INDEX_URL` environment variable.
```

[`--find-links`](#uv-tool-run--find-links), `-f` *find-links* : Locations to search for candidate distributions, in addition to those found in the registry indexes.

```
If a path, the target must be a directory that contains packages as wheel files (`.whl`) or source distributions (e.g., `.tar.gz` or `.zip`) at the top level.

If a URL, the page must contain a flat list of links to package files adhering to the formats described above.

May also be set with the `UV_FIND_LINKS` environment variable.
```

[`--fork-strategy`](#uv-tool-run--fork-strategy) *fork-strategy* : The strategy to use when selecting multiple versions of a given package across Python versions and platforms.

```
By default, uv will optimize for selecting the latest version of each package for each supported Python version (`requires-python`), while minimizing the number of selected versions across platforms.

Under `fewest`, uv will minimize the number of selected versions for each package, preferring older versions that are compatible with a wider range of supported Python versions or platforms.

May also be set with the `UV_FORK_STRATEGY` environment variable.

Possible values:

- `fewest`: Optimize for selecting the fewest number of versions for each package. Older versions may be preferred if they are compatible with a wider range of supported Python versions or platforms
- `requires-python`: Optimize for selecting latest supported version of each package, for each supported Python version
```

[`--from`](#uv-tool-run--from) *from* : Use the given package to provide the command.

```
By default, the package name is assumed to match the command name.
```

[`--help`](#uv-tool-run--help), `-h` : Display the concise help for this command

[`--index`](#uv-tool-run--index) *index* : The URLs to use when resolving dependencies, in addition to the default index.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--default-index` (which defaults to PyPI). When multiple `--index` flags are provided, earlier values take priority.

Index names are not supported as values. Relative paths must be disambiguated from index names with `./` or `../` on Unix or `.\\`, `..\\`, `./` or `../` on Windows.

May also be set with the `UV_INDEX` environment variable.
```

[`--index-strategy`](#uv-tool-run--index-strategy) *index-strategy* : The strategy to use when resolving against multiple index URLs.

```
By default, uv will stop at the first index on which a given package is available, and limit resolutions to those present on that first index (`first-index`). This prevents "dependency confusion" attacks, whereby an attacker can upload a malicious package under the same name to an alternate index.

May also be set with the `UV_INDEX_STRATEGY` environment variable.

Possible values:

- `first-index`: Only use results from the first index that returns a match for a given package name
- `unsafe-first-match`: Search for every package name across all indexes, exhausting the versions from the first index before moving on to the next
- `unsafe-best-match`: Search for every package name across all indexes, preferring the "best" version found. If a package version is in multiple indexes, only look at the entry for the first index
```

[`--index-url`](#uv-tool-run--index-url), `-i` *index-url* : (Deprecated: use `--default-index` instead) The URL of the Python package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--extra-index-url` flag.

May also be set with the `UV_INDEX_URL` environment variable.
```

[`--isolated`](#uv-tool-run--isolated) : Run the tool in an isolated virtual environment, ignoring any already-installed tools

```
May also be set with the `UV_ISOLATED` environment variable.
```

[`--keyring-provider`](#uv-tool-run--keyring-provider) *keyring-provider* : Attempt to use `keyring` for authentication for index URLs.

```
At present, only `--keyring-provider subprocess` is supported, which configures uv to use the `keyring` CLI to handle authentication.

Defaults to `disabled`.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--link-mode`](#uv-tool-run--link-mode) *link-mode* : The method to use when installing packages from the global cache.

```
Defaults to `clone` (also known as Copy-on-Write) on macOS, and `hardlink` on Linux and Windows.

WARNING: The use of symlink link mode is discouraged, as they create tight coupling between the cache and the target environment. For example, clearing the cache (`uv cache clean`) will break all installed packages by way of removing the underlying source files. Use symlinks with caution.

May also be set with the `UV_LINK_MODE` environment variable.

Possible values:

- `clone`: Clone (i.e., copy-on-write) packages from the wheel into the `site-packages` directory
- `copy`: Copy packages from the wheel into the `site-packages` directory
- `hardlink`: Hard link packages from the wheel into the `site-packages` directory
- `symlink`: Symbolically link packages from the wheel into the `site-packages` directory
```

[`--managed-python`](#uv-tool-run--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-tool-run--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-binary`](#uv-tool-run--no-binary) : Don't install pre-built wheels.

```
The given packages will be built and installed from source. The resolver will still use pre-built wheels to extract package metadata, if available.

May also be set with the `UV_NO_BINARY` environment variable.
```

[`--no-binary-package`](#uv-tool-run--no-binary-package) *no-binary-package* : Don't install pre-built wheels for a specific package

```
May also be set with the `UV_NO_BINARY_PACKAGE` environment variable.
```

[`--no-build`](#uv-tool-run--no-build) : Don't build source distributions.

```
When enabled, resolving will not run arbitrary Python code. The cached wheels of already-built source distributions will be reused, but operations that require building distributions will exit with an error.

May also be set with the `UV_NO_BUILD` environment variable.
```

[`--no-build-isolation`](#uv-tool-run--no-build-isolation) : Disable isolation when building source distributions.

```
Assumes that build dependencies specified by PEP 518 are already installed.

May also be set with the `UV_NO_BUILD_ISOLATION` environment variable.
```

[`--no-build-isolation-package`](#uv-tool-run--no-build-isolation-package) *no-build-isolation-package* : Disable isolation when building source distributions for a specific package.

```
Assumes that the packages' build dependencies specified by PEP 518 are already installed.
```

[`--no-build-package`](#uv-tool-run--no-build-package) *no-build-package* : Don't build source distributions for a specific package

```
May also be set with the `UV_NO_BUILD_PACKAGE` environment variable.
```

[`--no-cache`](#uv-tool-run--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-tool-run--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-env-file`](#uv-tool-run--no-env-file) : Avoid reading environment variables from a `.env` file

```
May also be set with the `UV_NO_ENV_FILE` environment variable.
```

[`--no-index`](#uv-tool-run--no-index) : Ignore the registry index (e.g., PyPI), instead relying on direct URL dependencies and those provided via `--find-links`

[`--no-managed-python`](#uv-tool-run--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-tool-run--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-tool-run--no-python-downloads) : Disable automatic downloads of Python.

[`--no-sources`](#uv-tool-run--no-sources) : Ignore the `tool.uv.sources` table when resolving dependencies. Used to lock against the standards-compliant, publishable package metadata, as opposed to using any workspace, Git, URL, or local path sources

[`--offline`](#uv-tool-run--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--overrides`](#uv-tool-run--overrides), `--override` *overrides* : Override versions using the given requirements files.

```
Overrides files are `requirements.txt`-like files that force a specific version of a requirement to be installed, regardless of the requirements declared by any constituent package, and regardless of whether this would be considered an invalid resolution.

While constraints are *additive*, in that they're combined with the requirements of the constituent packages, overrides are *absolute*, in that they completely replace the requirements of the constituent packages.

May also be set with the `UV_OVERRIDE` environment variable.
```

[`--prerelease`](#uv-tool-run--prerelease) *prerelease* : The strategy to use when considering pre-release versions.

```
By default, uv will accept pre-releases for packages that *only* publish pre-releases, along with first-party requirements that contain an explicit pre-release marker in the declared specifiers (`if-necessary-or-explicit`).

May also be set with the `UV_PRERELEASE` environment variable.

Possible values:

- `disallow`: Disallow all pre-release versions
- `allow`: Allow all pre-release versions
- `if-necessary`: Allow pre-release versions if all versions of a package are pre-release
- `explicit`: Allow pre-release versions for first-party packages with explicit pre-release markers in their version requirements
- `if-necessary-or-explicit`: Allow pre-release versions if all versions of a package are pre-release, or if the package has an explicit pre-release marker in its version requirements
```

[`--project`](#uv-tool-run--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--python`](#uv-tool-run--python), `-p` *python* : The Python interpreter to use to build the run environment.

```
See [uv python](#uv-python) for details on Python discovery and supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--python-platform`](#uv-tool-run--python-platform) *python-platform* : The platform for which requirements should be installed.

```
Represented as a "target triple", a string that describes the target platform in terms of its CPU, vendor, and operating system name, like `x86_64-unknown-linux-gnu` or `aarch64-apple-darwin`.

When targeting macOS (Darwin), the default minimum version is `13.0`. Use `MACOSX_DEPLOYMENT_TARGET` to specify a different minimum version, e.g., `14.0`.

When targeting iOS, the default minimum version is `13.0`. Use `IPHONEOS_DEPLOYMENT_TARGET` to specify a different minimum version, e.g., `14.0`.

When targeting Android, the default minimum Android API level is `24`. Use `ANDROID_API_LEVEL` to specify a different minimum version, e.g., `26`.

WARNING: When specified, uv will select wheels that are compatible with the *target* platform; as a result, the installed distributions may not be compatible with the *current* platform. Conversely, any distributions that are built from source may be incompatible with the *target* platform, as they will be built for the *current* platform. The `--python-platform` option is intended for advanced use cases.

Possible values:

- `windows`: An alias for `x86_64-pc-windows-msvc`, the default target for Windows
- `linux`: An alias for `x86_64-unknown-linux-gnu`, the default target for Linux
- `macos`: An alias for `aarch64-apple-darwin`, the default target for macOS
- `x86_64-pc-windows-msvc`: A 64-bit x86 Windows target
- `aarch64-pc-windows-msvc`: An ARM64 Windows target
- `i686-pc-windows-msvc`: A 32-bit x86 Windows target
- `x86_64-unknown-linux-gnu`: An x86 Linux target. Equivalent to `x86_64-manylinux_2_28`
- `aarch64-apple-darwin`: An ARM-based macOS target, as seen on Apple Silicon devices
- `x86_64-apple-darwin`: An x86 macOS target
- `aarch64-unknown-linux-gnu`: An ARM64 Linux target. Equivalent to `aarch64-manylinux_2_28`
- `aarch64-unknown-linux-musl`: An ARM64 Linux target
- `x86_64-unknown-linux-musl`: An `x86_64` Linux target
- `riscv64-unknown-linux`: A RISCV64 Linux target
- `x86_64-manylinux2014`: An `x86_64` target for the `manylinux2014` platform. Equivalent to `x86_64-manylinux_2_17`
- `x86_64-manylinux_2_17`: An `x86_64` target for the `manylinux_2_17` platform
- `x86_64-manylinux_2_28`: An `x86_64` target for the `manylinux_2_28` platform
- `x86_64-manylinux_2_31`: An `x86_64` target for the `manylinux_2_31` platform
- `x86_64-manylinux_2_32`: An `x86_64` target for the `manylinux_2_32` platform
- `x86_64-manylinux_2_33`: An `x86_64` target for the `manylinux_2_33` platform
- `x86_64-manylinux_2_34`: An `x86_64` target for the `manylinux_2_34` platform
- `x86_64-manylinux_2_35`: An `x86_64` target for the `manylinux_2_35` platform
- `x86_64-manylinux_2_36`: An `x86_64` target for the `manylinux_2_36` platform
- `x86_64-manylinux_2_37`: An `x86_64` target for the `manylinux_2_37` platform
- `x86_64-manylinux_2_38`: An `x86_64` target for the `manylinux_2_38` platform
- `x86_64-manylinux_2_39`: An `x86_64` target for the `manylinux_2_39` platform
- `x86_64-manylinux_2_40`: An `x86_64` target for the `manylinux_2_40` platform
- `aarch64-manylinux2014`: An ARM64 target for the `manylinux2014` platform. Equivalent to `aarch64-manylinux_2_17`
- `aarch64-manylinux_2_17`: An ARM64 target for the `manylinux_2_17` platform
- `aarch64-manylinux_2_28`: An ARM64 target for the `manylinux_2_28` platform
- `aarch64-manylinux_2_31`: An ARM64 target for the `manylinux_2_31` platform
- `aarch64-manylinux_2_32`: An ARM64 target for the `manylinux_2_32` platform
- `aarch64-manylinux_2_33`: An ARM64 target for the `manylinux_2_33` platform
- `aarch64-manylinux_2_34`: An ARM64 target for the `manylinux_2_34` platform
- `aarch64-manylinux_2_35`: An ARM64 target for the `manylinux_2_35` platform
- `aarch64-manylinux_2_36`: An ARM64 target for the `manylinux_2_36` platform
- `aarch64-manylinux_2_37`: An ARM64 target for the `manylinux_2_37` platform
- `aarch64-manylinux_2_38`: An ARM64 target for the `manylinux_2_38` platform
- `aarch64-manylinux_2_39`: An ARM64 target for the `manylinux_2_39` platform
- `aarch64-manylinux_2_40`: An ARM64 target for the `manylinux_2_40` platform
- `aarch64-linux-android`: An ARM64 Android target
- `x86_64-linux-android`: An `x86_64` Android target
- `wasm32-pyodide2024`: A wasm32 target using the Pyodide 2024 platform. Meant for use with Python 3.12
- `arm64-apple-ios`: An ARM64 target for iOS device
- `arm64-apple-ios-simulator`: An ARM64 target for iOS simulator
- `x86_64-apple-ios-simulator`: An `x86_64` target for iOS simulator
```

[`--quiet`](#uv-tool-run--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--refresh`](#uv-tool-run--refresh) : Refresh all cached data

[`--refresh-package`](#uv-tool-run--refresh-package) *refresh-package* : Refresh cached data for a specific package

[`--reinstall`](#uv-tool-run--reinstall), `--force-reinstall` : Reinstall all packages, regardless of whether they're already installed. Implies `--refresh`

[`--reinstall-package`](#uv-tool-run--reinstall-package) *reinstall-package* : Reinstall a specific package, regardless of whether it's already installed. Implies `--refresh-package`

[`--resolution`](#uv-tool-run--resolution) *resolution* : The strategy to use when selecting between the different compatible versions for a given package requirement.

```
By default, uv will use the latest compatible version of each package (`highest`).

May also be set with the `UV_RESOLUTION` environment variable.

Possible values:

- `highest`: Resolve the highest compatible version of each package
- `lowest`: Resolve the lowest compatible version of each package
- `lowest-direct`: Resolve the lowest compatible version of any direct dependencies, and the highest compatible version of any transitive dependencies
```

[`--upgrade`](#uv-tool-run--upgrade), `-U` : Allow package upgrades, ignoring pinned versions in any existing output file. Implies `--refresh`

[`--upgrade-package`](#uv-tool-run--upgrade-package), `-P` *upgrade-package* : Allow upgrades for a specific package, ignoring pinned versions in any existing output file. Implies `--refresh-package`

[`--verbose`](#uv-tool-run--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

[`--with`](#uv-tool-run--with), `-w` *with* : Run with the given packages installed

[`--with-editable`](#uv-tool-run--with-editable) *with-editable* : Run with the given packages installed in editable mode

```
When used in a project, these dependencies will be layered on top of the uv tool's environment in a separate, ephemeral environment. These dependencies are allowed to conflict with those specified.
```

[`--with-requirements`](#uv-tool-run--with-requirements) *with-requirements* : Run with the packages listed in the given files.

```
The following formats are supported: `requirements.txt`, `.py` files with inline metadata, and `pylock.toml`.
```

### [uv tool install](#uv-tool-install)

Install commands provided by a Python package.

Packages are installed into an isolated virtual environment in the uv tools directory. The executables are linked the tool executable directory, which is determined according to the XDG standard and can be retrieved with `uv tool dir --bin`.

If the tool was previously installed, the existing tool will generally be replaced.

### Usage

```
uv tool install [OPTIONS] <PACKAGE>

```

### Arguments

[PACKAGE](#uv-tool-install--package) : The package to install commands from

### Options

[`--allow-insecure-host`](#uv-tool-install--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--build-constraints`](#uv-tool-install--build-constraints), `--build-constraint`, `-b` *build-constraints* : Constrain build dependencies using the given requirements files when building source distributions.

```
Constraints files are `requirements.txt`-like files that only control the *version* of a requirement that's installed. However, including a package in a constraints file will *not* trigger the installation of that package.

May also be set with the `UV_BUILD_CONSTRAINT` environment variable.
```

[`--cache-dir`](#uv-tool-install--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-tool-install--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--compile-bytecode`](#uv-tool-install--compile-bytecode), `--compile` : Compile Python files to bytecode after installation.

```
By default, uv does not compile Python (`.py`) files to bytecode (`__pycache__/*.pyc`); instead, compilation is performed lazily the first time a module is imported. For use-cases in which start time is critical, such as CLI applications and Docker containers, this option can be enabled to trade longer installation times for faster start times.

When enabled, uv will process the entire site-packages directory (including packages that are not being modified by the current operation) for consistency. Like pip, it will also ignore errors.

May also be set with the `UV_COMPILE_BYTECODE` environment variable.
```

[`--config-file`](#uv-tool-install--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--config-setting`](#uv-tool-install--config-setting), `--config-settings`, `-C` *config-setting* : Settings to pass to the PEP 517 build backend, specified as `KEY=VALUE` pairs

[`--config-settings-package`](#uv-tool-install--config-settings-package), `--config-settings-package` *config-settings-package* : Settings to pass to the PEP 517 build backend for a specific package, specified as `PACKAGE:KEY=VALUE` pairs

[`--constraints`](#uv-tool-install--constraints), `--constraint`, `-c` *constraints* : Constrain versions using the given requirements files.

```
Constraints files are `requirements.txt`-like files that only control the *version* of a requirement that's installed. However, including a package in a constraints file will *not* trigger the installation of that package.

This is equivalent to pip's `--constraint` option.

May also be set with the `UV_CONSTRAINT` environment variable.
```

[`--default-index`](#uv-tool-install--default-index) *default-index* : The URL of the default package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--index` flag.

May also be set with the `UV_DEFAULT_INDEX` environment variable.
```

[`--directory`](#uv-tool-install--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--editable`](#uv-tool-install--editable), `-e` : Install the target package in editable mode, such that changes in the package's source directory are reflected without reinstallation

[`--exclude-newer`](#uv-tool-install--exclude-newer) *exclude-newer* : Limit candidate packages to those that were uploaded prior to the given date.

```
Accepts both RFC 3339 timestamps (e.g., `2006-12-02T02:07:43Z`) and local dates in the same format (e.g., `2006-12-02`) in your system's configured time zone.

May also be set with the `UV_EXCLUDE_NEWER` environment variable.
```

[`--exclude-newer-package`](#uv-tool-install--exclude-newer-package) *exclude-newer-package* : Limit candidate packages for specific packages to those that were uploaded prior to the given date.

```
Accepts package-date pairs in the format `PACKAGE=DATE`, where `DATE` is an RFC 3339 timestamp (e.g., `2006-12-02T02:07:43Z`) or local date (e.g., `2006-12-02`) in your system's configured time zone.

Can be provided multiple times for different packages.
```

[`--extra-index-url`](#uv-tool-install--extra-index-url) *extra-index-url* : (Deprecated: use `--index` instead) Extra URLs of package indexes to use, in addition to `--index-url`.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--index-url` (which defaults to PyPI). When multiple `--extra-index-url` flags are provided, earlier values take priority.

May also be set with the `UV_EXTRA_INDEX_URL` environment variable.
```

[`--find-links`](#uv-tool-install--find-links), `-f` *find-links* : Locations to search for candidate distributions, in addition to those found in the registry indexes.

```
If a path, the target must be a directory that contains packages as wheel files (`.whl`) or source distributions (e.g., `.tar.gz` or `.zip`) at the top level.

If a URL, the page must contain a flat list of links to package files adhering to the formats described above.

May also be set with the `UV_FIND_LINKS` environment variable.
```

[`--force`](#uv-tool-install--force) : Force installation of the tool.

```
Will replace any existing entry points with the same name in the executable directory.
```

[`--fork-strategy`](#uv-tool-install--fork-strategy) *fork-strategy* : The strategy to use when selecting multiple versions of a given package across Python versions and platforms.

```
By default, uv will optimize for selecting the latest version of each package for each supported Python version (`requires-python`), while minimizing the number of selected versions across platforms.

Under `fewest`, uv will minimize the number of selected versions for each package, preferring older versions that are compatible with a wider range of supported Python versions or platforms.

May also be set with the `UV_FORK_STRATEGY` environment variable.

Possible values:

- `fewest`: Optimize for selecting the fewest number of versions for each package. Older versions may be preferred if they are compatible with a wider range of supported Python versions or platforms
- `requires-python`: Optimize for selecting latest supported version of each package, for each supported Python version
```

[`--help`](#uv-tool-install--help), `-h` : Display the concise help for this command

[`--index`](#uv-tool-install--index) *index* : The URLs to use when resolving dependencies, in addition to the default index.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--default-index` (which defaults to PyPI). When multiple `--index` flags are provided, earlier values take priority.

Index names are not supported as values. Relative paths must be disambiguated from index names with `./` or `../` on Unix or `.\\`, `..\\`, `./` or `../` on Windows.

May also be set with the `UV_INDEX` environment variable.
```

[`--index-strategy`](#uv-tool-install--index-strategy) *index-strategy* : The strategy to use when resolving against multiple index URLs.

```
By default, uv will stop at the first index on which a given package is available, and limit resolutions to those present on that first index (`first-index`). This prevents "dependency confusion" attacks, whereby an attacker can upload a malicious package under the same name to an alternate index.

May also be set with the `UV_INDEX_STRATEGY` environment variable.

Possible values:

- `first-index`: Only use results from the first index that returns a match for a given package name
- `unsafe-first-match`: Search for every package name across all indexes, exhausting the versions from the first index before moving on to the next
- `unsafe-best-match`: Search for every package name across all indexes, preferring the "best" version found. If a package version is in multiple indexes, only look at the entry for the first index
```

[`--index-url`](#uv-tool-install--index-url), `-i` *index-url* : (Deprecated: use `--default-index` instead) The URL of the Python package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--extra-index-url` flag.

May also be set with the `UV_INDEX_URL` environment variable.
```

[`--keyring-provider`](#uv-tool-install--keyring-provider) *keyring-provider* : Attempt to use `keyring` for authentication for index URLs.

```
At present, only `--keyring-provider subprocess` is supported, which configures uv to use the `keyring` CLI to handle authentication.

Defaults to `disabled`.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--link-mode`](#uv-tool-install--link-mode) *link-mode* : The method to use when installing packages from the global cache.

```
Defaults to `clone` (also known as Copy-on-Write) on macOS, and `hardlink` on Linux and Windows.

WARNING: The use of symlink link mode is discouraged, as they create tight coupling between the cache and the target environment. For example, clearing the cache (`uv cache clean`) will break all installed packages by way of removing the underlying source files. Use symlinks with caution.

May also be set with the `UV_LINK_MODE` environment variable.

Possible values:

- `clone`: Clone (i.e., copy-on-write) packages from the wheel into the `site-packages` directory
- `copy`: Copy packages from the wheel into the `site-packages` directory
- `hardlink`: Hard link packages from the wheel into the `site-packages` directory
- `symlink`: Symbolically link packages from the wheel into the `site-packages` directory
```

[`--managed-python`](#uv-tool-install--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-tool-install--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-binary`](#uv-tool-install--no-binary) : Don't install pre-built wheels.

```
The given packages will be built and installed from source. The resolver will still use pre-built wheels to extract package metadata, if available.

May also be set with the `UV_NO_BINARY` environment variable.
```

[`--no-binary-package`](#uv-tool-install--no-binary-package) *no-binary-package* : Don't install pre-built wheels for a specific package

```
May also be set with the `UV_NO_BINARY_PACKAGE` environment variable.
```

[`--no-build`](#uv-tool-install--no-build) : Don't build source distributions.

```
When enabled, resolving will not run arbitrary Python code. The cached wheels of already-built source distributions will be reused, but operations that require building distributions will exit with an error.

May also be set with the `UV_NO_BUILD` environment variable.
```

[`--no-build-isolation`](#uv-tool-install--no-build-isolation) : Disable isolation when building source distributions.

```
Assumes that build dependencies specified by PEP 518 are already installed.

May also be set with the `UV_NO_BUILD_ISOLATION` environment variable.
```

[`--no-build-isolation-package`](#uv-tool-install--no-build-isolation-package) *no-build-isolation-package* : Disable isolation when building source distributions for a specific package.

```
Assumes that the packages' build dependencies specified by PEP 518 are already installed.
```

[`--no-build-package`](#uv-tool-install--no-build-package) *no-build-package* : Don't build source distributions for a specific package

```
May also be set with the `UV_NO_BUILD_PACKAGE` environment variable.
```

[`--no-cache`](#uv-tool-install--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-tool-install--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-index`](#uv-tool-install--no-index) : Ignore the registry index (e.g., PyPI), instead relying on direct URL dependencies and those provided via `--find-links`

[`--no-managed-python`](#uv-tool-install--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-tool-install--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-tool-install--no-python-downloads) : Disable automatic downloads of Python.

[`--no-sources`](#uv-tool-install--no-sources) : Ignore the `tool.uv.sources` table when resolving dependencies. Used to lock against the standards-compliant, publishable package metadata, as opposed to using any workspace, Git, URL, or local path sources

[`--offline`](#uv-tool-install--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--overrides`](#uv-tool-install--overrides), `--override` *overrides* : Override versions using the given requirements files.

```
Overrides files are `requirements.txt`-like files that force a specific version of a requirement to be installed, regardless of the requirements declared by any constituent package, and regardless of whether this would be considered an invalid resolution.

While constraints are *additive*, in that they're combined with the requirements of the constituent packages, overrides are *absolute*, in that they completely replace the requirements of the constituent packages.

May also be set with the `UV_OVERRIDE` environment variable.
```

[`--prerelease`](#uv-tool-install--prerelease) *prerelease* : The strategy to use when considering pre-release versions.

```
By default, uv will accept pre-releases for packages that *only* publish pre-releases, along with first-party requirements that contain an explicit pre-release marker in the declared specifiers (`if-necessary-or-explicit`).

May also be set with the `UV_PRERELEASE` environment variable.

Possible values:

- `disallow`: Disallow all pre-release versions
- `allow`: Allow all pre-release versions
- `if-necessary`: Allow pre-release versions if all versions of a package are pre-release
- `explicit`: Allow pre-release versions for first-party packages with explicit pre-release markers in their version requirements
- `if-necessary-or-explicit`: Allow pre-release versions if all versions of a package are pre-release, or if the package has an explicit pre-release marker in its version requirements
```

[`--project`](#uv-tool-install--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--python`](#uv-tool-install--python), `-p` *python* : The Python interpreter to use to build the tool environment.

```
See [uv python](#uv-python) for details on Python discovery and supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--python-platform`](#uv-tool-install--python-platform) *python-platform* : The platform for which requirements should be installed.

```
Represented as a "target triple", a string that describes the target platform in terms of its CPU, vendor, and operating system name, like `x86_64-unknown-linux-gnu` or `aarch64-apple-darwin`.

When targeting macOS (Darwin), the default minimum version is `13.0`. Use `MACOSX_DEPLOYMENT_TARGET` to specify a different minimum version, e.g., `14.0`.

When targeting iOS, the default minimum version is `13.0`. Use `IPHONEOS_DEPLOYMENT_TARGET` to specify a different minimum version, e.g., `14.0`.

When targeting Android, the default minimum Android API level is `24`. Use `ANDROID_API_LEVEL` to specify a different minimum version, e.g., `26`.

WARNING: When specified, uv will select wheels that are compatible with the *target* platform; as a result, the installed distributions may not be compatible with the *current* platform. Conversely, any distributions that are built from source may be incompatible with the *target* platform, as they will be built for the *current* platform. The `--python-platform` option is intended for advanced use cases.

Possible values:

- `windows`: An alias for `x86_64-pc-windows-msvc`, the default target for Windows
- `linux`: An alias for `x86_64-unknown-linux-gnu`, the default target for Linux
- `macos`: An alias for `aarch64-apple-darwin`, the default target for macOS
- `x86_64-pc-windows-msvc`: A 64-bit x86 Windows target
- `aarch64-pc-windows-msvc`: An ARM64 Windows target
- `i686-pc-windows-msvc`: A 32-bit x86 Windows target
- `x86_64-unknown-linux-gnu`: An x86 Linux target. Equivalent to `x86_64-manylinux_2_28`
- `aarch64-apple-darwin`: An ARM-based macOS target, as seen on Apple Silicon devices
- `x86_64-apple-darwin`: An x86 macOS target
- `aarch64-unknown-linux-gnu`: An ARM64 Linux target. Equivalent to `aarch64-manylinux_2_28`
- `aarch64-unknown-linux-musl`: An ARM64 Linux target
- `x86_64-unknown-linux-musl`: An `x86_64` Linux target
- `riscv64-unknown-linux`: A RISCV64 Linux target
- `x86_64-manylinux2014`: An `x86_64` target for the `manylinux2014` platform. Equivalent to `x86_64-manylinux_2_17`
- `x86_64-manylinux_2_17`: An `x86_64` target for the `manylinux_2_17` platform
- `x86_64-manylinux_2_28`: An `x86_64` target for the `manylinux_2_28` platform
- `x86_64-manylinux_2_31`: An `x86_64` target for the `manylinux_2_31` platform
- `x86_64-manylinux_2_32`: An `x86_64` target for the `manylinux_2_32` platform
- `x86_64-manylinux_2_33`: An `x86_64` target for the `manylinux_2_33` platform
- `x86_64-manylinux_2_34`: An `x86_64` target for the `manylinux_2_34` platform
- `x86_64-manylinux_2_35`: An `x86_64` target for the `manylinux_2_35` platform
- `x86_64-manylinux_2_36`: An `x86_64` target for the `manylinux_2_36` platform
- `x86_64-manylinux_2_37`: An `x86_64` target for the `manylinux_2_37` platform
- `x86_64-manylinux_2_38`: An `x86_64` target for the `manylinux_2_38` platform
- `x86_64-manylinux_2_39`: An `x86_64` target for the `manylinux_2_39` platform
- `x86_64-manylinux_2_40`: An `x86_64` target for the `manylinux_2_40` platform
- `aarch64-manylinux2014`: An ARM64 target for the `manylinux2014` platform. Equivalent to `aarch64-manylinux_2_17`
- `aarch64-manylinux_2_17`: An ARM64 target for the `manylinux_2_17` platform
- `aarch64-manylinux_2_28`: An ARM64 target for the `manylinux_2_28` platform
- `aarch64-manylinux_2_31`: An ARM64 target for the `manylinux_2_31` platform
- `aarch64-manylinux_2_32`: An ARM64 target for the `manylinux_2_32` platform
- `aarch64-manylinux_2_33`: An ARM64 target for the `manylinux_2_33` platform
- `aarch64-manylinux_2_34`: An ARM64 target for the `manylinux_2_34` platform
- `aarch64-manylinux_2_35`: An ARM64 target for the `manylinux_2_35` platform
- `aarch64-manylinux_2_36`: An ARM64 target for the `manylinux_2_36` platform
- `aarch64-manylinux_2_37`: An ARM64 target for the `manylinux_2_37` platform
- `aarch64-manylinux_2_38`: An ARM64 target for the `manylinux_2_38` platform
- `aarch64-manylinux_2_39`: An ARM64 target for the `manylinux_2_39` platform
- `aarch64-manylinux_2_40`: An ARM64 target for the `manylinux_2_40` platform
- `aarch64-linux-android`: An ARM64 Android target
- `x86_64-linux-android`: An `x86_64` Android target
- `wasm32-pyodide2024`: A wasm32 target using the Pyodide 2024 platform. Meant for use with Python 3.12
- `arm64-apple-ios`: An ARM64 target for iOS device
- `arm64-apple-ios-simulator`: An ARM64 target for iOS simulator
- `x86_64-apple-ios-simulator`: An `x86_64` target for iOS simulator
```

[`--quiet`](#uv-tool-install--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--refresh`](#uv-tool-install--refresh) : Refresh all cached data

[`--refresh-package`](#uv-tool-install--refresh-package) *refresh-package* : Refresh cached data for a specific package

[`--reinstall`](#uv-tool-install--reinstall), `--force-reinstall` : Reinstall all packages, regardless of whether they're already installed. Implies `--refresh`

[`--reinstall-package`](#uv-tool-install--reinstall-package) *reinstall-package* : Reinstall a specific package, regardless of whether it's already installed. Implies `--refresh-package`

[`--resolution`](#uv-tool-install--resolution) *resolution* : The strategy to use when selecting between the different compatible versions for a given package requirement.

```
By default, uv will use the latest compatible version of each package (`highest`).

May also be set with the `UV_RESOLUTION` environment variable.

Possible values:

- `highest`: Resolve the highest compatible version of each package
- `lowest`: Resolve the lowest compatible version of each package
- `lowest-direct`: Resolve the lowest compatible version of any direct dependencies, and the highest compatible version of any transitive dependencies
```

[`--upgrade`](#uv-tool-install--upgrade), `-U` : Allow package upgrades, ignoring pinned versions in any existing output file. Implies `--refresh`

[`--upgrade-package`](#uv-tool-install--upgrade-package), `-P` *upgrade-package* : Allow upgrades for a specific package, ignoring pinned versions in any existing output file. Implies `--refresh-package`

[`--verbose`](#uv-tool-install--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

[`--with`](#uv-tool-install--with), `-w` *with* : Include the following additional requirements

[`--with-editable`](#uv-tool-install--with-editable) *with-editable* : Include the given packages in editable mode

[`--with-executables-from`](#uv-tool-install--with-executables-from) *with-executables-from* : Install executables from the following packages

[`--with-requirements`](#uv-tool-install--with-requirements) *with-requirements* : Run with the packages listed in the given files.

```
The following formats are supported: `requirements.txt`, `.py` files with inline metadata, and `pylock.toml`.
```

### [uv tool upgrade](#uv-tool-upgrade)

Upgrade installed tools.

If a tool was installed with version constraints, they will be respected on upgrade — to upgrade a tool beyond the originally provided constraints, use `uv tool install` again.

If a tool was installed with specific settings, they will be respected on upgraded. For example, if `--prereleases allow` was provided during installation, it will continue to be respected in upgrades.

### Usage

```
uv tool upgrade [OPTIONS] <NAME>...

```

### Arguments

[NAME](#uv-tool-upgrade--name) : The name of the tool to upgrade, along with an optional version specifier

### Options

[`--all`](#uv-tool-upgrade--all) : Upgrade all tools

[`--allow-insecure-host`](#uv-tool-upgrade--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-tool-upgrade--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-tool-upgrade--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--compile-bytecode`](#uv-tool-upgrade--compile-bytecode), `--compile` : Compile Python files to bytecode after installation.

```
By default, uv does not compile Python (`.py`) files to bytecode (`__pycache__/*.pyc`); instead, compilation is performed lazily the first time a module is imported. For use-cases in which start time is critical, such as CLI applications and Docker containers, this option can be enabled to trade longer installation times for faster start times.

When enabled, uv will process the entire site-packages directory (including packages that are not being modified by the current operation) for consistency. Like pip, it will also ignore errors.

May also be set with the `UV_COMPILE_BYTECODE` environment variable.
```

[`--config-file`](#uv-tool-upgrade--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--config-setting`](#uv-tool-upgrade--config-setting), `--config-settings`, `-C` *config-setting* : Settings to pass to the PEP 517 build backend, specified as `KEY=VALUE` pairs

[`--config-setting-package`](#uv-tool-upgrade--config-setting-package), `--config-settings-package` *config-setting-package* : Settings to pass to the PEP 517 build backend for a specific package, specified as `PACKAGE:KEY=VALUE` pairs

[`--default-index`](#uv-tool-upgrade--default-index) *default-index* : The URL of the default package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--index` flag.

May also be set with the `UV_DEFAULT_INDEX` environment variable.
```

[`--directory`](#uv-tool-upgrade--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--exclude-newer`](#uv-tool-upgrade--exclude-newer) *exclude-newer* : Limit candidate packages to those that were uploaded prior to the given date.

```
Accepts both RFC 3339 timestamps (e.g., `2006-12-02T02:07:43Z`) and local dates in the same format (e.g., `2006-12-02`) in your system's configured time zone.

May also be set with the `UV_EXCLUDE_NEWER` environment variable.
```

[`--exclude-newer-package`](#uv-tool-upgrade--exclude-newer-package) *exclude-newer-package* : Limit candidate packages for specific packages to those that were uploaded prior to the given date.

```
Accepts package-date pairs in the format `PACKAGE=DATE`, where `DATE` is an RFC 3339 timestamp (e.g., `2006-12-02T02:07:43Z`) or local date (e.g., `2006-12-02`) in your system's configured time zone.

Can be provided multiple times for different packages.
```

[`--extra-index-url`](#uv-tool-upgrade--extra-index-url) *extra-index-url* : (Deprecated: use `--index` instead) Extra URLs of package indexes to use, in addition to `--index-url`.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--index-url` (which defaults to PyPI). When multiple `--extra-index-url` flags are provided, earlier values take priority.

May also be set with the `UV_EXTRA_INDEX_URL` environment variable.
```

[`--find-links`](#uv-tool-upgrade--find-links), `-f` *find-links* : Locations to search for candidate distributions, in addition to those found in the registry indexes.

```
If a path, the target must be a directory that contains packages as wheel files (`.whl`) or source distributions (e.g., `.tar.gz` or `.zip`) at the top level.

If a URL, the page must contain a flat list of links to package files adhering to the formats described above.

May also be set with the `UV_FIND_LINKS` environment variable.
```

[`--fork-strategy`](#uv-tool-upgrade--fork-strategy) *fork-strategy* : The strategy to use when selecting multiple versions of a given package across Python versions and platforms.

```
By default, uv will optimize for selecting the latest version of each package for each supported Python version (`requires-python`), while minimizing the number of selected versions across platforms.

Under `fewest`, uv will minimize the number of selected versions for each package, preferring older versions that are compatible with a wider range of supported Python versions or platforms.

May also be set with the `UV_FORK_STRATEGY` environment variable.

Possible values:

- `fewest`: Optimize for selecting the fewest number of versions for each package. Older versions may be preferred if they are compatible with a wider range of supported Python versions or platforms
- `requires-python`: Optimize for selecting latest supported version of each package, for each supported Python version
```

[`--help`](#uv-tool-upgrade--help), `-h` : Display the concise help for this command

[`--index`](#uv-tool-upgrade--index) *index* : The URLs to use when resolving dependencies, in addition to the default index.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--default-index` (which defaults to PyPI). When multiple `--index` flags are provided, earlier values take priority.

Index names are not supported as values. Relative paths must be disambiguated from index names with `./` or `../` on Unix or `.\\`, `..\\`, `./` or `../` on Windows.

May also be set with the `UV_INDEX` environment variable.
```

[`--index-strategy`](#uv-tool-upgrade--index-strategy) *index-strategy* : The strategy to use when resolving against multiple index URLs.

```
By default, uv will stop at the first index on which a given package is available, and limit resolutions to those present on that first index (`first-index`). This prevents "dependency confusion" attacks, whereby an attacker can upload a malicious package under the same name to an alternate index.

May also be set with the `UV_INDEX_STRATEGY` environment variable.

Possible values:

- `first-index`: Only use results from the first index that returns a match for a given package name
- `unsafe-first-match`: Search for every package name across all indexes, exhausting the versions from the first index before moving on to the next
- `unsafe-best-match`: Search for every package name across all indexes, preferring the "best" version found. If a package version is in multiple indexes, only look at the entry for the first index
```

[`--index-url`](#uv-tool-upgrade--index-url), `-i` *index-url* : (Deprecated: use `--default-index` instead) The URL of the Python package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--extra-index-url` flag.

May also be set with the `UV_INDEX_URL` environment variable.
```

[`--keyring-provider`](#uv-tool-upgrade--keyring-provider) *keyring-provider* : Attempt to use `keyring` for authentication for index URLs.

```
At present, only `--keyring-provider subprocess` is supported, which configures uv to use the `keyring` CLI to handle authentication.

Defaults to `disabled`.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--link-mode`](#uv-tool-upgrade--link-mode) *link-mode* : The method to use when installing packages from the global cache.

```
Defaults to `clone` (also known as Copy-on-Write) on macOS, and `hardlink` on Linux and Windows.

WARNING: The use of symlink link mode is discouraged, as they create tight coupling between the cache and the target environment. For example, clearing the cache (`uv cache clean`) will break all installed packages by way of removing the underlying source files. Use symlinks with caution.

May also be set with the `UV_LINK_MODE` environment variable.

Possible values:

- `clone`: Clone (i.e., copy-on-write) packages from the wheel into the `site-packages` directory
- `copy`: Copy packages from the wheel into the `site-packages` directory
- `hardlink`: Hard link packages from the wheel into the `site-packages` directory
- `symlink`: Symbolically link packages from the wheel into the `site-packages` directory
```

[`--managed-python`](#uv-tool-upgrade--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-tool-upgrade--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-binary`](#uv-tool-upgrade--no-binary) : Don't install pre-built wheels.

```
The given packages will be built and installed from source. The resolver will still use pre-built wheels to extract package metadata, if available.

May also be set with the `UV_NO_BINARY` environment variable.
```

[`--no-binary-package`](#uv-tool-upgrade--no-binary-package) *no-binary-package* : Don't install pre-built wheels for a specific package

```
May also be set with the `UV_NO_BINARY_PACKAGE` environment variable.
```

[`--no-build`](#uv-tool-upgrade--no-build) : Don't build source distributions.

```
When enabled, resolving will not run arbitrary Python code. The cached wheels of already-built source distributions will be reused, but operations that require building distributions will exit with an error.

May also be set with the `UV_NO_BUILD` environment variable.
```

[`--no-build-isolation`](#uv-tool-upgrade--no-build-isolation) : Disable isolation when building source distributions.

```
Assumes that build dependencies specified by PEP 518 are already installed.

May also be set with the `UV_NO_BUILD_ISOLATION` environment variable.
```

[`--no-build-isolation-package`](#uv-tool-upgrade--no-build-isolation-package) *no-build-isolation-package* : Disable isolation when building source distributions for a specific package.

```
Assumes that the packages' build dependencies specified by PEP 518 are already installed.
```

[`--no-build-package`](#uv-tool-upgrade--no-build-package) *no-build-package* : Don't build source distributions for a specific package

```
May also be set with the `UV_NO_BUILD_PACKAGE` environment variable.
```

[`--no-cache`](#uv-tool-upgrade--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-tool-upgrade--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-index`](#uv-tool-upgrade--no-index) : Ignore the registry index (e.g., PyPI), instead relying on direct URL dependencies and those provided via `--find-links`

[`--no-managed-python`](#uv-tool-upgrade--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-tool-upgrade--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-tool-upgrade--no-python-downloads) : Disable automatic downloads of Python.

[`--no-sources`](#uv-tool-upgrade--no-sources) : Ignore the `tool.uv.sources` table when resolving dependencies. Used to lock against the standards-compliant, publishable package metadata, as opposed to using any workspace, Git, URL, or local path sources

[`--offline`](#uv-tool-upgrade--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--prerelease`](#uv-tool-upgrade--prerelease) *prerelease* : The strategy to use when considering pre-release versions.

```
By default, uv will accept pre-releases for packages that *only* publish pre-releases, along with first-party requirements that contain an explicit pre-release marker in the declared specifiers (`if-necessary-or-explicit`).

May also be set with the `UV_PRERELEASE` environment variable.

Possible values:

- `disallow`: Disallow all pre-release versions
- `allow`: Allow all pre-release versions
- `if-necessary`: Allow pre-release versions if all versions of a package are pre-release
- `explicit`: Allow pre-release versions for first-party packages with explicit pre-release markers in their version requirements
- `if-necessary-or-explicit`: Allow pre-release versions if all versions of a package are pre-release, or if the package has an explicit pre-release marker in its version requirements
```

[`--project`](#uv-tool-upgrade--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--python`](#uv-tool-upgrade--python), `-p` *python* : Upgrade a tool, and specify it to use the given Python interpreter to build its environment. Use with `--all` to apply to all tools.

```
See [uv python](#uv-python) for details on Python discovery and supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--python-platform`](#uv-tool-upgrade--python-platform) *python-platform* : The platform for which requirements should be installed.

```
Represented as a "target triple", a string that describes the target platform in terms of its CPU, vendor, and operating system name, like `x86_64-unknown-linux-gnu` or `aarch64-apple-darwin`.

When targeting macOS (Darwin), the default minimum version is `13.0`. Use `MACOSX_DEPLOYMENT_TARGET` to specify a different minimum version, e.g., `14.0`.

When targeting iOS, the default minimum version is `13.0`. Use `IPHONEOS_DEPLOYMENT_TARGET` to specify a different minimum version, e.g., `14.0`.

When targeting Android, the default minimum Android API level is `24`. Use `ANDROID_API_LEVEL` to specify a different minimum version, e.g., `26`.

WARNING: When specified, uv will select wheels that are compatible with the *target* platform; as a result, the installed distributions may not be compatible with the *current* platform. Conversely, any distributions that are built from source may be incompatible with the *target* platform, as they will be built for the *current* platform. The `--python-platform` option is intended for advanced use cases.

Possible values:

- `windows`: An alias for `x86_64-pc-windows-msvc`, the default target for Windows
- `linux`: An alias for `x86_64-unknown-linux-gnu`, the default target for Linux
- `macos`: An alias for `aarch64-apple-darwin`, the default target for macOS
- `x86_64-pc-windows-msvc`: A 64-bit x86 Windows target
- `aarch64-pc-windows-msvc`: An ARM64 Windows target
- `i686-pc-windows-msvc`: A 32-bit x86 Windows target
- `x86_64-unknown-linux-gnu`: An x86 Linux target. Equivalent to `x86_64-manylinux_2_28`
- `aarch64-apple-darwin`: An ARM-based macOS target, as seen on Apple Silicon devices
- `x86_64-apple-darwin`: An x86 macOS target
- `aarch64-unknown-linux-gnu`: An ARM64 Linux target. Equivalent to `aarch64-manylinux_2_28`
- `aarch64-unknown-linux-musl`: An ARM64 Linux target
- `x86_64-unknown-linux-musl`: An `x86_64` Linux target
- `riscv64-unknown-linux`: A RISCV64 Linux target
- `x86_64-manylinux2014`: An `x86_64` target for the `manylinux2014` platform. Equivalent to `x86_64-manylinux_2_17`
- `x86_64-manylinux_2_17`: An `x86_64` target for the `manylinux_2_17` platform
- `x86_64-manylinux_2_28`: An `x86_64` target for the `manylinux_2_28` platform
- `x86_64-manylinux_2_31`: An `x86_64` target for the `manylinux_2_31` platform
- `x86_64-manylinux_2_32`: An `x86_64` target for the `manylinux_2_32` platform
- `x86_64-manylinux_2_33`: An `x86_64` target for the `manylinux_2_33` platform
- `x86_64-manylinux_2_34`: An `x86_64` target for the `manylinux_2_34` platform
- `x86_64-manylinux_2_35`: An `x86_64` target for the `manylinux_2_35` platform
- `x86_64-manylinux_2_36`: An `x86_64` target for the `manylinux_2_36` platform
- `x86_64-manylinux_2_37`: An `x86_64` target for the `manylinux_2_37` platform
- `x86_64-manylinux_2_38`: An `x86_64` target for the `manylinux_2_38` platform
- `x86_64-manylinux_2_39`: An `x86_64` target for the `manylinux_2_39` platform
- `x86_64-manylinux_2_40`: An `x86_64` target for the `manylinux_2_40` platform
- `aarch64-manylinux2014`: An ARM64 target for the `manylinux2014` platform. Equivalent to `aarch64-manylinux_2_17`
- `aarch64-manylinux_2_17`: An ARM64 target for the `manylinux_2_17` platform
- `aarch64-manylinux_2_28`: An ARM64 target for the `manylinux_2_28` platform
- `aarch64-manylinux_2_31`: An ARM64 target for the `manylinux_2_31` platform
- `aarch64-manylinux_2_32`: An ARM64 target for the `manylinux_2_32` platform
- `aarch64-manylinux_2_33`: An ARM64 target for the `manylinux_2_33` platform
- `aarch64-manylinux_2_34`: An ARM64 target for the `manylinux_2_34` platform
- `aarch64-manylinux_2_35`: An ARM64 target for the `manylinux_2_35` platform
- `aarch64-manylinux_2_36`: An ARM64 target for the `manylinux_2_36` platform
- `aarch64-manylinux_2_37`: An ARM64 target for the `manylinux_2_37` platform
- `aarch64-manylinux_2_38`: An ARM64 target for the `manylinux_2_38` platform
- `aarch64-manylinux_2_39`: An ARM64 target for the `manylinux_2_39` platform
- `aarch64-manylinux_2_40`: An ARM64 target for the `manylinux_2_40` platform
- `aarch64-linux-android`: An ARM64 Android target
- `x86_64-linux-android`: An `x86_64` Android target
- `wasm32-pyodide2024`: A wasm32 target using the Pyodide 2024 platform. Meant for use with Python 3.12
- `arm64-apple-ios`: An ARM64 target for iOS device
- `arm64-apple-ios-simulator`: An ARM64 target for iOS simulator
- `x86_64-apple-ios-simulator`: An `x86_64` target for iOS simulator
```

[`--quiet`](#uv-tool-upgrade--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--reinstall`](#uv-tool-upgrade--reinstall), `--force-reinstall` : Reinstall all packages, regardless of whether they're already installed. Implies `--refresh`

[`--reinstall-package`](#uv-tool-upgrade--reinstall-package) *reinstall-package* : Reinstall a specific package, regardless of whether it's already installed. Implies `--refresh-package`

[`--resolution`](#uv-tool-upgrade--resolution) *resolution* : The strategy to use when selecting between the different compatible versions for a given package requirement.

```
By default, uv will use the latest compatible version of each package (`highest`).

May also be set with the `UV_RESOLUTION` environment variable.

Possible values:

- `highest`: Resolve the highest compatible version of each package
- `lowest`: Resolve the lowest compatible version of each package
- `lowest-direct`: Resolve the lowest compatible version of any direct dependencies, and the highest compatible version of any transitive dependencies
```

[`--verbose`](#uv-tool-upgrade--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv tool list](#uv-tool-list)

List installed tools

### Usage

```
uv tool list [OPTIONS]

```

### Options

[`--allow-insecure-host`](#uv-tool-list--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-tool-list--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-tool-list--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-tool-list--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-tool-list--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--help`](#uv-tool-list--help), `-h` : Display the concise help for this command

[`--managed-python`](#uv-tool-list--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-tool-list--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-tool-list--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-tool-list--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-tool-list--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-tool-list--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--offline`](#uv-tool-list--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-tool-list--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--quiet`](#uv-tool-list--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--show-extras`](#uv-tool-list--show-extras) : Whether to display the extra requirements installed with each tool

[`--show-paths`](#uv-tool-list--show-paths) : Whether to display the path to each tool environment and installed executable

[`--show-python`](#uv-tool-list--show-python) : Whether to display the Python version associated with run each tool

[`--show-version-specifiers`](#uv-tool-list--show-version-specifiers) : Whether to display the version specifier(s) used to install each tool

[`--show-with`](#uv-tool-list--show-with) : Whether to display the additional requirements installed with each tool

[`--verbose`](#uv-tool-list--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv tool uninstall](#uv-tool-uninstall)

Uninstall a tool

### Usage

```
uv tool uninstall [OPTIONS] <NAME>...

```

### Arguments

[NAME](#uv-tool-uninstall--name) : The name of the tool to uninstall

### Options

[`--all`](#uv-tool-uninstall--all) : Uninstall all tools

[`--allow-insecure-host`](#uv-tool-uninstall--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-tool-uninstall--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-tool-uninstall--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-tool-uninstall--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-tool-uninstall--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--help`](#uv-tool-uninstall--help), `-h` : Display the concise help for this command

[`--managed-python`](#uv-tool-uninstall--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-tool-uninstall--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-tool-uninstall--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-tool-uninstall--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-tool-uninstall--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-tool-uninstall--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-tool-uninstall--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-tool-uninstall--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-tool-uninstall--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--quiet`](#uv-tool-uninstall--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--verbose`](#uv-tool-uninstall--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv tool update-shell](#uv-tool-update-shell)

Ensure that the tool executable directory is on the `PATH`.

If the tool executable directory is not present on the `PATH`, uv will attempt to add it to the relevant shell configuration files.

If the shell configuration files already include a blurb to add the executable directory to the path, but the directory is not present on the `PATH`, uv will exit with an error.

The tool executable directory is determined according to the XDG standard and can be retrieved with `uv tool dir --bin`.

### Usage

```
uv tool update-shell [OPTIONS]

```

### Options

[`--allow-insecure-host`](#uv-tool-update-shell--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-tool-update-shell--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-tool-update-shell--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-tool-update-shell--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-tool-update-shell--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--help`](#uv-tool-update-shell--help), `-h` : Display the concise help for this command

[`--managed-python`](#uv-tool-update-shell--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-tool-update-shell--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-tool-update-shell--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-tool-update-shell--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-tool-update-shell--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-tool-update-shell--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-tool-update-shell--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-tool-update-shell--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-tool-update-shell--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--quiet`](#uv-tool-update-shell--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--verbose`](#uv-tool-update-shell--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv tool dir](#uv-tool-dir)

Show the path to the uv tools directory.

The tools directory is used to store environments and metadata for installed tools.

By default, tools are stored in the uv data directory at `$XDG_DATA_HOME/uv/tools` or `$HOME/.local/share/uv/tools` on Unix and `%APPDATA%\uv\data\tools` on Windows.

The tool installation directory may be overridden with `$UV_TOOL_DIR`.

To instead view the directory uv installs executables into, use the `--bin` flag.

### Usage

```
uv tool dir [OPTIONS]

```

### Options

[`--allow-insecure-host`](#uv-tool-dir--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--bin`](#uv-tool-dir--bin) : Show the directory into which `uv tool` will install executables.

```
By default, `uv tool dir` shows the directory into which the tool Python environments
themselves are installed, rather than the directory containing the linked executables.

The tool executable directory is determined according to the XDG standard and is derived
from the following environment variables, in order of preference:

- `$UV_TOOL_BIN_DIR`
- `$XDG_BIN_HOME`
- `$XDG_DATA_HOME/../bin`
- `$HOME/.local/bin`
```

[`--cache-dir`](#uv-tool-dir--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-tool-dir--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-tool-dir--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-tool-dir--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--help`](#uv-tool-dir--help), `-h` : Display the concise help for this command

[`--managed-python`](#uv-tool-dir--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-tool-dir--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-tool-dir--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-tool-dir--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-tool-dir--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-tool-dir--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-tool-dir--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-tool-dir--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-tool-dir--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--quiet`](#uv-tool-dir--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--verbose`](#uv-tool-dir--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

## [uv python](#uv-python)

Manage Python versions and installations

Generally, uv first searches for Python in a virtual environment, either active or in a `.venv` directory in the current working directory or any parent directory. If a virtual environment is not required, uv will then search for a Python interpreter. Python interpreters are found by searching for Python executables in the `PATH` environment variable.

On Windows, the registry is also searched for Python executables.

By default, uv will download Python if a version cannot be found. This behavior can be disabled with the `--no-python-downloads` flag or the `python-downloads` setting.

The `--python` option allows requesting a different interpreter.

The following Python version request formats are supported:

- `<version>` e.g. `3`, `3.12`, `3.12.3`
- `<version-specifier>` e.g. `>=3.12,<3.13`
- `<version><short-variant>` (e.g., `3.13t`, `3.12.0d`)
- `<version>+<variant>` (e.g., `3.13+freethreaded`, `3.12.0+debug`)
- `<implementation>` e.g. `cpython` or `cp`
- `<implementation>@<version>` e.g. `cpython@3.12`
- `<implementation><version>` e.g. `cpython3.12` or `cp312`
- `<implementation><version-specifier>` e.g. `cpython>=3.12,<3.13`
- `<implementation>-<version>-<os>-<arch>-<libc>` e.g. `cpython-3.12.3-macos-aarch64-none`

Additionally, a specific system Python interpreter can often be requested with:

- `<executable-path>` e.g. `/opt/homebrew/bin/python3`
- `<executable-name>` e.g. `mypython3`
- `<install-dir>` e.g. `/some/environment/`

When the `--python` option is used, normal discovery rules apply but discovered interpreters are checked for compatibility with the request, e.g., if `pypy` is requested, uv will first check if the virtual environment contains a PyPy interpreter then check if each executable in the path is a PyPy interpreter.

uv supports discovering CPython, PyPy, and GraalPy interpreters. Unsupported interpreters will be skipped during discovery. If an unsupported interpreter implementation is requested, uv will exit with an error.

### Usage

```
uv python [OPTIONS] <COMMAND>

```

### Commands

[`uv python list`](#uv-python-list) : List the available Python installations

[`uv python install`](#uv-python-install) : Download and install Python versions

[`uv python upgrade`](#uv-python-upgrade) : Upgrade installed Python versions

[`uv python find`](#uv-python-find) : Search for a Python installation

[`uv python pin`](#uv-python-pin) : Pin to a specific Python version

[`uv python dir`](#uv-python-dir) : Show the uv Python installation directory

[`uv python uninstall`](#uv-python-uninstall) : Uninstall Python versions

[`uv python update-shell`](#uv-python-update-shell) : Ensure that the Python executable directory is on the `PATH`

### [uv python list](#uv-python-list)

List the available Python installations.

By default, installed Python versions and the downloads for latest available patch version of each supported Python major version are shown.

Use `--managed-python` to view only managed Python versions.

Use `--no-managed-python` to omit managed Python versions.

Use `--all-versions` to view all available patch versions.

Use `--only-installed` to omit available downloads.

### Usage

```
uv python list [OPTIONS] [REQUEST]

```

### Arguments

[REQUEST](#uv-python-list--request) : A Python request to filter by.

```
See [uv python](#uv-python) to view supported request formats.
```

### Options

[`--all-arches`](#uv-python-list--all-arches), `--all_architectures` : List Python downloads for all architectures.

```
By default, only downloads for the current architecture are shown.
```

[`--all-platforms`](#uv-python-list--all-platforms) : List Python downloads for all platforms.

```
By default, only downloads for the current platform are shown.
```

[`--all-versions`](#uv-python-list--all-versions) : List all Python versions, including old patch versions.

```
By default, only the latest patch version is shown for each minor version.
```

[`--allow-insecure-host`](#uv-python-list--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-python-list--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-python-list--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-python-list--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-python-list--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--help`](#uv-python-list--help), `-h` : Display the concise help for this command

[`--managed-python`](#uv-python-list--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-python-list--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-python-list--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-python-list--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-python-list--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-python-list--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-python-list--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-python-list--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--only-downloads`](#uv-python-list--only-downloads) : Only show available Python downloads.

```
By default, installed distributions and available downloads for the current platform are shown.
```

[`--only-installed`](#uv-python-list--only-installed) : Only show installed Python versions.

```
By default, installed distributions and available downloads for the current platform are shown.
```

[`--output-format`](#uv-python-list--output-format) *output-format* : Select the output format

```
[default: text]

Possible values:

- `text`: Plain text (for humans)
- `json`: JSON (for computers)
```

[`--project`](#uv-python-list--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--python-downloads-json-url`](#uv-python-list--python-downloads-json-url) *python-downloads-json-url* : URL pointing to JSON of custom Python installations.

```
Note that currently, only local paths are supported.
```

[`--quiet`](#uv-python-list--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--show-urls`](#uv-python-list--show-urls) : Show the URLs of available Python downloads.

```
By default, these display as `<download available>`.
```

[`--verbose`](#uv-python-list--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv python install](#uv-python-install)

Download and install Python versions.

Supports CPython and PyPy. CPython distributions are downloaded from the Astral `python-build-standalone` project. PyPy distributions are downloaded from `python.org`. The available Python versions are bundled with each uv release. To install new Python versions, you may need upgrade uv.

Python versions are installed into the uv Python directory, which can be retrieved with `uv python dir`.

By default, Python executables are added to a directory on the path with a minor version suffix, e.g., `python3.13`. To install `python3` and `python`, use the `--default` flag. Use `uv python dir --bin` to see the target directory.

Multiple Python versions may be requested.

See `uv help python` to view supported request formats.

### Usage

```
uv python install [OPTIONS] [TARGETS]...

```

### Arguments

[TARGETS](#uv-python-install--targets) : The Python version(s) to install.

```
If not provided, the requested Python version(s) will be read from the `UV_PYTHON` environment variable then `.python-versions` or `.python-version` files. If none of the above are present, uv will check if it has installed any Python versions. If not, it will install the latest stable version of Python.

See [uv python](#uv-python) to view supported request formats.
```

### Options

[`--allow-insecure-host`](#uv-python-install--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-python-install--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-python-install--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-python-install--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--default`](#uv-python-install--default) : Use as the default Python version.

```
By default, only a `python{major}.{minor}` executable is installed, e.g., `python3.10`. When the `--default` flag is used, `python{major}`, e.g., `python3`, and `python` executables are also installed.

Alternative Python variants will still include their tag. For example, installing 3.13+freethreaded with `--default` will include in `python3t` and `pythont`, not `python3` and `python`.

If multiple Python versions are requested, uv will exit with an error.
```

[`--directory`](#uv-python-install--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--force`](#uv-python-install--force), `-f` : Replace existing Python executables during installation.

```
By default, uv will refuse to replace executables that it does not manage.

Implies `--reinstall`.
```

[`--help`](#uv-python-install--help), `-h` : Display the concise help for this command

[`--install-dir`](#uv-python-install--install-dir), `-i` *install-dir* : The directory to store the Python installation in.

```
If provided, `UV_PYTHON_INSTALL_DIR` will need to be set for subsequent operations for uv to discover the Python installation.

See `uv python dir` to view the current Python installation directory. Defaults to `~/.local/share/uv/python`.

May also be set with the `UV_PYTHON_INSTALL_DIR` environment variable.
```

[`--managed-python`](#uv-python-install--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--mirror`](#uv-python-install--mirror) *mirror* : Set the URL to use as the source for downloading Python installations.

```
The provided URL will replace `https://github.com/astral-sh/python-build-standalone/releases/download` in, e.g., `https://github.com/astral-sh/python-build-standalone/releases/download/20240713/cpython-3.12.4%2B20240713-aarch64-apple-darwin-install_only.tar.gz`.

Distributions can be read from a local directory by using the `file://` URL scheme.
```

[`--native-tls`](#uv-python-install--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-bin`](#uv-python-install--no-bin) : Do not install a Python executable into the `bin` directory.

```
This can also be set with `UV_PYTHON_INSTALL_BIN=0`.
```

[`--no-cache`](#uv-python-install--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-python-install--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-python-install--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-python-install--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-python-install--no-python-downloads) : Disable automatic downloads of Python.

[`--no-registry`](#uv-python-install--no-registry) : Do not register the Python installation in the Windows registry.

```
This can also be set with `UV_PYTHON_INSTALL_REGISTRY=0`.
```

[`--offline`](#uv-python-install--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-python-install--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--pypy-mirror`](#uv-python-install--pypy-mirror) *pypy-mirror* : Set the URL to use as the source for downloading PyPy installations.

```
The provided URL will replace `https://downloads.python.org/pypy` in, e.g., `https://downloads.python.org/pypy/pypy3.8-v7.3.7-osx64.tar.bz2`.

Distributions can be read from a local directory by using the `file://` URL scheme.
```

[`--python-downloads-json-url`](#uv-python-install--python-downloads-json-url) *python-downloads-json-url* : URL pointing to JSON of custom Python installations.

```
Note that currently, only local paths are supported.
```

[`--quiet`](#uv-python-install--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--reinstall`](#uv-python-install--reinstall), `-r` : Reinstall the requested Python version, if it's already installed.

```
By default, uv will exit successfully if the version is already installed.
```

[`--verbose`](#uv-python-install--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv python upgrade](#uv-python-upgrade)

Upgrade installed Python versions.

Upgrades versions to the latest supported patch release. Requires the `python-upgrade` preview feature.

A target Python minor version to upgrade may be provided, e.g., `3.13`. Multiple versions may be provided to perform more than one upgrade.

If no target version is provided, then uv will upgrade all managed CPython versions.

During an upgrade, uv will not uninstall outdated patch versions.

When an upgrade is performed, virtual environments created by uv will automatically use the new version. However, if the virtual environment was created before the upgrade functionality was added, it will continue to use the old Python version; to enable upgrades, the environment must be recreated.

Upgrades are not yet supported for alternative implementations, like PyPy.

### Usage

```
uv python upgrade [OPTIONS] [TARGETS]...

```

### Arguments

[TARGETS](#uv-python-upgrade--targets) : The Python minor version(s) to upgrade.

```
If no target version is provided, then uv will upgrade all managed CPython versions.
```

### Options

[`--allow-insecure-host`](#uv-python-upgrade--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-python-upgrade--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-python-upgrade--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-python-upgrade--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-python-upgrade--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--help`](#uv-python-upgrade--help), `-h` : Display the concise help for this command

[`--install-dir`](#uv-python-upgrade--install-dir), `-i` *install-dir* : The directory Python installations are stored in.

```
If provided, `UV_PYTHON_INSTALL_DIR` will need to be set for subsequent operations for uv to discover the Python installation.

See `uv python dir` to view the current Python installation directory. Defaults to `~/.local/share/uv/python`.

May also be set with the `UV_PYTHON_INSTALL_DIR` environment variable.
```

[`--managed-python`](#uv-python-upgrade--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--mirror`](#uv-python-upgrade--mirror) *mirror* : Set the URL to use as the source for downloading Python installations.

```
The provided URL will replace `https://github.com/astral-sh/python-build-standalone/releases/download` in, e.g., `https://github.com/astral-sh/python-build-standalone/releases/download/20240713/cpython-3.12.4%2B20240713-aarch64-apple-darwin-install_only.tar.gz`.

Distributions can be read from a local directory by using the `file://` URL scheme.
```

[`--native-tls`](#uv-python-upgrade--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-python-upgrade--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-python-upgrade--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-python-upgrade--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-python-upgrade--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-python-upgrade--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-python-upgrade--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-python-upgrade--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--pypy-mirror`](#uv-python-upgrade--pypy-mirror) *pypy-mirror* : Set the URL to use as the source for downloading PyPy installations.

```
The provided URL will replace `https://downloads.python.org/pypy` in, e.g., `https://downloads.python.org/pypy/pypy3.8-v7.3.7-osx64.tar.bz2`.

Distributions can be read from a local directory by using the `file://` URL scheme.
```

[`--python-downloads-json-url`](#uv-python-upgrade--python-downloads-json-url) *python-downloads-json-url* : URL pointing to JSON of custom Python installations.

```
Note that currently, only local paths are supported.
```

[`--quiet`](#uv-python-upgrade--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--reinstall`](#uv-python-upgrade--reinstall), `-r` : Reinstall the latest Python patch, if it's already installed.

```
By default, uv will exit successfully if the latest patch is already installed.
```

[`--verbose`](#uv-python-upgrade--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv python find](#uv-python-find)

Search for a Python installation.

Displays the path to the Python executable.

See `uv help python` to view supported request formats and details on discovery behavior.

### Usage

```
uv python find [OPTIONS] [REQUEST]

```

### Arguments

[REQUEST](#uv-python-find--request) : The Python request.

```
See [uv python](#uv-python) to view supported request formats.
```

### Options

[`--allow-insecure-host`](#uv-python-find--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-python-find--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-python-find--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-python-find--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-python-find--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--help`](#uv-python-find--help), `-h` : Display the concise help for this command

[`--managed-python`](#uv-python-find--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-python-find--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-python-find--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-python-find--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-python-find--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-python-find--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-project`](#uv-python-find--no-project), `--no_workspace` : Avoid discovering a project or workspace.

```
Otherwise, when no request is provided, the Python requirement of a project in the current directory or parent directories will be used.
```

[`--no-python-downloads`](#uv-python-find--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-python-find--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-python-find--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--quiet`](#uv-python-find--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--script`](#uv-python-find--script) *script* : Find the environment for a Python script, rather than the current project

[`--show-version`](#uv-python-find--show-version) : Show the Python version that would be used instead of the path to the interpreter

[`--system`](#uv-python-find--system) : Only find system Python interpreters.

```
By default, uv will report the first Python interpreter it would use, including those in an active virtual environment or a virtual environment in the current working directory or any parent directory.

The `--system` option instructs uv to skip virtual environment Python interpreters and restrict its search to the system path.

May also be set with the `UV_SYSTEM_PYTHON` environment variable.
```

[`--verbose`](#uv-python-find--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv python pin](#uv-python-pin)

Pin to a specific Python version.

Writes the pinned Python version to a `.python-version` file, which is used by other uv commands to determine the required Python version.

If no version is provided, uv will look for an existing `.python-version` file and display the currently pinned version. If no `.python-version` file is found, uv will exit with an error.

See `uv help python` to view supported request formats.

### Usage

```
uv python pin [OPTIONS] [REQUEST]

```

### Arguments

[REQUEST](#uv-python-pin--request) : The Python version request.

```
uv supports more formats than other tools that read `.python-version` files, i.e., `pyenv`. If compatibility with those tools is needed, only use version numbers instead of complex requests such as `cpython@3.10`.

If no request is provided, the currently pinned version will be shown.

See [uv python](#uv-python) to view supported request formats.
```

### Options

[`--allow-insecure-host`](#uv-python-pin--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-python-pin--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-python-pin--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-python-pin--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-python-pin--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--global`](#uv-python-pin--global) : Update the global Python version pin.

```
Writes the pinned Python version to a `.python-version` file in the uv user configuration directory: `XDG_CONFIG_HOME/uv` on Linux/macOS and `%APPDATA%/uv` on Windows.

When a local Python version pin is not found in the working directory or an ancestor directory, this version will be used instead.
```

[`--help`](#uv-python-pin--help), `-h` : Display the concise help for this command

[`--managed-python`](#uv-python-pin--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-python-pin--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-python-pin--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-python-pin--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-python-pin--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-python-pin--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-project`](#uv-python-pin--no-project), `--no-workspace` : Avoid validating the Python pin is compatible with the project or workspace.

```
By default, a project or workspace is discovered in the current directory or any parent directory. If a workspace is found, the Python pin is validated against the workspace's `requires-python` constraint.
```

[`--no-python-downloads`](#uv-python-pin--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-python-pin--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-python-pin--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--quiet`](#uv-python-pin--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--resolved`](#uv-python-pin--resolved) : Write the resolved Python interpreter path instead of the request.

```
Ensures that the exact same interpreter is used.

This option is usually not safe to use when committing the `.python-version` file to version control.
```

[`--rm`](#uv-python-pin--rm) : Remove the Python version pin

[`--verbose`](#uv-python-pin--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv python dir](#uv-python-dir)

Show the uv Python installation directory.

By default, Python installations are stored in the uv data directory at `$XDG_DATA_HOME/uv/python` or `$HOME/.local/share/uv/python` on Unix and `%APPDATA%\uv\data\python` on Windows.

The Python installation directory may be overridden with `$UV_PYTHON_INSTALL_DIR`.

To view the directory where uv installs Python executables instead, use the `--bin` flag. The Python executable directory may be overridden with `$UV_PYTHON_BIN_DIR`. Note that Python executables are only installed when preview mode is enabled.

### Usage

```
uv python dir [OPTIONS]

```

### Options

[`--allow-insecure-host`](#uv-python-dir--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--bin`](#uv-python-dir--bin) : Show the directory into which `uv python` will install Python executables.

```
Note that this directory is only used when installing Python with preview mode enabled.

The Python executable directory is determined according to the XDG standard and is derived
from the following environment variables, in order of preference:

- `$UV_PYTHON_BIN_DIR`
- `$XDG_BIN_HOME`
- `$XDG_DATA_HOME/../bin`
- `$HOME/.local/bin`
```

[`--cache-dir`](#uv-python-dir--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-python-dir--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-python-dir--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-python-dir--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--help`](#uv-python-dir--help), `-h` : Display the concise help for this command

[`--managed-python`](#uv-python-dir--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-python-dir--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-python-dir--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-python-dir--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-python-dir--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-python-dir--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-python-dir--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-python-dir--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-python-dir--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--quiet`](#uv-python-dir--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--verbose`](#uv-python-dir--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv python uninstall](#uv-python-uninstall)

Uninstall Python versions

### Usage

```
uv python uninstall [OPTIONS] <TARGETS>...

```

### Arguments

[TARGETS](#uv-python-uninstall--targets) : The Python version(s) to uninstall.

```
See [uv python](#uv-python) to view supported request formats.
```

### Options

[`--all`](#uv-python-uninstall--all) : Uninstall all managed Python versions

[`--allow-insecure-host`](#uv-python-uninstall--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-python-uninstall--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-python-uninstall--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-python-uninstall--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-python-uninstall--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--help`](#uv-python-uninstall--help), `-h` : Display the concise help for this command

[`--install-dir`](#uv-python-uninstall--install-dir), `-i` *install-dir* : The directory where the Python was installed

```
May also be set with the `UV_PYTHON_INSTALL_DIR` environment variable.
```

[`--managed-python`](#uv-python-uninstall--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-python-uninstall--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-python-uninstall--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-python-uninstall--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-python-uninstall--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-python-uninstall--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-python-uninstall--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-python-uninstall--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-python-uninstall--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--quiet`](#uv-python-uninstall--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--verbose`](#uv-python-uninstall--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv python update-shell](#uv-python-update-shell)

Ensure that the Python executable directory is on the `PATH`.

If the Python executable directory is not present on the `PATH`, uv will attempt to add it to the relevant shell configuration files.

If the shell configuration files already include a blurb to add the executable directory to the path, but the directory is not present on the `PATH`, uv will exit with an error.

The Python executable directory is determined according to the XDG standard and can be retrieved with `uv python dir --bin`.

### Usage

```
uv python update-shell [OPTIONS]

```

### Options

[`--allow-insecure-host`](#uv-python-update-shell--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-python-update-shell--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-python-update-shell--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-python-update-shell--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-python-update-shell--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--help`](#uv-python-update-shell--help), `-h` : Display the concise help for this command

[`--managed-python`](#uv-python-update-shell--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-python-update-shell--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-python-update-shell--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-python-update-shell--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-python-update-shell--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-python-update-shell--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-python-update-shell--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-python-update-shell--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-python-update-shell--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--quiet`](#uv-python-update-shell--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--verbose`](#uv-python-update-shell--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

## [uv pip](#uv-pip)

Manage Python packages with a pip-compatible interface

### Usage

```
uv pip [OPTIONS] <COMMAND>

```

### Commands

[`uv pip compile`](#uv-pip-compile) : Compile a `requirements.in` file to a `requirements.txt` or `pylock.toml` file

[`uv pip sync`](#uv-pip-sync) : Sync an environment with a `requirements.txt` or `pylock.toml` file

[`uv pip install`](#uv-pip-install) : Install packages into an environment

[`uv pip uninstall`](#uv-pip-uninstall) : Uninstall packages from an environment

[`uv pip freeze`](#uv-pip-freeze) : List, in requirements format, packages installed in an environment

[`uv pip list`](#uv-pip-list) : List, in tabular format, packages installed in an environment

[`uv pip show`](#uv-pip-show) : Show information about one or more installed packages

[`uv pip tree`](#uv-pip-tree) : Display the dependency tree for an environment

[`uv pip check`](#uv-pip-check) : Verify installed packages have compatible dependencies

### [uv pip compile](#uv-pip-compile)

Compile a `requirements.in` file to a `requirements.txt` or `pylock.toml` file

### Usage

```
uv pip compile [OPTIONS] <SRC_FILE|--group <GROUP>>

```

### Arguments

[SRC_FILE](#uv-pip-compile--src_file) : Include the packages listed in the given files.

```
The following formats are supported: `requirements.txt`, `.py` files with inline metadata, `pylock.toml`, `pyproject.toml`, `setup.py`, and `setup.cfg`.

If a `pyproject.toml`, `setup.py`, or `setup.cfg` file is provided, uv will extract the requirements for the relevant project.

If `-` is provided, then requirements will be read from stdin.

The order of the requirements files and the requirements in them is used to determine priority during resolution.
```

### Options

[`--all-extras`](#uv-pip-compile--all-extras) : Include all optional dependencies.

```
Only applies to `pyproject.toml`, `setup.py`, and `setup.cfg` sources.
```

[`--allow-insecure-host`](#uv-pip-compile--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--annotation-style`](#uv-pip-compile--annotation-style) *annotation-style* : The style of the annotation comments included in the output file, used to indicate the source of each package.

```
Defaults to `split`.

Possible values:

- `line`: Render the annotations on a single, comma-separated line
- `split`: Render each annotation on its own line
```

[`--build-constraints`](#uv-pip-compile--build-constraints), `--build-constraint`, `-b` *build-constraints* : Constrain build dependencies using the given requirements files when building source distributions.

```
Constraints files are `requirements.txt`-like files that only control the *version* of a requirement that's installed. However, including a package in a constraints file will *not* trigger the installation of that package.

May also be set with the `UV_BUILD_CONSTRAINT` environment variable.
```

[`--cache-dir`](#uv-pip-compile--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-pip-compile--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-pip-compile--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--config-setting`](#uv-pip-compile--config-setting), `--config-settings`, `-C` *config-setting* : Settings to pass to the PEP 517 build backend, specified as `KEY=VALUE` pairs

[`--config-settings-package`](#uv-pip-compile--config-settings-package), `--config-settings-package` *config-settings-package* : Settings to pass to the PEP 517 build backend for a specific package, specified as `PACKAGE:KEY=VALUE` pairs

[`--constraints`](#uv-pip-compile--constraints), `--constraint`, `-c` *constraints* : Constrain versions using the given requirements files.

```
Constraints files are `requirements.txt`-like files that only control the *version* of a requirement that's installed. However, including a package in a constraints file will *not* trigger the installation of that package.

This is equivalent to pip's `--constraint` option.

May also be set with the `UV_CONSTRAINT` environment variable.
```

[`--custom-compile-command`](#uv-pip-compile--custom-compile-command) *custom-compile-command* : The header comment to include at the top of the output file generated by `uv pip compile`.

```
Used to reflect custom build scripts and commands that wrap `uv pip compile`.

May also be set with the `UV_CUSTOM_COMPILE_COMMAND` environment variable.
```

[`--default-index`](#uv-pip-compile--default-index) *default-index* : The URL of the default package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--index` flag.

May also be set with the `UV_DEFAULT_INDEX` environment variable.
```

[`--directory`](#uv-pip-compile--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--emit-build-options`](#uv-pip-compile--emit-build-options) : Include `--no-binary` and `--only-binary` entries in the generated output file

[`--emit-find-links`](#uv-pip-compile--emit-find-links) : Include `--find-links` entries in the generated output file

[`--emit-index-annotation`](#uv-pip-compile--emit-index-annotation) : Include comment annotations indicating the index used to resolve each package (e.g., `# from https://pypi.org/simple`)

[`--emit-index-url`](#uv-pip-compile--emit-index-url) : Include `--index-url` and `--extra-index-url` entries in the generated output file

[`--exclude-newer`](#uv-pip-compile--exclude-newer) *exclude-newer* : Limit candidate packages to those that were uploaded prior to the given date.

```
Accepts both RFC 3339 timestamps (e.g., `2006-12-02T02:07:43Z`) and local dates in the same format (e.g., `2006-12-02`) in your system's configured time zone.

May also be set with the `UV_EXCLUDE_NEWER` environment variable.
```

[`--exclude-newer-package`](#uv-pip-compile--exclude-newer-package) *exclude-newer-package* : Limit candidate packages for a specific package to those that were uploaded prior to the given date.

```
Accepts package-date pairs in the format `PACKAGE=DATE`, where `DATE` is an RFC 3339 timestamp (e.g., `2006-12-02T02:07:43Z`) or local date (e.g., `2006-12-02`) in your system's configured time zone.

Can be provided multiple times for different packages.
```

[`--extra`](#uv-pip-compile--extra) *extra* : Include optional dependencies from the specified extra name; may be provided more than once.

```
Only applies to `pyproject.toml`, `setup.py`, and `setup.cfg` sources.
```

[`--extra-index-url`](#uv-pip-compile--extra-index-url) *extra-index-url* : (Deprecated: use `--index` instead) Extra URLs of package indexes to use, in addition to `--index-url`.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--index-url` (which defaults to PyPI). When multiple `--extra-index-url` flags are provided, earlier values take priority.

May also be set with the `UV_EXTRA_INDEX_URL` environment variable.
```

[`--find-links`](#uv-pip-compile--find-links), `-f` *find-links* : Locations to search for candidate distributions, in addition to those found in the registry indexes.

```
If a path, the target must be a directory that contains packages as wheel files (`.whl`) or source distributions (e.g., `.tar.gz` or `.zip`) at the top level.

If a URL, the page must contain a flat list of links to package files adhering to the formats described above.

May also be set with the `UV_FIND_LINKS` environment variable.
```

[`--fork-strategy`](#uv-pip-compile--fork-strategy) *fork-strategy* : The strategy to use when selecting multiple versions of a given package across Python versions and platforms.

```
By default, uv will optimize for selecting the latest version of each package for each supported Python version (`requires-python`), while minimizing the number of selected versions across platforms.

Under `fewest`, uv will minimize the number of selected versions for each package, preferring older versions that are compatible with a wider range of supported Python versions or platforms.

May also be set with the `UV_FORK_STRATEGY` environment variable.

Possible values:

- `fewest`: Optimize for selecting the fewest number of versions for each package. Older versions may be preferred if they are compatible with a wider range of supported Python versions or platforms
- `requires-python`: Optimize for selecting latest supported version of each package, for each supported Python version
```

[`--format`](#uv-pip-compile--format) *format* : The format in which the resolution should be output.

```
Supports both `requirements.txt` and `pylock.toml` (PEP 751) output formats.

uv will infer the output format from the file extension of the output file, if provided. Otherwise, defaults to `requirements.txt`.

Possible values:

- `requirements.txt`: Export in `requirements.txt` format
- `pylock.toml`: Export in `pylock.toml` format
```

[`--generate-hashes`](#uv-pip-compile--generate-hashes) : Include distribution hashes in the output file

[`--group`](#uv-pip-compile--group) *group* : Install the specified dependency group from a `pyproject.toml`.

```
If no path is provided, the `pyproject.toml` in the working directory is used.

May be provided multiple times.
```

[`--help`](#uv-pip-compile--help), `-h` : Display the concise help for this command

[`--index`](#uv-pip-compile--index) *index* : The URLs to use when resolving dependencies, in addition to the default index.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--default-index` (which defaults to PyPI). When multiple `--index` flags are provided, earlier values take priority.

Index names are not supported as values. Relative paths must be disambiguated from index names with `./` or `../` on Unix or `.\\`, `..\\`, `./` or `../` on Windows.

May also be set with the `UV_INDEX` environment variable.
```

[`--index-strategy`](#uv-pip-compile--index-strategy) *index-strategy* : The strategy to use when resolving against multiple index URLs.

```
By default, uv will stop at the first index on which a given package is available, and limit resolutions to those present on that first index (`first-index`). This prevents "dependency confusion" attacks, whereby an attacker can upload a malicious package under the same name to an alternate index.

May also be set with the `UV_INDEX_STRATEGY` environment variable.

Possible values:

- `first-index`: Only use results from the first index that returns a match for a given package name
- `unsafe-first-match`: Search for every package name across all indexes, exhausting the versions from the first index before moving on to the next
- `unsafe-best-match`: Search for every package name across all indexes, preferring the "best" version found. If a package version is in multiple indexes, only look at the entry for the first index
```

[`--index-url`](#uv-pip-compile--index-url), `-i` *index-url* : (Deprecated: use `--default-index` instead) The URL of the Python package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--extra-index-url` flag.

May also be set with the `UV_INDEX_URL` environment variable.
```

[`--keyring-provider`](#uv-pip-compile--keyring-provider) *keyring-provider* : Attempt to use `keyring` for authentication for index URLs.

```
At present, only `--keyring-provider subprocess` is supported, which configures uv to use the `keyring` CLI to handle authentication.

Defaults to `disabled`.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--link-mode`](#uv-pip-compile--link-mode) *link-mode* : The method to use when installing packages from the global cache.

```
This option is only used when building source distributions.

Defaults to `clone` (also known as Copy-on-Write) on macOS, and `hardlink` on Linux and Windows.

WARNING: The use of symlink link mode is discouraged, as they create tight coupling between the cache and the target environment. For example, clearing the cache (`uv cache clean`) will break all installed packages by way of removing the underlying source files. Use symlinks with caution.

May also be set with the `UV_LINK_MODE` environment variable.

Possible values:

- `clone`: Clone (i.e., copy-on-write) packages from the wheel into the `site-packages` directory
- `copy`: Copy packages from the wheel into the `site-packages` directory
- `hardlink`: Hard link packages from the wheel into the `site-packages` directory
- `symlink`: Symbolically link packages from the wheel into the `site-packages` directory
```

[`--managed-python`](#uv-pip-compile--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-pip-compile--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-annotate`](#uv-pip-compile--no-annotate) : Exclude comment annotations indicating the source of each package

[`--no-binary`](#uv-pip-compile--no-binary) *no-binary* : Don't install pre-built wheels.

```
The given packages will be built and installed from source. The resolver will still use pre-built wheels to extract package metadata, if available.

Multiple packages may be provided. Disable binaries for all packages with `:all:`. Clear previously specified packages with `:none:`.
```

[`--no-build`](#uv-pip-compile--no-build) : Don't build source distributions.

```
When enabled, resolving will not run arbitrary Python code. The cached wheels of already-built source distributions will be reused, but operations that require building distributions will exit with an error.

Alias for `--only-binary :all:`.
```

[`--no-build-isolation`](#uv-pip-compile--no-build-isolation) : Disable isolation when building source distributions.

```
Assumes that build dependencies specified by PEP 518 are already installed.

May also be set with the `UV_NO_BUILD_ISOLATION` environment variable.
```

[`--no-build-isolation-package`](#uv-pip-compile--no-build-isolation-package) *no-build-isolation-package* : Disable isolation when building source distributions for a specific package.

```
Assumes that the packages' build dependencies specified by PEP 518 are already installed.
```

[`--no-cache`](#uv-pip-compile--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-deps`](#uv-pip-compile--no-deps) : Ignore package dependencies, instead only add those packages explicitly listed on the command line to the resulting requirements file

[`--no-emit-package`](#uv-pip-compile--no-emit-package), `--unsafe-package` *no-emit-package* : Specify a package to omit from the output resolution. Its dependencies will still be included in the resolution. Equivalent to pip-compile's `--unsafe-package` option

[`--no-header`](#uv-pip-compile--no-header) : Exclude the comment header at the top of the generated output file

[`--no-index`](#uv-pip-compile--no-index) : Ignore the registry index (e.g., PyPI), instead relying on direct URL dependencies and those provided via `--find-links`

[`--no-managed-python`](#uv-pip-compile--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-pip-compile--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-pip-compile--no-python-downloads) : Disable automatic downloads of Python.

[`--no-sources`](#uv-pip-compile--no-sources) : Ignore the `tool.uv.sources` table when resolving dependencies. Used to lock against the standards-compliant, publishable package metadata, as opposed to using any workspace, Git, URL, or local path sources

[`--no-strip-extras`](#uv-pip-compile--no-strip-extras) : Include extras in the output file.

```
By default, uv strips extras, as any packages pulled in by the extras are already included as dependencies in the output file directly. Further, output files generated with `--no-strip-extras` cannot be used as constraints files in `install` and `sync` invocations.
```

[`--no-strip-markers`](#uv-pip-compile--no-strip-markers) : Include environment markers in the output file.

```
By default, uv strips environment markers, as the resolution generated by `compile` is only guaranteed to be correct for the target environment.
```

[`--offline`](#uv-pip-compile--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--only-binary`](#uv-pip-compile--only-binary) *only-binary* : Only use pre-built wheels; don't build source distributions.

```
When enabled, resolving will not run code from the given packages. The cached wheels of already-built source distributions will be reused, but operations that require building distributions will exit with an error.

Multiple packages may be provided. Disable binaries for all packages with `:all:`. Clear previously specified packages with `:none:`.
```

[`--output-file`](#uv-pip-compile--output-file), `-o` *output-file* : Write the compiled requirements to the given `requirements.txt` or `pylock.toml` file.

```
If the file already exists, the existing versions will be preferred when resolving dependencies, unless `--upgrade` is also specified.
```

[`--overrides`](#uv-pip-compile--overrides), `--override` *overrides* : Override versions using the given requirements files.

```
Overrides files are `requirements.txt`-like files that force a specific version of a requirement to be installed, regardless of the requirements declared by any constituent package, and regardless of whether this would be considered an invalid resolution.

While constraints are *additive*, in that they're combined with the requirements of the constituent packages, overrides are *absolute*, in that they completely replace the requirements of the constituent packages.

May also be set with the `UV_OVERRIDE` environment variable.
```

[`--prerelease`](#uv-pip-compile--prerelease) *prerelease* : The strategy to use when considering pre-release versions.

```
By default, uv will accept pre-releases for packages that *only* publish pre-releases, along with first-party requirements that contain an explicit pre-release marker in the declared specifiers (`if-necessary-or-explicit`).

May also be set with the `UV_PRERELEASE` environment variable.

Possible values:

- `disallow`: Disallow all pre-release versions
- `allow`: Allow all pre-release versions
- `if-necessary`: Allow pre-release versions if all versions of a package are pre-release
- `explicit`: Allow pre-release versions for first-party packages with explicit pre-release markers in their version requirements
- `if-necessary-or-explicit`: Allow pre-release versions if all versions of a package are pre-release, or if the package has an explicit pre-release marker in its version requirements
```

[`--project`](#uv-pip-compile--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--python`](#uv-pip-compile--python), `-p` *python* : The Python interpreter to use during resolution.

```
A Python interpreter is required for building source distributions to determine package
metadata when there are not wheels.

The interpreter is also used to determine the default minimum Python version, unless
`--python-version` is provided.

This option respects `UV_PYTHON`, but when set via environment variable, it is overridden
by `--python-version`.

See [uv python](#uv-python) for details on Python discovery and supported request formats.
```

[`--python-platform`](#uv-pip-compile--python-platform) *python-platform* : The platform for which requirements should be resolved.

```
Represented as a "target triple", a string that describes the target platform in terms of its CPU, vendor, and operating system name, like `x86_64-unknown-linux-gnu` or `aarch64-apple-darwin`.

When targeting macOS (Darwin), the default minimum version is `13.0`. Use `MACOSX_DEPLOYMENT_TARGET` to specify a different minimum version, e.g., `14.0`.

When targeting iOS, the default minimum version is `13.0`. Use `IPHONEOS_DEPLOYMENT_TARGET` to specify a different minimum version, e.g., `14.0`.

When targeting Android, the default minimum Android API level is `24`. Use `ANDROID_API_LEVEL` to specify a different minimum version, e.g., `26`.

Possible values:

- `windows`: An alias for `x86_64-pc-windows-msvc`, the default target for Windows
- `linux`: An alias for `x86_64-unknown-linux-gnu`, the default target for Linux
- `macos`: An alias for `aarch64-apple-darwin`, the default target for macOS
- `x86_64-pc-windows-msvc`: A 64-bit x86 Windows target
- `aarch64-pc-windows-msvc`: An ARM64 Windows target
- `i686-pc-windows-msvc`: A 32-bit x86 Windows target
- `x86_64-unknown-linux-gnu`: An x86 Linux target. Equivalent to `x86_64-manylinux_2_28`
- `aarch64-apple-darwin`: An ARM-based macOS target, as seen on Apple Silicon devices
- `x86_64-apple-darwin`: An x86 macOS target
- `aarch64-unknown-linux-gnu`: An ARM64 Linux target. Equivalent to `aarch64-manylinux_2_28`
- `aarch64-unknown-linux-musl`: An ARM64 Linux target
- `x86_64-unknown-linux-musl`: An `x86_64` Linux target
- `riscv64-unknown-linux`: A RISCV64 Linux target
- `x86_64-manylinux2014`: An `x86_64` target for the `manylinux2014` platform. Equivalent to `x86_64-manylinux_2_17`
- `x86_64-manylinux_2_17`: An `x86_64` target for the `manylinux_2_17` platform
- `x86_64-manylinux_2_28`: An `x86_64` target for the `manylinux_2_28` platform
- `x86_64-manylinux_2_31`: An `x86_64` target for the `manylinux_2_31` platform
- `x86_64-manylinux_2_32`: An `x86_64` target for the `manylinux_2_32` platform
- `x86_64-manylinux_2_33`: An `x86_64` target for the `manylinux_2_33` platform
- `x86_64-manylinux_2_34`: An `x86_64` target for the `manylinux_2_34` platform
- `x86_64-manylinux_2_35`: An `x86_64` target for the `manylinux_2_35` platform
- `x86_64-manylinux_2_36`: An `x86_64` target for the `manylinux_2_36` platform
- `x86_64-manylinux_2_37`: An `x86_64` target for the `manylinux_2_37` platform
- `x86_64-manylinux_2_38`: An `x86_64` target for the `manylinux_2_38` platform
- `x86_64-manylinux_2_39`: An `x86_64` target for the `manylinux_2_39` platform
- `x86_64-manylinux_2_40`: An `x86_64` target for the `manylinux_2_40` platform
- `aarch64-manylinux2014`: An ARM64 target for the `manylinux2014` platform. Equivalent to `aarch64-manylinux_2_17`
- `aarch64-manylinux_2_17`: An ARM64 target for the `manylinux_2_17` platform
- `aarch64-manylinux_2_28`: An ARM64 target for the `manylinux_2_28` platform
- `aarch64-manylinux_2_31`: An ARM64 target for the `manylinux_2_31` platform
- `aarch64-manylinux_2_32`: An ARM64 target for the `manylinux_2_32` platform
- `aarch64-manylinux_2_33`: An ARM64 target for the `manylinux_2_33` platform
- `aarch64-manylinux_2_34`: An ARM64 target for the `manylinux_2_34` platform
- `aarch64-manylinux_2_35`: An ARM64 target for the `manylinux_2_35` platform
- `aarch64-manylinux_2_36`: An ARM64 target for the `manylinux_2_36` platform
- `aarch64-manylinux_2_37`: An ARM64 target for the `manylinux_2_37` platform
- `aarch64-manylinux_2_38`: An ARM64 target for the `manylinux_2_38` platform
- `aarch64-manylinux_2_39`: An ARM64 target for the `manylinux_2_39` platform
- `aarch64-manylinux_2_40`: An ARM64 target for the `manylinux_2_40` platform
- `aarch64-linux-android`: An ARM64 Android target
- `x86_64-linux-android`: An `x86_64` Android target
- `wasm32-pyodide2024`: A wasm32 target using the Pyodide 2024 platform. Meant for use with Python 3.12
- `arm64-apple-ios`: An ARM64 target for iOS device
- `arm64-apple-ios-simulator`: An ARM64 target for iOS simulator
- `x86_64-apple-ios-simulator`: An `x86_64` target for iOS simulator
```

[`--python-version`](#uv-pip-compile--python-version) *python-version* : The Python version to use for resolution.

```
For example, `3.8` or `3.8.17`.

Defaults to the version of the Python interpreter used for resolution.

Defines the minimum Python version that must be supported by the resolved requirements.

If a patch version is omitted, the minimum patch version is assumed. For example, `3.8` is mapped to `3.8.0`.
```

[`--quiet`](#uv-pip-compile--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--refresh`](#uv-pip-compile--refresh) : Refresh all cached data

[`--refresh-package`](#uv-pip-compile--refresh-package) *refresh-package* : Refresh cached data for a specific package

[`--resolution`](#uv-pip-compile--resolution) *resolution* : The strategy to use when selecting between the different compatible versions for a given package requirement.

```
By default, uv will use the latest compatible version of each package (`highest`).

May also be set with the `UV_RESOLUTION` environment variable.

Possible values:

- `highest`: Resolve the highest compatible version of each package
- `lowest`: Resolve the lowest compatible version of each package
- `lowest-direct`: Resolve the lowest compatible version of any direct dependencies, and the highest compatible version of any transitive dependencies
```

[`--system`](#uv-pip-compile--system) : Install packages into the system Python environment.

```
By default, uv uses the virtual environment in the current working directory or any parent directory, falling back to searching for a Python executable in `PATH`. The `--system` option instructs uv to avoid using a virtual environment Python and restrict its search to the system path.

May also be set with the `UV_SYSTEM_PYTHON` environment variable.
```

[`--torch-backend`](#uv-pip-compile--torch-backend) *torch-backend* : The backend to use when fetching packages in the PyTorch ecosystem (e.g., `cpu`, `cu126`, or `auto`).

```
When set, uv will ignore the configured index URLs for packages in the PyTorch ecosystem, and will instead use the defined backend.

For example, when set to `cpu`, uv will use the CPU-only PyTorch index; when set to `cu126`, uv will use the PyTorch index for CUDA 12.6.

The `auto` mode will attempt to detect the appropriate PyTorch index based on the currently installed CUDA drivers.

This option is in preview and may change in any future release.

May also be set with the `UV_TORCH_BACKEND` environment variable.

Possible values:

- `auto`: Select the appropriate PyTorch index based on the operating system and CUDA driver version
- `cpu`: Use the CPU-only PyTorch index
- `cu130`: Use the PyTorch index for CUDA 13.0
- `cu129`: Use the PyTorch index for CUDA 12.9
- `cu128`: Use the PyTorch index for CUDA 12.8
- `cu126`: Use the PyTorch index for CUDA 12.6
- `cu125`: Use the PyTorch index for CUDA 12.5
- `cu124`: Use the PyTorch index for CUDA 12.4
- `cu123`: Use the PyTorch index for CUDA 12.3
- `cu122`: Use the PyTorch index for CUDA 12.2
- `cu121`: Use the PyTorch index for CUDA 12.1
- `cu120`: Use the PyTorch index for CUDA 12.0
- `cu118`: Use the PyTorch index for CUDA 11.8
- `cu117`: Use the PyTorch index for CUDA 11.7
- `cu116`: Use the PyTorch index for CUDA 11.6
- `cu115`: Use the PyTorch index for CUDA 11.5
- `cu114`: Use the PyTorch index for CUDA 11.4
- `cu113`: Use the PyTorch index for CUDA 11.3
- `cu112`: Use the PyTorch index for CUDA 11.2
- `cu111`: Use the PyTorch index for CUDA 11.1
- `cu110`: Use the PyTorch index for CUDA 11.0
- `cu102`: Use the PyTorch index for CUDA 10.2
- `cu101`: Use the PyTorch index for CUDA 10.1
- `cu100`: Use the PyTorch index for CUDA 10.0
- `cu92`: Use the PyTorch index for CUDA 9.2
- `cu91`: Use the PyTorch index for CUDA 9.1
- `cu90`: Use the PyTorch index for CUDA 9.0
- `cu80`: Use the PyTorch index for CUDA 8.0
- `rocm6.3`: Use the PyTorch index for ROCm 6.3
- `rocm6.2.4`: Use the PyTorch index for ROCm 6.2.4
- `rocm6.2`: Use the PyTorch index for ROCm 6.2
- `rocm6.1`: Use the PyTorch index for ROCm 6.1
- `rocm6.0`: Use the PyTorch index for ROCm 6.0
- `rocm5.7`: Use the PyTorch index for ROCm 5.7
- `rocm5.6`: Use the PyTorch index for ROCm 5.6
- `rocm5.5`: Use the PyTorch index for ROCm 5.5
- `rocm5.4.2`: Use the PyTorch index for ROCm 5.4.2
- `rocm5.4`: Use the PyTorch index for ROCm 5.4
- `rocm5.3`: Use the PyTorch index for ROCm 5.3
- `rocm5.2`: Use the PyTorch index for ROCm 5.2
- `rocm5.1.1`: Use the PyTorch index for ROCm 5.1.1
- `rocm4.2`: Use the PyTorch index for ROCm 4.2
- `rocm4.1`: Use the PyTorch index for ROCm 4.1
- `rocm4.0.1`: Use the PyTorch index for ROCm 4.0.1
- `xpu`: Use the PyTorch index for Intel XPU
```

[`--universal`](#uv-pip-compile--universal) : Perform a universal resolution, attempting to generate a single `requirements.txt` output file that is compatible with all operating systems, architectures, and Python implementations.

```
In universal mode, the current Python version (or user-provided `--python-version`) will be treated as a lower bound. For example, `--universal --python-version 3.7` would produce a universal resolution for Python 3.7 and later.

Implies `--no-strip-markers`.
```

[`--upgrade`](#uv-pip-compile--upgrade), `-U` : Allow package upgrades, ignoring pinned versions in any existing output file. Implies `--refresh`

[`--upgrade-package`](#uv-pip-compile--upgrade-package), `-P` *upgrade-package* : Allow upgrades for a specific package, ignoring pinned versions in any existing output file. Implies `--refresh-package`

[`--verbose`](#uv-pip-compile--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv pip sync](#uv-pip-sync)

Sync an environment with a `requirements.txt` or `pylock.toml` file.

When syncing an environment, any packages not listed in the `requirements.txt` or `pylock.toml` file will be removed. To retain extraneous packages, use `uv pip install` instead.

The input file is presumed to be the output of a `pip compile` or `uv export` operation, in which it will include all transitive dependencies. If transitive dependencies are not present in the file, they will not be installed. Use `--strict` to warn if any transitive dependencies are missing.

### Usage

```
uv pip sync [OPTIONS] <SRC_FILE>...

```

### Arguments

[SRC_FILE](#uv-pip-sync--src_file) : Include the packages listed in the given files.

```
The following formats are supported: `requirements.txt`, `.py` files with inline metadata, `pylock.toml`, `pyproject.toml`, `setup.py`, and `setup.cfg`.

If a `pyproject.toml`, `setup.py`, or `setup.cfg` file is provided, uv will extract the requirements for the relevant project.

If `-` is provided, then requirements will be read from stdin.
```

### Options

[`--all-extras`](#uv-pip-sync--all-extras) : Include all optional dependencies.

```
Only applies to `pylock.toml`, `pyproject.toml`, `setup.py`, and `setup.cfg` sources.
```

[`--allow-empty-requirements`](#uv-pip-sync--allow-empty-requirements) : Allow sync of empty requirements, which will clear the environment of all packages

[`--allow-insecure-host`](#uv-pip-sync--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--break-system-packages`](#uv-pip-sync--break-system-packages) : Allow uv to modify an `EXTERNALLY-MANAGED` Python installation.

```
WARNING: `--break-system-packages` is intended for use in continuous integration (CI) environments, when installing into Python installations that are managed by an external package manager, like `apt`. It should be used with caution, as such Python installations explicitly recommend against modifications by other package managers (like uv or `pip`).

May also be set with the `UV_BREAK_SYSTEM_PACKAGES` environment variable.
```

[`--build-constraints`](#uv-pip-sync--build-constraints), `--build-constraint`, `-b` *build-constraints* : Constrain build dependencies using the given requirements files when building source distributions.

```
Constraints files are `requirements.txt`-like files that only control the *version* of a requirement that's installed. However, including a package in a constraints file will *not* trigger the installation of that package.

May also be set with the `UV_BUILD_CONSTRAINT` environment variable.
```

[`--cache-dir`](#uv-pip-sync--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-pip-sync--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--compile-bytecode`](#uv-pip-sync--compile-bytecode), `--compile` : Compile Python files to bytecode after installation.

```
By default, uv does not compile Python (`.py`) files to bytecode (`__pycache__/*.pyc`); instead, compilation is performed lazily the first time a module is imported. For use-cases in which start time is critical, such as CLI applications and Docker containers, this option can be enabled to trade longer installation times for faster start times.

When enabled, uv will process the entire site-packages directory (including packages that are not being modified by the current operation) for consistency. Like pip, it will also ignore errors.

May also be set with the `UV_COMPILE_BYTECODE` environment variable.
```

[`--config-file`](#uv-pip-sync--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--config-setting`](#uv-pip-sync--config-setting), `--config-settings`, `-C` *config-setting* : Settings to pass to the PEP 517 build backend, specified as `KEY=VALUE` pairs

[`--config-settings-package`](#uv-pip-sync--config-settings-package), `--config-settings-package` *config-settings-package* : Settings to pass to the PEP 517 build backend for a specific package, specified as `PACKAGE:KEY=VALUE` pairs

[`--constraints`](#uv-pip-sync--constraints), `--constraint`, `-c` *constraints* : Constrain versions using the given requirements files.

```
Constraints files are `requirements.txt`-like files that only control the *version* of a requirement that's installed. However, including a package in a constraints file will *not* trigger the installation of that package.

This is equivalent to pip's `--constraint` option.

May also be set with the `UV_CONSTRAINT` environment variable.
```

[`--default-index`](#uv-pip-sync--default-index) *default-index* : The URL of the default package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--index` flag.

May also be set with the `UV_DEFAULT_INDEX` environment variable.
```

[`--directory`](#uv-pip-sync--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--dry-run`](#uv-pip-sync--dry-run) : Perform a dry run, i.e., don't actually install anything but resolve the dependencies and print the resulting plan

[`--exclude-newer`](#uv-pip-sync--exclude-newer) *exclude-newer* : Limit candidate packages to those that were uploaded prior to the given date.

```
Accepts both RFC 3339 timestamps (e.g., `2006-12-02T02:07:43Z`) and local dates in the same format (e.g., `2006-12-02`) in your system's configured time zone.

May also be set with the `UV_EXCLUDE_NEWER` environment variable.
```

[`--exclude-newer-package`](#uv-pip-sync--exclude-newer-package) *exclude-newer-package* : Limit candidate packages for specific packages to those that were uploaded prior to the given date.

```
Accepts package-date pairs in the format `PACKAGE=DATE`, where `DATE` is an RFC 3339 timestamp (e.g., `2006-12-02T02:07:43Z`) or local date (e.g., `2006-12-02`) in your system's configured time zone.

Can be provided multiple times for different packages.
```

[`--extra`](#uv-pip-sync--extra) *extra* : Include optional dependencies from the specified extra name; may be provided more than once.

```
Only applies to `pylock.toml`, `pyproject.toml`, `setup.py`, and `setup.cfg` sources.
```

[`--extra-index-url`](#uv-pip-sync--extra-index-url) *extra-index-url* : (Deprecated: use `--index` instead) Extra URLs of package indexes to use, in addition to `--index-url`.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--index-url` (which defaults to PyPI). When multiple `--extra-index-url` flags are provided, earlier values take priority.

May also be set with the `UV_EXTRA_INDEX_URL` environment variable.
```

[`--find-links`](#uv-pip-sync--find-links), `-f` *find-links* : Locations to search for candidate distributions, in addition to those found in the registry indexes.

```
If a path, the target must be a directory that contains packages as wheel files (`.whl`) or source distributions (e.g., `.tar.gz` or `.zip`) at the top level.

If a URL, the page must contain a flat list of links to package files adhering to the formats described above.

May also be set with the `UV_FIND_LINKS` environment variable.
```

[`--group`](#uv-pip-sync--group) *group* : Install the specified dependency group from a `pylock.toml` or `pyproject.toml`.

```
If no path is provided, the `pylock.toml` or `pyproject.toml` in the working directory is used.

May be provided multiple times.
```

[`--help`](#uv-pip-sync--help), `-h` : Display the concise help for this command

[`--index`](#uv-pip-sync--index) *index* : The URLs to use when resolving dependencies, in addition to the default index.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--default-index` (which defaults to PyPI). When multiple `--index` flags are provided, earlier values take priority.

Index names are not supported as values. Relative paths must be disambiguated from index names with `./` or `../` on Unix or `.\\`, `..\\`, `./` or `../` on Windows.

May also be set with the `UV_INDEX` environment variable.
```

[`--index-strategy`](#uv-pip-sync--index-strategy) *index-strategy* : The strategy to use when resolving against multiple index URLs.

```
By default, uv will stop at the first index on which a given package is available, and limit resolutions to those present on that first index (`first-index`). This prevents "dependency confusion" attacks, whereby an attacker can upload a malicious package under the same name to an alternate index.

May also be set with the `UV_INDEX_STRATEGY` environment variable.

Possible values:

- `first-index`: Only use results from the first index that returns a match for a given package name
- `unsafe-first-match`: Search for every package name across all indexes, exhausting the versions from the first index before moving on to the next
- `unsafe-best-match`: Search for every package name across all indexes, preferring the "best" version found. If a package version is in multiple indexes, only look at the entry for the first index
```

[`--index-url`](#uv-pip-sync--index-url), `-i` *index-url* : (Deprecated: use `--default-index` instead) The URL of the Python package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--extra-index-url` flag.

May also be set with the `UV_INDEX_URL` environment variable.
```

[`--keyring-provider`](#uv-pip-sync--keyring-provider) *keyring-provider* : Attempt to use `keyring` for authentication for index URLs.

```
At present, only `--keyring-provider subprocess` is supported, which configures uv to use the `keyring` CLI to handle authentication.

Defaults to `disabled`.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--link-mode`](#uv-pip-sync--link-mode) *link-mode* : The method to use when installing packages from the global cache.

```
Defaults to `clone` (also known as Copy-on-Write) on macOS, and `hardlink` on Linux and Windows.

WARNING: The use of symlink link mode is discouraged, as they create tight coupling between the cache and the target environment. For example, clearing the cache (`uv cache clean`) will break all installed packages by way of removing the underlying source files. Use symlinks with caution.

May also be set with the `UV_LINK_MODE` environment variable.

Possible values:

- `clone`: Clone (i.e., copy-on-write) packages from the wheel into the `site-packages` directory
- `copy`: Copy packages from the wheel into the `site-packages` directory
- `hardlink`: Hard link packages from the wheel into the `site-packages` directory
- `symlink`: Symbolically link packages from the wheel into the `site-packages` directory
```

[`--managed-python`](#uv-pip-sync--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-pip-sync--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-allow-empty-requirements`](#uv-pip-sync--no-allow-empty-requirements)

[`--no-binary`](#uv-pip-sync--no-binary) *no-binary* : Don't install pre-built wheels.

```
The given packages will be built and installed from source. The resolver will still use pre-built wheels to extract package metadata, if available.

Multiple packages may be provided. Disable binaries for all packages with `:all:`. Clear previously specified packages with `:none:`.
```

[`--no-break-system-packages`](#uv-pip-sync--no-break-system-packages)

[`--no-build`](#uv-pip-sync--no-build) : Don't build source distributions.

```
When enabled, resolving will not run arbitrary Python code. The cached wheels of already-built source distributions will be reused, but operations that require building distributions will exit with an error.

Alias for `--only-binary :all:`.
```

[`--no-build-isolation`](#uv-pip-sync--no-build-isolation) : Disable isolation when building source distributions.

```
Assumes that build dependencies specified by PEP 518 are already installed.

May also be set with the `UV_NO_BUILD_ISOLATION` environment variable.
```

[`--no-cache`](#uv-pip-sync--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-index`](#uv-pip-sync--no-index) : Ignore the registry index (e.g., PyPI), instead relying on direct URL dependencies and those provided via `--find-links`

[`--no-managed-python`](#uv-pip-sync--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-pip-sync--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-pip-sync--no-python-downloads) : Disable automatic downloads of Python.

[`--no-sources`](#uv-pip-sync--no-sources) : Ignore the `tool.uv.sources` table when resolving dependencies. Used to lock against the standards-compliant, publishable package metadata, as opposed to using any workspace, Git, URL, or local path sources

[`--no-verify-hashes`](#uv-pip-sync--no-verify-hashes) : Disable validation of hashes in the requirements file.

```
By default, uv will verify any available hashes in the requirements file, but will not require that all requirements have an associated hash. To enforce hash validation, use `--require-hashes`.

May also be set with the `UV_NO_VERIFY_HASHES` environment variable.
```

[`--offline`](#uv-pip-sync--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--only-binary`](#uv-pip-sync--only-binary) *only-binary* : Only use pre-built wheels; don't build source distributions.

```
When enabled, resolving will not run code from the given packages. The cached wheels of already-built source distributions will be reused, but operations that require building distributions will exit with an error.

Multiple packages may be provided. Disable binaries for all packages with `:all:`. Clear previously specified packages with `:none:`.
```

[`--prefix`](#uv-pip-sync--prefix) *prefix* : Install packages into `lib`, `bin`, and other top-level folders under the specified directory, as if a virtual environment were present at that location.

```
In general, prefer the use of `--python` to install into an alternate environment, as scripts and other artifacts installed via `--prefix` will reference the installing interpreter, rather than any interpreter added to the `--prefix` directory, rendering them non-portable.
```

[`--project`](#uv-pip-sync--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--python`](#uv-pip-sync--python), `-p` *python* : The Python interpreter into which packages should be installed.

```
By default, syncing requires a virtual environment. A path to an alternative Python can be
provided, but it is only recommended in continuous integration (CI) environments and should
be used with caution, as it can modify the system Python installation.

See [uv python](#uv-python) for details on Python discovery and supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--python-platform`](#uv-pip-sync--python-platform) *python-platform* : The platform for which requirements should be installed.

```
Represented as a "target triple", a string that describes the target platform in terms of its CPU, vendor, and operating system name, like `x86_64-unknown-linux-gnu` or `aarch64-apple-darwin`.

When targeting macOS (Darwin), the default minimum version is `13.0`. Use `MACOSX_DEPLOYMENT_TARGET` to specify a different minimum version, e.g., `14.0`.

When targeting iOS, the default minimum version is `13.0`. Use `IPHONEOS_DEPLOYMENT_TARGET` to specify a different minimum version, e.g., `14.0`.

When targeting Android, the default minimum Android API level is `24`. Use `ANDROID_API_LEVEL` to specify a different minimum version, e.g., `26`.

WARNING: When specified, uv will select wheels that are compatible with the *target* platform; as a result, the installed distributions may not be compatible with the *current* platform. Conversely, any distributions that are built from source may be incompatible with the *target* platform, as they will be built for the *current* platform. The `--python-platform` option is intended for advanced use cases.

Possible values:

- `windows`: An alias for `x86_64-pc-windows-msvc`, the default target for Windows
- `linux`: An alias for `x86_64-unknown-linux-gnu`, the default target for Linux
- `macos`: An alias for `aarch64-apple-darwin`, the default target for macOS
- `x86_64-pc-windows-msvc`: A 64-bit x86 Windows target
- `aarch64-pc-windows-msvc`: An ARM64 Windows target
- `i686-pc-windows-msvc`: A 32-bit x86 Windows target
- `x86_64-unknown-linux-gnu`: An x86 Linux target. Equivalent to `x86_64-manylinux_2_28`
- `aarch64-apple-darwin`: An ARM-based macOS target, as seen on Apple Silicon devices
- `x86_64-apple-darwin`: An x86 macOS target
- `aarch64-unknown-linux-gnu`: An ARM64 Linux target. Equivalent to `aarch64-manylinux_2_28`
- `aarch64-unknown-linux-musl`: An ARM64 Linux target
- `x86_64-unknown-linux-musl`: An `x86_64` Linux target
- `riscv64-unknown-linux`: A RISCV64 Linux target
- `x86_64-manylinux2014`: An `x86_64` target for the `manylinux2014` platform. Equivalent to `x86_64-manylinux_2_17`
- `x86_64-manylinux_2_17`: An `x86_64` target for the `manylinux_2_17` platform
- `x86_64-manylinux_2_28`: An `x86_64` target for the `manylinux_2_28` platform
- `x86_64-manylinux_2_31`: An `x86_64` target for the `manylinux_2_31` platform
- `x86_64-manylinux_2_32`: An `x86_64` target for the `manylinux_2_32` platform
- `x86_64-manylinux_2_33`: An `x86_64` target for the `manylinux_2_33` platform
- `x86_64-manylinux_2_34`: An `x86_64` target for the `manylinux_2_34` platform
- `x86_64-manylinux_2_35`: An `x86_64` target for the `manylinux_2_35` platform
- `x86_64-manylinux_2_36`: An `x86_64` target for the `manylinux_2_36` platform
- `x86_64-manylinux_2_37`: An `x86_64` target for the `manylinux_2_37` platform
- `x86_64-manylinux_2_38`: An `x86_64` target for the `manylinux_2_38` platform
- `x86_64-manylinux_2_39`: An `x86_64` target for the `manylinux_2_39` platform
- `x86_64-manylinux_2_40`: An `x86_64` target for the `manylinux_2_40` platform
- `aarch64-manylinux2014`: An ARM64 target for the `manylinux2014` platform. Equivalent to `aarch64-manylinux_2_17`
- `aarch64-manylinux_2_17`: An ARM64 target for the `manylinux_2_17` platform
- `aarch64-manylinux_2_28`: An ARM64 target for the `manylinux_2_28` platform
- `aarch64-manylinux_2_31`: An ARM64 target for the `manylinux_2_31` platform
- `aarch64-manylinux_2_32`: An ARM64 target for the `manylinux_2_32` platform
- `aarch64-manylinux_2_33`: An ARM64 target for the `manylinux_2_33` platform
- `aarch64-manylinux_2_34`: An ARM64 target for the `manylinux_2_34` platform
- `aarch64-manylinux_2_35`: An ARM64 target for the `manylinux_2_35` platform
- `aarch64-manylinux_2_36`: An ARM64 target for the `manylinux_2_36` platform
- `aarch64-manylinux_2_37`: An ARM64 target for the `manylinux_2_37` platform
- `aarch64-manylinux_2_38`: An ARM64 target for the `manylinux_2_38` platform
- `aarch64-manylinux_2_39`: An ARM64 target for the `manylinux_2_39` platform
- `aarch64-manylinux_2_40`: An ARM64 target for the `manylinux_2_40` platform
- `aarch64-linux-android`: An ARM64 Android target
- `x86_64-linux-android`: An `x86_64` Android target
- `wasm32-pyodide2024`: A wasm32 target using the Pyodide 2024 platform. Meant for use with Python 3.12
- `arm64-apple-ios`: An ARM64 target for iOS device
- `arm64-apple-ios-simulator`: An ARM64 target for iOS simulator
- `x86_64-apple-ios-simulator`: An `x86_64` target for iOS simulator
```

[`--python-version`](#uv-pip-sync--python-version) *python-version* : The minimum Python version that should be supported by the requirements (e.g., `3.7` or `3.7.9`).

```
If a patch version is omitted, the minimum patch version is assumed. For example, `3.7` is mapped to `3.7.0`.
```

[`--quiet`](#uv-pip-sync--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--refresh`](#uv-pip-sync--refresh) : Refresh all cached data

[`--refresh-package`](#uv-pip-sync--refresh-package) *refresh-package* : Refresh cached data for a specific package

[`--reinstall`](#uv-pip-sync--reinstall), `--force-reinstall` : Reinstall all packages, regardless of whether they're already installed. Implies `--refresh`

[`--reinstall-package`](#uv-pip-sync--reinstall-package) *reinstall-package* : Reinstall a specific package, regardless of whether it's already installed. Implies `--refresh-package`

[`--require-hashes`](#uv-pip-sync--require-hashes) : Require a matching hash for each requirement.

```
By default, uv will verify any available hashes in the requirements file, but will not require that all requirements have an associated hash.

When `--require-hashes` is enabled, *all* requirements must include a hash or set of hashes, and *all* requirements must either be pinned to exact versions (e.g., `==1.0.0`), or be specified via direct URL.

Hash-checking mode introduces a number of additional constraints:

- Git dependencies are not supported. - Editable installations are not supported. - Local dependencies are not supported, unless they point to a specific wheel (`.whl`) or source archive (`.zip`, `.tar.gz`), as opposed to a directory.

May also be set with the `UV_REQUIRE_HASHES` environment variable.
```

[`--strict`](#uv-pip-sync--strict) : Validate the Python environment after completing the installation, to detect packages with missing dependencies or other issues

[`--system`](#uv-pip-sync--system) : Install packages into the system Python environment.

```
By default, uv installs into the virtual environment in the current working directory or any parent directory. The `--system` option instructs uv to instead use the first Python found in the system `PATH`.

WARNING: `--system` is intended for use in continuous integration (CI) environments and should be used with caution, as it can modify the system Python installation.

May also be set with the `UV_SYSTEM_PYTHON` environment variable.
```

[`--target`](#uv-pip-sync--target) *target* : Install packages into the specified directory, rather than into the virtual or system Python environment. The packages will be installed at the top-level of the directory

[`--torch-backend`](#uv-pip-sync--torch-backend) *torch-backend* : The backend to use when fetching packages in the PyTorch ecosystem (e.g., `cpu`, `cu126`, or `auto`).

```
When set, uv will ignore the configured index URLs for packages in the PyTorch ecosystem, and will instead use the defined backend.

For example, when set to `cpu`, uv will use the CPU-only PyTorch index; when set to `cu126`, uv will use the PyTorch index for CUDA 12.6.

The `auto` mode will attempt to detect the appropriate PyTorch index based on the currently installed CUDA drivers.

This option is in preview and may change in any future release.

May also be set with the `UV_TORCH_BACKEND` environment variable.

Possible values:

- `auto`: Select the appropriate PyTorch index based on the operating system and CUDA driver version
- `cpu`: Use the CPU-only PyTorch index
- `cu130`: Use the PyTorch index for CUDA 13.0
- `cu129`: Use the PyTorch index for CUDA 12.9
- `cu128`: Use the PyTorch index for CUDA 12.8
- `cu126`: Use the PyTorch index for CUDA 12.6
- `cu125`: Use the PyTorch index for CUDA 12.5
- `cu124`: Use the PyTorch index for CUDA 12.4
- `cu123`: Use the PyTorch index for CUDA 12.3
- `cu122`: Use the PyTorch index for CUDA 12.2
- `cu121`: Use the PyTorch index for CUDA 12.1
- `cu120`: Use the PyTorch index for CUDA 12.0
- `cu118`: Use the PyTorch index for CUDA 11.8
- `cu117`: Use the PyTorch index for CUDA 11.7
- `cu116`: Use the PyTorch index for CUDA 11.6
- `cu115`: Use the PyTorch index for CUDA 11.5
- `cu114`: Use the PyTorch index for CUDA 11.4
- `cu113`: Use the PyTorch index for CUDA 11.3
- `cu112`: Use the PyTorch index for CUDA 11.2
- `cu111`: Use the PyTorch index for CUDA 11.1
- `cu110`: Use the PyTorch index for CUDA 11.0
- `cu102`: Use the PyTorch index for CUDA 10.2
- `cu101`: Use the PyTorch index for CUDA 10.1
- `cu100`: Use the PyTorch index for CUDA 10.0
- `cu92`: Use the PyTorch index for CUDA 9.2
- `cu91`: Use the PyTorch index for CUDA 9.1
- `cu90`: Use the PyTorch index for CUDA 9.0
- `cu80`: Use the PyTorch index for CUDA 8.0
- `rocm6.3`: Use the PyTorch index for ROCm 6.3
- `rocm6.2.4`: Use the PyTorch index for ROCm 6.2.4
- `rocm6.2`: Use the PyTorch index for ROCm 6.2
- `rocm6.1`: Use the PyTorch index for ROCm 6.1
- `rocm6.0`: Use the PyTorch index for ROCm 6.0
- `rocm5.7`: Use the PyTorch index for ROCm 5.7
- `rocm5.6`: Use the PyTorch index for ROCm 5.6
- `rocm5.5`: Use the PyTorch index for ROCm 5.5
- `rocm5.4.2`: Use the PyTorch index for ROCm 5.4.2
- `rocm5.4`: Use the PyTorch index for ROCm 5.4
- `rocm5.3`: Use the PyTorch index for ROCm 5.3
- `rocm5.2`: Use the PyTorch index for ROCm 5.2
- `rocm5.1.1`: Use the PyTorch index for ROCm 5.1.1
- `rocm4.2`: Use the PyTorch index for ROCm 4.2
- `rocm4.1`: Use the PyTorch index for ROCm 4.1
- `rocm4.0.1`: Use the PyTorch index for ROCm 4.0.1
- `xpu`: Use the PyTorch index for Intel XPU
```

[`--verbose`](#uv-pip-sync--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv pip install](#uv-pip-install)

Install packages into an environment

### Usage

```
uv pip install [OPTIONS] <PACKAGE|--requirements <REQUIREMENTS>|--editable <EDITABLE>|--group <GROUP>>

```

### Arguments

[PACKAGE](#uv-pip-install--package) : Install all listed packages.

```
The order of the packages is used to determine priority during resolution.
```

### Options

[`--all-extras`](#uv-pip-install--all-extras) : Include all optional dependencies.

```
Only applies to `pylock.toml`, `pyproject.toml`, `setup.py`, and `setup.cfg` sources.
```

[`--allow-insecure-host`](#uv-pip-install--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--break-system-packages`](#uv-pip-install--break-system-packages) : Allow uv to modify an `EXTERNALLY-MANAGED` Python installation.

```
WARNING: `--break-system-packages` is intended for use in continuous integration (CI) environments, when installing into Python installations that are managed by an external package manager, like `apt`. It should be used with caution, as such Python installations explicitly recommend against modifications by other package managers (like uv or `pip`).

May also be set with the `UV_BREAK_SYSTEM_PACKAGES` environment variable.
```

[`--build-constraints`](#uv-pip-install--build-constraints), `--build-constraint`, `-b` *build-constraints* : Constrain build dependencies using the given requirements files when building source distributions.

```
Constraints files are `requirements.txt`-like files that only control the *version* of a requirement that's installed. However, including a package in a constraints file will *not* trigger the installation of that package.

May also be set with the `UV_BUILD_CONSTRAINT` environment variable.
```

[`--cache-dir`](#uv-pip-install--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-pip-install--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--compile-bytecode`](#uv-pip-install--compile-bytecode), `--compile` : Compile Python files to bytecode after installation.

```
By default, uv does not compile Python (`.py`) files to bytecode (`__pycache__/*.pyc`); instead, compilation is performed lazily the first time a module is imported. For use-cases in which start time is critical, such as CLI applications and Docker containers, this option can be enabled to trade longer installation times for faster start times.

When enabled, uv will process the entire site-packages directory (including packages that are not being modified by the current operation) for consistency. Like pip, it will also ignore errors.

May also be set with the `UV_COMPILE_BYTECODE` environment variable.
```

[`--config-file`](#uv-pip-install--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--config-setting`](#uv-pip-install--config-setting), `--config-settings`, `-C` *config-setting* : Settings to pass to the PEP 517 build backend, specified as `KEY=VALUE` pairs

[`--config-settings-package`](#uv-pip-install--config-settings-package), `--config-settings-package` *config-settings-package* : Settings to pass to the PEP 517 build backend for a specific package, specified as `PACKAGE:KEY=VALUE` pairs

[`--constraints`](#uv-pip-install--constraints), `--constraint`, `-c` *constraints* : Constrain versions using the given requirements files.

```
Constraints files are `requirements.txt`-like files that only control the *version* of a requirement that's installed. However, including a package in a constraints file will *not* trigger the installation of that package.

This is equivalent to pip's `--constraint` option.

May also be set with the `UV_CONSTRAINT` environment variable.
```

[`--default-index`](#uv-pip-install--default-index) *default-index* : The URL of the default package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--index` flag.

May also be set with the `UV_DEFAULT_INDEX` environment variable.
```

[`--directory`](#uv-pip-install--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--dry-run`](#uv-pip-install--dry-run) : Perform a dry run, i.e., don't actually install anything but resolve the dependencies and print the resulting plan

[`--editable`](#uv-pip-install--editable), `-e` *editable* : Install the editable package based on the provided local file path

[`--exact`](#uv-pip-install--exact) : Perform an exact sync, removing extraneous packages.

```
By default, installing will make the minimum necessary changes to satisfy the requirements. When enabled, uv will update the environment to exactly match the requirements, removing packages that are not included in the requirements.
```

[`--exclude-newer`](#uv-pip-install--exclude-newer) *exclude-newer* : Limit candidate packages to those that were uploaded prior to the given date.

```
Accepts both RFC 3339 timestamps (e.g., `2006-12-02T02:07:43Z`) and local dates in the same format (e.g., `2006-12-02`) in your system's configured time zone.

May also be set with the `UV_EXCLUDE_NEWER` environment variable.
```

[`--exclude-newer-package`](#uv-pip-install--exclude-newer-package) *exclude-newer-package* : Limit candidate packages for specific packages to those that were uploaded prior to the given date.

```
Accepts package-date pairs in the format `PACKAGE=DATE`, where `DATE` is an RFC 3339 timestamp (e.g., `2006-12-02T02:07:43Z`) or local date (e.g., `2006-12-02`) in your system's configured time zone.

Can be provided multiple times for different packages.
```

[`--extra`](#uv-pip-install--extra) *extra* : Include optional dependencies from the specified extra name; may be provided more than once.

```
Only applies to `pylock.toml`, `pyproject.toml`, `setup.py`, and `setup.cfg` sources.
```

[`--extra-index-url`](#uv-pip-install--extra-index-url) *extra-index-url* : (Deprecated: use `--index` instead) Extra URLs of package indexes to use, in addition to `--index-url`.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--index-url` (which defaults to PyPI). When multiple `--extra-index-url` flags are provided, earlier values take priority.

May also be set with the `UV_EXTRA_INDEX_URL` environment variable.
```

[`--find-links`](#uv-pip-install--find-links), `-f` *find-links* : Locations to search for candidate distributions, in addition to those found in the registry indexes.

```
If a path, the target must be a directory that contains packages as wheel files (`.whl`) or source distributions (e.g., `.tar.gz` or `.zip`) at the top level.

If a URL, the page must contain a flat list of links to package files adhering to the formats described above.

May also be set with the `UV_FIND_LINKS` environment variable.
```

[`--fork-strategy`](#uv-pip-install--fork-strategy) *fork-strategy* : The strategy to use when selecting multiple versions of a given package across Python versions and platforms.

```
By default, uv will optimize for selecting the latest version of each package for each supported Python version (`requires-python`), while minimizing the number of selected versions across platforms.

Under `fewest`, uv will minimize the number of selected versions for each package, preferring older versions that are compatible with a wider range of supported Python versions or platforms.

May also be set with the `UV_FORK_STRATEGY` environment variable.

Possible values:

- `fewest`: Optimize for selecting the fewest number of versions for each package. Older versions may be preferred if they are compatible with a wider range of supported Python versions or platforms
- `requires-python`: Optimize for selecting latest supported version of each package, for each supported Python version
```

[`--group`](#uv-pip-install--group) *group* : Install the specified dependency group from a `pylock.toml` or `pyproject.toml`.

```
If no path is provided, the `pylock.toml` or `pyproject.toml` in the working directory is used.

May be provided multiple times.
```

[`--help`](#uv-pip-install--help), `-h` : Display the concise help for this command

[`--index`](#uv-pip-install--index) *index* : The URLs to use when resolving dependencies, in addition to the default index.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--default-index` (which defaults to PyPI). When multiple `--index` flags are provided, earlier values take priority.

Index names are not supported as values. Relative paths must be disambiguated from index names with `./` or `../` on Unix or `.\\`, `..\\`, `./` or `../` on Windows.

May also be set with the `UV_INDEX` environment variable.
```

[`--index-strategy`](#uv-pip-install--index-strategy) *index-strategy* : The strategy to use when resolving against multiple index URLs.

```
By default, uv will stop at the first index on which a given package is available, and limit resolutions to those present on that first index (`first-index`). This prevents "dependency confusion" attacks, whereby an attacker can upload a malicious package under the same name to an alternate index.

May also be set with the `UV_INDEX_STRATEGY` environment variable.

Possible values:

- `first-index`: Only use results from the first index that returns a match for a given package name
- `unsafe-first-match`: Search for every package name across all indexes, exhausting the versions from the first index before moving on to the next
- `unsafe-best-match`: Search for every package name across all indexes, preferring the "best" version found. If a package version is in multiple indexes, only look at the entry for the first index
```

[`--index-url`](#uv-pip-install--index-url), `-i` *index-url* : (Deprecated: use `--default-index` instead) The URL of the Python package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--extra-index-url` flag.

May also be set with the `UV_INDEX_URL` environment variable.
```

[`--keyring-provider`](#uv-pip-install--keyring-provider) *keyring-provider* : Attempt to use `keyring` for authentication for index URLs.

```
At present, only `--keyring-provider subprocess` is supported, which configures uv to use the `keyring` CLI to handle authentication.

Defaults to `disabled`.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--link-mode`](#uv-pip-install--link-mode) *link-mode* : The method to use when installing packages from the global cache.

```
Defaults to `clone` (also known as Copy-on-Write) on macOS, and `hardlink` on Linux and Windows.

WARNING: The use of symlink link mode is discouraged, as they create tight coupling between the cache and the target environment. For example, clearing the cache (`uv cache clean`) will break all installed packages by way of removing the underlying source files. Use symlinks with caution.

May also be set with the `UV_LINK_MODE` environment variable.

Possible values:

- `clone`: Clone (i.e., copy-on-write) packages from the wheel into the `site-packages` directory
- `copy`: Copy packages from the wheel into the `site-packages` directory
- `hardlink`: Hard link packages from the wheel into the `site-packages` directory
- `symlink`: Symbolically link packages from the wheel into the `site-packages` directory
```

[`--managed-python`](#uv-pip-install--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-pip-install--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-binary`](#uv-pip-install--no-binary) *no-binary* : Don't install pre-built wheels.

```
The given packages will be built and installed from source. The resolver will still use pre-built wheels to extract package metadata, if available.

Multiple packages may be provided. Disable binaries for all packages with `:all:`. Clear previously specified packages with `:none:`.
```

[`--no-break-system-packages`](#uv-pip-install--no-break-system-packages)

[`--no-build`](#uv-pip-install--no-build) : Don't build source distributions.

```
When enabled, resolving will not run arbitrary Python code. The cached wheels of already-built source distributions will be reused, but operations that require building distributions will exit with an error.

Alias for `--only-binary :all:`.
```

[`--no-build-isolation`](#uv-pip-install--no-build-isolation) : Disable isolation when building source distributions.

```
Assumes that build dependencies specified by PEP 518 are already installed.

May also be set with the `UV_NO_BUILD_ISOLATION` environment variable.
```

[`--no-build-isolation-package`](#uv-pip-install--no-build-isolation-package) *no-build-isolation-package* : Disable isolation when building source distributions for a specific package.

```
Assumes that the packages' build dependencies specified by PEP 518 are already installed.
```

[`--no-cache`](#uv-pip-install--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-pip-install--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-deps`](#uv-pip-install--no-deps) : Ignore package dependencies, instead only installing those packages explicitly listed on the command line or in the requirements files

[`--no-index`](#uv-pip-install--no-index) : Ignore the registry index (e.g., PyPI), instead relying on direct URL dependencies and those provided via `--find-links`

[`--no-managed-python`](#uv-pip-install--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-pip-install--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-pip-install--no-python-downloads) : Disable automatic downloads of Python.

[`--no-sources`](#uv-pip-install--no-sources) : Ignore the `tool.uv.sources` table when resolving dependencies. Used to lock against the standards-compliant, publishable package metadata, as opposed to using any workspace, Git, URL, or local path sources

[`--no-verify-hashes`](#uv-pip-install--no-verify-hashes) : Disable validation of hashes in the requirements file.

```
By default, uv will verify any available hashes in the requirements file, but will not require that all requirements have an associated hash. To enforce hash validation, use `--require-hashes`.

May also be set with the `UV_NO_VERIFY_HASHES` environment variable.
```

[`--offline`](#uv-pip-install--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--only-binary`](#uv-pip-install--only-binary) *only-binary* : Only use pre-built wheels; don't build source distributions.

```
When enabled, resolving will not run code from the given packages. The cached wheels of already-built source distributions will be reused, but operations that require building distributions will exit with an error.

Multiple packages may be provided. Disable binaries for all packages with `:all:`. Clear previously specified packages with `:none:`.
```

[`--overrides`](#uv-pip-install--overrides), `--override` *overrides* : Override versions using the given requirements files.

```
Overrides files are `requirements.txt`-like files that force a specific version of a requirement to be installed, regardless of the requirements declared by any constituent package, and regardless of whether this would be considered an invalid resolution.

While constraints are *additive*, in that they're combined with the requirements of the constituent packages, overrides are *absolute*, in that they completely replace the requirements of the constituent packages.

May also be set with the `UV_OVERRIDE` environment variable.
```

[`--prefix`](#uv-pip-install--prefix) *prefix* : Install packages into `lib`, `bin`, and other top-level folders under the specified directory, as if a virtual environment were present at that location.

```
In general, prefer the use of `--python` to install into an alternate environment, as scripts and other artifacts installed via `--prefix` will reference the installing interpreter, rather than any interpreter added to the `--prefix` directory, rendering them non-portable.
```

[`--prerelease`](#uv-pip-install--prerelease) *prerelease* : The strategy to use when considering pre-release versions.

```
By default, uv will accept pre-releases for packages that *only* publish pre-releases, along with first-party requirements that contain an explicit pre-release marker in the declared specifiers (`if-necessary-or-explicit`).

May also be set with the `UV_PRERELEASE` environment variable.

Possible values:

- `disallow`: Disallow all pre-release versions
- `allow`: Allow all pre-release versions
- `if-necessary`: Allow pre-release versions if all versions of a package are pre-release
- `explicit`: Allow pre-release versions for first-party packages with explicit pre-release markers in their version requirements
- `if-necessary-or-explicit`: Allow pre-release versions if all versions of a package are pre-release, or if the package has an explicit pre-release marker in its version requirements
```

[`--project`](#uv-pip-install--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--python`](#uv-pip-install--python), `-p` *python* : The Python interpreter into which packages should be installed.

```
By default, installation requires a virtual environment. A path to an alternative Python can
be provided, but it is only recommended in continuous integration (CI) environments and
should be used with caution, as it can modify the system Python installation.

See [uv python](#uv-python) for details on Python discovery and supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--python-platform`](#uv-pip-install--python-platform) *python-platform* : The platform for which requirements should be installed.

```
Represented as a "target triple", a string that describes the target platform in terms of its CPU, vendor, and operating system name, like `x86_64-unknown-linux-gnu` or `aarch64-apple-darwin`.

When targeting macOS (Darwin), the default minimum version is `13.0`. Use `MACOSX_DEPLOYMENT_TARGET` to specify a different minimum version, e.g., `14.0`.

When targeting iOS, the default minimum version is `13.0`. Use `IPHONEOS_DEPLOYMENT_TARGET` to specify a different minimum version, e.g., `14.0`.

When targeting Android, the default minimum Android API level is `24`. Use `ANDROID_API_LEVEL` to specify a different minimum version, e.g., `26`.

WARNING: When specified, uv will select wheels that are compatible with the *target* platform; as a result, the installed distributions may not be compatible with the *current* platform. Conversely, any distributions that are built from source may be incompatible with the *target* platform, as they will be built for the *current* platform. The `--python-platform` option is intended for advanced use cases.

Possible values:

- `windows`: An alias for `x86_64-pc-windows-msvc`, the default target for Windows
- `linux`: An alias for `x86_64-unknown-linux-gnu`, the default target for Linux
- `macos`: An alias for `aarch64-apple-darwin`, the default target for macOS
- `x86_64-pc-windows-msvc`: A 64-bit x86 Windows target
- `aarch64-pc-windows-msvc`: An ARM64 Windows target
- `i686-pc-windows-msvc`: A 32-bit x86 Windows target
- `x86_64-unknown-linux-gnu`: An x86 Linux target. Equivalent to `x86_64-manylinux_2_28`
- `aarch64-apple-darwin`: An ARM-based macOS target, as seen on Apple Silicon devices
- `x86_64-apple-darwin`: An x86 macOS target
- `aarch64-unknown-linux-gnu`: An ARM64 Linux target. Equivalent to `aarch64-manylinux_2_28`
- `aarch64-unknown-linux-musl`: An ARM64 Linux target
- `x86_64-unknown-linux-musl`: An `x86_64` Linux target
- `riscv64-unknown-linux`: A RISCV64 Linux target
- `x86_64-manylinux2014`: An `x86_64` target for the `manylinux2014` platform. Equivalent to `x86_64-manylinux_2_17`
- `x86_64-manylinux_2_17`: An `x86_64` target for the `manylinux_2_17` platform
- `x86_64-manylinux_2_28`: An `x86_64` target for the `manylinux_2_28` platform
- `x86_64-manylinux_2_31`: An `x86_64` target for the `manylinux_2_31` platform
- `x86_64-manylinux_2_32`: An `x86_64` target for the `manylinux_2_32` platform
- `x86_64-manylinux_2_33`: An `x86_64` target for the `manylinux_2_33` platform
- `x86_64-manylinux_2_34`: An `x86_64` target for the `manylinux_2_34` platform
- `x86_64-manylinux_2_35`: An `x86_64` target for the `manylinux_2_35` platform
- `x86_64-manylinux_2_36`: An `x86_64` target for the `manylinux_2_36` platform
- `x86_64-manylinux_2_37`: An `x86_64` target for the `manylinux_2_37` platform
- `x86_64-manylinux_2_38`: An `x86_64` target for the `manylinux_2_38` platform
- `x86_64-manylinux_2_39`: An `x86_64` target for the `manylinux_2_39` platform
- `x86_64-manylinux_2_40`: An `x86_64` target for the `manylinux_2_40` platform
- `aarch64-manylinux2014`: An ARM64 target for the `manylinux2014` platform. Equivalent to `aarch64-manylinux_2_17`
- `aarch64-manylinux_2_17`: An ARM64 target for the `manylinux_2_17` platform
- `aarch64-manylinux_2_28`: An ARM64 target for the `manylinux_2_28` platform
- `aarch64-manylinux_2_31`: An ARM64 target for the `manylinux_2_31` platform
- `aarch64-manylinux_2_32`: An ARM64 target for the `manylinux_2_32` platform
- `aarch64-manylinux_2_33`: An ARM64 target for the `manylinux_2_33` platform
- `aarch64-manylinux_2_34`: An ARM64 target for the `manylinux_2_34` platform
- `aarch64-manylinux_2_35`: An ARM64 target for the `manylinux_2_35` platform
- `aarch64-manylinux_2_36`: An ARM64 target for the `manylinux_2_36` platform
- `aarch64-manylinux_2_37`: An ARM64 target for the `manylinux_2_37` platform
- `aarch64-manylinux_2_38`: An ARM64 target for the `manylinux_2_38` platform
- `aarch64-manylinux_2_39`: An ARM64 target for the `manylinux_2_39` platform
- `aarch64-manylinux_2_40`: An ARM64 target for the `manylinux_2_40` platform
- `aarch64-linux-android`: An ARM64 Android target
- `x86_64-linux-android`: An `x86_64` Android target
- `wasm32-pyodide2024`: A wasm32 target using the Pyodide 2024 platform. Meant for use with Python 3.12
- `arm64-apple-ios`: An ARM64 target for iOS device
- `arm64-apple-ios-simulator`: An ARM64 target for iOS simulator
- `x86_64-apple-ios-simulator`: An `x86_64` target for iOS simulator
```

[`--python-version`](#uv-pip-install--python-version) *python-version* : The minimum Python version that should be supported by the requirements (e.g., `3.7` or `3.7.9`).

```
If a patch version is omitted, the minimum patch version is assumed. For example, `3.7` is mapped to `3.7.0`.
```

[`--quiet`](#uv-pip-install--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--refresh`](#uv-pip-install--refresh) : Refresh all cached data

[`--refresh-package`](#uv-pip-install--refresh-package) *refresh-package* : Refresh cached data for a specific package

[`--reinstall`](#uv-pip-install--reinstall), `--force-reinstall` : Reinstall all packages, regardless of whether they're already installed. Implies `--refresh`

[`--reinstall-package`](#uv-pip-install--reinstall-package) *reinstall-package* : Reinstall a specific package, regardless of whether it's already installed. Implies `--refresh-package`

[`--require-hashes`](#uv-pip-install--require-hashes) : Require a matching hash for each requirement.

```
By default, uv will verify any available hashes in the requirements file, but will not require that all requirements have an associated hash.

When `--require-hashes` is enabled, *all* requirements must include a hash or set of hashes, and *all* requirements must either be pinned to exact versions (e.g., `==1.0.0`), or be specified via direct URL.

Hash-checking mode introduces a number of additional constraints:

- Git dependencies are not supported. - Editable installations are not supported. - Local dependencies are not supported, unless they point to a specific wheel (`.whl`) or source archive (`.zip`, `.tar.gz`), as opposed to a directory.

May also be set with the `UV_REQUIRE_HASHES` environment variable.
```

[`--requirements`](#uv-pip-install--requirements), `--requirement`, `-r` *requirements* : Install the packages listed in the given files.

```
The following formats are supported: `requirements.txt`, `.py` files with inline metadata, `pylock.toml`, `pyproject.toml`, `setup.py`, and `setup.cfg`.

If a `pyproject.toml`, `setup.py`, or `setup.cfg` file is provided, uv will extract the requirements for the relevant project.

If `-` is provided, then requirements will be read from stdin.
```

[`--resolution`](#uv-pip-install--resolution) *resolution* : The strategy to use when selecting between the different compatible versions for a given package requirement.

```
By default, uv will use the latest compatible version of each package (`highest`).

May also be set with the `UV_RESOLUTION` environment variable.

Possible values:

- `highest`: Resolve the highest compatible version of each package
- `lowest`: Resolve the lowest compatible version of each package
- `lowest-direct`: Resolve the lowest compatible version of any direct dependencies, and the highest compatible version of any transitive dependencies
```

[`--strict`](#uv-pip-install--strict) : Validate the Python environment after completing the installation, to detect packages with missing dependencies or other issues

[`--system`](#uv-pip-install--system) : Install packages into the system Python environment.

```
By default, uv installs into the virtual environment in the current working directory or any parent directory. The `--system` option instructs uv to instead use the first Python found in the system `PATH`.

WARNING: `--system` is intended for use in continuous integration (CI) environments and should be used with caution, as it can modify the system Python installation.

May also be set with the `UV_SYSTEM_PYTHON` environment variable.
```

[`--target`](#uv-pip-install--target) *target* : Install packages into the specified directory, rather than into the virtual or system Python environment. The packages will be installed at the top-level of the directory

[`--torch-backend`](#uv-pip-install--torch-backend) *torch-backend* : The backend to use when fetching packages in the PyTorch ecosystem (e.g., `cpu`, `cu126`, or `auto`)

```
When set, uv will ignore the configured index URLs for packages in the PyTorch ecosystem, and will instead use the defined backend.

For example, when set to `cpu`, uv will use the CPU-only PyTorch index; when set to `cu126`, uv will use the PyTorch index for CUDA 12.6.

The `auto` mode will attempt to detect the appropriate PyTorch index based on the currently installed CUDA drivers.

This option is in preview and may change in any future release.

May also be set with the `UV_TORCH_BACKEND` environment variable.

Possible values:

- `auto`: Select the appropriate PyTorch index based on the operating system and CUDA driver version
- `cpu`: Use the CPU-only PyTorch index
- `cu130`: Use the PyTorch index for CUDA 13.0
- `cu129`: Use the PyTorch index for CUDA 12.9
- `cu128`: Use the PyTorch index for CUDA 12.8
- `cu126`: Use the PyTorch index for CUDA 12.6
- `cu125`: Use the PyTorch index for CUDA 12.5
- `cu124`: Use the PyTorch index for CUDA 12.4
- `cu123`: Use the PyTorch index for CUDA 12.3
- `cu122`: Use the PyTorch index for CUDA 12.2
- `cu121`: Use the PyTorch index for CUDA 12.1
- `cu120`: Use the PyTorch index for CUDA 12.0
- `cu118`: Use the PyTorch index for CUDA 11.8
- `cu117`: Use the PyTorch index for CUDA 11.7
- `cu116`: Use the PyTorch index for CUDA 11.6
- `cu115`: Use the PyTorch index for CUDA 11.5
- `cu114`: Use the PyTorch index for CUDA 11.4
- `cu113`: Use the PyTorch index for CUDA 11.3
- `cu112`: Use the PyTorch index for CUDA 11.2
- `cu111`: Use the PyTorch index for CUDA 11.1
- `cu110`: Use the PyTorch index for CUDA 11.0
- `cu102`: Use the PyTorch index for CUDA 10.2
- `cu101`: Use the PyTorch index for CUDA 10.1
- `cu100`: Use the PyTorch index for CUDA 10.0
- `cu92`: Use the PyTorch index for CUDA 9.2
- `cu91`: Use the PyTorch index for CUDA 9.1
- `cu90`: Use the PyTorch index for CUDA 9.0
- `cu80`: Use the PyTorch index for CUDA 8.0
- `rocm6.3`: Use the PyTorch index for ROCm 6.3
- `rocm6.2.4`: Use the PyTorch index for ROCm 6.2.4
- `rocm6.2`: Use the PyTorch index for ROCm 6.2
- `rocm6.1`: Use the PyTorch index for ROCm 6.1
- `rocm6.0`: Use the PyTorch index for ROCm 6.0
- `rocm5.7`: Use the PyTorch index for ROCm 5.7
- `rocm5.6`: Use the PyTorch index for ROCm 5.6
- `rocm5.5`: Use the PyTorch index for ROCm 5.5
- `rocm5.4.2`: Use the PyTorch index for ROCm 5.4.2
- `rocm5.4`: Use the PyTorch index for ROCm 5.4
- `rocm5.3`: Use the PyTorch index for ROCm 5.3
- `rocm5.2`: Use the PyTorch index for ROCm 5.2
- `rocm5.1.1`: Use the PyTorch index for ROCm 5.1.1
- `rocm4.2`: Use the PyTorch index for ROCm 4.2
- `rocm4.1`: Use the PyTorch index for ROCm 4.1
- `rocm4.0.1`: Use the PyTorch index for ROCm 4.0.1
- `xpu`: Use the PyTorch index for Intel XPU
```

[`--upgrade`](#uv-pip-install--upgrade), `-U` : Allow package upgrades, ignoring pinned versions in any existing output file. Implies `--refresh`

[`--upgrade-package`](#uv-pip-install--upgrade-package), `-P` *upgrade-package* : Allow upgrades for a specific package, ignoring pinned versions in any existing output file. Implies `--refresh-package`

[`--user`](#uv-pip-install--user)

[`--verbose`](#uv-pip-install--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv pip uninstall](#uv-pip-uninstall)

Uninstall packages from an environment

### Usage

```
uv pip uninstall [OPTIONS] <PACKAGE|--requirements <REQUIREMENTS>>

```

### Arguments

[PACKAGE](#uv-pip-uninstall--package) : Uninstall all listed packages

### Options

[`--allow-insecure-host`](#uv-pip-uninstall--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--break-system-packages`](#uv-pip-uninstall--break-system-packages) : Allow uv to modify an `EXTERNALLY-MANAGED` Python installation.

```
WARNING: `--break-system-packages` is intended for use in continuous integration (CI) environments, when installing into Python installations that are managed by an external package manager, like `apt`. It should be used with caution, as such Python installations explicitly recommend against modifications by other package managers (like uv or `pip`).

May also be set with the `UV_BREAK_SYSTEM_PACKAGES` environment variable.
```

[`--cache-dir`](#uv-pip-uninstall--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-pip-uninstall--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-pip-uninstall--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-pip-uninstall--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--dry-run`](#uv-pip-uninstall--dry-run) : Perform a dry run, i.e., don't actually uninstall anything but print the resulting plan

[`--help`](#uv-pip-uninstall--help), `-h` : Display the concise help for this command

[`--keyring-provider`](#uv-pip-uninstall--keyring-provider) *keyring-provider* : Attempt to use `keyring` for authentication for remote requirements files.

```
At present, only `--keyring-provider subprocess` is supported, which configures uv to use the `keyring` CLI to handle authentication.

Defaults to `disabled`.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--managed-python`](#uv-pip-uninstall--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-pip-uninstall--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-break-system-packages`](#uv-pip-uninstall--no-break-system-packages)

[`--no-cache`](#uv-pip-uninstall--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-pip-uninstall--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-pip-uninstall--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-pip-uninstall--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-pip-uninstall--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-pip-uninstall--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--prefix`](#uv-pip-uninstall--prefix) *prefix* : Uninstall packages from the specified `--prefix` directory

[`--project`](#uv-pip-uninstall--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--python`](#uv-pip-uninstall--python), `-p` *python* : The Python interpreter from which packages should be uninstalled.

```
By default, uninstallation requires a virtual environment. A path to an alternative Python
can be provided, but it is only recommended in continuous integration (CI) environments and
should be used with caution, as it can modify the system Python installation.

See [uv python](#uv-python) for details on Python discovery and supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--quiet`](#uv-pip-uninstall--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--requirements`](#uv-pip-uninstall--requirements), `--requirement`, `-r` *requirements* : Uninstall the packages listed in the given files.

```
The following formats are supported: `requirements.txt`, `.py` files with inline metadata, `pylock.toml`, `pyproject.toml`, `setup.py`, and `setup.cfg`.
```

[`--system`](#uv-pip-uninstall--system) : Use the system Python to uninstall packages.

```
By default, uv uninstalls from the virtual environment in the current working directory or any parent directory. The `--system` option instructs uv to instead use the first Python found in the system `PATH`.

WARNING: `--system` is intended for use in continuous integration (CI) environments and should be used with caution, as it can modify the system Python installation.

May also be set with the `UV_SYSTEM_PYTHON` environment variable.
```

[`--target`](#uv-pip-uninstall--target) *target* : Uninstall packages from the specified `--target` directory

[`--verbose`](#uv-pip-uninstall--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv pip freeze](#uv-pip-freeze)

List, in requirements format, packages installed in an environment

### Usage

```
uv pip freeze [OPTIONS]

```

### Options

[`--allow-insecure-host`](#uv-pip-freeze--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-pip-freeze--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-pip-freeze--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-pip-freeze--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-pip-freeze--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--exclude-editable`](#uv-pip-freeze--exclude-editable) : Exclude any editable packages from output

[`--help`](#uv-pip-freeze--help), `-h` : Display the concise help for this command

[`--managed-python`](#uv-pip-freeze--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-pip-freeze--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-pip-freeze--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-pip-freeze--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-pip-freeze--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-pip-freeze--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-pip-freeze--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-pip-freeze--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--path`](#uv-pip-freeze--path) *paths* : Restrict to the specified installation path for listing packages (can be used multiple times)

[`--project`](#uv-pip-freeze--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--python`](#uv-pip-freeze--python), `-p` *python* : The Python interpreter for which packages should be listed.

```
By default, uv lists packages in a virtual environment but will show packages in a system
Python environment if no virtual environment is found.

See [uv python](#uv-python) for details on Python discovery and supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--quiet`](#uv-pip-freeze--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--strict`](#uv-pip-freeze--strict) : Validate the Python environment, to detect packages with missing dependencies and other issues

[`--system`](#uv-pip-freeze--system) : List packages in the system Python environment.

```
Disables discovery of virtual environments.

See [uv python](#uv-python) for details on Python discovery.

May also be set with the `UV_SYSTEM_PYTHON` environment variable.
```

[`--verbose`](#uv-pip-freeze--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv pip list](#uv-pip-list)

List, in tabular format, packages installed in an environment

### Usage

```
uv pip list [OPTIONS]

```

### Options

[`--allow-insecure-host`](#uv-pip-list--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-pip-list--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-pip-list--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-pip-list--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--default-index`](#uv-pip-list--default-index) *default-index* : The URL of the default package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--index` flag.

May also be set with the `UV_DEFAULT_INDEX` environment variable.
```

[`--directory`](#uv-pip-list--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--editable`](#uv-pip-list--editable), `-e` : Only include editable projects

[`--exclude`](#uv-pip-list--exclude) *exclude* : Exclude the specified package(s) from the output

[`--exclude-editable`](#uv-pip-list--exclude-editable) : Exclude any editable packages from output

[`--exclude-newer`](#uv-pip-list--exclude-newer) *exclude-newer* : Limit candidate packages to those that were uploaded prior to the given date.

```
Accepts both RFC 3339 timestamps (e.g., `2006-12-02T02:07:43Z`) and local dates in the same format (e.g., `2006-12-02`) in your system's configured time zone.

May also be set with the `UV_EXCLUDE_NEWER` environment variable.
```

[`--extra-index-url`](#uv-pip-list--extra-index-url) *extra-index-url* : (Deprecated: use `--index` instead) Extra URLs of package indexes to use, in addition to `--index-url`.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--index-url` (which defaults to PyPI). When multiple `--extra-index-url` flags are provided, earlier values take priority.

May also be set with the `UV_EXTRA_INDEX_URL` environment variable.
```

[`--find-links`](#uv-pip-list--find-links), `-f` *find-links* : Locations to search for candidate distributions, in addition to those found in the registry indexes.

```
If a path, the target must be a directory that contains packages as wheel files (`.whl`) or source distributions (e.g., `.tar.gz` or `.zip`) at the top level.

If a URL, the page must contain a flat list of links to package files adhering to the formats described above.

May also be set with the `UV_FIND_LINKS` environment variable.
```

[`--format`](#uv-pip-list--format) *format* : Select the output format

```
[default: columns]

Possible values:

- `columns`: Display the list of packages in a human-readable table
- `freeze`: Display the list of packages in a `pip freeze`-like format, with one package per line alongside its version
- `json`: Display the list of packages in a machine-readable JSON format
```

[`--help`](#uv-pip-list--help), `-h` : Display the concise help for this command

[`--index`](#uv-pip-list--index) *index* : The URLs to use when resolving dependencies, in addition to the default index.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--default-index` (which defaults to PyPI). When multiple `--index` flags are provided, earlier values take priority.

Index names are not supported as values. Relative paths must be disambiguated from index names with `./` or `../` on Unix or `.\\`, `..\\`, `./` or `../` on Windows.

May also be set with the `UV_INDEX` environment variable.
```

[`--index-strategy`](#uv-pip-list--index-strategy) *index-strategy* : The strategy to use when resolving against multiple index URLs.

```
By default, uv will stop at the first index on which a given package is available, and limit resolutions to those present on that first index (`first-index`). This prevents "dependency confusion" attacks, whereby an attacker can upload a malicious package under the same name to an alternate index.

May also be set with the `UV_INDEX_STRATEGY` environment variable.

Possible values:

- `first-index`: Only use results from the first index that returns a match for a given package name
- `unsafe-first-match`: Search for every package name across all indexes, exhausting the versions from the first index before moving on to the next
- `unsafe-best-match`: Search for every package name across all indexes, preferring the "best" version found. If a package version is in multiple indexes, only look at the entry for the first index
```

[`--index-url`](#uv-pip-list--index-url), `-i` *index-url* : (Deprecated: use `--default-index` instead) The URL of the Python package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--extra-index-url` flag.

May also be set with the `UV_INDEX_URL` environment variable.
```

[`--keyring-provider`](#uv-pip-list--keyring-provider) *keyring-provider* : Attempt to use `keyring` for authentication for index URLs.

```
At present, only `--keyring-provider subprocess` is supported, which configures uv to use the `keyring` CLI to handle authentication.

Defaults to `disabled`.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--managed-python`](#uv-pip-list--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-pip-list--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-pip-list--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-pip-list--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-index`](#uv-pip-list--no-index) : Ignore the registry index (e.g., PyPI), instead relying on direct URL dependencies and those provided via `--find-links`

[`--no-managed-python`](#uv-pip-list--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-pip-list--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-pip-list--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-pip-list--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--outdated`](#uv-pip-list--outdated) : List outdated packages.

```
The latest version of each package will be shown alongside the installed version. Up-to-date packages will be omitted from the output.
```

[`--project`](#uv-pip-list--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--python`](#uv-pip-list--python), `-p` *python* : The Python interpreter for which packages should be listed.

```
By default, uv lists packages in a virtual environment but will show packages in a system
Python environment if no virtual environment is found.

See [uv python](#uv-python) for details on Python discovery and supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--quiet`](#uv-pip-list--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--strict`](#uv-pip-list--strict) : Validate the Python environment, to detect packages with missing dependencies and other issues

[`--system`](#uv-pip-list--system) : List packages in the system Python environment.

```
Disables discovery of virtual environments.

See [uv python](#uv-python) for details on Python discovery.

May also be set with the `UV_SYSTEM_PYTHON` environment variable.
```

[`--verbose`](#uv-pip-list--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv pip show](#uv-pip-show)

Show information about one or more installed packages

### Usage

```
uv pip show [OPTIONS] [PACKAGE]...

```

### Arguments

[PACKAGE](#uv-pip-show--package) : The package(s) to display

### Options

[`--allow-insecure-host`](#uv-pip-show--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-pip-show--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-pip-show--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-pip-show--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-pip-show--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--files`](#uv-pip-show--files), `-f` : Show the full list of installed files for each package

[`--help`](#uv-pip-show--help), `-h` : Display the concise help for this command

[`--managed-python`](#uv-pip-show--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-pip-show--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-pip-show--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-pip-show--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-pip-show--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-pip-show--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-pip-show--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-pip-show--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-pip-show--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--python`](#uv-pip-show--python), `-p` *python* : The Python interpreter to find the package in.

```
By default, uv looks for packages in a virtual environment but will look for packages in a
system Python environment if no virtual environment is found.

See [uv python](#uv-python) for details on Python discovery and supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--quiet`](#uv-pip-show--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--strict`](#uv-pip-show--strict) : Validate the Python environment, to detect packages with missing dependencies and other issues

[`--system`](#uv-pip-show--system) : Show a package in the system Python environment.

```
Disables discovery of virtual environments.

See [uv python](#uv-python) for details on Python discovery.

May also be set with the `UV_SYSTEM_PYTHON` environment variable.
```

[`--verbose`](#uv-pip-show--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv pip tree](#uv-pip-tree)

Display the dependency tree for an environment

### Usage

```
uv pip tree [OPTIONS]

```

### Options

[`--allow-insecure-host`](#uv-pip-tree--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-pip-tree--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-pip-tree--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-pip-tree--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--default-index`](#uv-pip-tree--default-index) *default-index* : The URL of the default package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--index` flag.

May also be set with the `UV_DEFAULT_INDEX` environment variable.
```

[`--depth`](#uv-pip-tree--depth), `-d` *depth* : Maximum display depth of the dependency tree

```
[default: 255]
```

[`--directory`](#uv-pip-tree--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--exclude-newer`](#uv-pip-tree--exclude-newer) *exclude-newer* : Limit candidate packages to those that were uploaded prior to the given date.

```
Accepts both RFC 3339 timestamps (e.g., `2006-12-02T02:07:43Z`) and local dates in the same format (e.g., `2006-12-02`) in your system's configured time zone.

May also be set with the `UV_EXCLUDE_NEWER` environment variable.
```

[`--extra-index-url`](#uv-pip-tree--extra-index-url) *extra-index-url* : (Deprecated: use `--index` instead) Extra URLs of package indexes to use, in addition to `--index-url`.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--index-url` (which defaults to PyPI). When multiple `--extra-index-url` flags are provided, earlier values take priority.

May also be set with the `UV_EXTRA_INDEX_URL` environment variable.
```

[`--find-links`](#uv-pip-tree--find-links), `-f` *find-links* : Locations to search for candidate distributions, in addition to those found in the registry indexes.

```
If a path, the target must be a directory that contains packages as wheel files (`.whl`) or source distributions (e.g., `.tar.gz` or `.zip`) at the top level.

If a URL, the page must contain a flat list of links to package files adhering to the formats described above.

May also be set with the `UV_FIND_LINKS` environment variable.
```

[`--help`](#uv-pip-tree--help), `-h` : Display the concise help for this command

[`--index`](#uv-pip-tree--index) *index* : The URLs to use when resolving dependencies, in addition to the default index.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--default-index` (which defaults to PyPI). When multiple `--index` flags are provided, earlier values take priority.

Index names are not supported as values. Relative paths must be disambiguated from index names with `./` or `../` on Unix or `.\\`, `..\\`, `./` or `../` on Windows.

May also be set with the `UV_INDEX` environment variable.
```

[`--index-strategy`](#uv-pip-tree--index-strategy) *index-strategy* : The strategy to use when resolving against multiple index URLs.

```
By default, uv will stop at the first index on which a given package is available, and limit resolutions to those present on that first index (`first-index`). This prevents "dependency confusion" attacks, whereby an attacker can upload a malicious package under the same name to an alternate index.

May also be set with the `UV_INDEX_STRATEGY` environment variable.

Possible values:

- `first-index`: Only use results from the first index that returns a match for a given package name
- `unsafe-first-match`: Search for every package name across all indexes, exhausting the versions from the first index before moving on to the next
- `unsafe-best-match`: Search for every package name across all indexes, preferring the "best" version found. If a package version is in multiple indexes, only look at the entry for the first index
```

[`--index-url`](#uv-pip-tree--index-url), `-i` *index-url* : (Deprecated: use `--default-index` instead) The URL of the Python package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--extra-index-url` flag.

May also be set with the `UV_INDEX_URL` environment variable.
```

[`--invert`](#uv-pip-tree--invert), `--reverse` : Show the reverse dependencies for the given package. This flag will invert the tree and display the packages that depend on the given package

[`--keyring-provider`](#uv-pip-tree--keyring-provider) *keyring-provider* : Attempt to use `keyring` for authentication for index URLs.

```
At present, only `--keyring-provider subprocess` is supported, which configures uv to use the `keyring` CLI to handle authentication.

Defaults to `disabled`.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--managed-python`](#uv-pip-tree--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-pip-tree--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-pip-tree--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-pip-tree--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-dedupe`](#uv-pip-tree--no-dedupe) : Do not de-duplicate repeated dependencies. Usually, when a package has already displayed its dependencies, further occurrences will not re-display its dependencies, and will include a (\*) to indicate it has already been shown. This flag will cause those duplicates to be repeated

[`--no-index`](#uv-pip-tree--no-index) : Ignore the registry index (e.g., PyPI), instead relying on direct URL dependencies and those provided via `--find-links`

[`--no-managed-python`](#uv-pip-tree--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-pip-tree--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-pip-tree--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-pip-tree--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--outdated`](#uv-pip-tree--outdated) : Show the latest available version of each package in the tree

[`--package`](#uv-pip-tree--package) *package* : Display only the specified packages

[`--project`](#uv-pip-tree--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--prune`](#uv-pip-tree--prune) *prune* : Prune the given package from the display of the dependency tree

[`--python`](#uv-pip-tree--python), `-p` *python* : The Python interpreter for which packages should be listed.

```
By default, uv lists packages in a virtual environment but will show packages in a system
Python environment if no virtual environment is found.

See [uv python](#uv-python) for details on Python discovery and supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--quiet`](#uv-pip-tree--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--show-sizes`](#uv-pip-tree--show-sizes) : Show compressed wheel sizes for packages in the tree

[`--show-version-specifiers`](#uv-pip-tree--show-version-specifiers) : Show the version constraint(s) imposed on each package

[`--strict`](#uv-pip-tree--strict) : Validate the Python environment, to detect packages with missing dependencies and other issues

[`--system`](#uv-pip-tree--system) : List packages in the system Python environment.

```
Disables discovery of virtual environments.

See [uv python](#uv-python) for details on Python discovery.

May also be set with the `UV_SYSTEM_PYTHON` environment variable.
```

[`--verbose`](#uv-pip-tree--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv pip check](#uv-pip-check)

Verify installed packages have compatible dependencies

### Usage

```
uv pip check [OPTIONS]

```

### Options

[`--allow-insecure-host`](#uv-pip-check--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-pip-check--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-pip-check--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-pip-check--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-pip-check--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--help`](#uv-pip-check--help), `-h` : Display the concise help for this command

[`--managed-python`](#uv-pip-check--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-pip-check--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-pip-check--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-pip-check--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-pip-check--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-pip-check--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-pip-check--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-pip-check--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-pip-check--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--python`](#uv-pip-check--python), `-p` *python* : The Python interpreter for which packages should be checked.

```
By default, uv checks packages in a virtual environment but will check packages in a system
Python environment if no virtual environment is found.

See [uv python](#uv-python) for details on Python discovery and supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--python-platform`](#uv-pip-check--python-platform) *python-platform* : The platform for which packages should be checked.

```
By default, the installed packages are checked against the platform of the current interpreter.

Represented as a "target triple", a string that describes the target platform in terms of its CPU, vendor, and operating system name, like `x86_64-unknown-linux-gnu` or `aarch64-apple-darwin`.

When targeting macOS (Darwin), the default minimum version is `13.0`. Use `MACOSX_DEPLOYMENT_TARGET` to specify a different minimum version, e.g., `14.0`.

When targeting iOS, the default minimum version is `13.0`. Use `IPHONEOS_DEPLOYMENT_TARGET` to specify a different minimum version, e.g., `14.0`.

When targeting Android, the default minimum Android API level is `24`. Use `ANDROID_API_LEVEL` to specify a different minimum version, e.g., `26`.

Possible values:

- `windows`: An alias for `x86_64-pc-windows-msvc`, the default target for Windows
- `linux`: An alias for `x86_64-unknown-linux-gnu`, the default target for Linux
- `macos`: An alias for `aarch64-apple-darwin`, the default target for macOS
- `x86_64-pc-windows-msvc`: A 64-bit x86 Windows target
- `aarch64-pc-windows-msvc`: An ARM64 Windows target
- `i686-pc-windows-msvc`: A 32-bit x86 Windows target
- `x86_64-unknown-linux-gnu`: An x86 Linux target. Equivalent to `x86_64-manylinux_2_28`
- `aarch64-apple-darwin`: An ARM-based macOS target, as seen on Apple Silicon devices
- `x86_64-apple-darwin`: An x86 macOS target
- `aarch64-unknown-linux-gnu`: An ARM64 Linux target. Equivalent to `aarch64-manylinux_2_28`
- `aarch64-unknown-linux-musl`: An ARM64 Linux target
- `x86_64-unknown-linux-musl`: An `x86_64` Linux target
- `riscv64-unknown-linux`: A RISCV64 Linux target
- `x86_64-manylinux2014`: An `x86_64` target for the `manylinux2014` platform. Equivalent to `x86_64-manylinux_2_17`
- `x86_64-manylinux_2_17`: An `x86_64` target for the `manylinux_2_17` platform
- `x86_64-manylinux_2_28`: An `x86_64` target for the `manylinux_2_28` platform
- `x86_64-manylinux_2_31`: An `x86_64` target for the `manylinux_2_31` platform
- `x86_64-manylinux_2_32`: An `x86_64` target for the `manylinux_2_32` platform
- `x86_64-manylinux_2_33`: An `x86_64` target for the `manylinux_2_33` platform
- `x86_64-manylinux_2_34`: An `x86_64` target for the `manylinux_2_34` platform
- `x86_64-manylinux_2_35`: An `x86_64` target for the `manylinux_2_35` platform
- `x86_64-manylinux_2_36`: An `x86_64` target for the `manylinux_2_36` platform
- `x86_64-manylinux_2_37`: An `x86_64` target for the `manylinux_2_37` platform
- `x86_64-manylinux_2_38`: An `x86_64` target for the `manylinux_2_38` platform
- `x86_64-manylinux_2_39`: An `x86_64` target for the `manylinux_2_39` platform
- `x86_64-manylinux_2_40`: An `x86_64` target for the `manylinux_2_40` platform
- `aarch64-manylinux2014`: An ARM64 target for the `manylinux2014` platform. Equivalent to `aarch64-manylinux_2_17`
- `aarch64-manylinux_2_17`: An ARM64 target for the `manylinux_2_17` platform
- `aarch64-manylinux_2_28`: An ARM64 target for the `manylinux_2_28` platform
- `aarch64-manylinux_2_31`: An ARM64 target for the `manylinux_2_31` platform
- `aarch64-manylinux_2_32`: An ARM64 target for the `manylinux_2_32` platform
- `aarch64-manylinux_2_33`: An ARM64 target for the `manylinux_2_33` platform
- `aarch64-manylinux_2_34`: An ARM64 target for the `manylinux_2_34` platform
- `aarch64-manylinux_2_35`: An ARM64 target for the `manylinux_2_35` platform
- `aarch64-manylinux_2_36`: An ARM64 target for the `manylinux_2_36` platform
- `aarch64-manylinux_2_37`: An ARM64 target for the `manylinux_2_37` platform
- `aarch64-manylinux_2_38`: An ARM64 target for the `manylinux_2_38` platform
- `aarch64-manylinux_2_39`: An ARM64 target for the `manylinux_2_39` platform
- `aarch64-manylinux_2_40`: An ARM64 target for the `manylinux_2_40` platform
- `aarch64-linux-android`: An ARM64 Android target
- `x86_64-linux-android`: An `x86_64` Android target
- `wasm32-pyodide2024`: A wasm32 target using the Pyodide 2024 platform. Meant for use with Python 3.12
- `arm64-apple-ios`: An ARM64 target for iOS device
- `arm64-apple-ios-simulator`: An ARM64 target for iOS simulator
- `x86_64-apple-ios-simulator`: An `x86_64` target for iOS simulator
```

[`--python-version`](#uv-pip-check--python-version) *python-version* : The Python version against which packages should be checked.

```
By default, the installed packages are checked against the version of the current interpreter.
```

[`--quiet`](#uv-pip-check--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--system`](#uv-pip-check--system) : Check packages in the system Python environment.

```
Disables discovery of virtual environments.

See [uv python](#uv-python) for details on Python discovery.

May also be set with the `UV_SYSTEM_PYTHON` environment variable.
```

[`--verbose`](#uv-pip-check--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

## [uv venv](#uv-venv)

Create a virtual environment.

By default, creates a virtual environment named `.venv` in the working directory. An alternative path may be provided positionally.

If in a project, the default environment name can be changed with the `UV_PROJECT_ENVIRONMENT` environment variable; this only applies when run from the project root directory.

If a virtual environment exists at the target path, it will be removed and a new, empty virtual environment will be created.

When using uv, the virtual environment does not need to be activated. uv will find a virtual environment (named `.venv`) in the working directory or any parent directories.

### Usage

```
uv venv [OPTIONS] [PATH]

```

### Arguments

[PATH](#uv-venv--path) : The path to the virtual environment to create.

```
Default to `.venv` in the working directory.

Relative paths are resolved relative to the working directory.
```

### Options

[`--allow-existing`](#uv-venv--allow-existing) : Preserve any existing files or directories at the target path.

```
By default, `uv venv` will exit with an error if the given path is non-empty. The `--allow-existing` option will instead write to the given path, regardless of its contents, and without clearing it beforehand.

WARNING: This option can lead to unexpected behavior if the existing virtual environment and the newly-created virtual environment are linked to different Python interpreters.
```

[`--allow-insecure-host`](#uv-venv--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-venv--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--clear`](#uv-venv--clear), `-c` : Remove any existing files or directories at the target path.

```
By default, `uv venv` will exit with an error if the given path is non-empty. The `--clear` option will instead clear a non-empty path before creating a new virtual environment.

May also be set with the `UV_VENV_CLEAR` environment variable.
```

[`--color`](#uv-venv--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-venv--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--default-index`](#uv-venv--default-index) *default-index* : The URL of the default package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--index` flag.

May also be set with the `UV_DEFAULT_INDEX` environment variable.
```

[`--directory`](#uv-venv--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--exclude-newer`](#uv-venv--exclude-newer) *exclude-newer* : Limit candidate packages to those that were uploaded prior to the given date.

```
Accepts both RFC 3339 timestamps (e.g., `2006-12-02T02:07:43Z`) and local dates in the same format (e.g., `2006-12-02`) in your system's configured time zone.

May also be set with the `UV_EXCLUDE_NEWER` environment variable.
```

[`--exclude-newer-package`](#uv-venv--exclude-newer-package) *exclude-newer-package* : Limit candidate packages for a specific package to those that were uploaded prior to the given date.

```
Accepts package-date pairs in the format `PACKAGE=DATE`, where `DATE` is an RFC 3339 timestamp (e.g., `2006-12-02T02:07:43Z`) or local date (e.g., `2006-12-02`) in your system's configured time zone.

Can be provided multiple times for different packages.
```

[`--extra-index-url`](#uv-venv--extra-index-url) *extra-index-url* : (Deprecated: use `--index` instead) Extra URLs of package indexes to use, in addition to `--index-url`.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--index-url` (which defaults to PyPI). When multiple `--extra-index-url` flags are provided, earlier values take priority.

May also be set with the `UV_EXTRA_INDEX_URL` environment variable.
```

[`--find-links`](#uv-venv--find-links), `-f` *find-links* : Locations to search for candidate distributions, in addition to those found in the registry indexes.

```
If a path, the target must be a directory that contains packages as wheel files (`.whl`) or source distributions (e.g., `.tar.gz` or `.zip`) at the top level.

If a URL, the page must contain a flat list of links to package files adhering to the formats described above.

May also be set with the `UV_FIND_LINKS` environment variable.
```

[`--help`](#uv-venv--help), `-h` : Display the concise help for this command

[`--index`](#uv-venv--index) *index* : The URLs to use when resolving dependencies, in addition to the default index.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--default-index` (which defaults to PyPI). When multiple `--index` flags are provided, earlier values take priority.

Index names are not supported as values. Relative paths must be disambiguated from index names with `./` or `../` on Unix or `.\\`, `..\\`, `./` or `../` on Windows.

May also be set with the `UV_INDEX` environment variable.
```

[`--index-strategy`](#uv-venv--index-strategy) *index-strategy* : The strategy to use when resolving against multiple index URLs.

```
By default, uv will stop at the first index on which a given package is available, and limit resolutions to those present on that first index (`first-index`). This prevents "dependency confusion" attacks, whereby an attacker can upload a malicious package under the same name to an alternate index.

May also be set with the `UV_INDEX_STRATEGY` environment variable.

Possible values:

- `first-index`: Only use results from the first index that returns a match for a given package name
- `unsafe-first-match`: Search for every package name across all indexes, exhausting the versions from the first index before moving on to the next
- `unsafe-best-match`: Search for every package name across all indexes, preferring the "best" version found. If a package version is in multiple indexes, only look at the entry for the first index
```

[`--index-url`](#uv-venv--index-url), `-i` *index-url* : (Deprecated: use `--default-index` instead) The URL of the Python package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--extra-index-url` flag.

May also be set with the `UV_INDEX_URL` environment variable.
```

[`--keyring-provider`](#uv-venv--keyring-provider) *keyring-provider* : Attempt to use `keyring` for authentication for index URLs.

```
At present, only `--keyring-provider subprocess` is supported, which configures uv to use the `keyring` CLI to handle authentication.

Defaults to `disabled`.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--link-mode`](#uv-venv--link-mode) *link-mode* : The method to use when installing packages from the global cache.

```
This option is only used for installing seed packages.

Defaults to `clone` (also known as Copy-on-Write) on macOS, and `hardlink` on Linux and Windows.

WARNING: The use of symlink link mode is discouraged, as they create tight coupling between the cache and the target environment. For example, clearing the cache (`uv cache clean`) will break all installed packages by way of removing the underlying source files. Use symlinks with caution.

May also be set with the `UV_LINK_MODE` environment variable.

Possible values:

- `clone`: Clone (i.e., copy-on-write) packages from the wheel into the `site-packages` directory
- `copy`: Copy packages from the wheel into the `site-packages` directory
- `hardlink`: Hard link packages from the wheel into the `site-packages` directory
- `symlink`: Symbolically link packages from the wheel into the `site-packages` directory
```

[`--managed-python`](#uv-venv--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-venv--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-venv--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-venv--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-index`](#uv-venv--no-index) : Ignore the registry index (e.g., PyPI), instead relying on direct URL dependencies and those provided via `--find-links`

[`--no-managed-python`](#uv-venv--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-venv--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-project`](#uv-venv--no-project), `--no-workspace` : Avoid discovering a project or workspace.

```
By default, uv searches for projects in the current directory or any parent directory to determine the default path of the virtual environment and check for Python version constraints, if any.
```

[`--no-python-downloads`](#uv-venv--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-venv--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-venv--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--prompt`](#uv-venv--prompt) *prompt* : Provide an alternative prompt prefix for the virtual environment.

```
By default, the prompt is dependent on whether a path was provided to `uv venv`. If provided
(e.g, `uv venv project`), the prompt is set to the directory name. If not provided
(`uv venv`), the prompt is set to the current directory's name.

If "." is provided, the current directory name will be used regardless of whether a path was
provided to `uv venv`.
```

[`--python`](#uv-venv--python), `-p` *python* : The Python interpreter to use for the virtual environment.

```
During virtual environment creation, uv will not look for Python interpreters in virtual
environments.

See [uv python](#uv-python) for details on Python discovery and supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--quiet`](#uv-venv--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--refresh`](#uv-venv--refresh) : Refresh all cached data

[`--refresh-package`](#uv-venv--refresh-package) *refresh-package* : Refresh cached data for a specific package

[`--relocatable`](#uv-venv--relocatable) : Make the virtual environment relocatable.

```
A relocatable virtual environment can be moved around and redistributed without invalidating its associated entrypoint and activation scripts.

Note that this can only be guaranteed for standard `console_scripts` and `gui_scripts`. Other scripts may be adjusted if they ship with a generic `#!python[w]` shebang, and binaries are left as-is.

As a result of making the environment relocatable (by way of writing relative, rather than absolute paths), the entrypoints and scripts themselves will *not* be relocatable. In other words, copying those entrypoints and scripts to a location outside the environment will not work, as they reference paths relative to the environment itself.
```

[`--seed`](#uv-venv--seed) : Install seed packages (one or more of: `pip`, `setuptools`, and `wheel`) into the virtual environment.

```
Note that `setuptools` and `wheel` are not included in Python 3.12+ environments.

May also be set with the `UV_VENV_SEED` environment variable.
```

[`--system-site-packages`](#uv-venv--system-site-packages) : Give the virtual environment access to the system site packages directory.

```
Unlike `pip`, when a virtual environment is created with `--system-site-packages`, uv will *not* take system site packages into account when running commands like `uv pip list` or `uv pip install`. The `--system-site-packages` flag will provide the virtual environment with access to the system site packages directory at runtime, but will not affect the behavior of uv commands.
```

[`--verbose`](#uv-venv--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

## [uv build](#uv-build)

Build Python packages into source distributions and wheels.

`uv build` accepts a path to a directory or source distribution, which defaults to the current working directory.

By default, if passed a directory, `uv build` will build a source distribution ("sdist") from the source directory, and a binary distribution ("wheel") from the source distribution.

`uv build --sdist` can be used to build only the source distribution, `uv build --wheel` can be used to build only the binary distribution, and `uv build --sdist --wheel` can be used to build both distributions from source.

If passed a source distribution, `uv build --wheel` will build a wheel from the source distribution.

### Usage

```
uv build [OPTIONS] [SRC]

```

### Arguments

[SRC](#uv-build--src) : The directory from which distributions should be built, or a source distribution archive to build into a wheel.

```
Defaults to the current working directory.
```

### Options

[`--all-packages`](#uv-build--all-packages), `--all` : Builds all packages in the workspace.

```
The workspace will be discovered from the provided source directory, or the current directory if no source directory is provided.

If the workspace member does not exist, uv will exit with an error.
```

[`--allow-insecure-host`](#uv-build--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--build-constraints`](#uv-build--build-constraints), `--build-constraint`, `-b` *build-constraints* : Constrain build dependencies using the given requirements files when building distributions.

```
Constraints files are `requirements.txt`-like files that only control the *version* of a build dependency that's installed. However, including a package in a constraints file will *not* trigger the inclusion of that package on its own.

May also be set with the `UV_BUILD_CONSTRAINT` environment variable.
```

[`--cache-dir`](#uv-build--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-build--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-build--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--config-setting`](#uv-build--config-setting), `--config-settings`, `-C` *config-setting* : Settings to pass to the PEP 517 build backend, specified as `KEY=VALUE` pairs

[`--config-settings-package`](#uv-build--config-settings-package), `--config-settings-package` *config-settings-package* : Settings to pass to the PEP 517 build backend for a specific package, specified as `PACKAGE:KEY=VALUE` pairs

[`--default-index`](#uv-build--default-index) *default-index* : The URL of the default package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--index` flag.

May also be set with the `UV_DEFAULT_INDEX` environment variable.
```

[`--directory`](#uv-build--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--exclude-newer`](#uv-build--exclude-newer) *exclude-newer* : Limit candidate packages to those that were uploaded prior to the given date.

```
Accepts both RFC 3339 timestamps (e.g., `2006-12-02T02:07:43Z`) and local dates in the same format (e.g., `2006-12-02`) in your system's configured time zone.

May also be set with the `UV_EXCLUDE_NEWER` environment variable.
```

[`--exclude-newer-package`](#uv-build--exclude-newer-package) *exclude-newer-package* : Limit candidate packages for a specific package to those that were uploaded prior to the given date.

```
Accepts package-date pairs in the format `PACKAGE=DATE`, where `DATE` is an RFC 3339 timestamp (e.g., `2006-12-02T02:07:43Z`) or local date (e.g., `2006-12-02`) in your system's configured time zone.

Can be provided multiple times for different packages.
```

[`--extra-index-url`](#uv-build--extra-index-url) *extra-index-url* : (Deprecated: use `--index` instead) Extra URLs of package indexes to use, in addition to `--index-url`.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--index-url` (which defaults to PyPI). When multiple `--extra-index-url` flags are provided, earlier values take priority.

May also be set with the `UV_EXTRA_INDEX_URL` environment variable.
```

[`--find-links`](#uv-build--find-links), `-f` *find-links* : Locations to search for candidate distributions, in addition to those found in the registry indexes.

```
If a path, the target must be a directory that contains packages as wheel files (`.whl`) or source distributions (e.g., `.tar.gz` or `.zip`) at the top level.

If a URL, the page must contain a flat list of links to package files adhering to the formats described above.

May also be set with the `UV_FIND_LINKS` environment variable.
```

[`--force-pep517`](#uv-build--force-pep517) : Always build through PEP 517, don't use the fast path for the uv build backend.

```
By default, uv won't create a PEP 517 build environment for packages using the uv build backend, but use a fast path that calls into the build backend directly. This option forces always using PEP 517.
```

[`--fork-strategy`](#uv-build--fork-strategy) *fork-strategy* : The strategy to use when selecting multiple versions of a given package across Python versions and platforms.

```
By default, uv will optimize for selecting the latest version of each package for each supported Python version (`requires-python`), while minimizing the number of selected versions across platforms.

Under `fewest`, uv will minimize the number of selected versions for each package, preferring older versions that are compatible with a wider range of supported Python versions or platforms.

May also be set with the `UV_FORK_STRATEGY` environment variable.

Possible values:

- `fewest`: Optimize for selecting the fewest number of versions for each package. Older versions may be preferred if they are compatible with a wider range of supported Python versions or platforms
- `requires-python`: Optimize for selecting latest supported version of each package, for each supported Python version
```

[`--help`](#uv-build--help), `-h` : Display the concise help for this command

[`--index`](#uv-build--index) *index* : The URLs to use when resolving dependencies, in addition to the default index.

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

All indexes provided via this flag take priority over the index specified by `--default-index` (which defaults to PyPI). When multiple `--index` flags are provided, earlier values take priority.

Index names are not supported as values. Relative paths must be disambiguated from index names with `./` or `../` on Unix or `.\\`, `..\\`, `./` or `../` on Windows.

May also be set with the `UV_INDEX` environment variable.
```

[`--index-strategy`](#uv-build--index-strategy) *index-strategy* : The strategy to use when resolving against multiple index URLs.

```
By default, uv will stop at the first index on which a given package is available, and limit resolutions to those present on that first index (`first-index`). This prevents "dependency confusion" attacks, whereby an attacker can upload a malicious package under the same name to an alternate index.

May also be set with the `UV_INDEX_STRATEGY` environment variable.

Possible values:

- `first-index`: Only use results from the first index that returns a match for a given package name
- `unsafe-first-match`: Search for every package name across all indexes, exhausting the versions from the first index before moving on to the next
- `unsafe-best-match`: Search for every package name across all indexes, preferring the "best" version found. If a package version is in multiple indexes, only look at the entry for the first index
```

[`--index-url`](#uv-build--index-url), `-i` *index-url* : (Deprecated: use `--default-index` instead) The URL of the Python package index (by default: <https://pypi.org/simple>).

```
Accepts either a repository compliant with PEP 503 (the simple repository API), or a local directory laid out in the same format.

The index given by this flag is given lower priority than all other indexes specified via the `--extra-index-url` flag.

May also be set with the `UV_INDEX_URL` environment variable.
```

[`--keyring-provider`](#uv-build--keyring-provider) *keyring-provider* : Attempt to use `keyring` for authentication for index URLs.

```
At present, only `--keyring-provider subprocess` is supported, which configures uv to use the `keyring` CLI to handle authentication.

Defaults to `disabled`.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--link-mode`](#uv-build--link-mode) *link-mode* : The method to use when installing packages from the global cache.

```
This option is only used when building source distributions.

Defaults to `clone` (also known as Copy-on-Write) on macOS, and `hardlink` on Linux and Windows.

WARNING: The use of symlink link mode is discouraged, as they create tight coupling between the cache and the target environment. For example, clearing the cache (`uv cache clean`) will break all installed packages by way of removing the underlying source files. Use symlinks with caution.

May also be set with the `UV_LINK_MODE` environment variable.

Possible values:

- `clone`: Clone (i.e., copy-on-write) packages from the wheel into the `site-packages` directory
- `copy`: Copy packages from the wheel into the `site-packages` directory
- `hardlink`: Hard link packages from the wheel into the `site-packages` directory
- `symlink`: Symbolically link packages from the wheel into the `site-packages` directory
```

[`--managed-python`](#uv-build--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-build--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-binary`](#uv-build--no-binary) : Don't install pre-built wheels.

```
The given packages will be built and installed from source. The resolver will still use pre-built wheels to extract package metadata, if available.

May also be set with the `UV_NO_BINARY` environment variable.
```

[`--no-binary-package`](#uv-build--no-binary-package) *no-binary-package* : Don't install pre-built wheels for a specific package

```
May also be set with the `UV_NO_BINARY_PACKAGE` environment variable.
```

[`--no-build`](#uv-build--no-build) : Don't build source distributions.

```
When enabled, resolving will not run arbitrary Python code. The cached wheels of already-built source distributions will be reused, but operations that require building distributions will exit with an error.

May also be set with the `UV_NO_BUILD` environment variable.
```

[`--no-build-isolation`](#uv-build--no-build-isolation) : Disable isolation when building source distributions.

```
Assumes that build dependencies specified by PEP 518 are already installed.

May also be set with the `UV_NO_BUILD_ISOLATION` environment variable.
```

[`--no-build-isolation-package`](#uv-build--no-build-isolation-package) *no-build-isolation-package* : Disable isolation when building source distributions for a specific package.

```
Assumes that the packages' build dependencies specified by PEP 518 are already installed.
```

[`--no-build-logs`](#uv-build--no-build-logs) : Hide logs from the build backend

[`--no-build-package`](#uv-build--no-build-package) *no-build-package* : Don't build source distributions for a specific package

```
May also be set with the `UV_NO_BUILD_PACKAGE` environment variable.
```

[`--no-cache`](#uv-build--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-build--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-index`](#uv-build--no-index) : Ignore the registry index (e.g., PyPI), instead relying on direct URL dependencies and those provided via `--find-links`

[`--no-managed-python`](#uv-build--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-build--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-build--no-python-downloads) : Disable automatic downloads of Python.

[`--no-sources`](#uv-build--no-sources) : Ignore the `tool.uv.sources` table when resolving dependencies. Used to lock against the standards-compliant, publishable package metadata, as opposed to using any workspace, Git, URL, or local path sources

[`--no-verify-hashes`](#uv-build--no-verify-hashes) : Disable validation of hashes in the requirements file.

```
By default, uv will verify any available hashes in the requirements file, but will not require that all requirements have an associated hash. To enforce hash validation, use `--require-hashes`.

May also be set with the `UV_NO_VERIFY_HASHES` environment variable.
```

[`--offline`](#uv-build--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--out-dir`](#uv-build--out-dir), `-o` *out-dir* : The output directory to which distributions should be written.

```
Defaults to the `dist` subdirectory within the source directory, or the directory containing the source distribution archive.
```

[`--package`](#uv-build--package) *package* : Build a specific package in the workspace.

```
The workspace will be discovered from the provided source directory, or the current directory if no source directory is provided.

If the workspace member does not exist, uv will exit with an error.
```

[`--prerelease`](#uv-build--prerelease) *prerelease* : The strategy to use when considering pre-release versions.

```
By default, uv will accept pre-releases for packages that *only* publish pre-releases, along with first-party requirements that contain an explicit pre-release marker in the declared specifiers (`if-necessary-or-explicit`).

May also be set with the `UV_PRERELEASE` environment variable.

Possible values:

- `disallow`: Disallow all pre-release versions
- `allow`: Allow all pre-release versions
- `if-necessary`: Allow pre-release versions if all versions of a package are pre-release
- `explicit`: Allow pre-release versions for first-party packages with explicit pre-release markers in their version requirements
- `if-necessary-or-explicit`: Allow pre-release versions if all versions of a package are pre-release, or if the package has an explicit pre-release marker in its version requirements
```

[`--project`](#uv-build--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--python`](#uv-build--python), `-p` *python* : The Python interpreter to use for the build environment.

```
By default, builds are executed in isolated virtual environments. The discovered interpreter
will be used to create those environments, and will be symlinked or copied in depending on
the platform.

See [uv python](#uv-python) to view supported request formats.

May also be set with the `UV_PYTHON` environment variable.
```

[`--quiet`](#uv-build--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--refresh`](#uv-build--refresh) : Refresh all cached data

[`--refresh-package`](#uv-build--refresh-package) *refresh-package* : Refresh cached data for a specific package

[`--require-hashes`](#uv-build--require-hashes) : Require a matching hash for each requirement.

```
By default, uv will verify any available hashes in the requirements file, but will not require that all requirements have an associated hash.

When `--require-hashes` is enabled, *all* requirements must include a hash or set of hashes, and *all* requirements must either be pinned to exact versions (e.g., `==1.0.0`), or be specified via direct URL.

Hash-checking mode introduces a number of additional constraints:

- Git dependencies are not supported. - Editable installations are not supported. - Local dependencies are not supported, unless they point to a specific wheel (`.whl`) or source archive (`.zip`, `.tar.gz`), as opposed to a directory.

May also be set with the `UV_REQUIRE_HASHES` environment variable.
```

[`--resolution`](#uv-build--resolution) *resolution* : The strategy to use when selecting between the different compatible versions for a given package requirement.

```
By default, uv will use the latest compatible version of each package (`highest`).

May also be set with the `UV_RESOLUTION` environment variable.

Possible values:

- `highest`: Resolve the highest compatible version of each package
- `lowest`: Resolve the lowest compatible version of each package
- `lowest-direct`: Resolve the lowest compatible version of any direct dependencies, and the highest compatible version of any transitive dependencies
```

[`--sdist`](#uv-build--sdist) : Build a source distribution ("sdist") from the given directory

[`--upgrade`](#uv-build--upgrade), `-U` : Allow package upgrades, ignoring pinned versions in any existing output file. Implies `--refresh`

[`--upgrade-package`](#uv-build--upgrade-package), `-P` *upgrade-package* : Allow upgrades for a specific package, ignoring pinned versions in any existing output file. Implies `--refresh-package`

[`--verbose`](#uv-build--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

[`--wheel`](#uv-build--wheel) : Build a binary distribution ("wheel") from the given directory

## [uv publish](#uv-publish)

Upload distributions to an index

### Usage

```
uv publish [OPTIONS] [FILES]...

```

### Arguments

[FILES](#uv-publish--files) : Paths to the files to upload. Accepts glob expressions.

```
Defaults to the `dist` directory. Selects only wheels and source distributions, while ignoring other files.
```

### Options

[`--allow-insecure-host`](#uv-publish--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-publish--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--check-url`](#uv-publish--check-url) *check-url* : Check an index URL for existing files to skip duplicate uploads.

```
This option allows retrying publishing that failed after only some, but not all files have been uploaded, and handles errors due to parallel uploads of the same file.

Before uploading, the index is checked. If the exact same file already exists in the index, the file will not be uploaded. If an error occurred during the upload, the index is checked again, to handle cases where the identical file was uploaded twice in parallel.

The exact behavior will vary based on the index. When uploading to PyPI, uploading the same file succeeds even without `--check-url`, while most other indexes error. When uploading to pyx, the index URL can be inferred automatically from the publish URL.

The index must provide one of the supported hashes (SHA-256, SHA-384, or SHA-512).

May also be set with the `UV_PUBLISH_CHECK_URL` environment variable.
```

[`--color`](#uv-publish--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-publish--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-publish--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--dry-run`](#uv-publish--dry-run) : Perform a dry run without uploading files.

```
When enabled, the command will check for existing files if `--check-url` is provided, and will perform validation against the index if supported, but will not upload any files.
```

[`--help`](#uv-publish--help), `-h` : Display the concise help for this command

[`--index`](#uv-publish--index) *index* : The name of an index in the configuration to use for publishing.

````
The index must have a `publish-url` setting, for example:

```
[[tool.uv.index]]
name = "pypi"
url = "https://pypi.org/simple"
publish-url = "https://upload.pypi.org/legacy/"

```

The index `url` will be used to check for existing files to skip duplicate uploads.

With these settings, the following two calls are equivalent:

```
uv publish --index pypi
uv publish --publish-url https://upload.pypi.org/legacy/ --check-url https://pypi.org/simple

```

May also be set with the `UV_PUBLISH_INDEX` environment variable.
````

[`--keyring-provider`](#uv-publish--keyring-provider) *keyring-provider* : Attempt to use `keyring` for authentication for remote requirements files.

```
At present, only `--keyring-provider subprocess` is supported, which configures uv to use the `keyring` CLI to handle authentication.

Defaults to `disabled`.

May also be set with the `UV_KEYRING_PROVIDER` environment variable.

Possible values:

- `disabled`: Do not use keyring for credential lookup
- `subprocess`: Use the `keyring` command for credential lookup
```

[`--managed-python`](#uv-publish--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-publish--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-publish--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-publish--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-publish--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-publish--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-publish--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-publish--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--password`](#uv-publish--password), `-p` *password* : The password for the upload

```
May also be set with the `UV_PUBLISH_PASSWORD` environment variable.
```

[`--project`](#uv-publish--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--publish-url`](#uv-publish--publish-url) *publish-url* : The URL of the upload endpoint (not the index URL).

```
Note that there are typically different URLs for index access (e.g., `https:://.../simple`) and index upload.

Defaults to PyPI's publish URL (<https://upload.pypi.org/legacy/>).

May also be set with the `UV_PUBLISH_URL` environment variable.
```

[`--quiet`](#uv-publish--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--token`](#uv-publish--token), `-t` *token* : The token for the upload.

```
Using a token is equivalent to passing `__token__` as `--username` and the token as `--password` password.

May also be set with the `UV_PUBLISH_TOKEN` environment variable.
```

[`--trusted-publishing`](#uv-publish--trusted-publishing) *trusted-publishing* : Configure trusted publishing.

```
By default, uv checks for trusted publishing when running in a supported environment, but ignores it if it isn't configured.

uv's supported environments for trusted publishing include GitHub Actions and GitLab CI/CD.

Possible values:

- `automatic`: Attempt trusted publishing when we're in a supported environment, continue if that fails
- `always`
- `never`
```

[`--username`](#uv-publish--username), `-u` *username* : The username for the upload

```
May also be set with the `UV_PUBLISH_USERNAME` environment variable.
```

[`--verbose`](#uv-publish--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

## [uv cache](#uv-cache)

Manage uv's cache

### Usage

```
uv cache [OPTIONS] <COMMAND>

```

### Commands

[`uv cache clean`](#uv-cache-clean) : Clear the cache, removing all entries or those linked to specific packages

[`uv cache prune`](#uv-cache-prune) : Prune all unreachable objects from the cache

[`uv cache dir`](#uv-cache-dir) : Show the cache directory

### [uv cache clean](#uv-cache-clean)

Clear the cache, removing all entries or those linked to specific packages

### Usage

```
uv cache clean [OPTIONS] [PACKAGE]...

```

### Arguments

[PACKAGE](#uv-cache-clean--package) : The packages to remove from the cache

### Options

[`--allow-insecure-host`](#uv-cache-clean--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-cache-clean--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-cache-clean--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-cache-clean--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-cache-clean--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--force`](#uv-cache-clean--force) : Force removal of the cache, ignoring in-use checks.

```
By default, `uv cache clean` will block until no process is reading the cache. When `--force` is used, `uv cache clean` will proceed without taking a lock.
```

[`--help`](#uv-cache-clean--help), `-h` : Display the concise help for this command

[`--managed-python`](#uv-cache-clean--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-cache-clean--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-cache-clean--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-cache-clean--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-cache-clean--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-cache-clean--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-cache-clean--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-cache-clean--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-cache-clean--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--quiet`](#uv-cache-clean--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--verbose`](#uv-cache-clean--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv cache prune](#uv-cache-prune)

Prune all unreachable objects from the cache

### Usage

```
uv cache prune [OPTIONS]

```

### Options

[`--allow-insecure-host`](#uv-cache-prune--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-cache-prune--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--ci`](#uv-cache-prune--ci) : Optimize the cache for persistence in a continuous integration environment, like GitHub Actions.

```
By default, uv caches both the wheels that it builds from source and the pre-built wheels that it downloads directly, to enable high-performance package installation. In some scenarios, though, persisting pre-built wheels may be undesirable. For example, in GitHub Actions, it's faster to omit pre-built wheels from the cache and instead have re-download them on each run. However, it typically *is* faster to cache wheels that are built from source, since the wheel building process can be expensive, especially for extension modules.

In `--ci` mode, uv will prune any pre-built wheels from the cache, but retain any wheels that were built from source.
```

[`--color`](#uv-cache-prune--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-cache-prune--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-cache-prune--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--force`](#uv-cache-prune--force) : Force removal of the cache, ignoring in-use checks.

```
By default, `uv cache prune` will block until no process is reading the cache. When `--force` is used, `uv cache prune` will proceed without taking a lock.
```

[`--help`](#uv-cache-prune--help), `-h` : Display the concise help for this command

[`--managed-python`](#uv-cache-prune--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-cache-prune--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-cache-prune--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-cache-prune--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-cache-prune--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-cache-prune--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-cache-prune--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-cache-prune--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-cache-prune--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--quiet`](#uv-cache-prune--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--verbose`](#uv-cache-prune--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv cache dir](#uv-cache-dir)

Show the cache directory.

By default, the cache is stored in `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on Unix and `%LOCALAPPDATA%\uv\cache` on Windows.

When `--no-cache` is used, the cache is stored in a temporary directory and discarded when the process exits.

An alternative cache directory may be specified via the `cache-dir` setting, the `--cache-dir` option, or the `$UV_CACHE_DIR` environment variable.

Note that it is important for performance for the cache directory to be located on the same file system as the Python environment uv is operating on.

### Usage

```
uv cache dir [OPTIONS]

```

### Options

[`--allow-insecure-host`](#uv-cache-dir--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-cache-dir--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-cache-dir--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-cache-dir--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-cache-dir--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--help`](#uv-cache-dir--help), `-h` : Display the concise help for this command

[`--managed-python`](#uv-cache-dir--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-cache-dir--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-cache-dir--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-cache-dir--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-cache-dir--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-cache-dir--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-cache-dir--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-cache-dir--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-cache-dir--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--quiet`](#uv-cache-dir--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--verbose`](#uv-cache-dir--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

## [uv self](#uv-self)

Manage the uv executable

### Usage

```
uv self [OPTIONS] <COMMAND>

```

### Commands

[`uv self update`](#uv-self-update) : Update uv

[`uv self version`](#uv-self-version) : Display uv's version

### [uv self update](#uv-self-update)

Update uv

### Usage

```
uv self update [OPTIONS] [TARGET_VERSION]

```

### Arguments

[TARGET_VERSION](#uv-self-update--target_version) : Update to the specified version. If not provided, uv will update to the latest version

### Options

[`--allow-insecure-host`](#uv-self-update--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-self-update--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-self-update--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-self-update--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-self-update--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--dry-run`](#uv-self-update--dry-run) : Run without performing the update

[`--help`](#uv-self-update--help), `-h` : Display the concise help for this command

[`--managed-python`](#uv-self-update--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-self-update--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-self-update--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-self-update--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-self-update--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-self-update--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-self-update--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-self-update--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-self-update--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--quiet`](#uv-self-update--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--token`](#uv-self-update--token) *token* : A GitHub token for authentication. A token is not required but can be used to reduce the chance of encountering rate limits

```
May also be set with the `UV_GITHUB_TOKEN` environment variable.
```

[`--verbose`](#uv-self-update--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

### [uv self version](#uv-self-version)

Display uv's version

### Usage

```
uv self version [OPTIONS]

```

### Options

[`--allow-insecure-host`](#uv-self-version--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-self-version--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-self-version--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-self-version--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-self-version--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--help`](#uv-self-version--help), `-h` : Display the concise help for this command

[`--managed-python`](#uv-self-version--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-self-version--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-self-version--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-self-version--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-self-version--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-progress`](#uv-self-version--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-self-version--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-self-version--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--output-format`](#uv-self-version--output-format) *output-format*

[`--project`](#uv-self-version--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--quiet`](#uv-self-version--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--short`](#uv-self-version--short) : Only print the version

[`--verbose`](#uv-self-version--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```

## [uv generate-shell-completion](#uv-generate-shell-completion)

Generate shell completion

### Usage

```
uv generate-shell-completion [OPTIONS] <SHELL>

```

### Arguments

[SHELL](#uv-generate-shell-completion--shell) : The shell to generate the completion script for

### Options

[`--allow-insecure-host`](#uv-generate-shell-completion--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--directory`](#uv-generate-shell-completion--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--managed-python`](#uv-generate-shell-completion--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--no-managed-python`](#uv-generate-shell-completion--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--project`](#uv-generate-shell-completion--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

## [uv help](#uv-help)

Display documentation for a command

### Usage

```
uv help [OPTIONS] [COMMAND]...

```

### Arguments

[COMMAND](#uv-help--command)

### Options

[`--allow-insecure-host`](#uv-help--allow-insecure-host), `--trusted-host` *allow-insecure-host* : Allow insecure connections to a host.

```
Can be provided multiple times.

Expects to receive either a hostname (e.g., `localhost`), a host-port pair (e.g., `localhost:8080`), or a URL (e.g., `https://localhost`).

WARNING: Hosts included in this list will not be verified against the system's certificate store. Only use `--allow-insecure-host` in a secure network with verified sources, as it bypasses SSL verification and could expose you to MITM attacks.

May also be set with the `UV_INSECURE_HOST` environment variable.
```

[`--cache-dir`](#uv-help--cache-dir) *cache-dir* : Path to the cache directory.

```
Defaults to `$XDG_CACHE_HOME/uv` or `$HOME/.cache/uv` on macOS and Linux, and `%LOCALAPPDATA%\uv\cache` on Windows.

To view the location of the cache directory, run `uv cache dir`.

May also be set with the `UV_CACHE_DIR` environment variable.
```

[`--color`](#uv-help--color) *color-choice* : Control the use of color in output.

```
By default, uv will automatically detect support for colors when writing to a terminal.

Possible values:

- `auto`: Enables colored output only when the output is going to a terminal or TTY with support
- `always`: Enables colored output regardless of the detected environment
- `never`: Disables colored output
```

[`--config-file`](#uv-help--config-file) *config-file* : The path to a `uv.toml` file to use for configuration.

```
While uv configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

May also be set with the `UV_CONFIG_FILE` environment variable.
```

[`--directory`](#uv-help--directory) *directory* : Change to the given directory prior to running the command.

```
Relative paths are resolved with the given directory as the base.

See `--project` to only change the project root directory.

May also be set with the `UV_WORKING_DIRECTORY` environment variable.
```

[`--help`](#uv-help--help), `-h` : Display the concise help for this command

[`--managed-python`](#uv-help--managed-python) : Require use of uv-managed Python versions.

```
By default, uv prefers using Python versions it manages. However, it will use system Python versions if a uv-managed Python is not installed. This option disables use of system Python versions.

May also be set with the `UV_MANAGED_PYTHON` environment variable.
```

[`--native-tls`](#uv-help--native-tls) : Whether to load TLS certificates from the platform's native certificate store.

```
By default, uv loads certificates from the bundled `webpki-roots` crate. The `webpki-roots` are a reliable set of trust roots from Mozilla, and including them in uv improves portability and performance (especially on macOS).

However, in some cases, you may want to use the platform's native certificate store, especially if you're relying on a corporate trust root (e.g., for a mandatory proxy) that's included in your system's certificate store.

May also be set with the `UV_NATIVE_TLS` environment variable.
```

[`--no-cache`](#uv-help--no-cache), `--no-cache-dir`, `-n` : Avoid reading from or writing to the cache, instead using a temporary directory for the duration of the operation

```
May also be set with the `UV_NO_CACHE` environment variable.
```

[`--no-config`](#uv-help--no-config) : Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).

```
Normally, configuration files are discovered in the current directory, parent directories, or user configuration directories.

May also be set with the `UV_NO_CONFIG` environment variable.
```

[`--no-managed-python`](#uv-help--no-managed-python) : Disable use of uv-managed Python versions.

```
Instead, uv will search for a suitable Python version on the system.

May also be set with the `UV_NO_MANAGED_PYTHON` environment variable.
```

[`--no-pager`](#uv-help--no-pager) : Disable pager when printing help

[`--no-progress`](#uv-help--no-progress) : Hide all progress outputs.

```
For example, spinners or progress bars.

May also be set with the `UV_NO_PROGRESS` environment variable.
```

[`--no-python-downloads`](#uv-help--no-python-downloads) : Disable automatic downloads of Python.

[`--offline`](#uv-help--offline) : Disable network access.

```
When disabled, uv will only use locally cached data and locally available files.

May also be set with the `UV_OFFLINE` environment variable.
```

[`--project`](#uv-help--project) *project* : Run the command within the given project directory.

```
All `pyproject.toml`, `uv.toml`, and `.python-version` files will be discovered by walking up the directory tree from the project root, as will the project's virtual environment (`.venv`).

Other command-line arguments (such as relative paths) will be resolved relative to the current working directory.

See `--directory` to change the working directory entirely.

This setting has no effect when used in the `uv pip` interface.

May also be set with the `UV_PROJECT` environment variable.
```

[`--quiet`](#uv-help--quiet), `-q` : Use quiet output.

```
Repeating this option, e.g., `-qq`, will enable a silent mode in which uv will write no output to stdout.
```

[`--verbose`](#uv-help--verbose), `-v` : Use verbose output.

```
You can configure fine-grained logging using the `RUST_LOG` environment variable. (<https://docs.rs/tracing-subscriber/latest/tracing_subscriber/filter/struct.EnvFilter.html#directives>)
```
