# Day 1 (신규 아이템) — Confluence 기반 API 문서 자동화 도구

날짜: 2026-09-12

## 배경 — 아이템 전환 사유

OSS Risk Lite는 수요 신호가 반복적으로 약하게 나와 중단(자세한 내용: [../PROGRESS.md](../PROGRESS.md) 2026-09-12 Day2 항목). 다음 후보 선정 시 아래 2개는 검토 후 기각:

- **Claude Code용 유료 인증/보안 스킬**: 마켓플레이스(mcpmarket.com, claudemarketplaces.com 등)에 이미 무료 "Security/Auth" 스킬이 다수 존재 — 경쟁 난이도 높음, 기각.
- **Confluence/Jira MCP 커넥터 상품화**: Atlassian이 이미 공식 GA MCP 서버(`atlassian/atlassian-mcp-server`, 무료, OAuth 2.1 지원)를 제공 중 — 직접 경쟁 불가, 기각. ([Atlassian 공식 GitHub](https://github.com/atlassian/atlassian-mcp-server))

## 아이디어

**Confluence 테이블 기반 API 문서 → 자동 개발자 포털/필드 사전 변환 도구.** 준님이 실제로 회사에서 만들어 운영 중인 파이프라인(STOVE API 필드 사전: Confluence 테이블 → GitLab Pages 자동화)을 일반화한 상품.

## 시장 확인

- API 문서화 툴 시장 자체는 검증된 유료 카테고리: ReadMe.io, Redocly, Stoplight, Theneo 등 다수의 상용 제품이 존재. Redocly는 Pro $10/seat/월(프로젝트 1개, 100페이지), Enterprise $24/seat/월. ([redocly.com/pricing](https://redocly.com/pricing))
- **핵심 공백**: Redocly는 스스로를 "OpenAPI-generated documentation tool"이라 명시 — **OpenAPI 스펙이 이미 있다는 전제**. ReadMe/Stoplight 계열도 동일 전제인 경우가 대부분(전수 확인은 다음 세션 필요). 반면 다수의 조직(특히 레거시/사내 API)은 스펙 없이 **Confluence 테이블로만** API를 문서화하고 있음 — "How to Document APIs in Confluence"류 가이드가 여러 개 존재한다는 것 자체가 이 관행이 흔하다는 방증. ([DEV Community 가이드](https://dev.to/yamuno-software/how-to-document-apis-in-confluence-4kja), [Medium 가이드](https://medium.com/@vlad.prishhepa/simple-and-effective-api-documentation-in-confluence-86da8732039c))
- 즉 "OpenAPI 스펙 없이 Confluence만 있는 팀"은 기존 유료 툴들의 사각지대일 가능성.

## 실행 근거 (전문성 매치)

준님이 이미 직접 만들어서 운영 중인 파이프라인과 100% 동일한 문제:
- Confluence 테이블 → 정적 사이트(GitLab Pages) 자동화 (field-dictionary 프로젝트)
- Confluence Wiki 마이그레이션 스크립트 작성 경험

→ 처음부터 설계할 필요 없이 기존에 검증한 접근을 일반화만 하면 됨 — **실행 속도 매우 높음**.

## 수익화 가설 (검증 필요)

- 타깃: OpenAPI 스펙 없이 Confluence로 API를 관리하는 중소 규모 백엔드/플랫폼 팀, 에이전시.
- 가격 후보: self-serve 월 구독 $15~40/월(팀당) 또는 초기 셋업 1회성 + 낮은 유지비. Redocly 최저가($10/seat)보다 낮은 진입장벽 유지.
- 채널: 랜딩페이지 + Stripe, 또는 Atlassian Marketplace 앱(추가 조사 필요).

## 판단

**진행 → Day 2(최소 기능 설계)**. 단, 아래는 다음 세션에서 반드시 추가 확인:
- ReadMe/Stoplight/Theneo가 정말로 전부 OpenAPI 전제인지, Confluence 직접 지원 기능이 있는지 정확히 확인 (이번엔 Redocly만 1차 확인함).
- Atlassian Marketplace에 유사 앱이 이미 있는지 확인 (아직 안 함).

## 출처
- [Atlassian MCP Server (공식, GA)](https://github.com/atlassian/atlassian-mcp-server)
- [Redocly Pricing](https://redocly.com/pricing)
- [How to Document APIs in Confluence — DEV Community](https://dev.to/yamuno-software/how-to-document-apis-in-confluence-4kja)
- [Simple and Effective API Documentation in Confluence — Medium](https://medium.com/@vlad.prishhepa/simple-and-effective-api-documentation-in-confluence-86da8732039c)
