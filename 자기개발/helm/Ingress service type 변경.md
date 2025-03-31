
```yaml
service:  
  name: erp-prod-fe-service  
  type: ClusterIP  
  port: 80  
  targetPort: 3000  
  portName: http
annotations:
	alb.ingress.kubernetes.io/target-type: ip
defaultBackend:
	service:
		port:
			name: "http"

annotations:
	alb.ingress.kubernetes.io/target-type: instance
defaultBackend:
	service:
		port:
			number: 80
```