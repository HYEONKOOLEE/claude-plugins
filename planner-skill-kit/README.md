# planner-skill-kit

> 1인 창업가·소규모 사업가를 위한 **1주차 컨설팅 SOP 5종 스킬 패키지**

## 무엇을 하나요

5종 스킬이 **체인**으로 연결되어 1주(5일) 안에 사업의 핵심 골격을 자동으로 정제합니다.

```
1일차: idea-discovery          → 사업 아이디어 발굴·정의·Go/No-Go
2일차: competitor-radar        → 경쟁분석 + 무행동(No-action) 진단
3일차: mrd-writer              → 시장 요구사항 6섹션 (TAM/SAM/SOM·세그먼트·KPI·MoSCoW)
4일차: brand-strategy-designer → Hook·미션·비전·Value Ladder·30일 플랜
5일차: proposal-writer         → 정부지원·B2B·IR 제안서 9섹션 + 5프레임워크
```

각 스킬의 산출물이 다음 스킬의 입력으로 자동 전달되어, **재작업 없이 5일 안에 사업계획서 1차본**까지 도달합니다.

## 누가 쓰나요

- 1인 창업가·소상공인·예비창업자
- 정부지원사업 신청을 준비 중인 1인·소규모 사업가
- 사업 아이템이 흐릿하거나 후보 여러 개 중 결정 못 하는 분
- B2B 제안서·IR 자료를 빠르게 1차본까지 가고 싶은 분

## 포함된 스킬 5종

| # | 스킬명 | 트리거 키워드 (한국어 전용) | 출력 |
|---|---|---|---|
| 1 | **idea-discovery** | "사업 아이디어 발굴", "사업 아이템", "창업 아이템명", "SCAMPER", "이키가이" | `01_strategy_idea_discovery_v1.md` |
| 2 | **competitor-radar** | "경쟁 분석", "시장 조사", "대체재 분석", "무행동 분석", "진입 장벽" | `02_research_competitive_v1.md` |
| 3 | **mrd-writer** | "MRD 작성", "시장 요구사항", "TAM SAM SOM", "MoSCoW" | `03_mrd_v1.md` |
| 4 | **brand-strategy-designer** | "브랜드 전략", "미션 비전", "네이밍 슬로건", "Hook", "Value Ladder" | `04_brand_strategy_v1.md` |
| 5 | **proposal-writer** | "신청서", "제안서", "사업계획서", "정부지원", "PESTEL", "SWOT", "KSF" | `05_proposal_{종류}_{날짜}_v1.md` |

> ⚠️ **트리거는 한국어 전용**입니다. "아이디어 디스커버리"(한영 혼합) → 매칭 실패. "사업 아이디어 발굴"(한국어 명확) → OK.

## 설치는 어떻게 하나요

이 `.plugin` 파일은 단독 설치 가능하지만, **`planner-skill-kit-v7.4.zip` 스타터킷**과 함께 받으시면 자동 설치 스크립트·메모리 초기화 스크립트가 동봉되어 **3분 환경 셋팅**으로 끝납니다.

자세한 설치 가이드는 스타터킷 zip 루트의 `README.md` 참조.

**단독 설치 (Cowork)**: Settings → Plugins → "로컬 플러그인 업로드" → 이 파일 선택
**단독 설치 (Claude Code CLI)**: `/plugin marketplace add <폴더경로>` → `/plugin install`

## 작업 폴더 구조 (v7.2 이후 — 주차별 팀 폴더)

`init-memory` 스크립트가 본인 사업 폴더에 자동 생성:

```
[본인 사업 폴더]/
└── agents/strategy-team/                ← 1주차 전략기획팀
    ├── memory/
    │   ├── context.md                   ← 사업 정의·미션·Won't 7개 (가장 중요)
    │   ├── decisions.md                 ← 누적 의사결정 로그
    │   └── glossary.md                  ← 본인 사업 용어집
    ├── outputs/                          ← 5종 산출물 자동 저장
    └── skills/                           ← SKILL.md 5종 사본 (검토용)
```

차주에는 `agents/marketing-team/`, `agents/finance-team/` 등이 *동일 사업 폴더 안에 공존* 가능한 구조.

플러그인 안에는 `memory/` 3종 템플릿(`context.template.md`·`decisions.template.md`·`glossary.template.md`)이 들어 있어, `init-memory` 스크립트가 이를 복사·이름변경합니다.

## 5종 스킬 의존성 체인

```
context.md (memory)
   ↓
[idea-discovery]
   ↓ 01_strategy_idea_discovery_v1.md
[competitor-radar]
   ↓ 02_research_competitive_v1.md
   ├──→ [mrd-writer]
   │       ↓ 03_mrd_v1.md
   │       ↓
   └──→ [brand-strategy-designer]
           ↓ 04_brand_strategy_v1.md
           ↓
        [proposal-writer]
           ↓ 05_proposal_{종류}_{날짜}_v1.md (최종)
```

> ⚠️ `brand-strategy-designer`는 `mrd-writer` 출력을 입력으로 받습니다. 순서 지켜 진행하세요.

## 발화 시점 웹 리서치 의무 (§ 0-1)

5개 스킬 모두 **트렌드·정책·경쟁사·TAM/SAM/SOM·사업공고**는 학습 데이터 단독 답변 금지. 출처 URL + 발행일 동반, 최소 3개 카테고리 교차 검증. `proposal-writer`는 사업공고 원문을 신청 직전 1회 재확인합니다.

## ROI 예상

| 스킬 | Before (도구) | After (Skill) |
|---|---|---|
| idea-discovery | 5~10시간 | 30분 |
| competitor-radar | 4시간 | 30분 |
| mrd-writer | 6시간 | 40분 |
| brand-strategy-designer | 8~12시간 | 50분 |
| proposal-writer | 3시간 | 30분 |

**1주차 SOP 전체**: 26~36시간 → **약 3시간** (~90% 시간 절감)

## 강의·코호트에서 쓸 때

- 수강생 각자가 자기 PC에 `planner-skill-kit-v7.4.zip` 받아 4단계 셋팅 (3분)
- 1일 1스킬씩 자연어 한 줄로 진행
- 각 일차 산출물은 본인 사업 폴더의 `agents/strategy-team/outputs/`에 자동 저장

## 라이선스·재배포

플러그인 본인 사용·강의용 자유 배포. 상업적 재판매 시 작성자 사전 동의 필요.

---

*작성일: 2026-05-25 | 버전: v7.4*
