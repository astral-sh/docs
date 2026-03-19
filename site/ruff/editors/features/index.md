# [Features](#features)

This section provides a detailed overview of the features provided by the Ruff Language Server.

## [Diagnostic Highlighting](#diagnostic-highlighting)

Provide diagnostics for your Python code in real-time.

## [Dynamic Configuration](#dynamic-configuration)

The server dynamically refreshes the diagnostics when a configuration file is changed in the workspace, whether it's a `pyproject.toml`, `ruff.toml`, or `.ruff.toml` file.

The server relies on the file watching capabilities of the editor to detect changes to these files. If an editor does not support file watching, the server will not be able to detect changes to the configuration file and thus will not refresh the diagnostics.

## [Formatting](#formatting)

Provide code formatting for your Python code. The server can format an entire document or a specific range of lines.

The VS Code extension provides the `Ruff: Format Document` command to format an entire document. In VS Code, the range formatting can be triggered by selecting a range of lines, right-clicking, and selecting `Format Selection` from the context menu.

### [Markdown code blocks](#markdown-code-blocks)

*This feature is currently only available in [preview mode](https://docs.astral.sh/ruff/preview/preview.md#preview).*

The Ruff formatter can also format Python code blocks in Markdown files. The Ruff VS Code extension provides the `Format Document` command for Markdown files, which will then format the code blocks with the same settings as used for regular Python files.

Note that Ruff will not format any other parts of Markdown files. If you want to use Ruff formatting in addition to another Markdown formatting extension, then you will need to set one as the default in VS Code, and manually run the `Format Document With...` (or `Ruff: Format document`) command to run any other formatters separately.

To enable preview mode for formatting in VS Code, add the following to your `settings.json`:

```
{
  "ruff.format.preview": true,
}
```

To set Ruff as the default formatter for Markdown files in VS Code, add the following to your `settings.json`:

```
{
  "[markdown]": {
    "editor.defaultFormatter": "charliermarsh.ruff"
  }
}
```

Note that Ruff does not support range formatting for Markdown files, so if you have format-on-save enabled, you may also need to specify the following:

```
{
  "[markdown]": {
    "editor.formatOnSave": true,
    "editor.formatOnSaveMode": "file"
  }
}
```

See the [formatter documentation](https://docs.astral.sh/ruff/formatter/#markdown-code-formatting) for more details.

## [Code Actions](#code-actions)

Code actions are context-sensitive suggestions that can help you fix issues in your code. They are usually triggered by a shortcut or by clicking a light bulb icon in the editor. The Ruff Language Server provides the following code actions:

- Apply a quick fix for a diagnostic that has a fix available (e.g., removing an unused import).
- Ignore a diagnostic with a `# noqa` comment.
- Apply all quick fixes available in the document.
- Organize imports in the document.

You can even run these actions on-save. For example, to fix all issues and organize imports on save in VS Code, add the following to your `settings.json`:

```
{
  "[python]": {
    "editor.codeActionsOnSave": {
      "source.fixAll.ruff": "explicit",
      "source.organizeImports.ruff": "explicit"
    }
  }
}
```

### [Fix Safety](#fix-safety)

Ruff's automatic fixes are labeled as "safe" and "unsafe". By default, the "Fix all" action will not apply unsafe fixes. However, unsafe fixes can be applied manually with the "Quick fix" action. Application of unsafe fixes when using "Fix all" can be enabled by setting `unsafe-fixes = true` in your Ruff configuration file.

See the [Ruff fix documentation](https://docs.astral.sh/ruff/linter/#fix-safety) for more details on how fix safety works.

## [Hover](#hover)

The server can provide the rule documentation when focusing over a NoQA code in the comment. Focusing is usually hovering with a mouse, but can also be triggered with a shortcut.

## [Jupyter Notebook](#jupyter-notebook)

Similar to Ruff's CLI, the Ruff Language Server fully supports Jupyter Notebook files with all the capabilities available to Python files.

Note

Ruff has built-in support for Jupyter Notebooks. The native language server will discover and lint or format `.ipynb` files by default as of version 0.6.0. Refer to the [Jupyter Notebook discovery](../../configuration/#jupyter-notebook-discovery) section for more details.
