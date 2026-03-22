Run this

1. Create Deploy.yaml
```bash
kubectl apply -f deploy.yaml
```

2. Create Service.yaml
```bash
kubectl apply -f service.yaml
```

3. Create Ingress-nginx-controller
```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml
```

4. Create cert-manager.yaml
```bash
kubectl apply -f cert-manager.yaml
```
* To automate SSL certificate management inside Kubernetes.

5. Create issuer.yaml
```bash
kubectl apply -f issuer.yaml
```
* To tell cert-manager HOW and FROM WHERE to get SSL certificates.
  
6. Create ingress.yaml
```bash
kubectl apply -f ingress.yaml
```
