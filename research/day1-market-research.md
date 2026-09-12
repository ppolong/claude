# Day 1 — 시장/경쟁제품 확인 + 수익화 가설

날짜: 2026-09-12

## 1. 아이디어

**OSS Risk Lite**: 오픈소스 의존성의 라이선스 리스크 + 취약점을 스캔해서, 솔로 개발자/소규모 팀이 클라이언트나 인수자에게 보여줄 수 있는 간단한 리포트를 만들어주는 가벼운 툴.

## 2. 경쟁 구도 확인

### 2-1. 엔터프라이즈급 SCA/라이선스 툴

- **Snyk**: 무료 티어는 개발자당 프로젝트 5개까지. 유료는 Team $25/월/개발자(프로젝트 100개), Ignite $1,260/년/개발자(무제한). ([getpulsesignal.com](https://getpulsesignal.com/pricing/snyk))
- **FOSSA**: 공식 가격 페이지 접근 실패(봇 차단). 업계 통상 세일즈 견적 기반, 엔터프라이즈 타깃으로 알려짐 — 이 부분은 2차 출처 기반 추정이며 확인 필요.
- **GitHub Advanced Security**: 코드 스캐닝/시크릿 스캐닝/의존성 리뷰는 **퍼블릭 리포는 전부 무료**. **프라이빗 리포는 유료**(활성 커미터 단위 과금, 90일 기준). ([GitHub 공식 문서](https://docs.github.com/en/billing/concepts/product-billing/github-advanced-security))

→ 엔터프라이즈 툴은 전부 "회사 단위 계약 + 월 구독"이 기본 구조. 솔로 개발자/소규모 팀이 접근하기엔 가격도, 세일즈 프로세스도 무겁다.

### 2-2. 무료 오픈소스 툴

Trivy(32k+ stars), Grype, OWASP Dependency-Check, Syft(SBOM 생성), OSV-Scanner(Google) 등 — 전부 무료, CLI 기반, 상용 툴과 동일한 취약점 DB(NVD/OSV/GitHub Advisory) 사용. ([appsecsanta.com](https://appsecsanta.com/sca-tools/open-source-sca-tools))

**공통 한계 3가지:**
1. Reachability 분석 없음 → 실제 코드에서 안 쓰는 의존성도 다 취약점으로 잡아서 노이즈 많음
2. 자동 수정/리메디에이션 제안 없음
3. **라이선스 컴플라이언스는 수동** — 자동 정책 적용(예: "상용 프로젝트에 AGPL 섞이면 경고") 기능 없음

### 2-3. 라이선스 컴플라이언스 전용 툴

FOSSology, ScanCode Toolkit은 스캐너만 제공하고 정책 엔진/UI가 없어서 팀이 직접 워크플로우를 만들어야 함. Snyk Open Source는 라이선스 체크가 "partial"(듀얼 라이선스 감지 약함). ([appsecsanta.com](https://appsecsanta.com/sca-tools/open-source-license-compliance))

## 3. 발견한 공백

- 무료 취약점 스캐너는 이미 차고 넘침 (Trivy, OSV-Scanner 등) — 이 시장에 새로 들어가는 건 승산 없음.
- 반면 **"라이선스 리스크를 자동으로 걸러서 보여주는 가볍고 저렴한 툴"**은 공백. 있는 건 전부 엔터프라이즈 세일즈 기반(FOSSA, Black Duck)이거나 스캐너만 주는 오픈소스(ScanCode).
- 라이선스 리스크 확인 수요가 실제로 발생하는 시점: ① 사이드 프로젝트/SaaS를 팔거나(마이크로 인수) 투자 유치할 때 due diligence, ② 에이전시가 클라이언트에게 코드베이스 납품할 때, ③ 오픈소스를 상용 제품에 섞어 쓸 때 사내 정책 확인.

## 4. 수익화 가설

**타깃**: 엔터프라이즈 세일즈를 거칠 필요 없는 개인 — 인디 해커(마이크로 SaaS 인수/매각 준비), 소규모 에이전시, 1인 개발사.

**가설**: "리포 하나 스캔해서 사람이 읽을 수 있는 라이선스 리스크 리포트(PDF/링크)를 5분 안에 뽑아준다"는 것에 대해 **건당/1회성 결제**로 지불 의사가 있을 것이다. 구독보다 1회성 결제 장벽이 훨씬 낮음 (Gumroad/LemonSqueezy류 채널 활용).

**가격 후보** (검증 필요, 아직 확정 아님):
- 리포 1개 스캔 + 리포트: $9~29 1회성
- 지속 모니터링(월간 재스캔 + 알림): $5~15/월/리포

**채널 후보**: GitHub Marketplace 앱, 또는 독립 랜딩페이지 + Gumroad/LemonSqueezy 결제.

## 5. 판단

경쟁 난이도(엔터프라이즈 툴과 직접 경쟁 아님, 무료 툴과도 포지션 다름) + 초기 비용(무료 취약점 DB 재사용 가능, 신규 스캐너 개발 불필요) + 실행 속도(라이선스 파서 + 리포트 생성기만 있으면 MVP 가능) 조합이 나쁘지 않음. **진행** → Day 2(최소 기능 설계)로 이동.

## 출처

- [Snyk Pricing (PulseSignal 요약)](https://getpulsesignal.com/pricing/snyk)
- [GitHub Advanced Security 공식 billing 문서](https://docs.github.com/en/billing/concepts/product-billing/github-advanced-security)
- [12 Free Open-Source SCA Tools 2026 — AppSecSanta](https://appsecsanta.com/sca-tools/open-source-sca-tools)
- [License Compliance Scanner: 8 Open-Source Tools — AppSecSanta](https://appsecsanta.com/sca-tools/open-source-license-compliance)

**주의**: FOSSA 정확한 가격은 공식 사이트 접근이 막혀 직접 확인 못함(2차 출처 없이는 기재 안 함). Snyk/GitHub 항목도 2026년 9월 기준 스냅샷이며 변동 가능.
