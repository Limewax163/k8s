Для просмотра нод
```shell
kubectl get nodes
```

Для применения манифестов
```shell
kubectl -n <your_namespace> -f <your_manifest>
```
В кубере существуют `namespace`, что-то типо групп или каталогов (позволяющих отделять приложения друг от друга) внутри кубер кластера.
Для просмотра:
```shell
kubectl get ns
```
