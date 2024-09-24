## kind
`go install sigs.k8s.io/kind@v0.24.0`

`kind create cluster --name netpol`

NetworkPolicy works properly on kind, Tested with `extras/sts.yaml`

## Default Deny
`kubectl apply -f deny.yaml` # Deny all except `kube-system`

## Install
KubeDB

Prometheus

`helm install kube-prometheus-stack prometheus-community/kube-prometheus-stack --create-namespace -n monitoring -f /home/arnob/network-policy/prom-values.yaml`

Cert-manager

`helm install cert-manager jetstack/cert-manager --namespace cert-manager  --create-namespace --version v1.15.3 -f cert-values.yaml`

KubeStash
```
helm install kubestash oci://ghcr.io/appscode-charts/kubestash \
  --version v2024.8.30 \
  --namespace kubestash --create-namespace \
  --set-file global.license=/home/arnob/license/netpol.txt \
  --wait --burst-limit=10000 --debug
```

## Allow some
`kubectl apply -f allow.yaml`


## DB
`kubectl apply -f mongo.yaml`