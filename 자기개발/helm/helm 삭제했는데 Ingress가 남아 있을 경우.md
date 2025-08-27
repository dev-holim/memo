
- 대부분 ingress가 남아있고 ingress class가 없어서 생기는 문제
- ingress class 강제 추가 후 삭제

```
cat <<'EOF' | kubectl apply -f -
apiVersion: networking.k8s.io/v1
kind: IngressClass
metadata:
  name: sso-stage-ingress-class
spec:
  controller: ingress.k8s.aws/alb
EOF
```