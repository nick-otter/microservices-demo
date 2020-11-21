# Kubernetes monitoring

This is just an example cluster: a simple app with some monitoring resources. 

Current estate:

App **`Namespace`**
* [go-url-shortener](https://github.com/xcoulon/go-url-shortener)
* Postgres

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

Configure local firewall. E.g. RHEL 8.1 configuration is..
```
$ firewall-cmd --zone=public --add-masquerade --permanent &&
$ firewall-cmd --reload &&
```

Raise minikube cluster.
```
$ minikube start 
```

Apply all manifests.
```
$ skaffold run
```

Install Prometheus.
```
$ helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
$ helm repo add stable https://charts.helm.sh/stable
$ helm repo update
$ helm install prometheus prometheus-community/kube-prometheus-stack --namespace monitoring
```

No persistent ingress is configured right now, please use `port-forward` to view dashboards. 

`$ kubectl port-forward` `svc/` `prometheus` `grafana` `alertmanager` `9090` `8080:80` `-n monitoring`

---

Enjoy.
