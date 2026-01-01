# Часть 1: HPA
## Запуск Locust
![04](./img/04.png)

## До нагрузки

![01](./img/01.png)

## Масштабирование под нагрузкой

![02](./img/02.png)
![03](./img/03.png)

# Часть 2: Динамическая маршрутизация

## До нагрузки

![05](./img/05.png)

## Запуск Locust

![06](./img/06.png)

## Prometheus

![07](./img/07.png)

## Масштабирование под нагрузкой

![08](./img/08.png)

## Установка и настройка Prometheus

    helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
    helm repo update
    helm install prometheus prometheus-community/prometheus
    helm install prometheus-operator prometheus-community/kube-prometheus-stack
    helm install prometheus-adapter oci://ghcr.io/prometheus-community/charts/prometheus-adapter
    kubectl apply -f servicemonitor.yaml # apply all config files
    ....
    kubectl delete pod prometheus-prometheus-operator-kube-p-prometheus-0  # prometheus restart
    kubectl port-forward svc/prometheus-server 9090:80
    kubectl port-forward service/prometheus-operator-kube-p-prometheus 9090:9090

