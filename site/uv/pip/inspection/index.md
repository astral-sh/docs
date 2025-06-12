# [Inspecting environments](#inspecting-environments)

## [Listing installed packages](#listing-installed-packages)

To list all the packages in the environment:

```
$ uv pip list

```

To list the packages in a JSON format:

```
$ uv pip list --format json

```

To list all the packages in the environment in a `requirements.txt` format:

```
$ uv pip freeze

```

## [Inspecting a package](#inspecting-a-package)

To show information about an installed package, e.g., `numpy`:

```
$ uv pip show numpy

```

Multiple packages can be inspected at once.

## [Verifying an environment](#verifying-an-environment)

It is possible to install packages with conflicting requirements into an environment if installed in multiple steps.

To check for conflicts or missing dependencies in the environment:

```
$ uv pip check

```
