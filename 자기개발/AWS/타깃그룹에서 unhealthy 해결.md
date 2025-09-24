
```
 kubectl describe ingressclass sso-be-alb-ingress-class
```


```
kubectl -n sso describe ingress sso-be-prod-alb-ingress | sed -n '1,200p'
```

결과
```
...

alb.ingress.kubernetes.io/group.name: eks-sso-be-prod-tg
alb.ingress.kubernetes.io/healthcheck-headers: [{"name":"Host","value":"sso.telepix.net"}]
alb.ingress.kubernetes.io/healthcheck-host: sso.telepix.net

...

#  alb.ingress.kubernetes.io/healthcheck-path가 적용되지 않았음을 확인
```

```
kubectl -n sso annotate ingress sso-be-prod-alb-ingress \
  alb.ingress.kubernetes.io/healthcheck-path="/_health/" \
  --overwrite
```

결과
```
...

alb.ingress.kubernetes.io/group.name: eks-sso-be-prod-tg
alb.ingress.kubernetes.io/healthcheck-headers: [{"name":"Host","value":"sso.telepix.net"}]
alb.ingress.kubernetes.io/healthcheck-host: sso.telepix.net
alb.ingress.kubernetes.io/healthcheck-path: /_health/

...
```


바로 반영
```
kubectl -n sso annotate ingress sso-be-prod-alb-ingress \
  alb.ingress.kubernetes.io/reconcile-tick="$(date +%s)" --overwrite
```


확인
```
kubectl -n kube-system logs deploy/aws-load-balancer-controller | tail -n 120
```