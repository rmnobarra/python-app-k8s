## Configura app python + traefik ingress + traefik ui.

### 1. Deployment
```bash
kubectl apply -f python-app-deployment.yaml
``` 
### 2. Service
```bash
kubectl apply -f python-app-service.yaml
```
### 3. RBAC
```bash
kubectl apply -f traefik-rbac.yaml
```
### 4. Daemonset
```bash
kubectl apply -f traefik-ds.yaml
```
### 4b. (alternativo) - Deployment
```bash
kubectl apply -f traefik-deployment.yaml
```
### 5. Traefik UI
```bash
kubectl apply -f ui.yaml
```
### 6. Ingress app python
```bash
python-app-ingress.yaml
```

ref:
https://docs.traefik.io/user-guide/kubernetes/
https://github.com/containous/traefik/tree/v1.7/examples/k8s