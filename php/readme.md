#### This example is from [Kubernetes.io](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale-walkthrough/)

```
kubectl apply -f https://k8s.io/examples/application/php-apache.yaml -n scaler
kubectl autoscale deployment php-apache --cpu-percent=50 --min=1 --max=10 -n scaler
kubectl run -i --tty load-generator1 --rm --image=busybox -n scaler --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://php-apache:80/; done"
kubectl run -i --tty load-generator2 --rm --image=busybox -n scaler --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://php-apache:80/; done"
kubectl run -i --tty load-generator3 --rm --image=busybox -n scaler --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://php-apache:80/; done"
kubectl get deployment php-apache -n scaler
kubectl get hpa -n scaler
```

### expose php service
```
kubectl expose deployment php-apache --type=NodePort --name=php-apache-port -n scaler
```
