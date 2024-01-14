## Архитектура:


```
                                                                   __________    ______
              Kubernetes                              |        | |            | |       |
          _____ MASTER ______       _________________ |        | |  kubelet   | | POD 1 | -> Container1,Container2,Container3
        |                    |    |                   | DOCKER | |            | | POD 2 | -> Container1
UI  ->  |     API Server     | -> |   WORKER NODE 1   |        | | Kube-proxy | | POD 3 | -> Container1,Container2
        |     Scheduler      |    | _________________ |        | | __________ | | _____ |
        | Controller-Manager |    |                   |        | |            | |       |
CLI ->  |        etcd        | -> |   WORKER NODE 2   |        | |  kubelet   | | POD 1 | -> Container1,Container2
        | __________________ |    | _________________ | DOCKER | |            | | POD 2 | -> Container1,Container2,Container3
                                                      |        | | Kube-proxy | | POD 3 | -> Container1
                                                      |        | | __________ | | _____ |

```

`UI` - User Interface (Lens, k9s)

`kubectl` - Утилита для взаимодействия с k8s

`API Server` - Взаимодействие с k8s

`Shceduler` - Оптимизирует взаимодействие с k8s для API

`Controller-Manager` - Исполняет задание отправленное через API

`etcd` - База <ключ_значение>. Сохраняет изменения производимые в нодах.

`kubelet` - Основной процесс который стартует весь kuber в WORKER NODE

`Kube-proxy` - Отвечает за все сетевые взаимодействия в kuber

---

### Нагрузки:
* [`POD`](https://github.com/Limewax163/k8s/blob/main/Architecture/examples/POD.md)
* [`Replicaset`](https://github.com/Limewax163/k8s/blob/main/Architecture/examples/ReplicaSet.md) - Для горизонтального масштабирования контейнеров
* [`Deployment`](https://github.com/Limewax163/k8s/blob/main/Architecture/examples/Deployment.md) - Подходит для большинства ситуаций при деплое приложений
* [`StatefulSet`](https://github.com/Limewax163/k8s/blob/main/Architecture/examples/StatefulSet.md) - Контейнеры запускаются с порядковыми номерами, так же запонинает порядок их запуска и позволяет настраивать его
* [`DaemonSet`](https://github.com/Limewax163/k8s/blob/main/Architecture/examples/DaemonSet.md) - Создает по 1 контейнеру на каждой ноде

### Сеть:
* Service:
  - [`ClusterIP`](https://github.com/Limewax163/k8s/blob/main/Architecture/examples/ClusterIP.md) - Балансировщик (RoundRobin)
  - [`NodePort`](https://github.com/Limewax163/k8s/blob/main/Architecture/examples/NodePort.md) - Позволяет создавать порт на каждой ноде кластера
  - [`LoadBalancer`](https://github.com/Limewax163/k8s/blob/main/Architecture/examples/LoadBalancer.md) - Предназначен для kubernetes кластеров находящихся на облаках
  - [`External`](https://github.com/Limewax163/k8s/blob/main/Architecture/examples/External.md) - Создает DNS имя в kubernetes кластере (маскирует за собой какой-то внешний ресурс)
  - [`Headless`](https://github.com/Limewax163/k8s/blob/main/Architecture/examples/Headless.md) - Позволяет напрямую подсоединиться к целевому контейнеру (без дополнительных хопов)
* [`Ingress`](https://github.com/Limewax163/k8s/blob/main/Architecture/examples/Ingress.md) - Ingress контроллер позволяет перенаправить внешнее подключение на внутренний сервис

### Конфигурации:
* ConfigMap
* Secret


