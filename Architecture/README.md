## Архитектура:


```
                                                                   __________    ______
              Kubernetes                              |        | |            | |       |
          _____ MASTER ______       _________________ |        | |  kubelet   | | POD 1 | -> Container_1,Container_2,Container_3
        |                    |    |                   | DOCKER | |            | | POD 2 | -> Container_1
UI  ->  |     API Server     | -> |   WORKER NODE 1   |        | | Kube-proxy | | POD 3 | -> Container_1,Container_2
        |     Scheduler      |    | _________________ |        | | __________ | | _____ |
        | Controller-Manager |    |                   |        | |            | |       |
CLI ->  |        etcd        | -> |   WORKER NODE 2   |        | |  kubelet   | | POD 1 | -> Container_1,Container_2
        | __________________ |    | _________________ | DOCKER | |            | | POD 2 | -> Container_1,Container_2,Container_3
                                                      |        | | Kube-proxy | | POD 3 | -> Container_1
                                                      |        | | __________ | | _____ |

```

`UI` - User Interface

`kubectl` - Утилита для взаимодействия с k8s

`API Server` - Взаимодействие с k8s

`Shceduler` - Оптимизирует взаимодействие с k8s для API

`Controller-Manager` - Исполняет задание отправленное через API

`etcd` - База <ключ_значение>. Сохраняет изменения производимые в нодах.

`kubelet` - Основной процесс который стартует весь kuber в WORKER NODE

`Kube-proxy` - Отвечает за все сетевые взаимодействия в kuber

---

### Нагрузки:

POD -

[`Replicaset`](https://github.com/Limewax163/k8s/blob/main/Replicaset) - Для горизонтального масштабирования контейнеров

[`Deployment`](https://github.com/Limewax163/k8s/blob/main/Deployment) - Подходит для большинства ситуаций при деплое приложений

[`StatefulSet`](https://github.com/Limewax163/k8s/blob/main/StatefulSet) - Контейнеры запускаются с порядковыми номерами

[`DaemonSet`](https://github.com/Limewax163/k8s/blob/main/DaemonSet) - Создает по 1 контейнеру на каждой ноде

### Сеть:

Service:

ClusterIP

NodePort

LoadBalancer

Ingress:

### Конфигурации:

ConfigMap

Secret

Для просмотре нод - `kubectl get nodes`
Для применения манифестов - `kubectl -n <your_namespace> -f <your_manifest>`
