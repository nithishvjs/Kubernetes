How SSL Works on Browser?

when we use HTTPS, the browser automatically asks for the certificate and server provide certificates(cert + key) and browser verify it and start.

How to Setup SSL-cert?

1. Run Deploy.yaml
```bash
kubectl apply -f deploy.yaml
```

2. Run Service.yaml
```bash
kubectl apply -f service.yaml
```

3. Run Ingress-nginx-controller
```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml
```

4. Run cert-manager.yaml
```bash
kubectl apply -f cert-manager.yaml
```
* To automate SSL certificate management inside Kubernetes.

5. Run issuer.yaml
```bash
kubectl apply -f issuer.yaml
```
* To tell cert-manager HOW and FROM WHERE to get SSL certificates.
  
6. Run ingress.yaml
```bash
kubectl apply -f ingress.yaml
```

What is Cert-manager and Lets encrypt?

cert-manager : "It request, stores and renew certificates"

Lets encrypt : "It generates cert and keys"

How ssl provides by lets encrypt on kubernetes?

Step 1 : kubectl apply -f ingress.yaml

Step 2 : cert-manager detects it and talks to lets encrypt(“Please give SSL for mydomain.com”)

Step 3 : Let’s Encrypt challenges you(“Prove you own this domain”)

Step 4 : cert-manager solves challenge by using (http01) by create temporary pods and ingress and url for it

Step 5 : Lets encrypt verifies it by using access temporary url

Step 6 : If access is success, lets encrypt provides cert + key and cert-manager store it on secrets.
