# Kubernetes monitoring

This is just an example cluster: a simple app with some monitoring resources. 

Current estate:

App **`Namespace`**
* [go-url-shortener](https://github.com/xcoulon/go-url-shortener)
* Postrges

Monitoring **`Namespace`**
* Prometheus

Kube-system **`Namespace`**
* Traefik ingress controller

# Requirements

* Minikube
* Kuberenetes 
* Helm
* Skaffold


# Deployment

```
$ minikube start 
```
```
firewall-cmd --zone=public --add-masquerade --permanent &&
firewall-cmd --reload &&
```

```
$ skaffold run
```

Install Prometheus

```
$ helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
$ helm repo add stable https://charts.helm.sh/stable
$ helm repo update
```

```
$ helm install prometheus prometheus-community/kube-prometheus-stack --namespace monitoring
```

---
