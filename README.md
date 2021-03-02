# k8s-argocd-v1

## Create cluster
```
gcloud container clusters create poc-v1 --zone europe-west1 \
    --node-locations europe-west1-b --machine-type=e2-medium --num-nodes=1
```

## Configure cluster access for kubectl
```
gcloud container clusters get-credentials poc-v1 --region=europe-west1
```

## Create argocd namespace
```
kubectl create ns argocd
```

## Deploy ArgoCD
```
kubectl -n argocd apply -f ./k8s-argocd-v1/resources/vendor.yaml
```

## Get ArgoCD Password
```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base65 -d && echo
```

## Expose ArgoCD deployment
```
kubectl expose deployment argocd-server --name argocd-lb-service \
    --type LoadBalancer --port 8000 --target-port 8080 -n argocd
```
## Get LB IP
```
kubectl get service argocd-lb-service -n argocd -o json
```

## Deploy ArgoCD Project and Application
```
kubectl 
```

## How the bundle manifest has been created

``` bash
git clone https://github.com/argoproj/argo-cd.git

mkdir k8s-argocd-v1 && mkdir k8s-argocd-v1/resources

cp argo-cd/manifests/install.yaml k8s-argocd-v1/resources/vendor.yaml
```
