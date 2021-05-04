#### Install PHP Sample App from Kubernetes
```
kubectl apply -f https://k8s.io/examples/application/php-apache.yaml -n scaler
kubectl autoscale deployment php-apache --cpu-percent=50 --min=1 --max=10 -n scaler
```