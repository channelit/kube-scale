#### Install PHP Sample App from Kubernetes
```
kubectl apply -f https://k8s.io/examples/application/php-apache.yaml -n scaler
```

#### Create hpa (Horizontal Pod Autoscaler) and Cronjobs
```
kubectl create namespace scaler
kubectl apply -f serviceAccount.yml -n scaler
kubectl apply -f hpa.yml -n scaler
kubectl apply -f cron.yml -n scaler
```

#### (Reference) Manually create hpa
```
kubectl autoscale deployment php-apache --cpu-percent=50 --min=1 --max=10 -n scaler
```