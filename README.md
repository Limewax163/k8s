Для автоматизации процессов можно использовать make. Создается файл Makefile. В нем указываются ключи и команды которые будут соответствовать выполнению по ключам.
Команда shell будет выглядять так:

```shell
make <key>
```

Для примера и наглядного понимания построения структуры файла [`MAKEFILE`](https://github.com/Limewax163/k8s/blob/main/Makefile.md)

> [!NOTE]
> Makefile не нужны права на исполнение
---

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

Команда для получения информации об определенном поде в определенном неймспейсе
```shell
kubectl describe pod <pod_name> -n <namespace_name>
```
Команда для просмотра логов (РАБОТАЕТ ТОЛЬКО С PODами)

```shell
kubectl logs <POD_NAME> -n <NAMESPACE_NAME>
```

Отладочный способ для подключения к контейнеру внутри kuber кластера (проброс портов)

```shell
kubectl port-forward pod <POD_NAME> <PORT_OUT:PORT_IN> -n <NAMESPACE_NAME>
```
