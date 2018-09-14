## Kong+Introduction

[Kong](https://getkong.org/) is an open-source API Gateway and Microservices
Management Layer, delivering high performance and reliability.

This chart is a work in progress expanding on the [existing chart](https://github.com/helm/charts/tree/master/stable/kong). Most of the existing chart's readme still applies. It adds support for Kong Enterprise and several other features.

Most documentation is in the chart itself. In-progress sections typically include a longer comment prefixed with `#!`.

By default, this chart installs Kong Community. Kong Enterprise users should set `flavor: ee` in `values.yaml` and specify their Docker registry (as there is no public Kong Enterprise registry).
