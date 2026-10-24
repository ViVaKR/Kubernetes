# Kubernetes

> 쿠버네티스 (K8s) 이야기

## 삭제 및 정리

```bash

# 모든 배포 및 파드(Pod) 일괄 정리
# buddham 네임스페이스 내의 모든 Deployment, StatefulSet, Service 일괄 삭제
kubectl delete deployments,statefulsets,services,cronjobs,jobs --all -n <namespace>

# (선택) 아예 네임스페이스 통째로 폭파하고 싶다면?
# 네임스페이스 전체 삭제 (안의 모든 팟/시크릿/설정 싹 삭제됨)
kubectl delete namespace buddham

# (선택) StatefulSet 완전 삭제
kubectl delete statefulset buddham-ollama -n <namespace>

# (선택) Deployment 완전 삭제
kubectl delete deployment buddham-ai-deploy -n <namespace>

# 디스크 볼륨(PVC)까지 완전히 삭제해서 용량 확보!
kubectl delete pvc --all

# 확인
kubectl get pods

# 1. (docker) 실행 중인 모든 도커 컨테이너 일괄 중지 및 삭제!
docker stop $(docker ps -a -q) && docker rm $(docker ps -a -q)

# 2. (docker) 미사용 컨테이너, 이미지, 볼륨, 네트워크 싹 청소해서 디스크 100% 확보!
docker system prune -a --volumes -f
```
