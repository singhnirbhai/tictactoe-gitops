# How we configure gitops on kubernetes 
## create a new namespace 
```bash
kubectl create namespace argocd
```

## Apply yamk config file 

```bash
kubectl apply -n argocd  -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
## Check pods 

```bash
kubectl get pods -n argocd
```
## port forwarding argo-server service pod
```bash
kubectl port-forward svc/argocd-server -n argocd 8443:443 --address=0.0.0.0 &
```
## open with instance public ip
```bash
https://public-ip:8443
```
## Get password to login argocd 
```bash
kubectl get secret argocd-initial-admin-secret -n argocd \
-o jsonpath="{.data.password}" | base64 -d
```


