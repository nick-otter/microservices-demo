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
$ helm 
```

---
