# KIND кластер


Пример создания kind кластера на основе конфигурационного yaml файла <mykind.yaml> с одной рабочей нодой `worker` и одной мастер нодой `conotrol-plane`:

```shell
kind: kind-cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: worker
- role: control-plane

```
Для создания кластера по этой конфигурации <mykind.yaml> необходимо вызвать команду

```shell
kind create cluster --config=./mykind.yaml
```
> [!NOTE]
> Название конфигурации может быть любым, важно что при вызове команды явно указывается файл конфигурации на который будет ссылаться команда, в нашем случае это файл который лежит в рабочей директории с названием <myklind.yaml>

Для автоматизации процессов можно использовать make. Создается файл <Makefile>.
Пример и наглядное понимания построения структуры файла [`MAKEFILE`](https://github.com/Limewax163/k8s/blob/main/Makefile.md)

> [!NOTE]
> Makefile не нужны права на исполнение
---

Для просмотра любых сущностей в кубер можно воспользоваться командой:

```shell
kubectl get ns <NAMESPACE_NAME> -o yaml
```
> [!NOTE]
> вывести информацию можно как в json так и в yaml. Разница будет в окончании команды

Соответственно для отладки и быстрого получения настроек для любого удобного редактирования либо парсинга можно пользоваться перенаправлением вывода в файл:

```shell
kubectl get ns <NAMESPACE_NAME> -o yaml > test.yaml
```
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
