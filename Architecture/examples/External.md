```shell
apiVersion: v1
kind: Service
metadata:
  name: my-service
  namespase: prod
spec:
  type: ExternalName
  externalname: my.database.example.com
```
