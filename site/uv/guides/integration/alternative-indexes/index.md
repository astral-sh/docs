# [Using alternative package indexes](#using-alternative-package-indexes)

While uv uses the official Python Package Index (PyPI) by default, it also supports [alternative package indexes](../../../concepts/indexes/). Most alternative indexes require various forms of authentication, which require some initial setup.

Important

If using the pip interface, please read the documentation on [using multiple indexes](../../../pip/compatibility/#packages-that-exist-on-multiple-indexes) in uv — the default behavior is different from pip to prevent dependency confusion attacks, but this means that uv may not find the versions of a package as you'd expect.

## [Azure Artifacts](#azure-artifacts)

uv can install packages from [Azure Artifacts](https://learn.microsoft.com/en-us/azure/devops/artifacts/start-using-azure-artifacts?view=azure-devops&tabs=nuget%2Cnugetserver), either by using a [Personal Access Token](https://learn.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=Windows) (PAT), or using the [`keyring`](https://github.com/jaraco/keyring) package.

To use Azure Artifacts, add the index to your project:

pyproject.toml

```
[[tool.uv.index]]
name = "private-registry"
url = "https://pkgs.dev.azure.com/<ORGANIZATION>/<PROJECT>/_packaging/<FEED>/pypi/simple/"

```

### [Authenticate with an Azure access token](#authenticate-with-an-azure-access-token)

If there is a personal access token (PAT) available (e.g., [`$(System.AccessToken)` in an Azure pipeline](https://learn.microsoft.com/en-us/azure/devops/pipelines/build/variables?view=azure-devops&tabs=yaml#systemaccesstoken)), credentials can be provided via "Basic" HTTP authentication scheme. Include the PAT in the password field of the URL. A username must be included as well, but can be any string.

For example, with the token stored in the `$AZURE_ARTIFACTS_TOKEN` environment variable, set credentials for the index with:

```
export UV_INDEX_PRIVATE_REGISTRY_USERNAME=dummy
export UV_INDEX_PRIVATE_REGISTRY_PASSWORD="$AZURE_ARTIFACTS_TOKEN"

```

Note

`PRIVATE_REGISTRY` should match the name of the index defined in your `pyproject.toml`.

### [Authenticate with `keyring` and `artifacts-keyring`](#authenticate-with-keyring-and-artifacts-keyring)

You can also authenticate to Artifacts using [`keyring`](https://github.com/jaraco/keyring) package with the [`artifacts-keyring` plugin](https://github.com/Microsoft/artifacts-keyring). Because these two packages are required to authenticate to Azure Artifacts, they must be pre-installed from a source other than Artifacts.

The `artifacts-keyring` plugin wraps the [Azure Artifacts Credential Provider tool](https://github.com/microsoft/artifacts-credprovider). The credential provider supports a few different authentication modes including interactive login — see the [tool's documentation](https://github.com/microsoft/artifacts-credprovider) for information on configuration.

uv only supports using the `keyring` package in [subprocess mode](../../../reference/settings/#keyring-provider). The `keyring` executable must be in the `PATH`, i.e., installed globally or in the active environment. The `keyring` CLI requires a username in the URL, and it must be `VssSessionToken`.

```
# Pre-install keyring and the Artifacts plugin from the public PyPI
uv tool install keyring --with artifacts-keyring

# Enable keyring authentication
export UV_KEYRING_PROVIDER=subprocess

# Set the username for the index
export UV_INDEX_PRIVATE_REGISTRY_USERNAME=VssSessionToken

```

Note

The [`tool.uv.keyring-provider`](../../../reference/settings/#keyring-provider) setting can be used to enable keyring in your `uv.toml` or `pyproject.toml`.

Similarly, the username for the index can be added directly to the index URL.

### [Publishing packages to Azure Artifacts](#publishing-packages-to-azure-artifacts)

If you also want to publish your own packages to Azure Artifacts, you can use `uv publish` as described in the [Building and publishing guide](../../package/).

First, add a `publish-url` to the index you want to publish packages to. For example:

pyproject.toml

```
[[tool.uv.index]]
name = "private-registry"
url = "https://pkgs.dev.azure.com/<ORGANIZATION>/<PROJECT>/_packaging/<FEED>/pypi/simple/"
publish-url = "https://pkgs.dev.azure.com/<ORGANIZATION>/<PROJECT>/_packaging/<FEED>/pypi/upload/"

```

Then, configure credentials (if not using keyring):

```
$ export UV_PUBLISH_USERNAME=dummy
$ export UV_PUBLISH_PASSWORD="$AZURE_ARTIFACTS_TOKEN"

```

And publish the package:

```
$ uv publish --index private-registry

```

To use `uv publish` without adding the `publish-url` to the project, you can set `UV_PUBLISH_URL`:

```
$ export UV_PUBLISH_URL=https://pkgs.dev.azure.com/<ORGANIZATION>/<PROJECT>/_packaging/<FEED>/pypi/upload/
$ uv publish

```

Note this method is not preferable because uv cannot check if the package is already published before uploading artifacts.

## [Google Artifact Registry](#google-artifact-registry)

uv can install packages from [Google Artifact Registry](https://cloud.google.com/artifact-registry/docs), either by using an access token, or using the [`keyring`](https://github.com/jaraco/keyring) package.

Note

This guide assumes that [`gcloud`](https://cloud.google.com/sdk/gcloud) CLI is installed and authenticated.

To use Google Artifact Registry, add the index to your project:

pyproject.toml

```
[[tool.uv.index]]
name = "private-registry"
url = "https://<REGION>-python.pkg.dev/<PROJECT>/<REPOSITORY>/simple/"

```

### [Authenticate with a Google access token](#authenticate-with-a-google-access-token)

Credentials can be provided via "Basic" HTTP authentication scheme. Include access token in the password field of the URL. Username must be `oauth2accesstoken`, otherwise authentication will fail.

Generate a token with `gcloud`:

```
export ARTIFACT_REGISTRY_TOKEN=$(
    gcloud auth application-default print-access-token
)

```

Note

You might need to pass extra parameters to properly generate the token (like `--project`), this is a basic example.

Then set credentials for the index with:

```
export UV_INDEX_PRIVATE_REGISTRY_USERNAME=oauth2accesstoken
export UV_INDEX_PRIVATE_REGISTRY_PASSWORD="$ARTIFACT_REGISTRY_TOKEN"

```

Note

`PRIVATE_REGISTRY` should match the name of the index defined in your `pyproject.toml`.

### [Authenticate with `keyring` and `keyrings.google-artifactregistry-auth`](#authenticate-with-keyring-and-keyringsgoogle-artifactregistry-auth)

You can also authenticate to Artifact Registry using [`keyring`](https://github.com/jaraco/keyring) package with the [`keyrings.google-artifactregistry-auth` plugin](https://github.com/GoogleCloudPlatform/artifact-registry-python-tools). Because these two packages are required to authenticate to Artifact Registry, they must be pre-installed from a source other than Artifact Registry.

The `keyrings.google-artifactregistry-auth` plugin wraps [gcloud CLI](https://cloud.google.com/sdk/gcloud) to generate short-lived access tokens, securely store them in system keyring, and refresh them when they are expired.

uv only supports using the `keyring` package in [subprocess mode](../../../reference/settings/#keyring-provider). The `keyring` executable must be in the `PATH`, i.e., installed globally or in the active environment. The `keyring` CLI requires a username in the URL and it must be `oauth2accesstoken`.

```
# Pre-install keyring and Artifact Registry plugin from the public PyPI
uv tool install keyring --with keyrings.google-artifactregistry-auth

# Enable keyring authentication
export UV_KEYRING_PROVIDER=subprocess

# Set the username for the index
export UV_INDEX_PRIVATE_REGISTRY_USERNAME=oauth2accesstoken

```

Note

The [`tool.uv.keyring-provider`](../../../reference/settings/#keyring-provider) setting can be used to enable keyring in your `uv.toml` or `pyproject.toml`.

Similarly, the username for the index can be added directly to the index URL.

### [Publishing packages to Google Artifact Registry](#publishing-packages-to-google-artifact-registry)

If you also want to publish your own packages to Google Artifact Registry, you can use `uv publish` as described in the [Building and publishing guide](../../package/).

First, add a `publish-url` to the index you want to publish packages to. For example:

pyproject.toml

```
[[tool.uv.index]]
name = "private-registry"
url = "https://<REGION>-python.pkg.dev/<PROJECT>/<REPOSITORY>/simple/"
publish-url = "https://<REGION>-python.pkg.dev/<PROJECT>/<REPOSITORY>/"

```

Then, configure credentials (if not using keyring):

```
$ export UV_PUBLISH_USERNAME=oauth2accesstoken
$ export UV_PUBLISH_PASSWORD="$ARTIFACT_REGISTRY_TOKEN"

```

And publish the package:

```
$ uv publish --index private-registry

```

To use `uv publish` without adding the `publish-url` to the project, you can set `UV_PUBLISH_URL`:

```
$ export UV_PUBLISH_URL=https://<REGION>-python.pkg.dev/<PROJECT>/<REPOSITORY>/
$ uv publish

```

Note this method is not preferable because uv cannot check if the package is already published before uploading artifacts.

## [AWS CodeArtifact](#aws-codeartifact)

uv can install packages from [AWS CodeArtifact](https://docs.aws.amazon.com/codeartifact/latest/ug/using-python.html), either by using an access token, or using the [`keyring`](https://github.com/jaraco/keyring) package.

Note

This guide assumes that [`awscli`](https://aws.amazon.com/cli/) is installed and authenticated.

The index can be declared like so:

pyproject.toml

```
[[tool.uv.index]]
name = "private-registry"
url = "https://<DOMAIN>-<ACCOUNT_ID>.d.codeartifact.<REGION>.amazonaws.com/pypi/<REPOSITORY>/simple/"

```

### [Authenticate with an AWS access token](#authenticate-with-an-aws-access-token)

Credentials can be provided via "Basic" HTTP authentication scheme. Include access token in the password field of the URL. Username must be `aws`, otherwise authentication will fail.

Generate a token with `awscli`:

```
export AWS_CODEARTIFACT_TOKEN="$(
    aws codeartifact get-authorization-token \
    --domain <DOMAIN> \
    --domain-owner <ACCOUNT_ID> \
    --query authorizationToken \
    --output text
)"

```

Note

You might need to pass extra parameters to properly generate the token (like `--region`), this is a basic example.

Then set credentials for the index with:

```
export UV_INDEX_PRIVATE_REGISTRY_USERNAME=aws
export UV_INDEX_PRIVATE_REGISTRY_PASSWORD="$AWS_CODEARTIFACT_TOKEN"

```

Note

`PRIVATE_REGISTRY` should match the name of the index defined in your `pyproject.toml`.

### [Authenticate with `keyring` and `keyrings.codeartifact`](#authenticate-with-keyring-and-keyringscodeartifact)

You can also authenticate to Artifact Registry using [`keyring`](https://github.com/jaraco/keyring) package with the [`keyrings.codeartifact` plugin](https://github.com/jmkeyes/keyrings.codeartifact). Because these two packages are required to authenticate to Artifact Registry, they must be pre-installed from a source other than Artifact Registry.

The `keyrings.codeartifact` plugin wraps [boto3](https://pypi.org/project/boto3/) to generate short-lived access tokens, securely store them in system keyring, and refresh them when they are expired.

uv only supports using the `keyring` package in [subprocess mode](../../../reference/settings/#keyring-provider). The `keyring` executable must be in the `PATH`, i.e., installed globally or in the active environment. The `keyring` CLI requires a username in the URL and it must be `aws`.

```
# Pre-install keyring and AWS CodeArtifact plugin from the public PyPI
uv tool install keyring --with keyrings.codeartifact

# Enable keyring authentication
export UV_KEYRING_PROVIDER=subprocess

# Set the username for the index
export UV_INDEX_PRIVATE_REGISTRY_USERNAME=aws

```

Note

The [`tool.uv.keyring-provider`](../../../reference/settings/#keyring-provider) setting can be used to enable keyring in your `uv.toml` or `pyproject.toml`.

Similarly, the username for the index can be added directly to the index URL.

### [Publishing packages to AWS CodeArtifact](#publishing-packages-to-aws-codeartifact)

If you also want to publish your own packages to AWS CodeArtifact, you can use `uv publish` as described in the [Building and publishing guide](../../package/).

First, add a `publish-url` to the index you want to publish packages to. For example:

pyproject.toml

```
[[tool.uv.index]]
name = "private-registry"
url = "https://<DOMAIN>-<ACCOUNT_ID>.d.codeartifact.<REGION>.amazonaws.com/pypi/<REPOSITORY>/simple/"
publish-url = "https://<DOMAIN>-<ACCOUNT_ID>.d.codeartifact.<REGION>.amazonaws.com/pypi/<REPOSITORY>/"

```

Then, configure credentials (if not using keyring):

```
$ export UV_PUBLISH_USERNAME=aws
$ export UV_PUBLISH_PASSWORD="$AWS_CODEARTIFACT_TOKEN"

```

And publish the package:

```
$ uv publish --index private-registry

```

To use `uv publish` without adding the `publish-url` to the project, you can set `UV_PUBLISH_URL`:

```
$ export UV_PUBLISH_URL=https://<DOMAIN>-<ACCOUNT_ID>.d.codeartifact.<REGION>.amazonaws.com/pypi/<REPOSITORY>/
$ uv publish

```

Note this method is not preferable because uv cannot check if the package is already published before uploading artifacts.

## [JFrog Artifactory](#jfrog-artifactory)

uv can install packages from JFrog Artifactory, either by using a username and password or a JWT token.

To use it, add the index to your project:

pyproject.toml

```
[[tool.uv.index]]
name = "private-registry"
url = "https://<organization>.jfrog.io/artifactory/api/pypi/<repository>/simple"

```

### [Authenticate with username and password](#authenticate-with-username-and-password)

```
$ export UV_INDEX_PRIVATE_REGISTRY_USERNAME="<username>"
$ export UV_INDEX_PRIVATE_REGISTRY_PASSWORD="<password>"

```

### [Authenticate with JWT token](#authenticate-with-jwt-token)

```
$ export UV_INDEX_PRIVATE_REGISTRY_USERNAME=""
$ export UV_INDEX_PRIVATE_REGISTRY_PASSWORD="$JFROG_JWT_TOKEN"

```

Note

Replace `PRIVATE_REGISTRY` in the environment variable names with the actual index name defined in your `pyproject.toml`.

### [Publishing packages to JFrog Artifactory](#publishing-packages-to-jfrog-artifactory)

Add a `publish-url` to your index definition:

pyproject.toml

```
[[tool.uv.index]]
name = "private-registry"
url = "https://<organization>.jfrog.io/artifactory/api/pypi/<repository>/simple"
publish-url = "https://<organization>.jfrog.io/artifactory/api/pypi/<repository>"

```

Important

If you use `--token "$JFROG_TOKEN"` or `UV_PUBLISH_TOKEN` with JFrog, you will receive a 401 Unauthorized error as JFrog requires an empty username but uv passes `__token__` for as the username when `--token` is used.

To authenticate, pass your token as the password and set the username to an empty string:

```
$ uv publish --index <index_name> -u "" -p "$JFROG_TOKEN"

```

Alternatively, you can set environment variables:

```
$ export UV_PUBLISH_USERNAME=""
$ export UV_PUBLISH_PASSWORD="$JFROG_TOKEN"
$ uv publish --index private-registry

```

Note

The publish environment variables (`UV_PUBLISH_USERNAME` and `UV_PUBLISH_PASSWORD`) do not include the index name.
