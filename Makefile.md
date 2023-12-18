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
Выполняется команда:
```shell
kind <ключ>
```
Примечания к файлу:

* preprovision: -------------------------------------------------Здесь указывается ключ для выполнения определенной команды
  - echo "Cluster Deployment" -----------------------------------Первая команда которая будет выполняться при вызове ключа <preprovision>
  - kind create cluster --config kind.yaml ----------------------Вторая команда которая будет выполняться при вызве ключа <preprovision>

* destroy: ------------------------------------------------------Еще один ключ для выполнения определенной команды
  - kind delete cluster --name kind -----------------------------Первая команда которая будет выполняться при вызове ключа <destroy>

* install-app: --------------------------------------------------И так далее
  - echo "Namespase create"
  - kubectl apply -f ns.yaml
  - echo "Database deployment"
  - kubectl apply -f db.yaml  

* clean-app:
  - echo "Database delete"
  - kubectl delete -f db.yaml
  - echo "Namespase delete"
  - kubectl delete -f ns.yaml
