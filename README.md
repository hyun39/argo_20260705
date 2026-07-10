# argo_20260705 — GitOps 데모 저장소

`L15_운영배포/08_Helm_Argo_진화관점.md`의 Wave 3(GitOps 원칙) ~ Wave 6(App of Apps/ApplicationSet)
실습에서 사용하는 저장소입니다. **backend/frontend 2개 앱 × dev/prd 2개 환경**을 다룹니다.

```
.
├── charts/
│   ├── backend/      # Helm 차트 (backend 전용)
│   └── frontend/     # Helm 차트 (frontend 전용)
└── envs/
    ├── dev/
    │   ├── backend.yaml   # dev 오버라이드
    │   └── frontend.yaml
    └── prd/
        ├── backend.yaml   # prd 오버라이드 — 이 파일의 변경이 곧 "prd 배포 요청"
        └── frontend.yaml
```

- **Wave 3**: 이 구조 자체가 "Git = 진실의 원천"이다. `envs/prd/*.yaml`을 수정하고 커밋하는 것이
  배포 요청이며, `git log`가 배포 이력이 된다. 단, 이 시점엔 아직 아무것도 자동으로 클러스터에
  반영되지 않는다 — 그게 Wave 3에서 발견하는 한계다.
- **Wave 4~6**: Argo CD Application들이 이 저장소를 직접 pull해 그 한계를 해소하고(Wave 4),
  드리프트를 자동 복구하며(Wave 5), App of Apps/ApplicationSet으로 backend/frontend × dev/prd
  4가지 조합을 자동 등록·관리한다(Wave 6).
