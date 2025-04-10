
1. AWS IAM 키를 Secret으로 생성
```
kubectl create secret generic aws-credentials \
  --namespace=erp \
  --from-literal=AWS_ACCESS_KEY_ID=AKIATREFTAAHSVRKDJP3 \
  --from-literal=AWS_SECRET_ACCESS_KEY=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
```


```yaml
apiVersion: batch/v1  
kind: CronJob  
metadata:  
  name: refresh-erp-ecr-secret  
  namespace: erp  
spec:  
  schedule: "0 */12 * * *"  # 매 12시간마다  
  jobTemplate:  
    spec:  
      template:  
        spec:  
          containers:  
          - name: erp-ecr-secret-refresh  
            image: amazon/aws-cli  
            command:  
            - /bin/sh  
            - -c  
            - |  
              echo "🔄 Refreshing ECR docker-registry secret..."  
              aws ecr get-login-password --region ap-northeast-2 | \  
              kubectl create secret docker-registry ecr-erp-credential \  
                --docker-server=242945818639.dkr.ecr.ap-northeast-2.amazonaws.com \  
                --docker-username=AWS \  
                --docker-password=$(aws ecr get-login-password --region ap-northeast-2) \  
                --namespace=erp \  
              kubectl apply -f -  
              echo "✅ Done"  
            env:  
            - name: AWS_ACCESS_KEY_ID  
              valueFrom:  
                secretKeyRef:  
                  name: aws-credentials  
                  key: AWS_ACCESS_KEY_ID  
            - name: AWS_SECRET_ACCESS_KEY  
              valueFrom:  
                secretKeyRef:  
                  name: aws-credentials  
                  key: AWS_SECRET_ACCESS_KEY  
          restartPolicy: OnFailure
```


```bash
kubectl apply -f ecr-refresh-cronjob.yaml
```