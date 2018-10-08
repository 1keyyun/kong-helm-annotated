## Kong+Introduction

[Kong](https://getkong.org/) is an open-source API Gateway and Microservices
Management Layer, delivering high performance and reliability.

This chart is a work in progress expanding on the [existing chart](https://github.com/helm/charts/tree/master/stable/kong). Most of the existing chart's readme still applies. It adds support for Kong Enterprise and several other features.

Most documentation is in the chart itself. In-progress sections typically include a longer comment prefixed with `#!`.

By default, this chart installs Kong Community. Kong Enterprise users should set `flavor: ee` in `values.yaml` and specify their Docker registry (as there is no public Kong Enterprise registry).

## Container registry

Kong Enterprise is not available in Docker Hub, and must be pulled from a private registry. Managed Kubernetes providers typically include zero-configuration integration with the provider's container registry offering (e.g. Google Container Registry or AWS Elastic Container Registry). Pulling from an external private registry, such as Bintray, will require [configuring Kubernetes to access
it](https://kubernetes.io/docs/tasks/configure-pod-container/pull-image-private-registry/).

## License handling

When set to install Kong Enterprise, the chart expects to find Kong's license in a [Secret](https://kubernetes.io/docs/concepts/configuration/secret/) named `license`, e.g.

```
apiVersion: v1
data:
  license: BASE64_ENCODED_LICENSE_JSON
kind: Secret
metadata:
  name: license
type: Opaque
```
Pods will fail to spawn if the license is not present.
