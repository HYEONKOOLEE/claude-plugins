---
name: proposal-writer
description: 1주차 1·2일차에 만든 모든 자산(idea-discovery·competitor-radar·MRD·brand-strategy)을 종합해 정부지원 신청서·B2B 제안서·IR 자료를 9개 표준 섹션 + 5가지 프레임워크(PESTEL·SWOT·BMC·MECE·KSF) 자동 인용으로 작성하는 스킬. 정부지원 1억+ ROI를 1주차 끝에 회수 가능. "신청서 / 제안서 / IR / 사업계획서 / 정부지원 / 예비창업 / 초기창업 / B2B 제안 / 투자 IR" 호출 시 자동 발현.
triggers: [신청서, 제안서, IR, 사업계획서, 정부지원, 예비창업, 초기창업, B2B 제안, 투자 IR, proposal, PESTEL, SWOT, KSF]
version: v2
---

# proposal-writer — 정부지원·B2B·IR 통합 제안서 자동 작성 (v2)

> **한 줄 정의**: 1주차 모든 자산을 종합해 **9섹션 + 5프레임워크 자동 인용**으로 신청서·제안서·IR 1쪽~다쪽을 30분 안에 작성하는 스킬

> **ROI**: 정부지원 1건 평균 통과 시 *예비창업·초기창업 5천만~1억 / B2B 제안 500~3,000만 / IR 수억*. 연 1~2건이면 1주차 강의료를 1주 안에 회수.

> **v2 핵심 변경 (2026-05-16)**:
> - **정부지원 사업공고·평가기준·마감일 실시간 확인 웹 리서치 의무화** (사업공고는 매월 갱신)
> - PESTEL·SWOT·KSF 인용 시 **출처 URL + 발행일 동반 필수** (단일 출처 의존 금지)
> - 학습 데이터 단독 답변 금지 — *반드시 명시*: "(주의: 학습 데이터 기준이며 변경 가능)"
> - **사업공고 신청 직전 *해당 공고 원문 1차 확인* 강제** (학습 데이터의 마감일·예산이 변경된 경우 신청 실패 위험)

---

## 1. 언제 호출되나

### Description 매칭 키워드
- *신청서*, *제안서*, *IR*, *사업계획서*
- *정부지원*, *예비창업*, *초기창업*
- *B2B 제안*, *투자 IR*, *proposal*
- *PESTEL*, *SWOT*, *KSF* (프레임워크 인용 트리거)

### 사용 시나리오 3가지
1. **정부지원 마감 3일 전** — 1주차 자산 5종이 갖춰진 상태에서 *한 줄 입력으로 1쪽 1차본*
2. **B2B 큰 거래처 제안 요청** — 같은 스킬로 *민간 제안서 톤*으로 자동 변환
3. **투자 유치 IR 자료** — 시장·BM·KSF가 5가지 프레임워크 인용으로 *근거 풍부*

---

## 2. 입력 (Input)

### 필수 입력 (1주차 4종 산출물 전부)
- `agents/strategy-team/outputs/01_strategy_idea_discovery_v1.md` — 사업 정의 + 3축 검증
- `agents/strategy-team/outputs/02_research_competitive_v1.docx` — 시장 환경 + 1순위 Pain
- `agents/strategy-team/outputs/03_mrd_v1.docx` — 시장 요구사항 + Must 3개
- `agents/strategy-team/outputs/04_brand_strategy_v1.docx` — Hook + 미션·비전 + 30일 플랜
- `agents/strategy-team/memory/{context,decisions,glossary}.md` — 회사 의식 3종

### 선택 입력 (제안 종류 결정)
- 신청서 양식 파일 (예: 예비창업패키지·초기창업패키지 양식 등)
- 제안 종류 (정부지원 / B2B / IR 중 선택)
- 분량 (1쪽 / 3쪽 / 다쪽 풀 사업계획서)

### 메모리 의존성
- 작업 직후 `agents/strategy-team/memory/decisions.md`에 *제출 일자·제안 종류·결과(나중에 기록)* 자동 추가

---

## 3. 처리 흐름 (Process) — 9섹션 + 5프레임워크

### 0-1. ⭐ 발화 시점 웹 리서치 의무 (신청서·제안서 작성 진입 시 필수)

**학습 데이터의 한계 보완을 위해, 본 스킬은 다음을 반드시 웹서치로 선행한다:**

| 적용 위치 | 필수 웹서치 키워드 |
|---|---|
| 사업공고 원문 (★ 최우선) | "[현재 연도] [사업명] 공고 bizinfo OR k-startup OR mss.go.kr", "[사업명] 평가기준 OR 가점항목 [현재 연도]" |
| 섹션 2 추진 배경 | "이재명정부 국정과제 [도메인]", "[현재 연도] [도메인] 정책 기조" |
| 섹션 3 시장 분석 (PESTEL) | "한국 [도메인] 시장 규모 [현재 연도]", "[도메인] 규제·인허가 [현재 연도]" |
| 섹션 4 차별성 (SWOT) | "[경쟁사] 동향 [현재 연도]", "[도메인] 진입장벽 OR 후발주자 트렌드" |
| 섹션 7 KSF | "[도메인] 성공 사례 [현재 연도]", "[사업명] 선정 사례 OR 통과 후기" |

**출력 시 인용 규칙 (정부지원 평가위원 신뢰도 직결)**:
- **사업공고 원문은 *반드시 원문 URL 확인* — 마감일·예산·신청자격 변경 가능성 점검**
- 모든 정책·시장·경쟁 인용은 **출처 URL + 발행일** 동반 필수 (After 기준 6건 +)
- 5가지 프레임워크(PESTEL·SWOT·BMC·MECE·KSF)는 *각각 최소 1건* 1차 출처 인용
- 한국 1차 출처(통계청·KOSIS·산업연구원·중기부) 우선, 글로벌은 보조
- 학습 데이터로만 답변 시 *반드시 명시*: "(주의: 학습 데이터 기준이며 [날짜] 이후 변경 가능 — 신청 전 원문 재확인 필수)"

**평가위원 관점 (왜 이게 ROI에 직결되나)**:
> 평가위원은 1쪽을 3분 본다. *틀린 정책 인용·만료된 사업공고*는 즉시 *근거 부족* 판정.
> 신청 전 1회 웹서치로 사업공고 원문을 확인하는 것이 1억 원 ROI를 지키는 *최후의 방어선*.

자세한 사업공고 검색·인용 양식은 `references/citation_apa_lite.md`(§ 과업 0)·`references/templates/`(각 양식 § 과업 0) 참조.

### 9개 표준 섹션 (정부지원 신청서 기준)

| # | 섹션 | 들어가는 1주차 자산 |
|---|---|---|
| 1 | **사업 개요** | idea-discovery 한 줄 정의 + brand-strategy Hook |
| 2 | **추진 배경·필요성** | brand-strategy 미션·비전 + competitor-radar 1순위 Pain |
| 3 | **시장 분석** | competitor-radar 3유형 + MRD TAM/SAM/SOM (**PESTEL** 자동 적용) |
| 4 | **차별성·경쟁력** | brand-strategy 미션·핵심가치 + competitor-radar 진입장벽 (**SWOT** 자동 적용) |
| 5 | **비즈니스 모델** | brand-strategy Value Ladder + MRD 요구사항 (**BMC 9블록** 자동 적용) |
| 6 | **추진 전략·실행안** | brand-strategy 30일 플랜 + MRD MoSCoW Must (**MECE** 자동 적용) |
| 7 | **핵심 성공 요인** | idea-discovery 3축 검증의 *보완 방안* (**KSF** 자동 적용) |
| 8 | **위험·대응** | idea-discovery 3축의 *치명 약점 3개* + 보완 방안 |
| 9 | **성과 지표·기대 효과** | MRD 정량 KPI 3 + 1·3년 목표값 |

### 5가지 프레임워크 자동 인용

| 프레임워크 | 적용 섹션 | references 파일 |
|---|---|---|
| **PESTEL** (정치·경제·사회·기술·환경·법) | 섹션 3 시장 분석 | `framework_pestel.md` |
| **SWOT** (강점·약점·기회·위협) | 섹션 4 차별성·경쟁력 | `framework_swot.md` |
| **BMC** (Business Model Canvas 9블록) | 섹션 5 비즈니스 모델 | `framework_bmc.md` |
| **MECE** (Mutually Exclusive·Collectively Exhaustive) | 섹션 6 추진 전략 (실행안 분류 검증) | `framework_mece.md` |
| **KSF** (Key Success Factor) | 섹션 7 핵심 성공 요인 | `framework_ksf.md` |

→ 각 프레임워크는 *해당 섹션에서 자동 호출*되며, 인용 시 *출처·연도·페이지* 명시.

### 출력 — DOCX 표준

1. **1차·최종 결과**: `agents/strategy-team/outputs/05_proposal_v1.docx` (DOCX) — **모든 케이스의 표준 출력**
2. **PPT 출력은 v1 범위 외** — 3주차 권정선 강사 디자인 시스템 완성 후 별도 스킬 `proposal-to-deck` (가칭)로 분리 예정 (6~7주차)

---

## 4. 사용 프레임워크

| 단계 | 프레임워크 |
|---|---|
| 시장 분석 | PESTEL 6요소 |
| 차별성 | SWOT 4분면 |
| 비즈니스 모델 | BMC 9블록 |
| 실행 전략 | MECE 분류 |
| 성공 요인 | KSF 3~5개 |
| 위험 관리 | 1주차 3축 검증 매트릭스 |

---

## 5. 출력 (Output)

### 파일명·저장 경로
```
agents/strategy-team/outputs/05_proposal_{종류}_{날짜}_v1.docx   ← 디폴트
```
- 종류: `gov` (정부지원) / `b2b` (B2B 제안) / `ir` (투자 IR)
- 날짜: YYYYMMDD
- **DOCX가 표준 출력 형식**
- PPT 변환은 v1 범위 외 (3주차 디자인 시스템 + 별도 스킬 `proposal-to-deck`로 6~7주차)

### 결과물 섹션 구조 (9섹션)
1. 사업 개요 (Hook + 한 줄 정의)
2. 추진 배경·필요성 (미션·비전 + 1순위 Pain)
3. 시장 분석 (PESTEL 적용)
4. 차별성·경쟁력 (SWOT 적용)
5. 비즈니스 모델 (BMC 9블록 적용)
6. 추진 전략·실행안 (30일 플랜 + MECE)
7. 핵심 성공 요인 (KSF 적용)
8. 위험·대응 (3축 약점 + 보완)
9. 성과 지표·기대 효과 (정량 KPI + 목표값)
* 부록: 출처 목록 + 프레임워크 인용 표

---

## 6. references/ 분리 자료

```
skills/proposal-writer/
├── SKILL.md (이 파일)
├── references/
│   ├── framework_pestel.md       — PESTEL 6요소 + 한국 적용 사례
│   ├── framework_swot.md         — SWOT 4분면 + TOWS 매트릭스
│   ├── framework_bmc.md          — BMC 9블록 + 작성 순서
│   ├── framework_mece.md         — MECE 분류 규칙 + 위반 사례
│   ├── framework_ksf.md          — KSF 도출 양식 + 사례
│   ├── citation_apa_lite.md      — APA-lite 인용 양식
│   └── templates/
│       ├── gov_yebi.md           — 예비창업패키지 9섹션 양식
│       ├── gov_chogi.md          — 초기창업패키지 9섹션 양식
│       ├── b2b_general.md        — B2B 일반 제안서 양식
│       └── ir_seed.md            — 시드·시리즈 A IR 양식
└── examples/
    └── notefriends_proposal.md   — 노트프렌즈 예비창업패키지 1쪽 완성 예시
```

---

## 7. 핸드오프 (Hand-off)

**받을 사람**: 없음 (1주차 최종 산출물) — 단, 결과는 *사이 3일 과제 #4* 로 본인 사업에 재사용

**전달 자료** (사이 3일 동안 본인이 사용):
- 5단계 빌드 패턴 학습 결과 → *다른 신청서에도 같은 패턴으로 적용 가능*
- 4종 양식 템플릿 → *예비창업·초기창업·B2B·IR 모두 가능*

**Before / After 비교 양식** (1주차 1일차 강사 메시지의 증거):

| 항목 | Before (도구 시절, ChatGPT 3시간) | After (Skill 자동 호출, 30분) |
|---|---|---|
| 출처 인용 | 0건 | 6건+ |
| 프레임워크 | 0개 | 5개 (PESTEL·SWOT·BMC·MECE·KSF) |
| 숫자·지표 | 0개 | 9개+ |
| 평가자 피드백 | "근거 부족" | "근거 명확" |

---

## 8. 검증 체크리스트

- [ ] *"예비창업 신청서 써줘"* 한 줄에 자동 발현되는가
- [ ] 9개 섹션 모두 채워지는가
- [ ] 5가지 프레임워크가 *해당 섹션에서* 자동 인용되는가
- [ ] 출처 6건+ / 프레임워크 5개 / 숫자 9개+ 충족되는가 (After 기준)
- [ ] 1주차 4종 산출물 모두 *해당 위치에 자동 매핑*되는가
- [ ] 결과물이 `agents/strategy-team/outputs/05_proposal_*.docx`로 자동 저장되는가
- [ ] B2B / IR 모드도 동일 패턴으로 작동하는가 (양식 5종 완비)

---

*작성일: 2026-05-15 | 버전: v2 (2026-05-16 웹 리서치 의무화 추가)*

### 변경 이력
- **v2.1 (2026-05-16 심야)**: 출력 형식 단순화 — DOCX 표준 출력으로 통일. 사용 빈도 낮은 양식 1종의 트리거·템플릿·참조 일괄 제거 (4종 표준 양식 유지).
- **v2 (2026-05-16)**: § 0-1 발화 시점 웹 리서치 의무 섹션 신설. 사업공고 원문·평가기준·마감일 실시간 확인 강제, 5프레임워크 인용 시 출처 URL + 발행일 강제, 한국 1차 출처 우선 규칙 명문화. `citation_apa_lite.md`·`templates/` § 과업 0 연계.
- **v1.1 (2026-05-15)**: DOCX를 표준 출력으로 명확화. PPT 출력은 별도 스킬 `proposal-to-deck`(가칭)로 분리 — 3주차 권정선 디자인 시스템 완성 후 6~7주차에서 작업 예정
- **v1 (2026-05-15)**: 초안 작성
