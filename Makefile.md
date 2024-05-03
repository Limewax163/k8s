```shell
.ONESHELL: ;
.NOTPARALLEL: ;

default: help;

help:

.PHONY preprovision destroy
preprovision:
  echo "Cluster Deployment"                      #Команды после указания вызова должны быть записаны через табуляцию (в том числе не подразумеваются 8 пробелов)
  kind create cluster --config kind.yaml
destroy:
  kind delete cluster --name kind

.PHONY install-app
install-app:
  echo "Namespase create"
  kubectl apply -f ns.yaml
  echo "Database deployment"
  kubectl apply -f db.yaml  

.PHONY clean-app
clean-app:
  echo "Database delete"
  kubectl delete -f db.yaml
  echo "Namespase delete"
  kubectl delete -f ns.yaml

```
Шаблон команды:
```shell
kind <команда>
```
Примечания к файлу:

>[!NOTE]
>Директива .PHONY в Makefile используется для указания того, что цель является "фиктивной", то есть не представляет конкретного файла. Это означает, что даже если файл с таким именем существует, Make будет выполнять действия для этой цели. Это >полезно, когда мы хотим иметь цели, не связанные с файлами (например, команды для очистки сборки или вывода справки).


1. .ONESHELL: Эта директива указывает make выполнять все команды для одной цели в одной оболочке, в отличие от стандартного поведения, когда каждая команда выполняется в новой оболочке. Это может быть полезно, если команды в цели зависят друг от друга и требуют сохранения состояния между ними.

2. .NOTPARALLEL: Эта директива запрещает параллельное выполнение целей. Это означает, что make будет выполнать цели последовательно, а не одновременно. Это может быть полезно, если выполнение целей одновременно может вызвать проблемы, например, если они конфликтуют за ресурсы.

3. default: help;: Это правило определяет цель по умолчанию, которая будет выполнена, если make вызывается без указания конкретной цели. В вашем случае, по умолчанию будет вызвана цель help.

* preprovision:  `Здесь указывается команда`
  - echo "Cluster Deployment" `Первая команда из инструкции которая будет выполняться при вызове make preprovision`
  - kind create cluster --config kind.yaml `Вторая команда из инструкции которая будет выполняться при вызве make preprovision`

* destroy: `Еще одна команда`
  - kind delete cluster --name kind `Первая команда из инструкции которая будет выполняться при вызове make destroy`

* install-app: `И так далее`
  - echo "Namespase create"
  - kubectl apply -f ns.yaml
  - echo "Database deployment"
  - kubectl apply -f db.yaml  

* clean-app:
  - echo "Database delete"
  - kubectl delete -f db.yaml
  - echo "Namespase delete"
  - kubectl delete -f ns.yaml
---

В итоге мы получаем инструкции описаные в файле `<Makefile>` при вызове которых через команду `<make>` будут выполняться сценарии, соответствующие данной команде.

В данном файле описаны четыре команды:

* make preprovision - которая создаст нам кластер на основе конфигурационного файла `<kind.yml>`

* make destroy - которая удалит существующий кластер kind

* make install-app - который создаст `<namespase>` в кластере kubernetes на основе конфигурации ns.yaml и db.yaml

* make clean-app - который удалит `<namespase>` в кластере kubernetes на основе конфигурации ns.yaml и db.yaml

> [!NOTE]
> В сценариях make можно указывать относительный путь для текущей директории (где находится `Makefile`) переменной `$(CURDIR)`
