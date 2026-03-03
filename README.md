first file
sudo kubectl port-forward --address 0.0.0.0 svc/frontend-service 8080:80 -n nginx --kubeconfig $HOME/.kube/config
kubectl exec -it deployment/frontend -n nginx -- sh -c "sed -i 's|proxy_pass http://backend-api:3000|proxy_pass http://backend-api|' /etc/nginx/conf.d/default.conf"
kubectl exec -it deployment/frontend -n nginx -- nginx -s reload
kubectl port-forward svc/frontend-service 8080:80 -n nginx --address 0.0.0.0 & // run service in background

