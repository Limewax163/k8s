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

В итоге мы получаем инструкции описаные в файле <Makefile> при вызове которых через команду <make> будут выполняться shell команды, соответствующие инструкциям описаным для каждого ключа в файле <Makefile>

В данном файле описаны четыре команды:

* make preprovision - которая создаст нам кластер на основе конфигурационного файла kind.yml

* make destroy - которая удалит существующий кластер kind

* make install-app - который создаст <namespase> в кластере kubernetes на основе конфигурации ns.yaml и db.yaml

* make clean-app - который удалит <namespase> в кластере kubernetes на основе конфигурации ns.yaml и db.yaml
