# novel-config.md 작성 가이드

창작/윤문/재작성 스킬이 프로젝트별 설정을 읽어오는 **프로젝트 설정 파일** 작성법.
각 소설 프로젝트 루트에 `novel-config.md`를 만들고, 파일 전체를 아래 YAML 구조로 작성한다.
마크다운 표를 섞지 않는다.

---

## 표준 YAML 스키마

```yaml
project:
  name: "소설 제목"
  target_platform: "문피아"           # 타겟 플랫폼 (문피아, 네이버시리즈, 카카오페이지, 리디, 조아라, 노벨피아만 지원)
  target_genre: "현대판타지"           # 타겟 장르
  episode_dir: "episode/"           # 에피소드 파일 위치 (ep001.md, ep002.md ...)
  work_dir: "revision/"             # fix_plan.md, learnings.md 등 윤문 작업 파일 위치
  design_dir: "design/"             # 설정문서 디렉토리

design_documents:
  bootstrap: "design/bootstrap.md"
  character_core: "design/character_sheet.md"
  character_detail: "design/character_sheet_detail.md"
  dialogue_dna: "design/character_sheet.md#dialogue-dna" # 선택. 없으면 character_detail로 대체
  writing_rules: "CLAUDE.md"                              # 선택. 없으면 프로젝트 루트 CLAUDE.md
  web_novel_guide: "design/web-novel-guide.md"            # 선택
  verification: "design/verification.md"                  # 선택
  plot_macro: "design/plot-hook-guide.md"                 # 선택

ep_range_table:
  - range: "EP001~EP026"
    label: "1막"
    plot_guide: "design/plot-hook-guide_act1.md"
    plot_guide_detail: ""                 # 선택. 작은 설계 산출물이 있으면 우선 사용
    character_detail: ""                  # 선택. 범위 전용 캐릭터 상세 문서
  - range: "EP027~EP076"
    label: "2막"
    plot_guide: "design/plot-hook-guide_act2.md"
    plot_guide_detail: "design/plot-hook-guide_act2_detail_ep027-076.md"
    character_detail: "design/character_sheet_detail_ep027-076.md"

guard_rails:
  - "전문성 밀도를 훼손하지 않는다"
  - "작품 고유 분위기를 유지한다"

number_source_priority:
  - ep_range_table[].plot_guide_detail
  - ep_range_table[].plot_guide
  - design_documents.bootstrap
  - design_documents.verification
  - previous_episode

key_turning_points:
  - ep: "EP025"
    purpose: "1막 종결 및 유료 전환 유도"
    min_hook_intensity: 4

custom_axes: {}

silence_exceptions:
  - "캐릭터Y"

create:
  draft_chars: "6000-10000"
  final_chars: "5000-8000"
  dialogue_ratio: "40-60%"
  max_scenes: 4
  continuity_lookback: 2
  hook_targets:
    opening_intensity: 4
    ending_intensity: 5

rewrite:
  character_dialogue_dna: "design/character-dialogue-dna.md" # 선택. 없으면 design_documents.dialogue_dna 사용
  work_dir: "revision/"                                      # 선택. 없으면 project.work_dir 사용
  guard_rails:
    - "경악 방식 교체 불가"
```

> `project.target_platform`에는 canonical name만 기록한다. 예: `문피아`, `카카오페이지`
> 모든 경로는 `novel-config.md`가 있는 프로젝트 루트 기준 상대 경로다.

## 필수 검증 규칙

- `project.target_platform`은 문피아, 네이버시리즈, 카카오페이지, 리디, 조아라, 노벨피아 중 하나여야 한다.
- `project.episode_dir`, `project.work_dir`, `project.design_dir`는 비어 있으면 안 된다.
- `design_documents.bootstrap`, `design_documents.character_core`, `design_documents.character_detail`은 파일이 존재해야 한다.
- `ep_range_table`은 최소 1개 행이 있어야 하며, 각 행의 `range`는 `EP001~EP026` 형식이어야 한다.
- `ep_range_table[].plot_guide`는 파일이 존재해야 한다.
- EP 범위는 겹치면 안 된다.
- 대상 EP가 어떤 범위에도 속하지 않으면 마지막 범위의 문서를 사용하고 `[범위초과]` 경고를 출력한다.
- `plot_guide_detail` 또는 범위 전용 `character_detail`이 있고 파일이 존재하면 공통 문서보다 우선 사용한다.

> **플랫폼별 기준**: `_workspace/platform-guide-{platform}.md` 파일이 있으면 platform-optimizer가 해당 플랫폼의 특화 기준을 자동 적용한다. 플랫폼은 문피아, 네이버시리즈, 카카오페이지, 리디, 조아라, 노벨피아만 허용한다. 예: `_workspace/platform-guide-문피아.md`, `_workspace/platform-guide-munpia.md`, `_workspace/platform-guide-kakaopage.md`
> 문피아 타겟에서 프로젝트 플랫폼 가이드가 없으면 `${CLAUDE_PLUGIN_ROOT}/skills/design/references/munpia-platform-seed.md`를 기본 기준으로 사용한다.
> 문피아 타겟의 운영 감각은 주 5~7일 연재와 5,000자 전후 회차지만, 실제 글자수 게이트는 항상 novel-config.md의 `create.final_chars`를 우선한다.

## 참조 키 의미

| 키 | 용도 |
|----|------|
| `design_documents.character_core` | 캐릭터 핵심 정의, 인물 관계, 고유 설정 |
| `design_documents.character_detail` | 보이스표, 호칭표, 비언어 태그, 관계 변화 |
| `design_documents.dialogue_dna` | Dialogue DNA. 없으면 character_detail로 대체 |
| `design_documents.bootstrap` | 매크로 수치, 세계관 규칙, 시간선 |
| `design_documents.writing_rules` | 집필 규칙 바이블 |
| `ep_range_table[].plot_guide` | 해당 EP 범위의 큰 설계 플롯 가이드 |
| `ep_range_table[].plot_guide_detail` | 해당 EP 범위의 작은 설계 플롯 가이드 |
| `ep_range_table[].character_detail` | 해당 EP 범위 전용 캐릭터 상세 문서 |

### 3. 에이전트별 문서 매핑

각 에이전트가 어떤 축을 진단할 때 어떤 문서를 참조하는지 명시.

#### rule-checker
| 축 | 참조 문서 키 | 용도 |
|----|------------|------|
| VOICE | design_documents.character_detail 또는 ep_range_table[].character_detail | 보이스표(종결어미·길이·패턴) 대조 |
| TITLE | design_documents.character_detail 또는 ep_range_table[].character_detail | 호칭 규칙표(화자×청자 매트릭스), 호칭 전환 조건 |
| BANNED | design_documents.character_core | 주인공 감정 표현 규칙 (있을 경우) |
| TRANS | — | grep 기반, 설정문서 불필요 |
| SILENCE | — | 카운트 기반, 설정문서 불필요 |

#### story-analyst
| 축 | 참조 문서 키 | 용도 |
|----|------------|------|
| TIMELINE | ep_range_table[].plot_guide 또는 plot_guide_detail, design_documents.bootstrap | EP별 확정 시간대, 사건 순서 |
| NUMBER | ep_range_table[].plot_guide 또는 plot_guide_detail, design_documents.bootstrap, design_documents.character_core | EP별 확정 수치 (면적·자금·수확량 등) |
| PLAUSIBILITY | design_documents.character_core | 캐릭터 능력, 시대 고증 |
| SCENE | 직전 2화 | 화간 연속성 (설정문서 불필요) |
| UNIFORM | 직전 2화 | 패턴 대조 (설정문서 불필요) |

#### platform-optimizer
| 축 | 참조 문서 키 | 용도 |
|----|------------|------|
| HOOK | ep_range_table[].plot_guide 또는 plot_guide_detail | EP별 훅 유형·감정강도, 핵심 전환 포인트 |
| OPENING | ep_range_table[].plot_guide 또는 plot_guide_detail | EP별 비트 구조 |
| MOBILE | design_documents.web_novel_guide | 모바일 최적화 원칙 |
| SUMMARY | — | 정량 측정 기반, 설정문서 불필요 |

#### alive-enhancer
| 축 | 참조 문서 키 | 용도 |
|----|------------|------|
| ALIVE-1 (메아리) | design_documents.character_detail 또는 ep_range_table[].character_detail | 대화 DNA, 캐릭터별 반응 경로 |
| ALIVE-2 (침묵) | design_documents.character_detail 또는 ep_range_table[].character_detail | 비언어 태그 팔레트 |
| ALIVE-3 (긴장점) | design_documents.character_core | 조연별 고유 긴장점, 핵심 역할 |
| ALIVE-4 (거리감) | design_documents.character_core | 주요 관계 곡선, 관계 규칙 |

#### revision-executor / revision-reviewer
| 교정/검증 유형 | 참조 문서 키 | 용도 |
|--------------|------------|------|
| TIMELINE/NUMBER | ep_range_table[].plot_guide 또는 plot_guide_detail, design_documents.bootstrap | 정본 수치 확인 |
| VOICE/TITLE | design_documents.character_detail 또는 ep_range_table[].character_detail | 보이스표·호칭표 준수 교정 |
| 캐릭터 고유 설정 | design_documents.character_core | 주인공 능력, 배경 정본 |
| ALIVE | design_documents.character_detail 또는 ep_range_table[].character_detail | 비언어 태그·관계 변화표 |

### 4. 보존 가드레일

교정 시 절대 훼손하지 않는 요소 목록. 프로젝트마다 다르다.

```markdown
1. 전문성 밀도 (기술 용어·데이터)
2. 작품 고유 분위기
3. 캐릭터 전문가 이미지
4. 주인공 고유 내면 톤
5. 시대 고증
6. [캐릭터별 보존 항목 — 예: "캐릭터X의 침묵 보존"]
7. [관계 규칙 — 예: "A-B 관계 선 넘지 않음"]
```

### 5. 수치 교차검증 정본 우선순위

수치 불일치 발견 시 어느 문서를 정본으로 삼을지 순서.

```markdown
1. ep_range_table[].plot_guide_detail — EP별 세부 확정 수치 (가장 구체적)
2. ep_range_table[].plot_guide — EP 범위별 확정 수치
3. design_documents.bootstrap — 매크로 수치, 세계관 규칙
4. design_documents.verification — 검증 완료 수치 기록
5. 직전 에피소드 — 서사 연속성
```

### 6. 핵심 전환 포인트

프로젝트별로 독자 이탈 방지 또는 유료 전환을 위한 핵심 에피소드를 정의한다.
해당 에피소드는 훅 강도 4+ 필수.

```markdown
# 예시 (프로젝트에 맞게 수정)
- EP025: 1막 종결 — 유료 전환 유도
- EP050: 중반 전환점
- EP075: 3막 진입
- EP100: 클라이맥스 전초
```

> 플랫폼별 기본 전환 포인트가 있을 경우 `_workspace/platform-guide-{platform}.md`에 정의하고, 프로젝트별로 오버라이드한다.

---

## 선택 섹션

### 7. 카타르시스 유형

작품의 핵심 카타르시스 유형을 정의한다. 자유 텍스트로 작성.

```markdown
# 예시
- 주인공의 전문 지식으로 위기를 돌파하는 지적 쾌감
- 숫자(수확량·매출)가 증명하는 성장의 쾌감
- 무시하던 인물들이 인정하는 반전 쾌감
```

### 8. 커스텀 진단 축

12축 외에 프로젝트 고유 진단이 필요하면 이 섹션에 정의한다.
story-analyst가 LOGIC 진단 시 함께 수행한다.

커스텀 축은 아래 3가지를 정의해야 한다:
1. **정본**: 이 축의 기준이 되는 설정문서 또는 섹션
2. **탐지 키워드**: grep으로 기계적 검출할 패턴 목록
3. **판별 기준**: VIOLATION(위반)과 ALLOWED(허용)의 경계 조건

#### 예시 A: PASTLIFE — 전생/회귀 설정 정합성 (회귀물)

```yaml
custom_axes:
  PASTLIFE:
    description: "주인공의 전생/회귀 설정과 에피소드 서술의 정합성 검증"
    agent: story-analyst
```

레이어 구성:
- **레이어 1 (키워드 직접 위반)**: `grep "전생"` → 정본과 모순되는 서술 검출
- **레이어 2 (능력 암묵적 부정합)**: 전생 능력 매트릭스의 탐지 키워드 grep → 서술자의 능력 부정합 검출
- **판별**: 서술자가 사실로 기술한 능력 부족 = VIOLATION / 전략적 은폐·타인 시점 = ALLOWED

이어서 novel-config.md에 정본 요약, 전생 능력 매트릭스(영어·시스템·지역·전문분야별 수준+탐지 키워드), 등급 기준을 상세 기술한다.

#### 예시 B: MAGIC_SYSTEM — 마법 체계 정합성 (판타지)

```yaml
custom_axes:
  MAGIC_SYSTEM:
    description: "마법/능력 체계의 규칙과 에피소드 서술의 정합성 검증"
    agent: story-analyst
```

레이어 구성:
- **레이어 1 (능력 한계 위반)**: 부트스트랩의 마법 규칙(비용·조건·한계)과 에피소드 내 마법 사용이 모순되는지 검출
- **레이어 2 (성장 곡선 위반)**: 캐릭터의 현재 등급/레벨에서 불가능한 마법 사용 검출
- **판별**: 규칙 명시적 위반 = VIOLATION / 규칙의 창의적 응용·예외 조건 충족 = ALLOWED

#### 예시 C: RELATIONSHIP_LOGIC — 관계선 정합성 (로맨스)

```yaml
custom_axes:
  RELATIONSHIP_LOGIC:
    description: "캐릭터 간 관계 단계와 에피소드 내 행동/대화의 정합성 검증"
    agent: story-analyst
```

레이어 구성:
- **레이어 1 (관계 단계 점프)**: 캐릭터 시트의 관계 단계표와 현재 EP의 행동이 모순되는지 검출 (예: 경계 단계에서 갑자기 스킨십)
- **레이어 2 (감정 역행)**: 이전 화에서 확인된 감정 변화가 설명 없이 이전 단계로 회귀하는지 검출
- **판별**: 단계 2칸+ 점프 = CRITICAL / 1칸 점프(촉매 이벤트 있음) = ALLOWED

### 9. 침묵 패턴 예외

침묵 상한(기본 4회)에서 제외되는 캐릭터. 설정상 침묵이 정체성인 캐릭터용.

```markdown
- 캐릭터Y (침묵이 캐릭터 정체성, 교체 금지)
```

### 10. 핵심 수치 빠른 참조

에이전트가 빠르게 확인할 수 있도록 주요 수치를 요약. 상세값은 설정문서 정본을 따른다.

```markdown
### 면적 진행
- 1막: EP5(5만평), EP10(9.2t/ha), EP26(60만평)
- 2막: EP36(480만평), EP71(3,000만평=1만ha)

### 자금
- EP21 총자산: 10.9억원
- EP27 투자: $2.6M
```

---

## novel-config.md 배치 위치

```
{소설_프로젝트_루트}/
├── novel-config.md          ← 이 파일
├── design/
│   ├── bootstrap.md
│   ├── character_sheet.md
│   ├── character_sheet_detail.md
│   └── plot-hook-guide_act{N}.md
├── episode/
│   ├── ep001.md
│   ├── ep002.md
│   └── ...
└── revision/               (또는 work_dir에 지정한 경로)
    ├── fix_plan.md
    ├── learnings.md
    └── alive-tracker.md
```

## 윤문/rewrite 스킬이 설정을 사용하는 방법

1. **Step 0 초기화**: `novel-config.md`를 읽고 설정 파싱
2. **EP별 문서 결정**: 설정의 `ep_range_table`에서 해당 EP의 플롯 문서 선택
3. **Phase 1 에이전트 호출**: 에이전트별 문서 매핑에 따라 설정문서 경로를 프롬프트에 포함
4. **Phase 2-3 교정/검증**: 보존 가드레일, 수치 정본 우선순위를 적용
5. **커스텀 축**: 정의되어 있으면 해당 에이전트에 추가 진단 지시

---

## Rewrite 전용 설정 (선택)

rewrite 스킬을 사용할 경우에만 작성한다. polish만 사용하면 이 섹션은 불필요.

### 대화 DNA 파일

캐릭터별 대화 DNA(사고 패턴, 정보 처리, 설득 방식, 상황별 변주)를 정의한 파일 경로.
이 파일이 없으면 `design_documents.dialogue_dna`, 그마저 없으면 `design_documents.character_detail`의 `## 대화 DNA` 섹션만으로 진단한다.

| 문서 키 | 경로 | 용도 |
|---------|------|------|
| rewrite.character_dialogue_dna | design/character-dialogue-dna.md | 대화 DNA — character-sculptor, episode-rewriter, episode-creator, quality-verifier 참조 |

**대화 DNA 정의 위치** (우선순위순):
1. `rewrite.character_dialogue_dna` 경로에 별도 파일이 존재하면 이를 사용
2. 없으면 `design_documents.dialogue_dna`, 그마저 없으면 `design_documents.character_detail` 문서 내 `## 대화 DNA` 섹션을 사용
3. 둘 다 없으면: `[대화DNA미정의]` 태그를 달고, 캐릭터 보이스표만으로 진단 (정밀도 낮음 경고)

**대화 DNA 섹션 필수 구조** (별도 파일이든 character_detail 내 섹션이든 동일 형식):

```markdown
## 대화 DNA

### {캐릭터명}

#### 사고 패턴
- **정보 처리 방식**: [분석형/직관형/감정형/실용형]
- **의사결정 스타일**: [데이터 기반/경험 기반/관계 기반/원칙 기반]
- **설득 방식**: [논리 제시/감정 호소/권위 인용/실례 나열]

#### 상황별 사고 경로
| 상황 유형 | 사고 경로 | 대사 예시 |
|----------|----------|----------|
| 좋은 소식 | [반응 패턴] | "예시 대사" |
| 위기 | [반응 패턴] | "예시 대사" |
| 갈등 | [반응 패턴] | "예시 대사" |
| 정보 전달 | [반응 패턴] | "예시 대사" |

#### 금지 패턴
- 이 캐릭터가 절대 하지 않을 말/사고방식 목록
```

### Rewrite 보존 가드레일

`guard_rails`에 추가되는 rewrite 전용 가드레일.

```markdown
1. 경악 방식 교체 불가 — 각 캐릭터의 고유 경악 언어를 다른 캐릭터에게 이식하지 않는다
2. [주인공 동기 표현 규칙 — 예: "목표 숫자를 직접 선언하지 않는다"]
```

### Rewrite 작업 디렉토리

```yaml
rewrite:
  work_dir: "revision/"  # rewrite-plan.md, rewrite-log.md 위치. 없으면 project.work_dir 사용
```
