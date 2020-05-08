gcrgc
=====

A Helm chart for the [GCR Garbage Collector](https://github.com/graillus/gcrgc)

---

## Installation

You need to create a secret contaning the Google service account key with write access to the registry:
```bash
kubectl create secret generic google-credentials --from-file=credentials.json
```

```bash
helm repo add graillus https://graillus.github.io/helm-charts
helm install gcrgc graillus/gcrgc --existingSecretName=google-credentials
```
