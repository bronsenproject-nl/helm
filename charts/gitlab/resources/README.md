
```bash
# list all pv's
kubectl get pv

# recreate namespace
kubectl create namespace gitlab

# make volume available again
kubectl patch pv [ fill-in-postgres-volume-name ] -p '{"spec":{"claimRef": null}}'
# make sure the same volumename is in the yaml you are about to apply
kubectl apply -f postgres-pvc.yaml

kubectl patch pv [ fill-in-redis-volume-name ] -p '{"spec":{"claimRef": null}}'
kubectl apply -f redis-pvc.yaml

kubectl patch pv [ fill-in-gitlab-data-volume-name ] -p '{"spec":{"claimRef": null}}'
kubectl apply -f data-gitlab-pvc.yaml

kubectl patch pv [ fill-in-gitlab-config-volume-name ] -p '{"spec":{"claimRef": null}}'
kubectl apply -f config-gitlab-pvc.yaml

kubectl patch pv [ fill-in-gitlab-logs-volume-name ] -p '{"spec":{"claimRef": null}}'
kubectl apply -f logs-gitlab-pvc.yaml







```