

K8dash
```
minikube dashboard --url --profile kubeapps
```

```
http://127.0.0.1:52814/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/
```

TogetToken=>k8dash=>secret=>token
```
apiVersion: v1
kind: Secret
metadata:
    name: kubeapps-operator-token
    namespace: default
    annotations:
      kubernetes.io/service-account.name: kubeapps-operator
type: kubernetes.io/service-account-token
```


ToAccessKubeapps

```
kubectl port-forward -n kubeapps svc/kubeapps 8080:80
```

```
kubectl -n <namespace> exec -it <pod> -- /bin/bash
```
