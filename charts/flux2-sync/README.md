# flux2-sync

![Version: 1.13.3](https://img.shields.io/badge/Version-1.13.3-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 2.6.4](https://img.shields.io/badge/AppVersion-2.6.4-informational?style=flat-square)

A Helm chart for flux2 GitRepository to sync with

This helm chart is maintained and released by the fluxcd-community on a best effort basis.

## Source Code

* <https://github.com/fluxcd-community/helm-charts>

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| cli.affinity | object | `{}` |  |
| cli.image | string | `"ghcr.io/fluxcd/flux-cli"` |  |
| cli.nodeSelector | object | `{}` |  |
| cli.tag | string | `"v2.6.4"` |  |
| cli.tolerations | list | `[]` |  |
| gitRepository.annotations | object | `{}` |  |
| gitRepository.labels | object | `{}` |  |
| gitRepository.spec.gitImplementation | string | `""` | _Optional_ Determines which git client library to use. Defaults to go-git, valid values are (‘go-git’, ‘libgit2’). |
| gitRepository.spec.ignore | string | `""` | _Optional_ Ignore overrides the set of excluded patterns in the .sourceignore format (which is the same as .gitignore). If not provided, a default will be used, consult the documentation for your version to find out what those are. Make sure to set this as yaml multiline string. |
| gitRepository.spec.include | list | `[]` | _Optional_ Extra git repositories to map into the repository |
| gitRepository.spec.interval | string | `"5m"` | The interval at which to check for repository updates. |
| gitRepository.spec.provider | string | `""` | The OIDC provider used for authentication. Valid values are generic, azure or github (defaults to generic when empty). |
| gitRepository.spec.recurseSubmodules | bool | `false` | _Optional_ When enabled, after the clone is created, initializes all submodules within, using their default settings. This option is available only when using the ‘go-git’ GitImplementation. |
| gitRepository.spec.ref | object | `{"branch":"master"}` | _Optional_ The Git reference to checkout and monitor for changes, defaults to master branch. |
| gitRepository.spec.secretRef | object | `{}` | _Optional_ The secret name containing the Git credentials. For HTTPS repositories the secret must contain username and password fields. For SSH repositories the secret must contain identity, identity.pub and known_hosts fields. For GitHub App authentication the secret must contain githubAppID, githubAppInstallationID and githubAppPrivateKey fields. If a secret.create is set, it will point to that one. |
| gitRepository.spec.suspend | string | `""` | _Optional_ This flag tells the controller to suspend the reconciliation of this source. |
| gitRepository.spec.timeout | string | `""` | _Optional_ The timeout for remote Git operations like cloning, defaults to 20s. |
| gitRepository.spec.url | string | `""` | The repository URL, can be an HTTP/S or SSH address. |
| gitRepository.spec.verify | object | `{}` | _Optional_ Verify OpenPGP signature for the Git commit HEAD points to. |
| kustomization.annotations | object | `{}` |  |
| kustomization.labels | object | `{}` |  |
| kustomization.spec.decryption | object | `{}` | _Optional_ Decrypt Kubernetes secrets before applying them on the cluster. |
| kustomization.spec.dependsOn | list | `[]` | _Optional_ DependsOn may contain a dependency.CrossNamespaceDependencyReference slice with references to Kustomization resources that must be ready before this Kustomization can be reconciled. |
| kustomization.spec.force | bool | `false` | _Optional_ Force instructs the controller to recreate resources when patching fails due to an immutable field change. Defaults to false. |
| kustomization.spec.healthChecks | list | `[]` | _Optional_ A list of resources to be included in the health assessment. |
| kustomization.spec.images | list | `[]` | _Optional_ Images is a list of (image name, new name, new tag or digest) for changing image names, tags or digests. This can also be achieved with a patch, but this operator is simpler to specify. |
| kustomization.spec.interval | string | `"5m"` | The interval at which to reconcile the Kustomization. |
| kustomization.spec.kubeConfig | object | `{}` | _Optional_ The KubeConfig for reconciling the Kustomization on a remote cluster. When specified, KubeConfig takes precedence over ServiceAccountName. |
| kustomization.spec.patches | list | `[]` | _Optional_ Strategic merge and JSON patches, defined as inline YAML objects, capable of targeting objects based on kind, label and annotation selectors. |
| kustomization.spec.path | string | `""` | _Optional_ Path to the directory containing the kustomization.yaml file, or the set of plain YAMLs a kustomization.yaml should be generated for. Defaults to ‘None’, which translates to the root path of the SourceRef. |
| kustomization.spec.postBuild | object | `{}` | _Optional_ PostBuild describes which actions to perform on the YAML manifest generated by building the kustomize overlay. |
| kustomization.spec.prune | bool | `true` | Prune enables garbage collection. Defaults to true. |
| kustomization.spec.retryInterval | string | `""` | _Optional_ The interval at which to retry a previously failed reconciliation. When not specified, the controller uses the KustomizationSpec.Interval value to retry failures. |
| kustomization.spec.serviceAccountName | string | `""` | _Optional_ The name of the Kubernetes service account to impersonate when reconciling this Kustomization. |
| kustomization.spec.suspend | string | `""` | _Optional_ This flag tells the controller to suspend subsequent kustomize executions, it does not apply to already started executions. Defaults to false. |
| kustomization.spec.targetNamespace | string | `""` | _Optional_ TargetNamespace sets or overrides the namespace in the kustomization.yaml file. |
| kustomization.spec.timeout | string | `""` | _Optional_ Timeout for validation, apply and health checking operations. Defaults to ‘Interval’ duration |
| kustomization.spec.wait | bool | `false` | _Optional_ Wait instructs the controller to check the health of all the reconciled resources. When enabled, the HealthChecks are ignored. Defaults to false. |
| kustomizationlist | object | `{}` | _Optional_ If you want multiple subdirectories which depend on each other in the same repo. Their name is derived from their path. |
| secret.create | bool | `false` | Create a secret for the git repository. Defaults to false. |
| secret.data | object | `{}` | Data of the secret. For HTTPS repositories the secret must contain username and password fields. For SSH repositories the secret must contain identity, identity.pub and known_hosts fields. For GitHub App authentication the secret must contain githubAppID, githubAppInstallationID and githubAppPrivateKey fields. Values will be encoded to base64 by the helm chart. |
| secret.generate | object | `{"sshEcdsaCurve":"p521","sshKeyAlgorithm":"ecdsa"}` | Algorithm of keys to generate. If `data` object above is empty, and `create` is set to true. The Chart will generate the Git SSH key secret automatically based on the key algorithms that are set below. |
