This folder contains Kubernetes manifests and ArgoCD configuration for deploying a small sample app.

Structure:
- `argocd/project.yaml` - ArgoCD AppProject allowing this repo as source.
- `argocd/application.yaml` - ArgoCD Application that syncs `manifests/k8s` into the cluster.
- `k8s/` - Kustomize directory containing `namespace`, `deployment`, `service` and `kustomization`.

How to use:
1. Install ArgoCD in your cluster and ensure the `argocd` namespace exists.
2. Apply the AppProject and Application (or create the Application in ArgoCD UI):

   kubectl apply -f manifests/argocd/project.yaml
   kubectl apply -f manifests/argocd/application.yaml

The ArgoCD Application will create the `new-project` namespace and deploy the sample nginx Deployment & Service.
