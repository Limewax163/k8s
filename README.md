Для просмотра нод
```shell
kubectl get nodes
```

Для применения манифестов
```shell
kubectl apply -n <namespace_name> -f <manifest_name>
```
В кубере существуют `namespace`, что-то типо групп или каталогов (позволяющих отделять приложения друг от друга) внутри кубер кластера.

Для просмотра:

```shell
kubectl get ns
```

Для создания:

```shell
kubectl create ns <name>
```


Построение SHELL команд kubectl:
* kubectl
  - get
  - create
  - delete
    - namespace / ns / -n
    - nodes
    - pods

