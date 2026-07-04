# argo_20260705

L15_운영배포 진화관점 대시보드의 "Argo CD (Pull GitOps 자동 동기화)" Wave가 실제로
Pull 기반 GitOps 동기화를 시연하기 위해 사용하는 데모 저장소입니다.

`manifests/`에 있는 Kubernetes 리소스를 Argo CD의 Application이 이 저장소를 감시(polling)하며
자동으로 클러스터에 동기화합니다. 이 파일들을 수정하고 push하면, 별도로 `kubectl apply`를
실행하지 않아도 Argo CD가 자동으로 클러스터 상태를 그 변경사항에 맞춰 갱신합니다(Self-Healing 포함).
