## Running Argo CD Locally

1. install Argo CD
```bash
brew install argocd
```

2. Enable Kubernetes in Docker Desktop
3. Create ArgoCD Namespace
```bash
kubectl create namespace argocd
```

4. Install ArgoCD into K8s
```bash
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

5. Get ArgoCD Password
```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```

6. Port Forward and Sign in:
```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

You can update the password with: `argocd account update-password`


[Landing Page](https://localhost:8080)

---

## Deploy Argo Guestbook
```bash
kubectl apply -f argo-guestbook.yaml -n argocd
```

You can now verify that Argo has deployed the tutorial Guestbook application

Delete the application with:
```bash
kubectl delete application guestbook -n argocd
```