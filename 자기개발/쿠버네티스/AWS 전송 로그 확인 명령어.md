
```bash
kubectl get pods -n kube-system | grep aws-load-balancer 


kubectl logs -f aws-load-balancer-controller-686d5547b9-5xv9v -n kube-system --tail=100
```