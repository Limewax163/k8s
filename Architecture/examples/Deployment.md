```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

* apiVersion:
* kind
* metadata:
  - name:
  - labels: - Метка для сущностей в kuber (в данном случае лейбл самого вида манифеста)
    - app: - например указываем название приложения
    - author: - например указываем автора данного манифеста
    - version: - например указываем версию приложения
* spec:
  - replicas: - Колличество реплик приложения [!NOTE]
  - selector:
    - matchLabels: - По каким лейблам выбираются контейнеры для реплик
      - app:
  - template:
    - metadata:
      - labels: - Лейблы которые отдаются уже непосредственно контейнерам.
        - app:
      - spec:
        - container:
          - name:
          - image:
          - ports:
            - containerPort:

> [!NOTE]
> Для динамического увеличения колличества реплик приложения существует Horizontal-pods-autoscaller
