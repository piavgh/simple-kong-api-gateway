# Simple Kong API Gateway

## How to use

1. Create sample deployment

```bash
kubectl apply -f foo.yaml
kubectl apply -f bar.yaml
```

2. Create Kong API Gateway

```bash
kubectl create -f https://bit.ly/k4k8s
```

3. Configure Kong Gateway

```bash
kubectl apply -f foo-ingress.yaml
kubectl apply -f bar-ingress.yaml
```

4. Get the external url

```bash
export PROXY_IP=$(minikube service -n kong kong-proxy --url | head -1)
```

Alternatively, you can run `kubectl -n kong get service kong-proxy` to get the external url of the load balancer, then run `export PROXY_IP=<the-external-url-you-see>`.

If you use `minikube`, you should run `minikube tunnel` before the above commands.

5. Verify

```bash
curl $PROXY_IP/foo
curl $PROXY_IP/bar
```
