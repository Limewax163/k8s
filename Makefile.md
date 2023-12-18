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
Шаблон команды:
```shell
kind <команда>
```
Примечания к файлу:

* preprovision:  `Здесь указывается команда`
  - echo "Cluster Deployment" -----Первая команда из инструкции которая будет выполняться при вызове make preprovision
  - kind create cluster --config kind.yaml --Вторая команда из инструкции которая будет выполняться при вызве make preprovision

* destroy: ------------------------------------------Еще одна команда
  - kind delete cluster --name kind ----Первая команда из инструкции которая будет выполняться при вызове ключа make destroy

* install-app: --------------------------------------И так далее
  - echo "Namespase create"
  - kubectl apply -f ns.yaml
  - echo "Database deployment"
  - kubectl apply -f db.yaml  

* clean-app:
  - echo "Database delete"
  - kubectl delete -f db.yaml
  - echo "Namespase delete"
  - kubectl delete -f ns.yaml

В итоге мы получаем инструкции описаные в файле <Makefile> при вызове которых через команду <make> будут выполняться сценарии, соответствующие данной команде.

В данном файле описаны четыре команды:

* make preprovision - которая создаст нам кластер на основе конфигурационного файла kind.yml

* make destroy - которая удалит существующий кластер kind

* make install-app - который создаст <namespase> в кластере kubernetes на основе конфигурации ns.yaml и db.yaml

* make clean-app - который удалит <namespase> в кластере kubernetes на основе конфигурации ns.yaml и db.yaml
