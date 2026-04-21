# Finito 서퍼 카드 — 오리 본체 SVG 3종

v3 mockup 에 사용 중인 오리 캐릭터의 본체 SVG fragment 전체. 디자인 업그레이드 시 **좌표·슬롯 앵커·레이어 순서는 절대 변경 금지**.

---

## 0. 공통 규칙

- 모든 오리는 `<g class="runner-body">` 안에 body 구조가 들어있고, 그 중간중간 `<g class="duck-slot" data-slot-name="...">` 빈 그룹이 **장신구 삽입 앵커** 입니다.
- 데이터 슬롯 5종: `body`, `head`, `extra`, `feet`, `ride` (ride 는 상위 `<g>` 로 별도 배치)
- JS 가 `innerHTML` 로 장신구 fragment 를 주입합니다. 그래서 **본체 좌표·viewBox·data-slot-\* 속성은 절대 바꾸지 마세요.** 리디자인은 `fill`·`stroke`·비례·shading 중심으로만.

## 1. 팔레트

```
#F3D180  head/body 골든
#D4A85E  꼬리/날개 gold
#FFF4D6  배 하이라이트
#E85D4A  부리 위 coral
#C03B28  부리 아래
#0A1628  눈동자
#F5F1E8  눈 하이라이트
#FFB3A0  볼 홍조 (opacity 0.55~0.6)
```

## 2. 스케일 체계

| 타입 | 사용처 | head r | body rx | data-slot-scale |
|------|--------|--------|---------|-----------------|
| small duck | 공유 카드 4종(Personal Best / Streak / Milestone / Grade Up) | 7.5 | 11 | 1.0 |
| detail hero duck | Detail Card "이번 주" 탭 중앙 히어로 | 9.5 | 14 | 1.4 |
| preview duck | 꾸미기 탭 프리뷰 | 9.1 | 13.2 | body 1.28 / head·extra·feet 1.32 |

---

## A. Small Duck — 공유 카드용 (Card 01~04 공통)

```svg
<g class="runner-body">
  <!-- 꼬리 (왼쪽 뒤) -->
  <path d="M -11,1 L -15,-2 L -10,5 Z" fill="#D4A85E"/>
  <!-- 몸통 (둥글고 통통) -->
  <ellipse cx="0" cy="4" rx="11" ry="10" fill="#F3D180"/>
  <!-- 배 하이라이트 -->
  <ellipse cx="0" cy="7" rx="6.5" ry="5.5" fill="#FFF4D6"/>
  <!-- 슬롯 앵커: 상의(몸통 위) -->
  <g class="duck-slot duck-slot-body" data-slot-name="body" data-slot-scale="1"></g>
  <!-- 날개 -->
  <ellipse cx="-4" cy="3" rx="4.5" ry="6" fill="#D4A85E"/>
  <!-- 머리 -->
  <circle cx="1" cy="-9" r="7.5" fill="#F3D180"/>
  <!-- 슬롯 앵커: 모자(머리 위) -->
  <g class="duck-slot duck-slot-head" data-slot-name="head" data-slot-scale="1"></g>
  <!-- 슬롯 앵커: 악세서리(머리 옆) -->
  <g class="duck-slot duck-slot-extra" data-slot-name="extra" data-slot-scale="1"></g>
  <!-- 부리 위 (오른쪽 앞) -->
  <ellipse cx="8" cy="-8" rx="4.5" ry="1.7" fill="#E85D4A"/>
  <!-- 부리 아래 -->
  <ellipse cx="7.8" cy="-6.6" rx="3.8" ry="1.2" fill="#C03B28"/>
  <!-- 눈 -->
  <circle cx="4" cy="-11" r="1.8" fill="#0A1628"/>
  <circle cx="4.5" cy="-11.5" r="0.7" fill="#F5F1E8"/>
  <!-- 볼 홍조 -->
  <circle cx="-1.5" cy="-7" r="1.6" fill="#FFB3A0" opacity="0.55"/>
  <!-- 슬롯 앵커: 발 -->
  <g class="duck-slot duck-slot-feet" data-slot-name="feet" data-slot-scale="1"></g>
</g>
<!-- ride 슬롯은 runner-body 외부, 몸통 아래 배치 -->
<!-- <g class="duck-slot duck-slot-ride" data-slot-name="ride" data-slot-scale="1"></g> -->
```

---

## B. Detail Hero Duck — 큰 오리 (Detail Card "이번 주" 탭)

상위 `<svg viewBox="0 -50 400 300">` (aspect-ratio 4:3, 상단 50유닛 = 말풍선 공간). 오리는 중앙 `translate(200, 180)` 근처 배치.

```svg
<g class="runner-body">
  <!-- 꼬리 -->
  <path d="M -14,2 L -18,-2 L -12,7 Z" fill="#D4A85E"/>
  <!-- 몸통 (통통) -->
  <ellipse cx="0" cy="5" rx="14" ry="13" fill="#F3D180"/>
  <!-- 배 -->
  <ellipse cx="0" cy="10" rx="8.5" ry="7" fill="#FFF4D6"/>
  <g class="duck-slot duck-slot-body" data-slot-name="body" data-slot-scale="1.4"></g>
  <!-- 날개 -->
  <ellipse cx="-5" cy="4" rx="5.5" ry="7.5" fill="#D4A85E"/>
  <!-- 머리 -->
  <circle cx="1" cy="-11" r="9.5" fill="#F3D180"/>
  <g class="duck-slot duck-slot-head" data-slot-name="head" data-slot-scale="1.4"></g>
  <g class="duck-slot duck-slot-extra" data-slot-name="extra" data-slot-scale="1.4"></g>
  <!-- 부리 위 -->
  <ellipse cx="10" cy="-10" rx="5.5" ry="2" fill="#E85D4A"/>
  <!-- 부리 아래 -->
  <ellipse cx="9.8" cy="-8.2" rx="4.7" ry="1.5" fill="#C03B28"/>
  <!-- 눈 -->
  <circle cx="5" cy="-13" r="2.1" fill="#0A1628"/>
  <circle cx="5.7" cy="-13.7" r="0.8" fill="#F5F1E8"/>
  <!-- 볼 홍조 -->
  <circle cx="-2" cy="-8" r="2" fill="#FFB3A0" opacity="0.6"/>
  <g class="duck-slot duck-slot-feet" data-slot-name="feet" data-slot-scale="1.4"></g>
</g>
```

---

## C. Preview Duck — 꾸미기 탭 프리뷰

```svg
<g class="runner-body">
  <path d="M -13,2 L -18,-2 L -12,7 Z" fill="#D4A85E"/>
  <ellipse cx="0" cy="5" rx="13.2" ry="12.4" fill="#F3D180"/>
  <ellipse cx="0" cy="9.6" rx="8.2" ry="6.7" fill="#FFF4D6"/>
  <g class="duck-slot duck-slot-body" data-slot-name="body" data-slot-scale="1.28"></g>
  <ellipse cx="-5.2" cy="4" rx="5.2" ry="7" fill="#D4A85E"/>
  <circle cx="1" cy="-10.6" r="9.1" fill="#F3D180"/>
  <g class="duck-slot duck-slot-head" data-slot-name="head" data-slot-scale="1.32"></g>
  <g class="duck-slot duck-slot-extra" data-slot-name="extra" data-slot-scale="1.32"></g>
  <ellipse cx="9.5" cy="-9.1" rx="5.2" ry="1.9" fill="#E85D4A"/>
  <ellipse cx="9.2" cy="-7.4" rx="4.4" ry="1.35" fill="#C03B28"/>
  <circle cx="4.8" cy="-12.4" r="1.9" fill="#0A1628"/>
  <circle cx="5.4" cy="-13" r="0.7" fill="#F5F1E8"/>
  <circle cx="-1.8" cy="-7.8" r="1.8" fill="#FFB3A0" opacity="0.55"/>
  <g class="duck-slot duck-slot-feet" data-slot-name="feet" data-slot-scale="1.32"></g>
</g>
```

---

## 3. 배치 순서 (Z-axis) — 중요

`<g class="runner-body">` 안 요소는 **선언 순서 = 레이어 순서** (뒤 → 앞):

1. 꼬리 (최하단 배경)
2. 몸통 → 배 → `duck-slot-body` → 날개
3. 머리 → `duck-slot-head` → `duck-slot-extra`
4. 부리 위 → 부리 아래 → 눈 → 볼 홍조
5. `duck-slot-feet` (최상단)

**ride 슬롯은 runner-body 외부**에 독립 `<g>` 로, **본체보다 아래(뒤)** 에 배치됩니다 (서프보드·카약·돌고래 등이 오리를 태우는 형태).

## 4. 리디자인 허용/금지

**허용**
- 색상 변주 (팔레트 내 재해석)
- 비례 미세 조정 (rx/ry 10% 이내)
- shading/highlight path 추가 (예: 날개 아래 그림자, 몸통 광택)
- 눈 스타일 변주 (반달눈·별눈 등) — cx=4, cy=-11 중심 유지
- 표정 변화 (미소·윙크) — 볼 홍조 위치 유지

**금지**
- `data-slot-*` 그룹 제거·이동 (JS 가 innerHTML 로 삽입하는 앵커)
- head cx/cy, body cx/cy 기준 좌표 이동 (장신구 fragment 가 이 기준으로 맞춰져 있음)
- 전혀 다른 캐릭터(곰·강아지 등)로 치환
- viewBox 범위 확장 (현재 좌표계 유지)
- 팔레트 밖 색상 추가
