```
  helm repo add bitnami https://charts.bitnami.com/bitnami
```

```
minikube start --cpus 2 --memory 2000 --profile kubeapps
```

```
helm install -n kubeapps --create-namespace kubeapps bitnami/kubeapps
```

```
kubectl create --namespace default serviceaccount kubeapps-operator
```

```
kubectl create clusterrolebinding kubeapps-operator --clusterrole=cluster-admin --serviceaccount=default:kubeapps-operator
```

## To access K8dash
```
minikube dashboard --url --profile kubeapps
```

```
http://127.0.0.1:52814/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/
```

## If you have no token already run following to get one.. You can create a new resource by clicking right corner plus (+) on k8dash 
### Then Go to Secret there look for kubeapps-operator-token
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


## To Access Kubeapps run following and get token (previous step)

```
kubectl port-forward -n kubeapps svc/kubeapps 8080:80
```

### To exec pod
```
kubectl -n <namespace> exec -it <pod> -- /bin/bash
```

### minikube-service

```
minikube service -n dev nginx --url
```


