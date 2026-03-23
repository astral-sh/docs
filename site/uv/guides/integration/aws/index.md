# [AWS CodeArtifact](#aws-codeartifact)

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

## [Authenticate with an AWS access token](#authenticate-with-an-aws-access-token)

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

## [Authenticate with `keyring` and `keyrings.codeartifact`](#authenticate-with-keyring-and-keyringscodeartifact)

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

## [Publishing packages](#publishing-packages)

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
