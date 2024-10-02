# Helmfiles <img src="https://avatars.githubusercontent.com/u/83191469?s=200&v=4" alt="Helm Logo" align="right" width="200"/>

[![License](https://img.shields.io/github/license/fmjstudios/helmfiles?label=License)][license]
[![Helmfile](https://img.shields.io/badge/Helmfile-v0.150.0-1B53C2)][helmfile]
[![Kubernetes](https://img.shields.io/badge/Kubernetes-v1.26-326CE5?logo=kubernetes&logoColor=FFFFFF)][kubernetes]
[![GitHub Release](https://img.shields.io/github/v/release/fmjstudios/helmfiles?label=Release)][github_releases]
[![GitHub Activity](https://img.shields.io/github/commit-activity/m/fmjstudios/helmfiles?label=Commits)][github_commits]
[![Renovate](https://img.shields.io/badge/Renovate-enabled-brightgreen?logo=renovate&logoColor=1A1F6C)][renovate]
[![PreCommit](https://img.shields.io/badge/PreCommit-enabled-brightgreen?logo=precommit&logoColor=FAB040)][precommit]


This repository contains our collection of [Helm][helm] charts configured for use with the [`helmfile`][helmfile]
command-line utility. `helmfile` is a declarative spec for deploying Helm charts to [Kubernetes][kubernetes] clusters,
which uses a `helmfile.yaml` configuration file, hence these are our _helmfiles_. It allows us to seamlessly
manage the configuration of multiple clusters across different environments like `prod` or `staging` without custom
tooling or messy Shell scripts. In some cases like `cert-manager` custom scripts are indeed required to install CRDs,
however these are constrained to a **minimum**. All sources within this repository are [MIT][license]-licensed.

## ✨ TL;DR

```yaml
bases:
  - environments.yaml

helmfiles:
  - path: git::https://github.com/fmjstudios/helmfiles.git@releases/cert-manager/helmfile.yaml?ref=X.Y.Z

# environments.yaml
environments:
  dev:
    values:
      cert-manager:
        chartNamespace: cert-manager
        chartVersion: X.Y.Z
        install: true
        chartValues:
          installCRDs: false
          # ...
```

<!-- INTERNAL REFERENCES -->

<!-- Chart references -->

<!-- File references -->

[license]: LICENSE

<!-- General links -->

[kubernetes]: https://kubernetes.io

[helmfile]: https://github.com/helmfile/helmfile

[helm]: https://helm.sh

<!-- Overview links -->

[go]: https://go.dev

[github_releases]: https://github.com/fmjstudios/helmfiles/releases

[github_commits]: https://github.com/fmjstudios/helmfiles/commits/main/

[renovate]: https://renovatebot.com/

[precommit]: https://pre-commit.com/
