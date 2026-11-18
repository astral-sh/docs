# [Checking standalone scripts](#checking-standalone-scripts)

Python scripts can declare their dependencies and Python version requirements using [inline script metadata (PEP 723)](https://peps.python.org/pep-0723/). ty can use [uv](https://docs.astral.sh/uv/) to install each script's dependencies in its own environment. This lets you check a project and its scripts together, even when they target different Python versions or use different versions of the same package.

Preview

The uv integration for scripts is in preview and currently **off by default**. The minimum supported versions are uv 0.12.3 and ty 0.0.76.

## [On the command line](#on-the-command-line)

For example, the following script requires `requests` and `rich`.

example.py

```
# /// script
# requires-python = ">=3.12"
# dependencies = ["requests<3", "rich"]
# ///

import requests
from rich.console import Console
from rich.pretty import pprint

response = requests.get("https://peps.python.org/api/peps.json")
peps = response.json()
Console().rule("Python Enhancement Proposals")
pprint([(number, pep["title"]) for number, pep in peps.items()][:10])
```

If these packages are missing from your Python environment, `ty check` reports unresolved imports.

```
$ ty check example.py
error[import-not-found]: Cannot resolve imported module `requests`
 --> example.py:6:8
  |
6 | import requests
  |        ^^^^^^^^

...

Found 3 diagnostics
```

When [`project-manager.script`](../reference/configuration/#script) is set to `"uv"`, ty uses uv to set up a separate environment and install the script's dependencies. To enable the integration for scripts in a project, add the option to your [configuration](../configuration/):

```
[tool.ty.project-manager]
script = "uv"
```

```
[project-manager]
script = "uv"
```

ty can now resolve the script's imports:

```
$ ty check example.py
All checks passed!
```

To check the project and all its scripts together, omit the file name:

```
ty check
```

For a single invocation, you can also pass the option with `--config`:

```
ty check --config 'project-manager.script="uv"' example.py
```

Alternatively, you can check the script with uv's experimental [`uv check --script example.py`](https://docs.astral.sh/uv/reference/cli/#uv-check--script) command, which enables the integration automatically.

## [In your editor](#in-your-editor)

The same `project-manager.script` setting enables the integration in your editor. In `example.py`, you can then use ty's [editor features](../features/language-server/) to complete imports from `rich`, see `pprint`'s signature on hover, or go to its definition.

\[ [Download the editor demo](../assets/scripts-editor-demo.mp4). \](../assets/scripts-editor-demo.mp4)

When the script is saved with `rich` in its dependency list, ty installs it with uv. Accepting the `Console` completion adds `from rich.console import Console`. Completions, hover, and Go to Definition now work with `rich`.

## [Configuring a script](#configuring-a-script)

A script in a project uses the [project's ty settings](../configuration/) by default. For example, if your project disables [`index-out-of-bounds`](../reference/rules/#index-out-of-bounds), ty skips that rule in `scripts/example.py`. An [`override`](../reference/configuration/#overrides) for `scripts/*.py` can turn the rule back on for that file.

ty also respects the script's Python version requirements. Changing `requires-python` to `">=3.13"` makes ty check `scripts/example.py` against Python 3.13, even if the project targets Python 3.12.

To share `scripts/example.py` with its own ty configuration, you can add a [`[tool.ty]`](../reference/configuration/) table to its inline metadata. The table uses the same syntax as in `pyproject.toml`.

scripts/example.py

```
# /// script
# requires-python = ">=3.12"
# dependencies = ["requests<3", "rich"]
#
# [tool.ty.project-manager]
# script = "uv"
#
# [tool.ty.rules]
# index-out-of-bounds = "warn"
# ///
```

The inline table replaces the project settings and overrides for the script, even if it is empty. With this configuration, ty continues to use uv for the script, treats `index-out-of-bounds` as a warning, and uses its defaults for other settings.
