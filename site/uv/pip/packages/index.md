# [Managing packages](#managing-packages)

## [Installing a package](#installing-a-package)

To install a package into the virtual environment, e.g., Flask:

```
$ uv pip install flask

```

To install a package with optional dependencies enabled, e.g., Flask with the "dotenv" extra:

```
$ uv pip install "flask[dotenv]"

```

To install multiple packages, e.g., Flask and Ruff:

```
$ uv pip install flask ruff

```

To install a package with a constraint, e.g., Ruff v0.2.0 or newer:

```
$ uv pip install 'ruff>=0.2.0'

```

To install a package at a specific version, e.g., Ruff v0.3.0:

```
$ uv pip install 'ruff==0.3.0'

```

To install a package from the disk:

```
$ uv pip install "ruff @ ./projects/ruff"

```

To install a package from GitHub:

```
$ uv pip install "git+https://github.com/astral-sh/ruff"

```

To install a package from GitHub at a specific reference:

```
$ # Install a tag
$ uv pip install "git+https://github.com/astral-sh/ruff@v0.2.0"

$ # Install a commit
$ uv pip install "git+https://github.com/astral-sh/ruff@1fadefa67b26508cc59cf38e6130bde2243c929d"

$ # Install a branch
$ uv pip install "git+https://github.com/astral-sh/ruff@main"

```

See the [Git authentication](../../concepts/authentication/#git-authentication) documentation for installation from a private repository.

## [Editable packages](#editable-packages)

Editable packages do not need to be reinstalled for changes to their source code to be active.

To install the current project as an editable package

```
$ uv pip install -e .

```

To install a project in another directory as an editable package:

```
$ uv pip install -e "ruff @ ./project/ruff"

```

## [Installing packages from files](#installing-packages-from-files)

Multiple packages can be installed at once from standard file formats.

Install from a `requirements.txt` file:

```
$ uv pip install -r requirements.txt

```

See the [`uv pip compile`](../compile/) documentation for more information on `requirements.txt` files.

Install from a `pyproject.toml` file:

```
$ uv pip install -r pyproject.toml

```

Install from a `pyproject.toml` file with optional dependencies enabled, e.g., the "foo" extra:

```
$ uv pip install -r pyproject.toml --extra foo

```

Install from a `pyproject.toml` file with all optional dependencies enabled:

```
$ uv pip install -r pyproject.toml --all-extras

```

To install dependency groups in the current project directory's `pyproject.toml`, for example the group `foo`:

```
$ uv pip install --group foo

```

To specify the project directory where groups should be sourced from:

```
$ uv pip install --project some/path/ --group foo --group bar

```

Alternatively, you can specify a path to a `pyproject.toml` for each group:

```
$ uv pip install --group some/path/pyproject.toml:foo --group other/pyproject.toml:bar

```

Note

As in pip, `--group` flags do not apply to other sources specified with flags like `-r` or `-e`. For instance, `uv pip install -r some/path/pyproject.toml --group foo` sources `foo` from `./pyproject.toml` and **not** `some/path/pyproject.toml`.

## [Uninstalling a package](#uninstalling-a-package)

To uninstall a package, e.g., Flask:

```
$ uv pip uninstall flask

```

To uninstall multiple packages, e.g., Flask and Ruff:

```
$ uv pip uninstall flask ruff

```
