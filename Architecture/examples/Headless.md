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
