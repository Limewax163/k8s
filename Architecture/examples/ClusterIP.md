```shell
apiVersion: v1
kind: Pod
metadata:
  name: nginx
  labels:
    app.kubernetes.io/name: proxy
spec:
  containers:
  - name: nginx
    image: nginx:stable
    ports:
      - containerPort: 80
        name: http-web-svc

---
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app.kubernetes.io/name: proxy
  ports:
  - name: name-of-service-port
    protocol: TCP
    port: 80
    targetPort: http-web-svc
```
На что обратить внимание:

* apiVersion: v1
* kind: Pod
* metadata:
  - name: nginx
  - labels:
    - app.kubernetes.io/name: proxy  ---------- Лейбл PODа
* spec:
  - containers:
    - name: nginx
    - image: nginx:stable
    - ports:
        - containerPort: 80 ---------- Порт на PODе
        - name: http-web-svc ---------- Имя порта к которому привязывается сервис из второго блока манифеста

--

* apiVersion: v1
* kind: Service
* metadata:
  - name: nginx-service
* spec:
  - selector:
    - app.kubernetes.io/name: proxy  ---------- Сервис работает на базе лейбла (в данном случае proxy) и по нему обращается к данному PODу (nginx)
  - ports:
    - name: name-of-service-port
    - protocol: TCP
    - port: 80   ---------- Слушает порт 80
    - targetPort: http-web-svc ---------- Привязывает порт к соответствующему порту в первом блоке манифеста
