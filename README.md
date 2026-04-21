# Finito Surfer Card — Design Preview

고연승T 수능 영어 학원의 **일차 성적표 "서퍼 카드"** 디자인 프리뷰 저장소.
Claude Design·외부 디자이너·동체 리뷰어가 함께 시각 고도화를 의논하기 위한 **공개 mockup** 입니다.

> **Live**: `https://finito-corp.github.io/finito-scorecard-mockup/` (GitHub Pages 활성화 후)

---

## 이 리포는 뭐예요

- 학생이 시험 직후에 받는 "성적표 카드 + 상세 리포트 + 꾸미기" 1일차 mockup
- 목표: **친구에게 자랑 / 팬덤 전환 / 공유율 상승**
- 기술 스택: **단일 HTML 파일 · 인라인 CSS/JS/SVG** (외부 의존 Google Fonts + Pretendard CDN 만)
- 실학생 데이터 **없음** (더미 수치 + 가상 카피)
- 학업 성능(점수/등급 계산)에는 **영향 없음** — 꾸미기 시스템은 cosmetic only

## 파일 지도

| 파일 | 용도 |
|------|------|
| `index.html` | 학생 뷰 본체. 4 공유 카드(Personal Best / Streak / Milestone / Grade Up) + Detail Card(이번 주·업적·분석·꾸미기 4탭) |
| `admin.html` | 좌측 학생뷰 iframe + 우측 관리자 리뷰 테이블. 70종 아이템 열기·닫기·메모 토글 |
| `DESIGN_SYSTEM.md` | 팔레트·타이포·오리 SVG 본체 좌표·티어 시각 공식·COSMETIC-ONLY 원칙. **Claude Design 등 외부 툴에 먼저 물려주세요** |
| `prompts/share-cards.md` | Claude Design 프롬프트 — 공유 카드 4종 고도화용 |
| `prompts/detail-card.md` | Claude Design 프롬프트 — Detail Card 4탭 레이아웃 리디자인용 |
| `prompts/dressup-tab.md` | Claude Design 프롬프트 — 꾸미기 탭 게임 감성 강화용 |

## Finito 브랜드 요지

- **태그라인**: "Ride your own waves. Surf With Us."
- **세계관**: 오리 캐릭터가 서핑보드 → 카약 → 보트 → 돌고래 로 성장
- **팬덤 퍼널**: Prospects → Light Fans → Core Fans(=flow-up·anchor-up) → Super Fans
- 공유 카드의 KPI는 **(1) 학생이 친구에게 자발적 공유, (2) 학부모가 보기 편한 구조, (3) 꾸미기 탭이 재방문 유도**

## Claude Design 연결 권장 순서

1. 이 리포 URL 또는 `DESIGN_SYSTEM.md` 를 Claude Design 에 등록 → 디자인 시스템 컨텍스트 고정
2. `prompts/` 의 프롬프트 중 하나 복사 → Claude Design 에 프롬프트로 전달
3. 첨부: `index.html` (학생뷰), 필요시 `admin.html`
4. 반복 수정 → export(PDF/URL/PPTX) → 리뷰

## 제약 · 준수 사항

- 학업 보너스 암시 표현 금지 (예: "+N% 정답률", "EXP 증가" 등)
- 기본 상태 = N 티어 15종 자동 지급, 현 시즌 열려있는 DEMO 16종
- 한국어 존댓말 기본, 영어 코드명 보조
- 슬롯 구성: 모자 / 상의 / 발 / 탈 것 / 악세서리 (고정)
- 티어: N 기본 / R 레어 / E 에픽 / L 전설 / M 신화 (각 슬롯 14개, 총 70개)

## 정본·배포 관계

- **정본 SSOT**: `finito-corp/finito-corp` (private) 리포의 `workspace/user/hyun/finito-mockup-score-card-v3-20260420.html`
- **이 리포(finito-scorecard-mockup)**: 해당 정본의 **디자인 리뷰용 공개 미러**
- 공개 리뷰가 확정되면 정본에 역반영 후 이 리포도 동기화

## 피드백 채널

- 내부: 동체 채널(#피니토-동체) 에 업데이트 공유
- 디자인 컨설팅: Claude Design 프롬프트 기반 대화
- 이슈 등록은 정본 리포 Linear 에 (이 리포 Issues 는 미사용)
