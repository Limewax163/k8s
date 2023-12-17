```shell
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: minimal-ingress
spec:
  ingressClassName: MYIngressCluster ---- Показывает к какому именно Ingress кластеру мы будем подключаться (поскольку их в kubernetes может быть не один)
  rules:
  - host: example.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: service-a
            port:
              number: 80
      - path: /service-b
        pathType: Prefix
        backend:
          service:
            name: service-b
            port:
              number: 80
```


# Создание

```shell
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
networking:
  podSubnet: "10.244.0.0/16" ---- необходимо учитывать что пробрасывая сеть подов нельзя пересекаться с уже используемыми сетями
  serviceSubnet: "10.96.0.0/12" ---- то-же самое и с сервисами
nodes:
- role: control-plane
  kubeadmConfigPatches:
  - |
    kind: InitConfiguration
    nodeRegistration:
      kubeletExtraArgs:
        node-labels: "ingress-ready=true"    ----- Назначение лейбла для НОДЫ
  extraPortMappings:
  - containerPort: 80
    hostPort: 80
    protocol: TCP
  - containerPort: 443
    hostPort: 443
    protocol: TCP
```

