# Databend Query Helm Chart

## Prerequisites

- Kubernetes 1.14+
- Helm v3+

## Install

To install the chart with release name `my-release`:
```
helm repo add databend https://charts.databend.rs
helm install my-release databend/databend-query --namespace databend --create-namespace
```

Note that for a production cluster, you will likely want to override the following parameters in [values.yaml](values.yaml) with your own values.
- `resources.requests.memory` and `resources.limit.memory` allocate memory resource to query pods in your cluser.
- `config.meta.embedded.enabled` defaults to `true` for persist meta state to disk, set to `false` to use [Databend Meta](../databend-meta).
- `config.meta.address` indicates the grpc address of a [Databend Meta](../databend-meta) service.
- `config.storage.type` defaults to `disk` for testing only, `s3` is recommended in production.