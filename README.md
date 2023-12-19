apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: todo-app-argo
  namespace: argocd
spec:
  project: default

  source:
    repoURL: https://github.com/Joelayo/Week_4-Kubernetes-Manifests.git
    targetRevision: HEAD
    path: kube-manifest
  destination: 
    server: https://kubernetes.default.svc
    namespace: todo-app

  syncPolicy:
    syncOptions:
    - CreateNamespace=true

    automated:
      selfHeal: true
      prune: true
