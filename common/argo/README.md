This section represents the manifests from [argo](https://github.com/argoproj/argo) along with our modifications.

## Structure

The source manifests are in `argo/source`. This is a direct copy from the github repository.

The current version is [2.12.9](https://github.com/argoproj/argo/tree/v2.12.9/manifests).

The manifests we use are in `argo/base` and `argo/overlays`.
These use the `argo/source` manifests and modify them through patches.

## Updating

To update to a newer version, copy the manifests from the argo github repository into `argo/source`.
Then, update the `argo/base` files with the appropriate patches and any other modifications you need.

The goal is to have source be a direct copy so it's easy to update.
