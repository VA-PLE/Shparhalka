# Kubectl
[Kubectl Cheat Sheet](https://kubernetes.io/ru/docs/reference/kubectl/cheatsheet/)

Сhange label on the node:
```sh
kubectl label nodes/[NODE_NAME] [KEY]=[VALUE] --overwrite
```
Restart daemonset/deployment:
```sh
rollout restart [KIND]/[NAME] -n [NAMESPACE]
```

# Metrics-server debug
Get metrics:
```sh
kubectl get --raw "/apis/metrics.k8s.io/v1beta1/nodes"
```

Describe metrics-server
```sh
kubectl describe apiservice v1beta1.metrics.k8s.io
```
