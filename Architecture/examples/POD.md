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
    - containerPort: 80
```
* `apiVersion` - Описывает версию API какого-то субъекта внутри kuber
* `kind` - Вид объекта
* `metadata`
  - `name` - название PODа
* `spec` - спецификация контейнера (можно запустить не один контейнер в поде например nginx+wsgi)
  - `containers`
    - `name` - название контейнера в PODе
    - `image` - образ
    - `ports`
      - `containerPort`
> [!NOTE]
> У любого контейнера в PODе будет один и тот же localhost
