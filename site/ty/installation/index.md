# [Installing ty](#installing-ty)

## [Running ty without installation](#running-ty-without-installation)

Use [uvx](https://docs.astral.sh/uv/guides/tools/) to quickly get started with ty:

```
uvx ty

```

## [Installation methods](#installation-methods)

### [Adding ty to your project](#adding-ty-to-your-project)

Tip

Adding ty as a dependency ensures that all developers on the project are using the same version of ty.

Use [uv](https://github.com/astral-sh/uv) (or your project manager of choice) to add ty as a development dependency:

```
uv add --dev ty

```

Then, use `uv run` to invoke ty:

```
uv run ty

```

To update ty, use `--upgrade-package`:

```
uv lock --upgrade-package ty

```

### [Installing globally with uv](#installing-globally-with-uv)

Install ty globally with uv:

```
uv tool install ty@latest

```

To update ty, use `uv tool upgrade`:

```
uv tool upgrade ty

```

### [Installing with the standalone installer](#installing-with-the-standalone-installer)

ty includes a standalone installer.

Use `curl` to download the script and execute it with `sh`:

```
$ curl -LsSf https://astral.sh/ty/install.sh | sh

```

If your system doesn't have `curl`, you can use `wget`:

```
$ wget -qO- https://astral.sh/ty/install.sh | sh

```

Request a specific version by including it in the URL:

```
$ curl -LsSf https://astral.sh/ty/0.0.16/install.sh | sh

```

Use `irm` to download the script and execute it with `iex`:

```
PS> powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/ty/install.ps1 | iex"

```

Changing the [execution policy](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.4#powershell-execution-policies) allows running a script from the internet.

Request a specific version by including it in the URL:

```
PS> powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/ty/0.0.16/install.ps1 | iex"

```

Tip

The installation script may be inspected before use:

```
$ curl -LsSf https://astral.sh/ty/install.sh | less

```

```
PS> powershell -c "irm https://astral.sh/ty/install.ps1 | more"

```

Alternatively, the installer or binaries can be downloaded directly from [GitHub](#installing-from-github-releases).

### [Installing from GitHub Releases](#installing-from-github-releases)

ty release artifacts can be downloaded directly from [GitHub Releases](https://github.com/astral-sh/ty/releases).

Each release page includes binaries for all supported platforms as well as instructions for using the standalone installer via `github.com` instead of `astral.sh`.

### [Installing globally with pipx](#installing-globally-with-pipx)

Install ty globally with pipx:

```
pipx install ty

```

To update ty, use `pipx upgrade`:

```
pipx upgrade ty

```

### [Installing with pip](#installing-with-pip)

Install ty into your current Python environment with pip:

```
pip install ty

```

### [Installing globally with mise](#installing-globally-with-mise)

Install ty globally with with [mise](https://github.com/jdx/mise):

```
mise install ty

```

To set it globally:

```
mise use --global ty

```

### [Installing in Docker](#installing-in-docker)

Install ty in Docker by copying the binary from the official image:

Dockerfile

```
COPY --from=ghcr.io/astral-sh/ty:latest /ty /bin/

```

The following tags are available:

- `ghcr.io/astral-sh/ty:latest`
- `ghcr.io/astral-sh/ty:{major}.{minor}.{patch}`, e.g., `ghcr.io/astral-sh/ty:0.0.16`
- `ghcr.io/astral-sh/ty:{major}.{minor}`, e.g., `ghcr.io/astral-sh/ty:0.0` (the latest patch version)

### [Using ty with Bazel](#using-ty-with-bazel)

[`aspect_rules_lint`](https://registry.bazel.build/docs/aspect_rules_lint#function-lint_ty_aspect) provides a Bazel lint aspect that runs ty. See its documentation for setup instructions.

## [Adding ty to your editor](#adding-ty-to-your-editor)

See the [editor integration](../editors/) guide to add ty to your editor.

## [Shell autocompletion](#shell-autocompletion)

Tip

You can run `echo $SHELL` to help you determine your shell.

To enable shell autocompletion for ty commands, run one of the following:

```
echo 'eval "$(ty generate-shell-completion bash)"' >> ~/.bashrc

```

```
echo 'eval "$(ty generate-shell-completion zsh)"' >> ~/.zshrc

```

```
echo 'ty generate-shell-completion fish | source' > ~/.config/fish/completions/ty.fish

```

```
echo 'eval (ty generate-shell-completion elvish | slurp)' >> ~/.elvish/rc.elv

```

```
if (!(Test-Path -Path $PROFILE)) {
  New-Item -ItemType File -Path $PROFILE -Force
}
Add-Content -Path $PROFILE -Value '(& ty generate-shell-completion powershell) | Out-String | Invoke-Expression'

```

Then restart the shell or source the shell config file.
