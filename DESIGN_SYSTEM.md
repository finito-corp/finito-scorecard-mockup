# Finito Surfer Card — Design System

Claude Design·외부 디자이너·동체 리뷰어가 이 mockup 을 업그레이드할 때 **반드시 먼저 읽고 준수**할 시각·카피 규칙.

---

## 1. 팔레트 (CSS variables, 고정)

```css
--ink:       #0A1628;  /* 본문 ink, dark background base */
--paper:     #F5F1E8;  /* 밝은 글자, 기본 종이색 */
--paper-dim: #C7BFAF;  /* 약한 글자, 보조 텍스트 */
--gold:      #D4A85E;  /* primary 강조, 서핑 트로피 톤 */
--gold-hi:   #F3D180;  /* highlight, equipped/승격 */
--amber:     #FF9D2E;  /* 2차 강조, 주의 환기 */
--coral:     #E85D4A;  /* 오류/warning 은 아니지만 생기있는 경고 포인트, 부리·립 */
--blue:      #4A8BFF;  /* 물·파도 기본 블루 */
--purple:    #7B61FF;  /* 에픽 티어 포인트 */
--steel:     #4E5868;  /* 기본 오리 본체 회색조 */
--bg-0:      #05090F;  /* 가장 어두운 배경 */
--bg-1:      #0C1524;  /* 카드 배경 */
--bg-2:      #111D33;  /* 버튼/input 배경 */
```

**사용 원칙**
- 추가 색 도입은 금지. Claude Design 이 임의로 neon·bright 파스텔을 넣으려 하면 위 팔레트 내에서 재해석할 것.
- 그라디언트는 위 변수들의 2~3색 조합만. 무지개·3원색 혼합은 M(신화) 티어에만 허용.
- dark theme 고정. light theme 버전은 이번 범위 밖.

## 2. 타이포그래피

```
font-family: "Pretendard Variable", "Pretendard", -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
```

- **한영 통일** — Pretendard Variable 로 한국어·영어 모두 처리. Anton, JetBrains Mono 는 디스플레이 보조로만 (영어 숫자 헤드라인용, 한국어에는 미사용)
- 영어 라벨은 대문자·letter-spacing 0.08~0.14em 로 "프리미엄 티셔츠 태그" 느낌
- 한국어 본문 line-height 1.4~1.5, 영어 라벨 line-height 1.1~1.2
- 숫자는 Pretendard Variable weight 800 + tabular-nums 로 통계 질감

## 3. 레이아웃 규칙

- **공유 카드 4종**: 각 카드 `aspect-ratio: 1 / 1`, 최대 그리드 4열. 모바일 1열 폴백
- **Detail Card**: 가로 폭 우선, 히어로 영역 `aspect-ratio: 4/3`
- **꾸미기 탭**: 미리보기 큰 오리 + 슬롯 칩 + 14개 인벤토리 카드 그리드(3~4열)
- 스페이싱은 8px grid (8·16·24·32)

## 4. 오리 캐릭터 본체 좌표 (SSOT, 절대 변경 금지)

```
기준: small duck (공유 카드용)
- head   circle:  cx="1"   cy="-8"   r="6.8"
- body   ellipse: cx="0"   cy="4"    rx="10"   ry="9"
- wing   ellipse: cx="-4"  cy="3"    rx="4"    ry="5.5"
- belly  ellipse: cx="0"   cy="7"    rx="6"    ry="5"
- beak   ellipse: x=7.3~7.5, y=-7~-5.8
- eye    circle:  cx="3.5" cy="-10"  r="1.1"
- blush  circle:  cx="-2"  cy="-7"   r="0.8"  (볼 홍조)
- tail   path:    M -11,1 L -15,-2 L -10,5 Z

Detail Hero Duck:
- head circle r=9.5 (small 오리 기준 약 1.4배)
- 공유카드 fragment 를 재사용할 때 scale(1.4) 로 통일
```

**꾸미기 슬롯 좌표**
```
- head 장신구 안전 범위:  x=-8.5~8.0, y=-20.5~-3.0
- body 장신구 안전 범위:  x=-8.0~12.5, y=-2.0~10.0
- head circle 뒤 레이어 (배경):  상어 지느러미
- head circle 앞 레이어 (전면):  헤드밴드, 별, 왕관, 이어링
- body 뒤 레이어:  메달, 팔찌, 책
- feet 아래:  신발·핀·부츠
- ride 최하단:  보드·카약·돌고래 (viewBox -30~30 횡 확장)
```

## 5. 티어 시각 공식 (중요)

| 티어 | 색상 계열 | stroke | glow | particle | 추가 효과 |
|------|----------|--------|------|----------|----------|
| N 기본 | steel #4E5868 톤 | 0.5px | 없음 | 없음 | 회색 라벨 |
| R 레어 | blue #4A8BFF | 0.6px | 약한 파랑 그림자 | 없음 | 미세 파랑 glow |
| E 에픽 | purple #7B61FF | 0.6~0.7px | 보라 중간 | sparkle 1~2개 | 점광 |
| L 전설 | gold 2색 (#F3D180 + #FF9D2E) | 0.8px + 2차 stroke 0.4px 오버레이 | 강한 gold | edge sparkle dot 2~3개 | 오라 링 |
| M 신화 | 무지개 gradient (gold + blue + purple) | 3색 레이어드 | 2단 aura halo | particle 4~6개 다채색 | prismatic outline, 애니메이션 border |

**Claude Design 이 준수해야 할 티어 원칙**
- 상위 티어일수록 "한 번 봐도 희귀하다"는 즉각적 시각 신호가 있어야 함
- 단 과하게 화려해지면 오리 본체가 가림 → 장식은 오리 주변 halo/aura 로만 확장
- M 신화는 전체 70개 중 **5개만** (슬롯당 1개). 남발 금지

## 6. 카피 톤

- 기본 **한국어 존댓말** + 차분한 서퍼 에너지
- 영어 코드명은 보조 라벨 역할 (PERSONAL BEST, STREAK, MILESTONE, GRADE UP, DRESS UP, COSMETIC ONLY)
- 학업 보너스 암시 단어 **금지** (예: "+N% 정답률", "EXP 증가", "시험 보너스", "성적 +")
- 미션 문구는 "○○ 달성 시 해금" 형식 또는 동사형 "3개월 스트릭 달성"
- 브랜드 태그라인: "Ride your own waves." 최소 1회, "Surf With Us" 선택

## 7. 애니메이션 규칙

- 기본 `prefers-reduced-motion: reduce` 지원
- 말풍선 float, streak 파도 상승, Grade Up 오리 상승 애니메이션 유지
- 신화 티어만 slow pulse (3~4s) 추가 가능
- GPU 안정 위해 `transform` 개별 속성(`translate`/`rotate`/`scale`) 사용, matrix 회피

## 8. 공유 카드 4종 — 디자인 목적

| 카드 | 호칭 | 핵심 메시지 | 시각 포인트 |
|------|------|-----------|------------|
| Card 01 | Personal Best | 이번 주 신기록 — 누구나 자랑 가능 | 파도 뒤 오리 무더기, 챔피언 오리 1마리 |
| Card 02 | Streak | 연속 출석 — 듀오링고 공식 | D7, 파도 상승, 불씨 fire icons |
| Card 03 | Milestone | 통산 마일스톤 — 장기전 드롭 | 트로피, 50명 회색 오리 군중 |
| Card 04 | Grade Up | 등급 상승자 전용 한정 드롭 | 왕관, 오리 상승 애니메이션 |

**공통**: 상단 브랜드 "고연승T · Winning House", 하단 카드 번호(01~04) + 학생 시리얼(-PB/-STK/-MIL/-GU), "저장 이미지로" CTA

## 9. Detail Card 4탭 구조

1. **이번 주 (THIS WAVE)**: 이번 주 요약 + 히어로 오리 + 코멘트
2. **업적 (BADGES)**: 5종 업적 (첫 달 라이딩 / 크레스트 돌파 / 상어 라이더 / 30일 롱 웨이브 / 리턴 라이더) + Club stamp SHARK RIDER IN TRAINING
3. **분석 (ANALYSIS)**: 유형별 정답률, 추이 라인 차트
4. **꾸미기 (DRESS UP)**: 5슬롯 × 70종 + 실시간 프리뷰 + localStorage 영속

## 10. 제약사항 · 금지 리스트

- 가챠 확률·과금 요소 **금지**
- 실학생 이름·점수·전화·이메일 **금지** (모두 더미)
- 학업 성능에 실제 영향 주는 요소 **금지** (항상 COSMETIC ONLY)
- 동체 Slack 채널 외 외부 공개 시 반드시 "Public Design Preview" 뱃지 고지
- 경쟁 브랜드(메가스터디·이투스 등) 로고·컬러 참조 **금지**
