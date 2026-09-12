# 일일 로그

형식: 오늘 한 일 → 확인된 사실 → 돈 될 가능성 → 문제 → 내일 할 일 → 승인 필요한 것

---

## 2026-09-12 (Day 1 — OSS Risk Lite)

**오늘 한 일**: 경쟁제품 조사(Snyk/FOSSA/GitHub Advanced Security/무료 OSS 스캐너 5종), 시장 공백 분석, 수익화 가설 수립. 리포 세팅(`ppolong/claude`).

**확인된 사실**: 무료 취약점 스캐너는 시장에 이미 충분(Trivy, OSV-Scanner 등). 반면 저렴하고 가벼운 "라이선스 리스크 리포트" 툴은 공백 — 있는 건 전부 엔터프라이즈 세일즈 기반(Snyk $25+/월, GitHub Advanced Security는 프라이빗 리포 유료).

**돈 될 가능성**: 중간. 인디 해커/소규모 에이전시 대상 1회성 결제($9~29/스캔) 가설 — 아직 실제 결제 의사 확인 전이라 가설 단계.

**문제**: FOSSA 등 일부 경쟁사 정확한 가격 확인 실패(사이트 접근 차단). 실제 구매 의사는 Day 6~7 전까지 확인 어려움 — 초반 판단은 리스크 있음. (참고: 클라우드 세션에서 이 리포로 직접 git push가 막혀 있어, 로컬 장비 연결을 통해 대신 푸시함 — 향후 코드 커밋도 이 경로 사용 예정.)

**내일 할 일**: Day 2 — 최소 기능 설계 (스캔 범위: package.json/requirements.txt/go.mod 등 주요 매니페스트 파서, 라이선스 정책 규칙 셋, 리포트 포맷).

**승인 필요한 것**: 없음 (Day 1 결론 그대로 진행).

상세: [research/day1-market-research.md](research/day1-market-research.md)
