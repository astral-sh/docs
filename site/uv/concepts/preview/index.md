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

For backwards compatibility, enabling preview features that do not exist will warn, but not error.

## [Using preview features](#using-preview-features)

Often, preview features can be used without changing any preview settings if the behavior change is gated by some sort of user interaction, For example, while `pylock.toml` support is in preview, you can use `uv pip install` with a `pylock.toml` file without additional configuration because specifying the `pylock.toml` file indicates you want to use the feature. However, a warning will be displayed that the feature is in preview. The preview feature can be enabled to silence the warning.

## [Available preview features](#available-preview-features)

The following preview features are available:

- `add-bounds`: Allows configuring the [default bounds for `uv add`](../../reference/settings/#add-bounds) invocations.
- `json-output`: Allows `--output-format json` for various uv commands.
- `package-conflicts`: Allows defining workspace conflicts at the package level.
- `pylock`: Allows installing from `pylock.toml` files.
- `python-install-default`: Allows [installing `python` and `python3` executables](../python-versions/#installing-python-executables).
- `format`: Allows using `uv format`.
- `native-auth`: Enables storage of credentials in a [system-native location](../authentication/http/#the-uv-credentials-store).
- `workspace-metadata`: Allows using `uv workspace metadata`.
- `workspace-dir`: Allows using `uv workspace dir`.
- `workspace-list`: Allows using `uv workspace list`.

## [Disabling preview features](#disabling-preview-features)

The `--no-preview` option can be used to disable preview features.
