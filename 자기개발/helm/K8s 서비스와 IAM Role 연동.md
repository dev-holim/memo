
```bash
# EKS 클러스터 리스트
aws eks list-clusters --region ap-northeast-2
```


```
eksctl create iamserviceaccount \
  --name ecr-access-sa \
  --namespace erp \
  --cluster <CLUSTER_NAME> \
  --attach-policy-arn arn:aws:iam::aws:policy/AmazonEC2ContainerRegistryReadOnly \
  --approve
```