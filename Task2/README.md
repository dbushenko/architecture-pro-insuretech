# Часть 1: HPA
## Locust
![04](./img/04.png)

## До нагрузки

![01](./img/01.png)

## Под нагрузкой

![02](./img/02.png)
![03](./img/03.png)

# Часть 2: Динамическая маршрутизация

## Установка и настройка Prometheus

    helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
    helm repo update
    helm install prometheus prometheus-community/prometheus
    helm install prometheus-operator prometheus-community/kube-prometheus-stack
    kubectl apply -f servicemonitor.yaml
    kubectl delete pod prometheus-prometheus-operator-kube-p-prometheus-0  # prometheus restart
    kubectl port-forward svc/prometheus-server 9090:80
    kubectl port-forward service/prometheus-operator-kube-p-prometheus 9090:9090

