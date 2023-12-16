Архитектура:


```
                                                        ______     __________    ______
                                                      |        | |            | |       |
                                    _________________ |        | |  kubelet   | | POD 1 | -> Container_1,Container_2,Container_3
                             |    |                   | DOCKER | |            | | POD 2 | -> Container_1
UI  ->  |     API Server     | -> |   WORKER NODE 1   |        | | Kube-proxy | | POD 3 | -> Container_1,Container_2
        |     Scheduler      |    | _________________ | ______ | | __________ | | _____ |
        | Controller-Manager |    |                   |        | |            | |       |
CLI ->  |        etcd        | -> |   WORKER NODE 2   |        | |  kubelet   | | POD 1 | -> Container_1,Container_2
                             |    | _________________ | DOCKER | |            | | POD 2 | -> Container_1,Container_2,Container_3
                                                      |        | | Kube-proxy | | POD 3 | -> Container_1
                                                      | ______ | | __________ | | _____ |

```

Нагрузки:

```
POD:
  Replicaset - Для горизонтального масштабирования контейнеров
  Deployment - Подходит для большинства ситуаций при деплое приложений
  StatefulSet - Контейнеры запускаются с порядковыми номерами
  DaemonSet - Создает по 1 контейнеру на каждой ноде

Сеть:
  Service:
    ClusterIP
    NodePort
    LoadBalancer
    ...
  Ingress

Конфигурации:
  ConfigMap
  Secret
```
Для применения манифестов - `kubectl -n <your_namespace> -f <your_manifest>`
