```shell
preprovision:
  echo "Cluster Deployment"
  kind create cluster --config kind.yml

destroy:
  kind delete cluster --name kind
```
