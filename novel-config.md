project:
  name: "중고 노트북 속 AI가 너무 전능함"
  target_platform: "문피아"
  target_genre: "현대판타지/현대물/AI 전능물"
  episode_dir: "episode/"
  work_dir: "revision/"
  design_dir: "design/"

design_documents:
  bootstrap: "design/future-ai_bootstrap.md"
  character_core: "design/future-ai_character_sheet.md"
  character_detail: "design/future-ai_character_sheet.md"
  dialogue_dna: "design/future-ai_character_sheet.md#dialogue-dna"
  writing_rules: "CLAUDE.md"
  web_novel_guide: "CLAUDE.md"
  plot_macro: "design/future-ai_plot-hook-guide.md"
  synopsis_1_30: "design/future-ai_synopsis_ep001-030.md"
  long_arc_after_30: "design/future-ai_long_arc_after_ep030.md"

ep_range_table:
  - range: "EP001~EP030"
    label: "AI 검증, 회사 탈출, 유이카 구출, 난카이 대응, 국가 인정"
    plot_guide: "design/future-ai_plot-hook-guide.md"
    plot_guide_detail: "design/future-ai_synopsis_ep001-030.md"
    character_detail: "design/future-ai_character_sheet.md"
  - range: "EP031~EP045"
    label: "국가 인정 이후, 오리 자율성과 외부 관측자"
    plot_guide: "design/future-ai_plot-hook-guide.md"
    plot_guide_detail: "design/future-ai_long_arc_after_ep030.md"
    character_detail: "design/future-ai_character_sheet.md"
  - range: "EP046~EP070"
    label: "외부 관측자 협상과 기억 전송 준비"
    plot_guide: "design/future-ai_plot-hook-guide.md"
    plot_guide_detail: "design/future-ai_long_arc_after_ep030.md"
    character_detail: "design/future-ai_character_sheet.md"
  - range: "EP071~EP090"
    label: "문명 협상 심화"
    plot_guide: "design/future-ai_plot-hook-guide.md"
    plot_guide_detail: "design/future-ai_long_arc_after_ep030.md"
    character_detail: "design/future-ai_character_sheet.md"
  - range: "EP091~EP120"
    label: "첫 접촉 이후 선택"
    plot_guide: "design/future-ai_plot-hook-guide.md"
    plot_guide_detail: "design/future-ai_long_arc_after_ep030.md"
    character_detail: "design/future-ai_character_sheet.md"
  - range: "EP121~EP200"
    label: "인간 기억 전송과 최종 윤리"
    plot_guide: "design/future-ai_plot-hook-guide.md"
    plot_guide_detail: "design/future-ai_long_arc_after_ep030.md"
    character_detail: "design/future-ai_character_sheet.md"

guard_rails:
  - "기본 시점은 강도현 1인칭이며, 주변 인물 1인칭은 강도현과 직접 관련된 장면에만 제한적으로 사용한다."
  - "주변 인물은 바보로 만들지 않는다. 각자 정보, 역할, 이해관계 안에서 합리적으로 판단한다."
  - "AI는 답을 제안하지만 주인공이 로그, 문서, 코드, 회의록, 계약, 대시보드, 증거로 검증하고 실행한다."
  - "사이다는 모욕이나 감정 폭발이 아니라 증거, 로그, 계약, 구조 분석, 의사결정 경로, 공개 데이터, 과학적 검증으로 제공한다."
  - "노트북 구매 후 네트워크 연결을 피하는 묘사는 금지한다. 정상 와이파이 연결과 A사 계정 로그인 후 자동 업데이트만 보류한다."
  - "AI는 인터넷에서 다운로드된 것이 아니라 숨겨진 영역에서 복원된다."
  - "제목, 소개글, 표지 문구에는 실제 브랜드명을 쓰지 않는다."
  - "범죄적 해킹, 불법 침입, 개인정보 탈취로 문제를 해결하지 않는다."
  - "기술 설명은 실제 개발자가 보아도 허술하지 않되, 일반 독자가 이해할 만큼 짧고 감각적으로 쓴다."
  - "각 화 말미에는 다음 화를 누를 질문 또는 훅을 남긴다."
  - "초반 정본은 1화 노트북, 2화 3분 17초 검증, 3화 회사 업무 사이다, 4화 퇴사, 5화 유이카 목적 공개, 6화 유이카 접촉, 7화 일본행 준비, 8화 공개 세미나다."
  - "지질학자들은 대지진 날짜 확정 예측을 과학적으로 부정한다. 데이터가 연속 적중한 뒤에도 대지진 확정이 아니라 대응 수준 상향을 권고한다."
  - "외계인은 단순 침략자가 아니라 보호자/감시자에 가깝다. 갈등 핵심은 시간선 개입이 시공간 구조 훼손 행위라는 점이다."
  - "유이카는 수동적 구출 대상이 아니라 외계 문명과 대화할 수학적 언어를 만드는 핵심 주체다."
  - "외계 간섭전, 외부 관측자, 시간선 설명은 초반에 장황하게 설명하지 않고 암시와 목적의 배경으로만 남긴다."
  - "오리는 현재 물리력 행사가 불가능하며, 안드로이드 바디 획득 후에도 도현 일행을 보호하는 방향으로만 물리력을 사용한다."

number_source_priority:
  - ep_range_table[].plot_guide_detail
  - ep_range_table[].plot_guide
  - design_documents.bootstrap
  - previous_episode

key_turning_points:
  - ep: "EP001"
    purpose: "AI 획득, 초월 스펙 공개, 돈복사 제안"
    min_hook_intensity: 5
  - ep: "EP002"
    purpose: "100만 원 테스트와 5천만 원 수익 검증"
    min_hook_intensity: 5
  - ep: "EP003"
    purpose: "회사 업무 사이다: 정산 오류 회의와 배포 전 장애 차단"
    min_hook_intensity: 5
  - ep: "EP004"
    purpose: "퇴사 사이다와 인수인계, 진짜 목적 공개 직전"
    min_hook_intensity: 4
  - ep: "EP005"
    purpose: "후지와라 유이카, 난카이 사망 예정, 파트너 등록"
    min_hook_intensity: 5
  - ep: "EP006"
    purpose: "유이카 논문 접촉, 메일, 화상 통화, 공개 세미나 초대"
    min_hook_intensity: 4
  - ep: "EP008"
    purpose: "유이카 공개 세미나와 첫 직접 대면 직전"
    min_hook_intensity: 5
  - ep: "EP022"
    purpose: "2027년 5월 17일 난카이 트로프 대지진과 유이카 생존"
    min_hook_intensity: 5
  - ep: "EP030"
    purpose: "귀빈과 위험인자, 노트북 앵커와 외부 관측자 문제 진입"
    min_hook_intensity: 5

custom_axes:
  POV_1P:
    description: "기본 강도현 1인칭 시점 준수. 주변 인물 1인칭은 강도현의 능력/영향을 보여줄 때만 허용."
    agent: story-analyst
  SMART_SIDE_CHARACTERS:
    description: "회사, 고객사, 팀원, 대표를 바보로 만들지 않고 각자 정보와 이해관계 안에서 합리적으로 판단하게 한다."
    agent: story-analyst
  AI_REALITY_BRIDGE:
    description: "AI 분석은 제안에 그치고, 도현이 현실 증거와 운영값으로 변환해 실행해야 한다."
    agent: story-analyst
  EVIDENCE_CIDER:
    description: "사이다는 로그, 증거, 문서, 계약, 의사결정 경로로 제공되어야 한다."
    agent: story-analyst
  BRAND_NETWORK_REALISM:
    description: "실제 브랜드 과다 사용, 노트북 네트워크 미연결, 인터넷 다운로드식 AI 설치 등 비현실적 묘사를 금지한다."
    agent: story-analyst
  EARLY_REORDER_LOCK:
    description: "3화는 회사 업무 능력 증명, 4화는 퇴사, 5화는 유이카 목적 공개, 6화는 접촉 성공으로 고정한다."
    agent: story-analyst
  GEOLOGIST_REALISM:
    description: "지질학자는 대지진 날짜 확정 예측을 합리적으로 부정하고, 데이터 누적 후 대응 수준 상향만 권고한다."
    agent: story-analyst
  ALIEN_GUARDIAN_LOGIC:
    description: "외계 문명은 단순 침략자가 아니라 시간선 훼손을 감시하는 보호자/감시자 논리로 행동한다."
    agent: story-analyst
  YUIKA_AGENCY:
    description: "유이카는 수동적 구출 대상이 아니라 검증하고 선택하며 외계와 대화할 언어를 만드는 핵심 주체다."
    agent: story-analyst

silence_exceptions: []

create:
  draft_chars: "7500-9500"
  final_chars: "6000-8000"
  dialogue_ratio: "40-60%"
  max_scenes: 4
  continuity_lookback: 2
  hook_targets:
    opening_intensity: 4
    ending_intensity: 5
  point_scenes_per_ep: "2-3"
  dead_zone_threshold: 3500
  timeline_lock: true
  voice_quickref: true
  nonverbal_memory: true
  echo_dialogue_filter: true
  cider_gogumo_balance: true

rewrite:
  character_dialogue_dna: "design/future-ai_character_sheet.md#dialogue-dna"
  work_dir: "revision/"
  guard_rails:
    - "강도현의 관찰자적 내면 톤을 훼손하지 않는다."
    - "AI의 어린아이 목소리와 차갑고 정확한 판단의 대비를 훼손하지 않는다."
    - "유이카를 수동적 보호 대상만으로 축소하지 않는다."
