This directory bootstraps Argo CD into a Kubernetes cluster using the official upstream install manifest.

Usage:

1. Apply via kustomize (will install Argo CD in the `argocd` namespace):

   kubectl apply -k manifests/argocd-install

2. Wait for Argo CD server to be ready and then port-forward or expose the `argocd-server` service.

3. Default admin password is set in the `argocd-initial-admin-secret` (check Argo CD docs for retrieval):

   kubectl -n argocd get secret argocd-initial-admin-secret -o yaml

Notes:
- This kustomization references the official `install.yaml` from the Argo CD repository's `stable` channel. You may change the URL to a specific release if needed.
- To change the initial admin password, create a bcrypt-hashed password and patch the `argocd-secret` as documented in Argo CD docs.
