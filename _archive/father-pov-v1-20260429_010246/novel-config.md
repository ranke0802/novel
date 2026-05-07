# novel-config.md (자동 생성 초안 - 검토 후 수정 가능)

## 프로젝트 기본 정보

```yaml
project:
  name: "사실 마왕이 하려던 건 이게 아니었는데"
  internal_working_title: "마왕의 딸은 아빠가 지킨다"
  target_platform: "문피아"
  target_genre: "육아 판타지, 오두막 디펜스 성장물, 마왕 딸 보호자물"
  episode_dir: "episode/"
  work_dir: "revision/"
  design_dir: "design/"
```

## 설정문서 매핑

### 공통 문서

| 문서 키 | 경로 | 용도 |
|---|---|---|
| character_core | design/사실 마왕이 하려던 건 이게 아니었는데_캐릭터시트.md | 캐릭터 핵심 정의, 인물 관계, 고유 설정 |
| character_detail | design/사실 마왕이 하려던 건 이게 아니었는데_캐릭터시트.md | 보이스표, 비언어 태그, 관계 변화 |
| dialogue_dna | design/사실 마왕이 하려던 건 이게 아니었는데_캐릭터시트.md#dialogue-dna | Dialogue DNA. 캐릭터시트 내 섹션 |
| bootstrap | design/사실 마왕이 하려던 건 이게 아니었는데_부트스트랩.md | 세계관, 마법 규칙, 매크로 수치 |
| writing_rules | CLAUDE.md | 집필 규칙 바이블 |

### EP 범위별 설정문서

| EP 범위 | 레이블 | 플롯 가이드 경로 | 세부 플롯 가이드 (선택) | 세부 캐릭터 시트 (선택) |
|---|---|---|---|---|
| EP001~EP003 | 프롤로그 - 성공이군 | design/사실 마왕이 하려던 건 이게 아니었는데_플롯훅가이드.md | design/사실 마왕이 하려던 건 이게 아니었는데_세부플롯훅가이드_1~25화.md | design/사실 마왕이 하려던 건 이게 아니었는데_세부캐릭터시트_1~25화.md |
| EP004~EP025 | 아크1 - 오두막에 태어난 재앙 | design/사실 마왕이 하려던 건 이게 아니었는데_플롯훅가이드.md | design/사실 마왕이 하려던 건 이게 아니었는데_세부플롯훅가이드_1~25화.md | design/사실 마왕이 하려던 건 이게 아니었는데_세부캐릭터시트_1~25화.md |
| EP026~EP050 | 아크2 - 숲속 요새의 아버지 | design/사실 마왕이 하려던 건 이게 아니었는데_플롯훅가이드.md | | |
| EP051~EP100 | 아크3 - 새 용사와 마왕의 아이 | design/사실 마왕이 하려던 건 이게 아니었는데_플롯훅가이드.md | | |
| EP101~EP150 | 아크4 - 전대 용사의 귀환 | design/사실 마왕이 하려던 건 이게 아니었는데_플롯훅가이드.md | | |
| EP151~EP200 | 아크5 - 아버지는 왕국을 버린다 | design/사실 마왕이 하려던 건 이게 아니었는데_플롯훅가이드.md | | |
| EP201~EP250 | 아크6 - 성역이 무너진 자리 | design/사실 마왕이 하려던 건 이게 아니었는데_플롯훅가이드.md | | |

### 보조 참조

| 문서 키 | 경로 | 용도 |
|---|---|---|
| proposal | 사실 마왕이 하려던 건 이게 아니었는데_제안서.md | 확정 선택안 |
| concept_analysis | _workspace/00_concept_analysis.md | 큰 설계 컨셉 복원 |
| research_r1 | _workspace/00_research/R1_장르DNA.md | 장르 DNA |
| research_r2 | _workspace/00_research/R2_플랫폼전략.md | 문피아 플랫폼 전략 |
| research_r3 | _workspace/00_research/R3_업계구조.md | 왕국/성역/오두막 디펜스 구조 |
| research_r4 | _workspace/00_research/R4_사건연표.md | 장기 사건 연표 |
| research_r5 | _workspace/00_research/R5_기존작분석.md | 유사 장르 포지셔닝 |
| research_r6 | _workspace/00_research/R6_갈등사례.md | 갈등 유형 |

### EP 범위별 리서치 참조

| 문서 키 | EP 범위 | 경로 | 용도 |
|---|---|---|---|
| research_r7 | EP001~EP025 | _workspace/00_research/R7_전문지식_1~25화.md | 오두막 결계/마석/육아 마법/성물 감응 디테일 |
| research_r8 | EP001~EP025 | _workspace/00_research/R8_사건상세_1~25화.md | 무료 구간 사건 상세 타임라인 |

## 에이전트별 문서 매핑

### rule-checker

| 축 | 참조 문서 키 | 용도 |
|---|---|---|
| VOICE | character_detail | 보이스표, Dialogue DNA 대조 |
| TITLE | character_detail | 호칭과 관계 단계 확인 |
| BANNED | bootstrap | 보존 가드레일 위반 확인 |
| TRANS | - | grep 기반 |
| SILENCE | - | 카운트 기반 |

### story-analyst

| 축 | 참조 문서 키 | 용도 |
|---|---|---|
| TIMELINE | plot_by_ep, bootstrap | EP별 사건 순서, 유리카 성장 단계 |
| NUMBER | plot_by_ep, bootstrap | 화수, 결계 단계, 시점 수치 |
| PLAUSIBILITY | bootstrap, character_core | 마법 규칙, 캐릭터 능력 정합성 |
| SCENE | 직전 2화 | 화간 연속성 |
| UNIFORM | 직전 2화 | 패턴 대조 |

### platform-optimizer

| 축 | 참조 문서 키 | 용도 |
|---|---|---|
| HOOK | plot_by_ep | 회차 말미 훅과 감정 강도 |
| OPENING | plot_by_ep | 회차별 도입 구조 |
| MOBILE | research_r2 | 문피아 독자 최적화 |
| SUMMARY | - | 정량 측정 기반 |

### alive-enhancer

| 축 | 참조 문서 키 | 용도 |
|---|---|---|
| ALIVE-1 | character_detail | 대화 DNA |
| ALIVE-2 | character_detail | 비언어 태그 |
| ALIVE-3 | character_core | 조연별 고유 긴장점 |
| ALIVE-4 | character_core | 관계 곡선 |

## 보존 가드레일

1. 유리카는 악한 마왕 환생이 아니라 위험한 마력 회로를 가진 아이로 유지한다.
2. 카엘은 딸의 위험성을 부정하지 않는다. 위험을 인정한 상태에서 처분 명령을 거부한다.
3. 왕국과 성역은 단순 악역이 아니다. 공공 안전, 전쟁 트라우마, 질서 유지 논리를 가진다.
4. 오두막 디펜스는 전투 반복이 아니라 생활, 육아, 자원, 관계 확장의 시스템이다.
5. 카엘의 전대 용사성은 단계적으로 드러난다. 초반부터 모든 진실을 알지 않는다.
6. 후반 비극은 부녀 애착이 충분히 쌓인 뒤 증폭한다.
7. 새 로맨스 라인을 만들지 않는다. 중심 정서는 사별, 부녀, 책임, 선택이다.
8. 마왕의 `성공`은 유리카를 악으로 만드는 계획이 아니라 성역 희생 순환을 끊을 가능성으로 회수한다.

## 수치 교차검증 정본 우선순위

1. plot_by_ep - EP별 확정 수치와 사건
2. bootstrap - 매크로 수치, 세계관 규칙
3. character_core - 캐릭터 나이, 관계, 능력 한계
4. verification - 검증 완료 수치 기록
5. 직전 에피소드 - 서사 연속성

## 핵심 전환 포인트

- EP001: 마왕의 `"..성공이군"`과 카엘의 악몽.
- EP003: 유리카 탄생 후 첫 마물 방어.
- EP025: 유리카 결계 사고와 성역 감지. 유료 전환 핵심.
- EP050: 오두막 2차 요새화와 성역 체포 작전 격퇴.
- EP100: 유리카의 마왕 잔향 공식 판정.
- EP150: 카엘이 전대 용사 아르덴의 이름으로도 딸 처분을 거부.
- EP200: 성역핵 절단, 카엘이 왕국보다 딸을 선택.
- EP250: 유리카의 새 보호 결계와 비극적 승리.

## 카타르시스 유형

- 딸을 위협하는 것을 아버지가 막아내는 보호 카타르시스.
- 오두막이 결계, 함정, 마석 회로, 망명자 거점으로 성장하는 디펜스 쾌감.
- 유리카의 귀여운 사고가 세계관급 마법 떡밥으로 뒤집히는 캐릭터 훅.
- 전대 용사였던 아버지가 왕국의 영웅이 아니라 딸의 아버지로 선택하는 비극적 금기 쾌감.

## 커스텀 진단 축

```yaml
custom_axis:
  name: MAGIC_DEFENSE_LOGIC
  description: "오두막 결계/마석/성물 감응/유리카 마력 규칙의 정합성 검증"
  agent: story-analyst
```

- **정본**: `bootstrap`, `plot_by_ep`, `research_r3`
- **탐지 키워드**: 결계, 마석, 성물, 보라빛, 마왕 잔향, 성검, 봉인, 성역핵
- **VIOLATION**: 현재 EP 성장 단계에서 불가능한 결계/마법을 설명 없이 사용, 유리카가 의도적 악의로 살해/지배, 성물 감응 규칙을 무시
- **ALLOWED**: 유리카의 무의식 사고, 카엘의 몸에 남은 전투 본능, 후반 정체 공개 이후의 성검식 사용

```yaml
custom_axis:
  name: FATHER_DAUGHTER_ETHIC
  description: "부녀 중심 윤리와 왕국/성역 갈등의 정합성 검증"
  agent: story-analyst
```

- **정본**: `bootstrap`, `character_core`, `research_r6`
- **탐지 키워드**: 딸, 아빠, 처분, 희생, 왕국, 성역, 마왕의 아이
- **VIOLATION**: 카엘이 충분한 압박 없이 유리카를 포기, 왕국/성역이 이유 없는 단순 악으로만 행동, 유리카가 아이답지 않은 악역 의식으로 행동
- **ALLOWED**: 후반부에서 카엘의 금기 선택, 왕국 인물의 공공 안전 논리, 유리카의 죄책감과 공포 반응

## 침묵 패턴 예외

- 카엘 베른: 감정을 생활 행동으로 숨기는 캐릭터. 다만 회차 내 핵심 감정선은 행동으로 반드시 드러내야 한다.
- 엘리오라: 죄책감 때문에 말문이 끊기는 장면 허용. 반복 사용 시 회상/기도문으로 변주한다.

## 핵심 수치 빠른 참조

- 총 예상 분량: 250화 내외
- 외부 작품 제목: 사실 마왕이 하려던 건 이게 아니었는데
- 내부 초기 가제: 마왕의 딸은 아빠가 지킨다
- 회차 분량: 5,000~6,500자
- 무료 구간: EP001~EP025
- 유료 전환: EP025 말 성역 감지, EP026 칼리아스 보고
- 마왕 토벌: 본편 7년 전
- 유리카 시작 나이: 출생 직후
- 카엘 시작 나이: 34세
- 주요 스케일: 오두막 -> 숲/마을 -> 변경/왕국 -> 성역 -> 세계 질서
