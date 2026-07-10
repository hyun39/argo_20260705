# argo_20260705 — GitOps 데모 저장소

`L15_운영배포/08_Helm_Argo_진화관점.md`의 Wave 3(GitOps 원칙) ~ Wave 4(Argo CD Pull GitOps)
실습에서 사용하는 저장소입니다.

```
.
├── charts/myapp/       # Helm 차트 (공통, Wave 2와 동일 구조)
└── envs/
    ├── dev/values.yaml   # dev 오버라이드
    └── prod/values.yaml  # prod 오버라이드 — 이 파일의 변경이 곧 "prod 배포 요청"
```

- **Wave 3**: 이 구조 자체가 "Git = 진실의 원천"이다. `envs/prod/values.yaml`을 수정하고 커밋하는 것이
  배포 요청이며, `git log`가 배포 이력이 된다. 단, 이 시점엔 아직 아무것도 자동으로 클러스터에
  반영되지 않는다 — 그게 Wave 3에서 발견하는 한계다.
- **Wave 4**: Argo CD Application이 이 저장소를 직접 pull해 그 한계를 해소한다.
