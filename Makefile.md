```shell
preprovision:
  echo "Cluster Deployment"
  kind create cluster --config kind.yaml

destroy:
  kind delete cluster --name kind

install-app:
  echo "Namespase create"
  kubectl apply -f ns.yaml
  echo "Database deployment"
  kubectl apply -f db.yaml  

clean-app:
  echo "Database delete"
  kubectl delete -f db.yaml
  echo "Namespase delete"
  kubectl delete -f ns.yaml

```
