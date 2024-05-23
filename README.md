# Shinobi Helm Charts

## Usage

Add the Shinobi repo:

```bash
helm repo add shinobi https://shinobisecurity.github.io/helm-charts/
helm repo update
```

### Install the kubernetes-config-collector

> [!IMPORTANT]
> You must specify `shinobi.api_key`, `shinobi.endpoint` and `cluster_name`

> [!NOTE]
> The helm chart installs a pod with readonly permissions for collecting your cluster configuration.
> The pod requires outbound HTTPS access to ship this configuration data to your Shinobi installation endpoint.

```bash
helm install --create-namespace -n shinobi \
    shinobi shinobi/kubernetes-config-collector \
    --set shinobi.api_key=XXX \
    --set shinobi.endpoint=YYY \
    --set cluster_name=ZZZ
```

### Kubeconfig context 

```bash
kubectl config get-contexts
```

### Upgrade

```bash
helm repo update
helm upgrade -n shinobi shinobi shinobi/kubernetes-config-collector
```

### Uninstall

```bash
helm uninstall -n shinobi shinobi
```

### Clean up

```bash
kubectl delete namespace shinobi
```
