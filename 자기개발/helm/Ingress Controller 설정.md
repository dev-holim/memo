
#### Helm Repo 추가 및 설치
```bash
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update
```


#### Helm으로 Ingress Contoller 설치 (NodePort 8001 바인딩)
```bash
helm upgrade --install ingress-nginx ingress-nginx/ingress-nginx \
  --namespace ingress-nginx --create-namespace \
  --set controller.ingressClass=nginx \
  --set controller.ingressClassResource.name={{ .Values.ingress.className }} \
  --set controller.service.type=NodePort \
  --set controller.service.nodePorts.http=30080 \
  --set controller.service.nodePorts.https=0 \
  --set controller.extraArgs.ingress-class={{ .Values.ingress.className }}


helm upgrade --install sso-be-nginx ingress-nginx/ingress-nginx \
  --namespace sso-nginx --create-namespace \
  --set controller.ingressClass=nginx \
  --set controller.ingressClassResource.name=sso-be-stage-nginx-ingress-class \
  --set controller.service.type=NodePort \
  --set controller.service.nodePorts.http=30080 \
  --set controller.service.nodePorts.https=0 \
  --set controller.extraArgs.ingress-class=sso-be-stage-nginx-ingress-class

helm upgrade --install erp-fe-nginx ingress-nginx/ingress-nginx \
  --namespace erp-ingress --create-namespace \
  --set controller.ingressClass=nginx \
  --set controller.ingressClassResource.name=erp-stage-fe-nginx-ingress-class \
  --set controller.service.type=NodePort \
  --set controller.service.nodePorts.http=30081 \
  --set controller.service.nodePorts.https=0 \
  --set controller.extraArgs.ingress-class=erp-stage-fe-nginx-ingress-class


helm upgrade --install erp-homepage-nginx ingress-nginx/ingress-nginx --namespace homepage-ingress --create-namespace --set controller.ingressClass=nginx --set controller.ingressClassResource.name=homepage-stage-be-nginx-ingress-class --set controller.service.type=NodePort --set controller.service.nodePorts.http=30082 --set controller.service.nodePorts.https=0 --set controller.extraArgs.ingress-class=homepage-stage-be-nginx-ingress-class
```