gcrgc
=====

A Helm chart for the [GCR Garbage Collector](https://github.com/graillus/gcrgc)

---

## Installation

You need to create a secret contaning the Google service account key with write access to the registry:
```bash
kubectl create secret generic google-credentials --from-file=credentials.json
```

Prepare the configuration file for gcrgc
values.yaml
```yaml
config:
  registry: eu.gcr.io/project-id
  retention-period: 90d
  exclude-tags:
    - latest
  exclude-semver-tags: true
```

Install the chart
```bash
helm repo add graillus https://graillus.github.io/helm-charts
helm install gcrgc graillus/gcrgc --set existingSecretName=google-credentials --values values.yaml
```

See the chart's `values.yaml` file for more options.
