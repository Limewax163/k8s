```shell
apiVersionL v1
kind: Service
metadata:
  name: my-web-app
spec:
  selector:
    app: my-web-app
  clusterIP: None
  ports:
    port: 80
    targetport: 8080
```

Удобно когда необходимо обращаться всегда к одному и тому-же контейнеру. Сервис запоминает связь двух контейнеров.
