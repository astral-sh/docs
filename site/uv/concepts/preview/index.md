# [Preview features](#preview-features)

uv includes opt-in preview features to provide an opportunity for community feedback and increase confidence that changes are a net-benefit before enabling them for everyone.

## [Enabling preview features](#enabling-preview-features)

To enable all preview features, use the `--preview` flag:

```
$ uv run --preview ...
```

Or, set the `UV_PREVIEW` environment variable:

```
$ UV_PREVIEW=1 uv run ...
```

To enable specific preview features, use the `--preview-features` flag:

```
$ uv run --preview-features foo ...
```

The `--preview-features` flag can be repeated to enable multiple features:

```
$ uv run --preview-features foo --preview-features bar ...
```

Or, features can be provided in a comma separated list:

```
$ uv run --preview-features foo,bar ...
```

The `UV_PREVIEW_FEATURES` environment variable can be used similarly, e.g.:

```
$ UV_PREVIEW_FEATURES=foo,bar uv run ...
```

Preview features can also be enabled in `uv.toml`, or under `[tool.uv]` in `pyproject.toml` and PEP 723 metadata:

```
preview-features = ["foo", "bar"]
```

Set `preview-features = true` to enable all preview features.

Some preview features take effect before configuration files are loaded and cannot be enabled from configuration.

For backwards compatibility, enabling preview features that do not exist will warn, but not error, regardless of the source.

## [Using preview features](#using-preview-features)

Often, preview features can be used without changing any preview settings if the behavior change is gated by some sort of user interaction, For example, while `pylock.toml` support is in preview, you can use `uv pip install` with a `pylock.toml` file without additional configuration because specifying the `pylock.toml` file indicates you want to use the feature. However, a warning will be displayed that the feature is in preview. The preview feature can be enabled to silence the warning.

## [Available preview features](#available-preview-features)

The following preview features are available:

- [`add-bounds`](#add-bounds): Allows configuring the [default bounds for `uv add`](../../reference/settings/#add-bounds) invocations.
- [`adjust-ulimit`](#adjust-ulimit): On Unix, raises the process's soft open-file limit at startup, up to the hard limit.
- [`artifact-hash-filtering`](#artifact-hash-filtering): Restricts generated requirement hashes to artifacts allowed by binary and build policies.
- [`audit-command`](#audit-command): Allows using `uv audit` and `uv tool audit`.
- [`auth-helper`](#auth-helper): Allows using `uv auth helper` as a credential helper for external tools.
- [`azure-endpoint`](#azure-endpoint): Allows signing requests to Azure Blob Storage endpoints with Azure credentials.
- [`batch-export`](#batch-export): Allows using `uv export --batch`.
- [`build-dependency-check`](#build-dependency-check): Checks build dependencies before nonisolated builds with `uv build`.
- [`build-lazy-imports`](#build-lazy-imports): Enables lazy imports in build backend invocations on CPython 3.15 and later. This can affect import-time side effects in third-party build backends.
- [`cache-physical-space`](#cache-physical-space): Reports the physical disk space reclaimed by cache cleanup, accounting for hardlinks and copy-on-write clones.
- [`cache-size`](#cache-size): Allows using `uv cache size`.
- [`centralized-project-envs`](#centralized-project-envs): Stores [project virtual environments](../projects/layout/#centralized-project-environments) in the uv cache.
- [`check-command`](#check-command): Allows using `uv check`.
- [`content-addressed-cache`](#content-addressed-cache): Enables content-addressed wheel archives in the cache.
- [`detect-module-conflicts`](#detect-module-conflicts): Warns when multiple packages would install conflicting Python modules into the same environment.
- [`extra-build-dependencies`](#extra-build-dependencies): Allows specifying additional dependencies for package builds.
- [`format-command`](#format-command): Allows using `uv format`.
- [`gcs-endpoint`](#gcs-endpoint): Allows signing requests to configured Google Cloud Storage endpoints.
- [`index-by-name`](#index-by-name): Allows selecting configured package indexes by name with `--index` and `--default-index`.
- [`index-exclude-newer`](#index-exclude-newer): Allows setting `exclude-newer` on configured package indexes.
- [`index-hash-algorithm`](#index-hash-algorithm): Allows requiring a hash algorithm for configured package indexes.
- [`init-project-flag`](#init-project-flag): Rejects the deprecated `--project` option in `uv init`.
- [`json-output`](#json-output): Allows `--output-format json` for various uv commands.
- [`lock-without-metadata`](#lock-without-metadata): Omit `package.metadata` from `uv.lock`, except for remote URL dependencies.
- [`lockfile-format-check`](#lockfile-format-check): Rejects non-canonical lockfile formatting when using `--locked` or `--check`.
- [`malware-check`](#malware-check): Allows `uv sync` and other commands to check for malware using [OSV](https://osv.dev) before installing packages.
- [`metadata-json`](#metadata-json): Includes JSON metadata files in built wheels.
- [`minimum-libc-version`](#minimum-libc-version): Allows setting minimum libc versions for universal resolutions.
- [`missing-exclude-newer-package-lock`](#missing-exclude-newer-package-lock): Exclude `exclude-newer-package` entries from the lockfile when not included in the project's resolved dependencies.
- [`native-auth`](#native-auth): Enables storage of credentials in a [system-native location](../authentication/http/#the-uv-credentials-store).
- [`no-distutils-patch`](#no-distutils-patch): Stops installing the `_virtualenv.py` / `_virtualenv.pth` distutils configuration monkeypatch in virtual environments for Python 3.10 and later.
- [`package-conflicts`](#package-conflicts): Allows defining workspace conflicts at the package level.
- [`packaged-init`](#packaged-init): Makes `uv init` create a packaged application with a `src/` layout, build system, and script entry point by default.
- [`project-directory-must-exist`](#project-directory-must-exist): Rejects an invalid `--project` path instead of warning and continuing. Except for `uv init`, the path must already exist as a directory or point to a `pyproject.toml` file. This feature takes effect before configuration is loaded.
- [`publish-require-normalized`](#publish-require-normalized): Requires normalized distribution filenames when publishing, skipping files whose names are not normalized.
- [`pylock`](#pylock): Allows installing from `pylock.toml` files.
- [`python-install-default`](#python-install-default): Allows [installing `python` and `python3` executables](../python-versions/#installing-python-executables).
- [`relocatable-envs-default`](#relocatable-envs-default): Creates relocatable virtual environments by default.
- [`resolution-inputs`](#resolution-inputs): Records runtime configuration consultations and omits unused constraints, overrides, exclusions, dependency metadata, and package-specific upload cutoffs from the lockfile.
- [`s3-endpoint`](#s3-endpoint): Allows signing requests to configured S3-compatible endpoints.
- [`sbom-export`](#sbom-export): Allows using `uv export --format=cyclonedx1.5`.
- [`special-conda-env-names`](#special-conda-env-names): Stops treating Conda environments named `base` or `root` as special.
- [`tar-codec`](#tar-codec): Uses the new `tar-codec` encoding/decoding backend, instead of `astral-tokio-tar`.
- [`target-workspace-discovery`](#target-workspace-discovery): Uses the directory containing a local `uv run` target, rather than the current working directory, as the starting point for project and workspace discovery. This feature takes effect before configuration is loaded.
- [`toml-backwards-compatibility`](#toml-backwards-compatibility): Rewrites `pyproject.toml` as TOML 1.0 when building source distributions, preserving the original as `pyproject.toml.orig` to ensure compatibility with older build tools.
- [`tool-install-locks`](#tool-install-locks): Stores a `uv.lock` alongside each installed tool and reuses it for reproducible installations, upgrades, and audits.
- [`venv-safe-clear`](#venv-safe-clear): Prevents `uv venv --clear` from clearing a directory that does not contain a `pyvenv.cfg` file unless `--force` is provided.
- [`workspace-dir`](#workspace-dir): Allows using `uv workspace dir`.
- [`workspace-list`](#workspace-list): Allows using `uv workspace list`.
- [`workspace-list-scripts`](#workspace-list-scripts): Allows using `uv workspace list --scripts`.
- [`workspace-metadata`](#workspace-metadata): Allows using `uv workspace metadata`.

## [Disabling preview features](#disabling-preview-features)

The `--no-preview` option can be used to disable preview features.
