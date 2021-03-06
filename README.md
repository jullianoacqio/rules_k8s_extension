# Bazel Kubernetes Extension Rules

## Overview

[Bazel](https://bazel.build/) is a tool for building and testing software and can handle large, multi-language projects at scale.

This project defines rules for creating the kubernetes artifacts of the kinds: `ConfigMap` and `Secret`.

## Setup

Add the following to your `WORKSPACE` file to add the necessary external dependencies:

```python
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "rules_k8s_extension",
    urls = [
        "https://github.com/acqio/rules_k8s_extension/archive/<revision>.tar.gz"
    ],
    strip_prefix = "rules_k8s_extension-<revision>",
    sha256 = "<sha256>",
)

load("@rules_k8s_extension//k8s_extension:repositories.bzl", k8s_extension_repositories = "repositories")

k8s_extension_repositories()
```

## Rules

* [k8s_configmap](docs/configmap.md) ([example](examples/))
* [k8s_secret](docs/secret.md) ([example](examples/))

## Limitations:

* The k8s_secret rule generate only ([Opaque](https://kubernetes.io/docs/concepts/configuration/secret/)) type artifact.
