argocd login localhost:8080


argocd app create nginx-1 --repo https://charts.bitnami.com/bitnami \
--helm-chart nginx --revision 13.2.33 \
--dest-server https://kubernetes.default.svc \
--dest-namespace nginx



