# Argo CD

brew install argocd
### automate deployment
k -n argocd apply -f .\argocd\install.yaml

### manual deployment
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# Port Forwarding
kubectl port-forward svc/argocd-server -n argocd 8080:80

argocd login <ARGOCD_SERVER>  # e.g. localhost:8080
### retrieve password
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
OjGHwwVpyRUfjicG%
T2pHSHd3VnB5UlVmamljRw==