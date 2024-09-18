## kind
`go install sigs.k8s.io/kind@v0.24.0`

`kind create cluster --name netpol`

NetworkPolicy works properly on kind, Tested with `sts.yaml`

## Default Deny
`kubectl apply -f deny.yaml` # Deny all except `kube-system`

## Install
KubeDB
Prometheus
`helm install kube-prometheus-stack prometheus-community/kube-prometheus-stack --create-namespace -n monitoring -f /home/arnob/network-policy/prom-values.yaml`

## Allow some
`kubectl apply -f allow.yaml`


## DB
`kubectl apply -f mongo.yaml`