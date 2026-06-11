---
name: mrd-writer
description: 1인 창업가의 시장 요구사항을 6개 표준 섹션(시장정의·세그먼트·문제·요구사항·성공지표·우선순위)으로 자동 정제해, 6주차 MVP 기획 PRD의 직속 상위 문서로 사용되는 MRD(Market Requirement Document)를 작성하는 스킬. competitor-radar 결과를 받아 *시장 인식 → 시장 요구* 로 변환하는 직렬 위치. "MRD 작성 / 시장 요구사항 / 요구사항 명세 / TAM SAM SOM / MoSCoW 우선순위" 호출 시 자동 발현.
triggers: [MRD 작성, 시장 요구사항, 요구사항 명세, market requirement, TAM SAM SOM, MoSCoW, 요구사항 우선순위, 시장 정의]
version: v2
---

# MRD-writer — 시장 요구사항 문서(Market Requirement Document) 자동 작성 (v2)

> **한 줄 정의**: competitor-radar의 *시장 인식*을 6개 표준 섹션의 *시장 요구사항*으로 변환해, 6주차 MVP 기획 PRD의 직속 상위 문서를 자동 작성하는 스킬

> **본질**: PRD(Product Requirement Document)는 "무엇을 만들 것인가"이고, MRD는 "왜 만들어야 하는가". 1주차 MRD가 6주차 PRD의 *근거 문서* 역할.

> **v2 핵심 변경 (2026-05-16)**:
> - TAM/SAM/SOM 산정 시 **발화 시점 웹 리서치 의무화** (시장 규모는 매분기 갱신)
> - 시장 데이터 인용 **출처 URL + 발행일 동반 필수** (단일 출처 의존 금지)
> - 학습 데이터 단독 추정 금지 — *반드시 명시*: "(주의: 학습 데이터 기준이며 변경 가능)"

---

## 1. 언제 호출되나

### Description 매칭 키워드
- *MRD*, *MRD 작성*, *시장 요구사항*, *요구사항 명세*
- *market requirement document*, *TAM SAM SOM*, *MoSCoW*
- *세그먼트 정의*, *성공 지표*, *요구사항 우선순위*

### 사용 시나리오 3가지
1. **competitor-radar 결과로 시장 요구를 정제할 때** — 9개 섹션 경쟁 분석을 6개 시장 요구사항으로 변환
2. **MVP 범위 결정 직전** — 6주차 김주영 강사의 PRD 작성 입력으로 직결
3. **투자 IR·정부지원 *시장성·필요성* 섹션 작성 시** — TAM/SAM/SOM + 요구사항이 그대로 들어감

---

## 2. 입력 (Input)

### 필수 입력
- `agents/strategy-team/outputs/01_strategy_idea_discovery_v1.md` — 사업 아이템 한 줄 정의
- `agents/strategy-team/outputs/02_research_competitive_v1.docx` — 3유형 경쟁 분석 + 1순위 Pain + 무행동 비율
- `agents/strategy-team/memory/context.md` — 절대 안 하는 것·핵심 가치

### 선택 입력
- 산업 시장 보고서 (KOSIS·산업연구원·국제 시장 데이터 등)
- 사용자 인터뷰 메모 (있으면 *Voice of Customer* 인용)

### 메모리 의존성
- 작업 직후 `agents/strategy-team/memory/decisions.md`에 *Must-have 요구사항 3개* 자동 기록
- `agents/strategy-team/memory/glossary.md`에 *세그먼트명·KPI명* 자동 추가

---

## 3. 처리 흐름 (Process) — 6개 표준 섹션

### 0-1. ⭐ 발화 시점 웹 리서치 의무 (시장 정의·KPI 산정 진입 시 필수)

**학습 데이터의 한계 보완을 위해, 본 스킬은 다음을 반드시 웹서치로 선행한다:**

| 산정 항목 | 필수 웹서치 키워드 |
|---|---|
| TAM (글로벌) | "global [domain] market size [현재 연도]", "[domain] CAGR Gartner OR IDC OR MarketsandMarkets" |
| SAM (한국) | "한국 [도메인] 시장 규모 [현재 연도] KOSIS OR 산업연구원 OR KISDI", "한국 [고객층] 인구·기업 수 통계청" |
| SOM (1~3년) | "한국 [도메인] 침투율 [현재 연도]", "[경쟁사] ARR OR 매출 [현재 연도]" |
| 정량 KPI 벤치마크 | "[도메인] SaaS 평균 MAU OR 전환율 OR 이탈률 [현재 연도]", "industry benchmark [metric] [year]" |

**출력 시 인용 규칙**:
- 모든 시장 규모는 **출처 URL + 발행일** 동반 필수
- TAM·SAM 산정은 **글로벌 1건 + 한국 1건** 최소 2건 교차
- "약 ○○조 원" 같은 추정치는 *반드시 산정 근거 (단가 × 고객 수 등)* 동반
- 학습 데이터로만 답변 시 *반드시 명시*: "(주의: 학습 데이터 기준이며 [날짜] 이후 변경 가능)"
- 산정 근거가 부족하면 *추정 보류 + 1차 데이터 수집 액션 1개* 제안

자세한 한국 시장 추정 데이터·출처는 `references/tam_sam_som_method.md`(§ 과업 0) 참조.

### 섹션 1. 시장 정의 (Market Definition)
- *우리가 노리는 시장은 무엇인가* 한 문장
- 정의 경계 (어디까지가 우리 시장이고 어디부터는 아닌가)
- TAM (Total Addressable Market) 1차 추정
- SAM (Serviceable Available Market) — 한국·도메인 한정
- SOM (Serviceable Obtainable Market) — 1~3년 현실 점유 목표

### 섹션 2. 타깃 세그먼트 (Target Segments)
- 1차 세그먼트 (Primary) — 가장 강한 Pain·가장 빠른 결제 의지
- 2차 세그먼트 (Secondary) — 확장 시 진입
- ※ 페르소나 카드는 3주차 권정선 강사 영역. 본 섹션은 *세그먼트 가설*까지만.

### 섹션 3. 핵심 문제 (Core Problems)
- 1순위 Pain (competitor-radar의 무행동 분석에서 도출) — *최우선*
- 2~3순위 Pain (대체재의 약점에서 도출)
- 각 Pain에 *현재 고객이 어떻게 해결하고 있는가* (Status quo) 명시

### 섹션 4. 요구사항 (Requirements)
- 기능 요구사항 (Functional) — 무엇을 할 수 있어야 하는가
- 비기능 요구사항 (Non-functional) — 정확도·속도·보안 등 품질 기준
- 제약 (Constraints) — 1인 운영 가능성·예산·시간 제약

### 섹션 5. 성공 지표 (Success Metrics)
- 정량 KPI 3개 — *측정 가능*해야 함 (예: 월 활성 사용자, 결제 전환율, 이탈률)
- 정성 KPI 2개 — *검증 방법*까지 명시 (예: NPS 50+, 인터뷰 80% 만족)
- 1년·3년 목표값 명시

### 섹션 6. 우선순위 (MoSCoW)

| 분류 | 정의 | 1인 기업가 운영 의미 |
|---|---|---|
| **Must** | 없으면 출시 불가 | MVP 범위 = Must만 |
| **Should** | 있어야 경쟁력 | v1.1~v1.2에 추가 |
| **Could** | 있으면 좋음 | v2 이후 |
| **Won't** | 이번 사이클 안 함 | *명시적으로 배제* (스코프 보호) |

→ 6주차 김주영 강사의 PRD가 *Must 항목만* 가져가서 본격 기획

---

## 4. 사용 프레임워크

| 단계 | 프레임워크 |
|---|---|
| 시장 정의 | TAM/SAM/SOM 3층 분석 |
| 세그먼트 | Primary·Secondary 2층 (페르소나는 3주차 위임) |
| 문제 | competitor-radar의 1순위 Pain 자동 인용 |
| 우선순위 | MoSCoW (Must·Should·Could·Won't) |
| 지표 | 정량 3 + 정성 2 (검증 방법 포함) |

---

## 5. 출력 (Output)

### 파일명·저장 경로
```
agents/strategy-team/outputs/03_mrd_v1.docx
```

### 결과물 섹션 구조 (자동 생성)
1. **시장 정의** — TAM/SAM/SOM 표 + 경계 정의
2. **타깃 세그먼트** — Primary·Secondary 2층
3. **핵심 문제** — 1~3순위 Pain + Status quo
4. **요구사항** — 기능·비기능·제약
5. **성공 지표** — 정량 3 + 정성 2 + 목표값
6. **우선순위(MoSCoW)** — Must·Should·Could·Won't 4구간
7. **다음 단계로 전달 (Hand-off)** — brand-strategy + 6주차 김주영 PRD

---

## 6. references/ 분리 자료

```
skills/MRD-writer/
├── SKILL.md (이 파일)
├── references/
│   ├── tam_sam_som_method.md      — TAM/SAM/SOM 계산법 + 한국 시장 추정 데이터 출처
│   ├── moscow_priority.md         — MoSCoW 분류 기준 + 사례
│   ├── kpi_quant_qual.md          — 정량/정성 KPI 양식 + 검증 방법
│   ├── voice_of_customer.md       — VoC 인용 양식 (인터뷰 메모 → MRD 변환)
│   └── prd_handoff_format.md      — 6주차 김주영 PRD 입력 양식
└── examples/
    └── notefriends_mrd.md         — 노트프렌즈 MRD 완성 예시
```

---

## 7. 핸드오프 (Hand-off)

**받을 사람**: `brand-strategy-designer` (2일차 블록 D) + `6주차 김주영` (MVP 기획 PRD)

**전달 자료**:
- `agents/strategy-team/outputs/03_mrd_v1.docx` 전체
- Must-have 요구사항 3개 (brand-strategy의 Value Ladder 입력)
- 세그먼트 1차 가설 (brand-strategy의 Dream Customer 입력)
- 정량 KPI 3개 (PRD 출시 성공 기준 입력)

**핸드오프 메모 양식** (결과물 마지막에 자동 추가):
```markdown
## 다음 단계로 전달 (Hand-off)

받을 사람: 04_brand_strategy_designer (1주차 내) + 6주차 김주영 (MVP PRD)

핵심 시사점 3가지:
1. Must-have 요구사항 3개: (...)
2. Primary 세그먼트 가설 1줄
3. 정량 KPI 3개 + 1년 목표값

다음 단계에서 해야 할 일:
- brand-strategy: Must 3개를 Value Ladder 무료~프리미엄 5단계에 매핑
- 6주차 김주영: Must만 가지고 MVP 기획 PRD 작성 시작

미해결 / 추가 검증 필요:
- TAM 추정의 한국 한정 데이터 보강 (3주 안 인터뷰 10건)
- (페르소나 카드는 3주차 권정선 강사 영역으로 위임)
```

---

## 8. 검증 체크리스트

- [ ] *"MRD 작성해줘"* 한 줄에 자동 발현되는가
- [ ] 6개 표준 섹션이 모두 채워지는가
- [ ] TAM/SAM/SOM이 *한국 한정 SAM* 까지 추정되는가
- [ ] MoSCoW의 Won't가 *명시적으로* 배제되는가 (스코프 보호)
- [ ] 정량 KPI 3개에 *측정 방법*까지 포함되는가
- [ ] competitor-radar의 1순위 Pain이 *핵심 문제 1번*으로 자동 매핑되는가
- [ ] 결과물이 `03_mrd_v1.docx`로 자동 저장되는가
- [ ] 6주차 김주영 PRD 입력 양식으로 자동 변환되는가

---

*작성일: 2026-05-15 | 버전: v2 (2026-05-16 웹 리서치 의무화 추가)*

### 변경 이력
- **v2 (2026-05-16)**: § 0-1 발화 시점 웹 리서치 의무 섹션 신설. TAM/SAM/SOM 산정 시 출처 URL + 발행일 강제, 글로벌·한국 최소 2건 교차 의무. `tam_sam_som_method.md` § 과업 0 연계.
- **v1 (2026-05-15)**: 초안 작성
