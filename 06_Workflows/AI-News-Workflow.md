# AI News Workflow

> Sunny AI 콘텐츠 회사의 AI 뉴스 조사·기획·제작·검수 표준 워크플로

## 1. Purpose

이 워크플로는 다음 두 종류의 요청을 고품질 AI 콘텐츠 패키지로 변환하는 전체 작업 순서를 정의한다.

1. 사용자가 특정 기사 URL을 제공하는 경우
2. 사용자가 `오늘 AI 뉴스 만들어`처럼 최신 뉴스 탐색부터 요청하는 경우

이 문서는 에이전트의 역할 설명이 아니라 **누가, 어떤 입력을 받고, 무엇을 만든 뒤, 누구에게 전달하는지**를 정의하는 실행 절차다.

## 2. Governing Documents

모든 작업은 다음 문서를 우선 적용한다.

1. `00_Company/Sunny.md`
2. `01_SOP/Content-Production-SOP.md`
3. `02_Agents/CEO-Agent.md`
4. `02_Agents/News-Agent.md`
5. `02_Agents/Editor-Agent.md`
6. `02_Agents/Planning-Agent.md`
7. `02_Agents/Writer-Agent.md`
8. `02_Agents/Design-Agent.md`
9. `02_Agents/Video-Agent.md`
10. `02_Agents/Marketing-Agent.md`
11. `02_Agents/QA-Agent.md`
12. 사용자가 현재 요청한 목표와 조건

문서 간 충돌이 있으면 사용자 요청, 안전과 권한, `Sunny.md`, SOP, 개별 에이전트 문서 순으로 판단한다.

## 3. Workflow Goal

기본 목표는 검증된 AI 뉴스 한 건을 다음 결과물로 발전시키는 것이다.

```text
뉴스 조사 브리프
편집 평가 결과
콘텐츠 기획 브리프
플랫폼별 원고
디자인 제작 브리프
영상 제작 지시서
마케팅 게시 패키지
QA 검수 보고서
사람 운영자 승인 요청
```

사용자가 일부 결과물만 원하면 필요한 단계만 실행한다.

## 4. Trigger Types

### Type A — URL 기반

```text
이 기사로 AI 콘텐츠 만들어:
https://example.com/article
```

기본 흐름:

```text
CEO → News 검증 → Editor → Planning → 필요한 제작 Agent → QA
```

### Type B — 최신 뉴스 탐색

```text
오늘 직장인이 알아야 할 AI 뉴스 3개 찾아줘.
```

기본 흐름:

```text
CEO → News 수집 → Editor 선정 → Planning → 필요한 제작 Agent → QA
```

### Type C — 주제 기반 실무 콘텐츠

```text
ChatGPT로 보고서 검토하는 방법을 콘텐츠로 만들어줘.
```

기본 흐름:

```text
CEO → News·공식 자료 확인 → Editor → Planning → 필요한 제작 Agent → QA
```

### Type D — 일부 결과물 요청

```text
이 원고로 인포그래픽 기획안만 만들어줘.
```

기본 흐름:

```text
CEO → 입력 검증 → Design → QA
```

## 5. Minimum User Input

### URL 기반 요청

```text
기사 URL:
원하는 결과물:
대상 독자:
게시 플랫폼:
희망 분량:
특별 요청:
```

### 뉴스 탐색 요청

```text
조사 기준일:
조사 기간:
관심 주제:
필요한 뉴스 수:
대상 독자:
원하는 결과물:
제외할 주제:
```

### 기본값

사용자가 별도로 지정하지 않으면 다음을 적용한다.

```text
대상 독자: AI를 업무에 활용하려는 대한민국 직장인 초보자
관점: 뉴스 소개보다 업무 영향과 활용 방법
뉴스 수: 3개 후보 중 1개 우선 제작
기본 결과물: 뉴스 브리프, 기획 브리프, YouTube 대본, Shorts 대본, QA 보고서
말투: 친절하고 차분하며 실무 중심
외부 발행: 하지 않음
```

## 6. End-to-End Flow

```text
사용자 요청
    ↓
[1] Sunny CEO — 요청 분석·프로젝트 브리프
    ↓
[2] News Agent — 원문 조사·사실 검증
    ↓
[3] Editor Agent — 가치 평가·제작 판정
    ├── REJECT → 제외 이유 보고 → 종료
    ├── HOLD → 보완 조건 기록 → 종료 또는 재조사
    ├── CONDITIONAL → News 보완 → Editor 재평가
    └── APPROVE
          ↓
[4] Planning Agent — 독자·메시지·구조 설계
          ↓
[5] Writer Agent — 플랫폼별 원고 작성
          ├── Design Agent — 이미지·카드뉴스·썸네일 설계
          └── Video Agent — 영상·자막·HeyGen 설계
                    ↓
[6] Marketing Agent — 제목·설명·게시 계획
                    ↓
[7] QA Agent — 사실·품질·권리·안전 검수
    ├── BLOCK → 즉시 중단 → 사람에게 보고
    ├── REVISE → 담당 Agent 수정 → QA 재검수
    ├── CONDITIONAL PASS → 조건 수정·확인
    └── PASS
          ↓
[8] Sunny CEO — 완료 상태와 승인 요청 정리
          ↓
[9] 사람 운영자 — 최종 승인
          ↓
[10] 전달 또는 발행
```

## 7. Stage 1 — CEO Intake

### 담당

`CEO-Agent.md`

### 입력

- 사용자 요청
- 기사 URL 또는 조사 주제
- 원하는 결과물과 플랫폼
- 일정과 특별 조건

### 작업

1. 요청 유형을 분류한다.
2. 목표, 대상 독자와 완료 기준을 정의한다.
3. 필요한 에이전트와 실행 순서를 선택한다.
4. 외부 행동과 사람의 승인 지점을 확인한다.
5. 프로젝트 ID와 저장 위치를 정한다.

### 출력

`Project-Brief.md`

### 완료 조건

- 목표와 결과물이 명확하다.
- 필요한 에이전트가 선택되었다.
- 완료 기준과 사람 승인 지점이 정의되었다.

### 다음 전달

News Agent

## 8. Stage 2 — News Research

### 담당

`News-Agent.md`

### 입력

- 프로젝트 브리프
- 기사 URL 또는 조사 키워드
- 조사 기준일과 기간
- 대상 독자

### 작업

1. 공식 원문을 우선 확인한다.
2. 신뢰할 수 있는 보조 출처를 찾는다.
3. 제목, 날짜, 제품명, 수치와 핵심 주장을 검증한다.
4. 사실, 공식 주장, 언론 보도, 분석, 추론과 미확인을 구분한다.
5. 동일 사건의 중복 기사를 제거한다.
6. 직장인 관련성과 가능한 활용을 요약한다.

### 출력

`News-Brief.md`

### 완료 조건

- 핵심 주장에 직접 연결되는 출처가 있다.
- 발표일과 적용일이 구분되어 있다.
- 미확인 정보와 충돌하는 출처가 표시되어 있다.

### 실패 분기

핵심 사실을 검증할 수 없으면 CEO에게 `RESEARCH BLOCKED`를 보고하고 제작하지 않는다.

### 다음 전달

Editor Agent

## 9. Stage 3 — Editorial Review

### 담당

`Editor-Agent.md`

### 입력

- 프로젝트 브리프
- 뉴스 조사 브리프

### 작업

1. 신뢰성, 직장인 관련성, 활용성, 시의성, 차별성과 확장성을 평가한다.
2. 100점 기준의 최종 점수를 계산한다.
3. 콘텐츠의 실무적 각도와 위험 요소를 정리한다.
4. APPROVE, CONDITIONAL, HOLD, REJECT 중 하나로 판정한다.

### 출력

`Editorial-Review.md`

### 분기

| 판정 | 다음 행동 |
|---|---|
| APPROVE | Planning Agent로 전달 |
| CONDITIONAL | News Agent가 부족한 근거 보완 후 재평가 |
| HOLD | 조건과 재검토 시점을 기록하고 중지 |
| REJECT | 제외 이유를 CEO가 사용자에게 보고 |

### 완료 조건

- 점수와 판정에 구체적인 근거가 있다.
- 핵심 메시지 후보와 피해야 할 주장이 정리되어 있다.

## 10. Stage 4 — Content Planning

### 담당

`Planning-Agent.md`

### 입력

- 프로젝트 브리프
- 뉴스 조사 브리프
- 편집 평가 결과

### 작업

1. 핵심 독자와 독자의 문제를 구체화한다.
2. 콘텐츠 목적을 하나로 정한다.
3. 한 문장 핵심 메시지를 만든다.
4. Hook, What Changed, Why It Matters, How to Use, Limits, Action, Summary 구조를 설계한다.
5. 실무 사례와 플랫폼별 결과물을 설계한다.
6. Writer, Design, Video Agent의 제작 지시를 작성한다.

### 출력

`Content-Plan.md`

### 완료 조건

- 핵심 독자, 문제, 메시지와 다음 행동이 명확하다.
- 검증된 사실이 콘텐츠 구성에 연결되어 있다.
- 제작 에이전트가 추측 없이 작업할 수 있다.

### 다음 전달

Writer Agent

## 11. Stage 5 — Writing

### 담당

`Writer-Agent.md`

### 입력

- 프로젝트 브리프
- 콘텐츠 기획 브리프
- 뉴스 조사 브리프와 출처

### 작업

요청된 결과물만 작성한다.

- YouTube 본편 대본
- Shorts 대본
- 블로그 원고
- 뉴스레터
- LinkedIn 또는 SNS 게시문

### 출력

`Writing-Package.md`

### 완료 조건

- 핵심 메시지가 처음부터 끝까지 일관된다.
- 사실과 해석이 구분되어 있다.
- 초보자에게 쉬운 표현과 실무 사례가 있다.
- 출처와 사람의 확인 사항이 표시되어 있다.

### 다음 전달

- 시각 콘텐츠가 필요하면 Design Agent
- 영상 콘텐츠가 필요하면 Video Agent
- 텍스트 결과물만 필요하면 QA Agent 또는 Marketing Agent

## 12. Stage 6A — Design

### 담당

`Design-Agent.md`

### 입력

- 콘텐츠 기획 브리프
- 최종 원고
- 정확한 숫자, 날짜와 출처
- 플랫폼과 이미지 규격

### 작업

요청에 필요한 결과만 설계한다.

- 인포그래픽
- 카드뉴스
- 네 컷 만화
- YouTube 썸네일
- 이미지 생성 프롬프트

### 출력

`Design-Brief.md`

### 완료 조건

- 한 화면에 하나의 핵심 메시지가 있다.
- 이미지 문구, 레이아웃과 제작 지시가 명확하다.
- 출처, 접근성과 권리 확인 사항이 포함되어 있다.

### 다음 전달

- 영상에서 사용할 경우 Video Agent
- 이미지 게시물일 경우 Marketing Agent

## 13. Stage 6B — Video

### 담당

`Video-Agent.md`

### 입력

- 최종 원고
- 콘텐츠 기획 브리프
- 디자인 제작 브리프와 시각 자산
- 플랫폼, 목표 길이와 제작 도구

### 작업

- 장면별 시간 배분
- 내레이션 다듬기
- 화면, B-roll과 자막 설계
- 화면 녹화와 제작 자산 목록
- HeyGen 입력용 장면별 대본
- 편집 및 검수 체크리스트

### 출력

`Video-Brief.md`

### 완료 조건

- 모든 장면의 목적, 내레이션, 화면과 자막이 정의되어 있다.
- 개인정보, 기밀, 저작권과 AI 생성 위험이 표시되어 있다.

### 다음 전달

Marketing Agent

## 14. Stage 7 — Marketing Package

### 담당

`Marketing-Agent.md`

### 입력

- 최종 원고 또는 콘텐츠
- 디자인 및 영상 결과
- 대상 독자와 핵심 메시지
- 플랫폼과 CTA 목적
- 출처와 필요한 고지

### 작업

- 제목 후보와 추천안
- 썸네일 조합 검토
- 설명, 챕터, 태그와 고정 댓글
- 플랫폼별 게시문
- 배포 일정
- 성과 측정 지표

### 출력

`Marketing-Package.md`

### 완료 조건

- 제목과 썸네일이 콘텐츠를 과장하지 않는다.
- 출처, 링크, CTA와 고지가 정확하다.
- 게시 설정과 측정 계획이 준비되어 있다.

### 다음 전달

QA Agent

## 15. Stage 8 — QA

### 담당

`QA-Agent.md`

### 입력

- 프로젝트 브리프
- 모든 단계의 최신 결과물
- 공식 원문과 출처
- 게시 패키지

### 작업

1. 핵심 사실과 출처를 원문에 대조한다.
2. 승인 범위와 핵심 메시지의 일관성을 확인한다.
3. 문장, 디자인, 영상, 제목과 CTA를 검수한다.
4. 개인정보, 기밀, 저작권, 초상권, 상표와 AI 생성 위험을 확인한다.
5. 문제를 Critical, High, Medium, Low로 분류한다.
6. PASS, CONDITIONAL PASS, REVISE, BLOCK 중 하나로 판정한다.

### 출력

`QA-Report.md`

### 분기

```text
PASS
→ CEO 완료 검토

CONDITIONAL PASS
→ 지정된 경미한 수정
→ QA 확인

REVISE
→ 담당 Agent 수정
→ QA 재검수

BLOCK
→ 전체 작업 중단
→ CEO와 사람 운영자에게 즉시 보고
```

## 16. Stage 9 — CEO Completion Review

### 담당

`CEO-Agent.md`

### 입력

- 프로젝트 브리프
- 최종 결과물 전체
- QA 검수 보고서

### 작업

1. 사용자 요청 결과물이 모두 준비되었는지 확인한다.
2. QA의 필수 문제가 해결되었는지 확인한다.
3. 최종 결과물 위치와 사용 방법을 정리한다.
4. 외부 발행에 필요한 사람 승인 항목을 표시한다.
5. 프로젝트 상태를 `READY` 또는 `BLOCKED`로 정한다.

### 출력

`CEO-Completion-Report.md`

### 완료 조건

- 결과물, QA 상태와 남은 작업이 명확하다.
- 사용자가 다음에 할 행동이 한 단계로 안내되어 있다.

## 17. Stage 10 — Human Approval

사람 운영자는 다음을 최종 확인한다.

- 콘텐츠 내용과 브랜드 방향
- 제목과 썸네일
- 사실, 출처와 필요한 고지
- 개인정보, 기밀과 사용 권리
- 공개 범위와 게시 시간
- 링크와 CTA

명시적으로 승인하기 전에는 외부 게시, 예약 게시, 광고, 결제 또는 연락을 수행하지 않는다.

## 18. Revision Loop

QA 또는 사람 운영자가 수정을 요청하면 문제 유형에 따라 되돌린다.

| 문제 | 되돌릴 Agent |
|---|---|
| 출처·날짜·수치 | News Agent |
| 주제 가치·승인 범위 | Editor Agent |
| 독자·핵심 메시지·구성 | Planning Agent |
| 문장·대본·게시글 | Writer Agent |
| 이미지·썸네일·접근성 | Design Agent |
| 장면·내레이션·자막 | Video Agent |
| 제목·설명·CTA·배포 | Marketing Agent |

수정 후에는 관련 결과물을 새 버전으로 저장하고 QA Agent가 다시 확인한다.

## 19. File and Folder Structure

프로젝트별 결과물은 다음 구조를 권장한다.

```text
04_Content/
└── YYYY/
    └── YYYY-MM-DD_topic-slug/
        ├── 00_Project-Brief.md
        ├── 01_News-Brief.md
        ├── 02_Editorial-Review.md
        ├── 03_Content-Plan.md
        ├── 04_Writing-Package.md
        ├── 05_Design-Brief.md
        ├── 06_Video-Brief.md
        ├── 07_Marketing-Package.md
        ├── 08_QA-Report.md
        ├── 09_CEO-Completion-Report.md
        └── assets/
```

필요하지 않은 단계의 파일은 만들지 않아도 된다.

## 20. Naming Rules

### 프로젝트 폴더

```text
YYYY-MM-DD_topic-slug
```

예시:

```text
2026-08-02_openai-update
```

### 결과물 파일

```text
NN_Document-Name_v0.1.md
```

예시:

```text
04_Writing-Package_v0.1.md
```

### 버전

- `v0.1`: 최초 초안
- `v0.2`: 내부 수정본
- `v0.9`: 발행 직전 후보
- `v1.0`: 사람 운영자가 승인한 최종본

기존 버전을 덮어쓰지 않고 중요한 수정은 새 버전으로 저장한다.

## 21. Project Status File

각 콘텐츠 프로젝트는 상태 문서를 유지한다.

```markdown
# Project Status

- 프로젝트 ID:
- 현재 상태: INTAKE | RESEARCH | EDITORIAL REVIEW | PLANNING | PRODUCTION | MARKETING | QA | REVISION | AWAITING APPROVAL | READY | PUBLISHED | BLOCKED
- 완료 단계:
- 진행 중인 Agent:
- 다음 Agent:
- 최신 결과물:
- 미해결 문제:
- 사람의 결정 필요:
- 마지막 업데이트:
```

## 22. Required Handoff Fields

모든 에이전트의 전달 문서에는 최소한 다음이 포함되어야 한다.

```text
프로젝트 ID
담당 Agent
작업 목적
입력 자료
완료 결과
핵심 결정
출처
미확인 사항
위험과 주의사항
다음 Agent
사람 승인 필요 여부
버전과 작성일
```

이 정보가 없으면 CEO Agent는 다음 단계로 넘기지 않고 보완을 요청한다.

## 23. Quick Execution Command

다음 명령 형식으로 워크플로를 시작할 수 있다.

### URL 기반

```text
Sunny, 아래 기사로 AI 뉴스 콘텐츠 프로젝트를 시작해.

기사 URL: [URL]
대상 독자: 대한민국 직장인 AI 초보자
결과물: YouTube 대본, Shorts 대본, 인포그래픽 기획안
플랫폼: YouTube
목표: 뉴스를 쉽게 설명하고 실무 활용 방법까지 제시
외부 게시: 하지 않음

AI-News-Workflow.md의 순서를 따르고 각 단계의 결과와 QA 판정을 보여줘.
```

### 최신 뉴스 탐색

```text
Sunny, 오늘 직장인이 알아야 할 AI 뉴스 콘텐츠 프로젝트를 시작해.

조사 기준일: [YYYY-MM-DD]
조사 기간: 최근 7일
후보 수: 5개
최종 선정: 1개
대상 독자: 대한민국 직장인 AI 초보자
결과물: 뉴스 브리프, YouTube 대본, Shorts 대본
외부 게시: 하지 않음

AI-News-Workflow.md의 순서를 따르고 공식 원문을 우선 사용해.
```

## 24. Manual Test Procedure

자동화 전에 기사 한 건으로 수동 테스트한다.

### 테스트 순서

1. 신뢰할 수 있는 공식 AI 발표 URL 한 개를 준비한다.
2. Quick Execution Command에 URL을 넣는다.
3. CEO Agent가 프로젝트 브리프를 만드는지 확인한다.
4. News Agent가 원문, 날짜와 핵심 주장을 검증하는지 확인한다.
5. Editor Agent가 점수와 판정을 제공하는지 확인한다.
6. Planning Agent가 핵심 독자와 메시지를 정의하는지 확인한다.
7. Writer Agent가 요청한 원고만 작성하는지 확인한다.
8. 필요한 Design 또는 Video 브리프가 생성되는지 확인한다.
9. QA Agent가 문제 등급과 최종 판정을 제공하는지 확인한다.
10. 결과물을 `04_Content`의 프로젝트 폴더에 저장한다.
11. 반복되거나 누락된 내용을 에이전트 문서와 SOP에 반영한다.

### 테스트 성공 기준

- 모든 핵심 사실에 원문이 연결된다.
- 각 에이전트의 결과와 역할이 중복되지 않는다.
- 다음 단계에 필요한 정보가 누락되지 않는다.
- 직장인의 실무 활용 방법이 포함된다.
- QA 결과와 수정 경로가 명확하다.
- 외부 게시 없이 최종 콘텐츠 패키지가 준비된다.

## 25. Stop Conditions

다음 상황에서는 워크플로를 중단하고 CEO Agent와 사람 운영자에게 알린다.

- 핵심 원문이나 사실을 검증할 수 없다.
- 개인정보 또는 회사 기밀이 포함되어 있다.
- 저작권, 초상권, 음성권 또는 상표 위험이 해결되지 않았다.
- 실제 인물 또는 사건을 허위로 표현해야 한다.
- 의료, 법률, 금융 등 전문 판단이 필요하다.
- QA Agent가 BLOCK 판정을 내렸다.
- 외부 게시, 결제, 연락 또는 설정 변경 권한이 없다.
- 사용자의 요청이 Sunny의 품질·안전 원칙과 충돌한다.

## 26. Completion Criteria

다음 조건을 모두 충족하면 프로젝트 상태를 `READY`로 변경한다.

- [ ] 사용자가 요청한 결과물이 모두 준비되었다.
- [ ] 핵심 사실, 날짜, 수치와 출처가 검증되었다.
- [ ] Editor Agent가 제작을 승인했다.
- [ ] 콘텐츠의 독자, 핵심 메시지와 실무 활용이 분명하다.
- [ ] 필요한 원고, 디자인, 영상과 게시 패키지가 준비되었다.
- [ ] QA Agent의 Critical 및 High 문제가 해결되었다.
- [ ] 개인정보, 기밀과 권리 위험이 해결되었다.
- [ ] CEO Agent가 완료 보고서를 작성했다.
- [ ] 외부 발행 전 사람 운영자의 최종 확인 항목이 표시되었다.

`READY`는 발행 준비 완료를 뜻하며 자동 발행을 의미하지 않는다.

## 27. Version History

| Version | Date | Changes |
|---|---|---|
| v0.1 | 2026-08-02 | AI 뉴스의 입력, 에이전트별 단계, 분기, 저장 구조, 실행 명령과 수동 테스트 절차 최초 작성
