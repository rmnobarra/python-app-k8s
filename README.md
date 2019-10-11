#Configura traefik ingress versão 1.7 como daemon set.

1. RBAC
```bash
kubectl apply -f traefik-rbac.yaml
```
1. Daemonset
```bash
kubectl apply -f traefik-ds.yaml
```
2b. (alternativo) - Deployment
```bash
kubectl apply -f traefik-deployment.yaml
```
1. Traefik UI
2. ```bash
kubectl apply -f ui.yaml
```
#Extras

Configurar autenticação para o dashboard do traefik

1. Gerar o hash com usuário e senha:
htpasswd -c ./auth myusername

2. Criar secret a partir do arquivo gerado no passo 1
kubectl create secret generic traefik-dash-secret --from-file auth

Testes:

Deploy 3 nginx
```bash
kubectl apply -f python-app-deployment
```
expose via clusterip os deployments
```bash
kubectl expose deploy nginx-deploy-main --port 80
kubectl expose deploy nginx-deploy-green --port 80
kubectl expose deploy nginx-deploy-blue --port 80
```

criar ingress resources para os deployments
```bash
kubectl apply -f ingress-resource-2.yaml
```

OBS: Este ingress resources criará rotas para nginx.example.com > nginx-deploy-main, blue.nginx.example.com > nginx-deploy-blue e green.nginx.example.com > nginx-deploy-green, logo adicione entradas no arquivo hosts de sua estação de acordo com os endereços acima + ip's dos workers e ou balances (de acordo com o ambiente)


ref:
https://docs.traefik.io/user-guide/kubernetes/
https://github.com/containous/traefik/tree/v1.7/examples/k8s