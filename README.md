# k8s-argocd-v1

## How the bundle manifest has been created

`git clone https://github.com/argoproj/argo-cd.git

kustomize build argo-cd/manifests/ha/cluster-install > k8s-argocd-v1/resources/vendor.yaml`

## How to use this kustomization
You can use this repo as a base for kustomization. You might need to patch all sort of things to configure ArgoCD to fit your requirements

``` yaml
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization
bases:
  - git@github.com:pabloolveira/k8s-argocd-v1.git
```

