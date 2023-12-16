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

```
Нагрузки:
  POD:
    Replicaset - Для горизонтального масштабирования контейнеров
    Deployment - Подходит для большинства ситуаций при деплое приложений
    StatefulSet - Контейнеры запускаются с порядковыми номерами
                  Например. удобно если с каонтейнерами работают базы данных которым нужнно постоянное подключение к опредленным хостам
    DaemonSet - Создает по 1 контейнеру на каждой ноде
                 Например. удобно для раскидывания сборщиков логов, агентов мониторинга

Сеть:
  Service:
    ClusterIP
    NodePort
    LoadBalancer
    ...

Конфигурации:
  ConfigMap
  Secret
Для применения манифестов - `kubectl -n <your_namespace> -f <your_manifest>`
```
