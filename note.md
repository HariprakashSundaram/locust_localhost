
# argocd steps
===================================================================
kubectl get secret argocd-initial-admin-secret -n argocd `
-o jsonpath="{.data.password}" |
  %{ [System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String($_)) }

kubectl rollout restart deployment argocd-repo-server -n argocd

kubectl get pods -n argocd

kubectl port-forward svc/argocd-server -n argocd 8080:443

HVM9TJl6bc7UqzX5
===================================================================
# to redeploy application from start

kubectl delete all --all
===================================================================
# to applu changes

kubectl apply -f application.yaml
===================================================================
# Get pod name
kubectl get pods -n locust

===================================================================
# Copy results to your machine

kubectl cp locust/locust-master-xyz:/results/results.csv ./results.csv

===================================================================
# View results
cat results.csv

===================================================================
# to copy files

kubectl cp locust/locust-master-59b6bdf9b-f87fp:/reports/report.html ./report.html
===================================================================
# to use like linux box

kubectl exec -it locust-master-<pod-id> -n locust -- bash

===================================================================
# Once inside the pod, navigate and explore
ls -la /reports
cd /reports
ls -la