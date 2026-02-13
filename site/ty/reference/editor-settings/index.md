# [Editor settings](#editor-settings)

The editor settings supported by ty's language server, as well as the settings specific to [ty's VS Code extension](https://marketplace.visualstudio.com/items?itemName=astral-sh.ty).

## [`configuration`](#configuration)

In-editor configuration of ty's settings. The inline settings always take precedence over the settings from configuration files, including the configuration specified with [`configurationFile`](#configurationfile).

Consult [the configuration reference](../../configuration/) for a list of all supported configuration options.

**Default value**: `null`

**Type**: `object`

**Example usage**:

```
{
  "ty.configuration": {
    "rules": {
      "unresolved-reference": "warn"
    }
  }
}

```

```
-- Neovim >=0.11:
vim.lsp.config('ty', {
  settings = {
    ty = {
      configuration = {
        rules = {
          ["unresolved-reference"] = "warn"
        }
      }
    },
  },
})

-- Neovim <0.11:
require('lspconfig').ty.setup({
  settings = {
    ty = {
      configuration = {
        rules = {
          ["unresolved-reference"] = "warn"
        }
      }
    },
  },
})

```

```
{
  "lsp": {
    "ty": {
      "settings": {
        "configuration": {
           "rules": {
            "unresolved-reference": "warn"
          }
        }
      }
    }
  }
}

```

## [`configurationFile`](#configurationfile)

The path to a `ty.toml` configuration file. ty will use the specified configuration over any automatically discovered configuration. ty will expand a tilde `~` at the start of a string to the user's home directory, as well as variables like `$A` or `${A}`.

Info

While ty configuration can be included in a `pyproject.toml` file, it is not allowed in this context.

**Default value**: `null`

**Type**: `string`

**Example usage**:

```
{
  "ty.configurationFile": "./.config/ty.toml"
}

```

```
-- Neovim >=0.11:
vim.lsp.config('ty', {
  settings = {
    ty = {
      configurationFile = "./.config/ty.toml"
    },
  },
})

-- Neovim <0.11:
require('lspconfig').ty.setup({
  settings = {
    ty = {
      configurationFile = "./.config/ty.toml"
    },
  },
})

```

```
{
  "lsp": {
    "ty": {
      "settings": {
        "configurationFile": "./.config/ty.toml"
      }
    }
  }
}

```

______________________________________________________________________

## [`disableLanguageServices`](#disablelanguageservices)

Whether to disable the language services for the ty language server like code completion, hover, go to definition, etc.

This is useful if you want to use ty exclusively for type checking and want to use another language server for features like code completion, hover, go to definition, etc.

**Default value**: `false`

**Type**: `boolean`

**Example usage**:

```
{
  "ty.disableLanguageServices": true
}

```

```
-- Neovim >=0.11:
vim.lsp.config('ty', {
  settings = {
    ty = {
      disableLanguageServices = true,
    },
  },
})

-- Neovim <0.11:
require('lspconfig').ty.setup({
  settings = {
    ty = {
      disableLanguageServices = true,
    },
  },
})

```

```
{
  "lsp": {
    "ty": {
      "settings": {
        "disableLanguageServices": true
      }
    }
  }
}

```

______________________________________________________________________

## [`diagnosticMode`](#diagnosticmode)

Determines the scope of the diagnostics reported by the language server.

Setting this to `off` is useful if you want to use ty exclusively for the language server features like code completion, hover, go to definition, etc.

- `off`: Diagnostics are disabled.
- `openFilesOnly`: Diagnostics are reported only for files that are currently open in the editor.
- `workspace`: Diagnostics are reported for all files in the workspace.

**Default value**: `"openFilesOnly"`

**Type**: `"off" | "workspace" | "openFilesOnly"`

**Example usage**:

```
{
  "ty.diagnosticMode": "workspace"
}

```

```
-- Neovim >=0.11:
vim.lsp.config('ty', {
  settings = {
    ty = {
      diagnosticMode = 'workspace',
    },
  },
})

-- Neovim <0.11:
require('lspconfig').ty.setup({
  settings = {
    ty = {
      diagnosticMode = 'workspace',
    },
  },
})

```

```
{
  "lsp": {
    "ty": {
      "settings": {
        "diagnosticMode": "workspace"
      }
    }
  }
}

```

______________________________________________________________________

## [`showSyntaxErrors`](#showsyntaxerrors)

Whether to show syntax error diagnostics.

This is useful when using ty with other language servers, allowing the user to refer to syntax errors from only one source.

**Default value**: `true`

**Type**: `bool`

**Example usage**:

```
{
    "ty.showSyntaxErrors": false
}

```

```
-- Neovim >=0.11:
vim.lsp.config('ty', {
  settings = {
    ty = {
      showSyntaxErrors = false,
    },
  },
})

-- Neovim <0.11:
require('lspconfig').ty.setup({
  settings = {
    ty = {
      showSyntaxErrors = false,
    },
  },
})

```

```
{
  "lsp": {
    "ty": {
      "settings": {
        "showSyntaxErrors": false
      }
    }
  }
}

```

______________________________________________________________________

## [`inlayHints`](#inlayhints)

These settings control the inline hints that ty provides in an editor.

### [`variableTypes`](#variabletypes)

Whether to show the types of variables as inline hints.

**Default value**: `true`

**Type**: `boolean`

**Example usage**:

```
{
  "ty.inlayHints.variableTypes": false
}

```

```
-- Neovim >=0.11:
vim.lsp.config('ty', {
  settings = {
    ty = {
      inlayHints = {
        variableTypes = false,
      },
    },
  },
})

-- Neovim <0.11:
require('lspconfig').ty.setup({
  settings = {
    ty = {
      inlayHints = {
        variableTypes = false,
      },
    },
  },
})

```

```
{
  "lsp": {
    "ty": {
      "settings": {
        "inlayHints": {
          "variableTypes": false
        }
      }
    }
  }
}

```

### [`callArgumentNames`](#callargumentnames)

Whether to show argument names in call expressions as inline hints.

**Default value**: `true`

**Type**: `boolean`

**Example usage**:

```
{
  "ty.inlayHints.callArgumentNames": false
}

```

```
-- Neovim >=0.11:
vim.lsp.config('ty', {
  settings = {
    ty = {
      inlayHints = {
        callArgumentNames = false,
      },
    },
  },
})

-- Neovim <0.11:
require('lspconfig').ty.setup({
  settings = {
    ty = {
      inlayHints = {
        callArgumentNames = false,
      },
    },
  },
})

```

```
{
  "lsp": {
    "ty": {
      "settings": {
        "inlayHints": {
          "callArgumentNames": false
        }
      }
    }
  }
}

```

______________________________________________________________________

## [`completions`](#completions)

These settings control how code completions offered by ty work.

### [`autoImport`](#autoimport)

Whether to include auto-import suggestions in code completions. That is, code completions will include symbols not currently in scope but available in your environment.

**Default value**: `true`

**Type**: `boolean`

**Example usage**:

```
{
  "ty.completions.autoImport": true
}

```

```
-- Neovim >=0.11:
vim.lsp.config('ty', {
  settings = {
    ty = {
      completions = {
        autoImport = true,
      },
    },
  },
})

-- Neovim <0.11:
require('lspconfig').ty.setup({
  settings = {
    ty = {
      completions = {
        autoImport = true,
      },
    },
  },
})

```

```
{
  "lsp": {
    "ty": {
      "settings": {
        "completions": {
          "autoImport": true
        }
      }
    }
  }
}

```

______________________________________________________________________

## [VS Code specific](#vs-code-specific)

The following settings are specific to [ty's VS Code extension](https://marketplace.visualstudio.com/items?itemName=astral-sh.ty).

### [`importStrategy`](#importstrategy)

Strategy for loading the `ty` executable.

- `fromEnvironment` finds ty in the environment, falling back to the bundled version
- `useBundled` uses the version bundled with the extension

**Default value**: `"fromEnvironment"`

**Type**: `"fromEnvironment" | "useBundled"`

**Example usage**:

```
{
  "ty.importStrategy": "useBundled"
}

```

______________________________________________________________________

### [`interpreter`](#interpreter)

A list of paths to Python interpreters. Even though this is a list, only the first interpreter is used.

The interpreter path is used to find the `ty` executable when [`ty.importStrategy`](#importstrategy) is set to `fromEnvironment`.

**Default value**: `[]`

**Type**: `string[]`

**Example usage**:

```
{
  "ty.interpreter": ["/home/user/.local/bin/python"]
}

```

______________________________________________________________________

### [`path`](#path)

A list of path to `ty` executables.

The extension uses the first executable that exists. This setting takes precedence over the [`ty.importStrategy`](#importstrategy) setting.

**Default value**: `[]`

**Type**: `string[]`

**Example usage**:

```
{
  "ty.path": ["/home/user/.local/bin/ty"]
}

```

______________________________________________________________________

### [`trace.server`](#traceserver)

The detail level at which messages between the language server and the editor (client) are logged.

This setting is useful for debugging issues with the language server. Refer to the [troubleshooting guide](https://github.com/astral-sh/ty-vscode/blob/6cf16b4e87342a49f2bec1310a730cde8229e1d9/TROUBLESHOOTING.md) in [ty's VS Code extension](https://marketplace.visualstudio.com/items?itemName=astral-sh.ty) for more information.

**Default value**: `"off"`

**Type**: `"off" | "messages" | "verbose"`

**Example usage**:

```
{
  "ty.trace.server": "messages"
}

```

______________________________________________________________________

## [Initialization options](#initialization-options)

The following settings are required when ty is initialized in an editor. These settings are static so changing them requires restarting the editor to take effect.

For VS Code users, these settings are defined in the `ty.*` namespace as usual, but for other editors, they would need to be provided in a separate field of the configuration that corresponds to the initialization options. Refer to the examples below for how to set these options in different editors.

### [`logFile`](#logfile)

Path to the file to which the language server writes its log messages. By default, ty writes log messages to stderr.

**Default value**: `null`

**Type**: `string`

**Example usage**:

```
{
  "ty.logFile": "/path/to/ty.log"
}

```

```
-- Neovim >=0.11:
vim.lsp.config('ty', {
  init_options = {
    logFile = '/path/to/ty.log',
  },
})

-- Neovim <0.11:
require('lspconfig').ty.setup({
  init_options = {
    logFile = '/path/to/ty.log',
  },
})

```

```
{
  "lsp": {
    "ty": {
      "initialization_options": {
        "logFile": "/path/to/ty.log"
      }
    }
  }
}

```

______________________________________________________________________

### [`logLevel`](#loglevel)

The log level to use for the language server.

**Default value**: `"info"`

**Type**: `"trace" | "debug" | "info" | "warn" | "error"`

**Example usage**:

```
{
  "ty.logLevel": "debug"
}

```

```
-- Neovim >=0.11:
vim.lsp.config('ty', {
  init_options = {
    logLevel = 'debug',
  },
})

-- Neovim <0.11:
require('lspconfig').ty.setup({
  init_options = {
    logLevel = 'debug',
  },
})

```

```
{
  "lsp": {
    "ty": {
      "initialization_options": {
        "logLevel": "debug"
      }
    }
  }
}

```
