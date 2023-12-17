```
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx:1.14.2
    ports:
    - name: nginx
    - containerPort: 80
    - protocol: TCP
```
* `apiVersion` - Описывает версию API какого-то субъекта внутри kuber
* `kind` - Вид объекта
* `metadata`
  - `name` - название PODа
* `spec` - спецификация контейнера (можно запустить не один контейнер в поде например nginx+wsgi) [!NOTE]
  - `containers`
    - `name` - название контейнера в PODе
    - `image` - образ
    - `ports`
      - `name` - Можно так-же указать имя для группы настроек
      - `containerPort`
      - `protocol`
> [!NOTE]
> У любого контейнера в PODе будет один и тот же localhost
