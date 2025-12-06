# [Installing uv](#installing-uv)

## [Installation methods](#installation-methods)

Install uv with our standalone installers or your package manager of choice.

### [Standalone installer](#standalone-installer)

uv provides a standalone installer to download and install uv:

Use `curl` to download the script and execute it with `sh`:

```
$ curl -LsSf https://astral.sh/uv/install.sh | sh

```

If your system doesn't have `curl`, you can use `wget`:

```
$ wget -qO- https://astral.sh/uv/install.sh | sh

```

Request a specific version by including it in the URL:

```
$ curl -LsSf https://astral.sh/uv/0.9.16/install.sh | sh

```

Use `irm` to download the script and execute it with `iex`:

```
PS> powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"

```

Changing the [execution policy](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.4#powershell-execution-policies) allows running a script from the internet.

Request a specific version by including it in the URL:

```
PS> powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/0.9.16/install.ps1 | iex"

```

Tip

The installation script may be inspected before use:

```
$ curl -LsSf https://astral.sh/uv/install.sh | less

```

```
PS> powershell -c "irm https://astral.sh/uv/install.ps1 | more"

```

Alternatively, the installer or binaries can be downloaded directly from [GitHub](#github-releases).

See the reference documentation on the [installer](../../reference/installer/) for details on customizing your uv installation.

### [PyPI](#pypi)

For convenience, uv is published to [PyPI](https://pypi.org/project/uv/).

If installing from PyPI, we recommend installing uv into an isolated environment, e.g., with `pipx`:

```
$ pipx install uv

```

However, `pip` can also be used:

```
$ pip install uv

```

Note

uv ships with prebuilt distributions (wheels) for many platforms; if a wheel is not available for a given platform, uv will be built from source, which requires a Rust toolchain. See the [contributing setup guide](https://github.com/astral-sh/uv/blob/main/CONTRIBUTING.md#setup) for details on building uv from source.

### [Homebrew](#homebrew)

uv is available in the core Homebrew packages.

```
$ brew install uv

```

### [MacPorts](#macports)

uv is available via [MacPorts](https://ports.macports.org/port/uv/).

```
$ sudo port install uv

```

### [WinGet](#winget)

uv is available via [WinGet](https://winstall.app/apps/astral-sh.uv).

```
$ winget install --id=astral-sh.uv  -e

```

### [Scoop](#scoop)

uv is available via [Scoop](https://scoop.sh/#/apps?q=uv).

```
$ scoop install main/uv

```

### [Docker](#docker)

uv provides a Docker image at [`ghcr.io/astral-sh/uv`](https://github.com/astral-sh/uv/pkgs/container/uv).

See our guide on [using uv in Docker](../../guides/integration/docker/) for more details.

### [GitHub Releases](#github-releases)

uv release artifacts can be downloaded directly from [GitHub Releases](https://github.com/astral-sh/uv/releases).

Each release page includes binaries for all supported platforms as well as instructions for using the standalone installer via `github.com` instead of `astral.sh`.

### [Cargo](#cargo)

uv is available via [crates.io](https://crates.io).

```
$ cargo install --locked uv

```

Note

This method builds uv from source, which requires a compatible Rust toolchain.

## [Upgrading uv](#upgrading-uv)

When uv is installed via the standalone installer, it can update itself on-demand:

```
$ uv self update

```

Tip

Updating uv will re-run the installer and can modify your shell profiles. To disable this behavior, set `UV_NO_MODIFY_PATH=1`.

When another installation method is used, self-updates are disabled. Use the package manager's upgrade method instead. For example, with `pip`:

```
$ pip install --upgrade uv

```

## [Shell autocompletion](#shell-autocompletion)

Tip

You can run `echo $SHELL` to help you determine your shell.

To enable shell autocompletion for uv commands, run one of the following:

```
echo 'eval "$(uv generate-shell-completion bash)"' >> ~/.bashrc

```

```
echo 'eval "$(uv generate-shell-completion zsh)"' >> ~/.zshrc

```

```
echo 'uv generate-shell-completion fish | source' > ~/.config/fish/completions/uv.fish

```

```
echo 'eval (uv generate-shell-completion elvish | slurp)' >> ~/.elvish/rc.elv

```

```
if (!(Test-Path -Path $PROFILE)) {
  New-Item -ItemType File -Path $PROFILE -Force
}
Add-Content -Path $PROFILE -Value '(& uv generate-shell-completion powershell) | Out-String | Invoke-Expression'

```

To enable shell autocompletion for uvx, run one of the following:

```
echo 'eval "$(uvx --generate-shell-completion bash)"' >> ~/.bashrc

```

```
echo 'eval "$(uvx --generate-shell-completion zsh)"' >> ~/.zshrc

```

```
echo 'uvx --generate-shell-completion fish | source' > ~/.config/fish/completions/uvx.fish

```

```
echo 'eval (uvx --generate-shell-completion elvish | slurp)' >> ~/.elvish/rc.elv

```

```
if (!(Test-Path -Path $PROFILE)) {
  New-Item -ItemType File -Path $PROFILE -Force
}
Add-Content -Path $PROFILE -Value '(& uvx --generate-shell-completion powershell) | Out-String | Invoke-Expression'

```

Then restart the shell or source the shell config file.

## [Uninstallation](#uninstallation)

If you need to remove uv from your system, follow these steps:

1. Clean up stored data (optional):

   ```
   $ uv cache clean
   $ rm -r "$(uv python dir)"
   $ rm -r "$(uv tool dir)"

   ```

   Tip

   Before removing the binaries, you may want to remove any data that uv has stored. See the [storage reference](../../reference/storage/) for details on where uv stores data.

1. Remove the uv, uvx, and uvw binaries:

   ```
   $ rm ~/.local/bin/uv ~/.local/bin/uvx

   ```

   ```
   PS> rm $HOME\.local\bin\uv.exe
   PS> rm $HOME\.local\bin\uvx.exe
   PS> rm $HOME\.local\bin\uvw.exe

   ```

   Note

   Prior to 0.5.0, uv was installed into `~/.cargo/bin`. The binaries can be removed from there to uninstall. Upgrading from an older version will not automatically remove the binaries from `~/.cargo/bin`.

## [Next steps](#next-steps)

See the [first steps](../first-steps/) or jump straight to the [guides](../../guides/) to start using uv.
