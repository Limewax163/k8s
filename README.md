Архитектура:


```
                                                   _____     ______     __________ 
                                                 |       | |        | |            |
                               _________________ | POD 3 | |        | |  kubelet   |
                             |                   | POD 2 | | DOCKER | |            | -> Container_1,Container_2,Container_3
UI  ->  |     API Server     |  -> WORKER NODE 1 | POD 3 | |        | | Kube-proxy |
        |     Scheduler      | _________________ | _____ | | ______ | | __________ |
        | Controller-Manager |                   |       | |        | |            |
CLI ->  |        etcd        |  -> WORKER NODE 2 | POD 1 | |        | |  kubelet   |
                             | _________________ | POD 2 | | DOCKER | |            | -> Container_1,Container_2,Container_3
                                                 | POD 3 | |        | | Kube-proxy |
                                                 | _____ | | ______ | | __________ |

```

Нагрузки:
  POD:
    Replicaset - Для горизонтального масштабирования контейнеров
    Deployment - Подходит для большинства ситуаций при деплое приложений
    StatefulSet - Контейнеры запускаются с порядковыми номерами (Например. удобно если с каонтейнерами работают базы данных которым нужнно постоянное подключение к опредленным хостам)
    DaemonSet - Создает по 1 контейнеру на каждой ноде (Например. удобно для раскидывания сборщиков логов, агентов мониторинга)

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
