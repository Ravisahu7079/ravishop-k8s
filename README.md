# ravishop-k8s

# ☸️ RaviShop Kubernetes

![Kubernetes](https://img.shields.io/badge/Kubernetes-K8s-blue)
![Helm](https://img.shields.io/badge/Helm-Charts-blue)
![ArgoCD](https://img.shields.io/badge/ArgoCD-orange)

## 📌 Overview

 Kubernetes manifests and GitOps configuration for RaviShop using Argo CD.

## 🏗️ Architecture Diagram

![Architecture](RaviShop%20Diagram.drawio.png)

## 📁 Structure

    ravishop-k8s/
       ⌊______manifests/
       ⌊______base/
       |——————deployment.yaml → App deployment (2 replicas)
       |——————service.yaml    → NodePort service
       |——————ingress.yaml    → Ingress rule
       |——————configmap.yaml  → App configuration
       |——————secret.yaml     → Sensitive data       

## 🚀 Deploy to Kubernetes

```bash
   kubectl apply -f manifests/base/
   kubectl get pods
   curl http://localhost:32099/health
```
♾️ GitOps with Argo CD

```bash
    argocd app create ravishop \
      --repo https://github.com/Ravisahu7079/ravishop-k8s.git \
      --path manifests/base \
      --dest-server https://kubernetes.default.svc \
      --dest-namespace default \
      --sync-policy automated
```
📊 Resources

| Resource | Details |
|---|---|
| Deployment | 2 replicas, liveness + readiness probes |
| Service | NodePort 32099 |
| Ingress | ravishop.local |
| Resources | CPU: 100m-500m, Memory: 128Mi-256Mi |

🧑‍💻 Author

    Ravi Sahu —— @Ravisahu7079 
