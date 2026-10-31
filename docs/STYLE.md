# STYLE — 운영 수준 UI (Pretendard · 토스/Apple 원칙)

참고한 공개 자료: 토스 디자인 시스템(TDS) 공개 문서의 컬러 · 타이포그래피 · Button · Top 컴포넌트 설명, Apple Human Interface Guidelines의 Layout · Color · Lists and tables.
TDS 자체(컴포넌트 · 피그마 키트)는 쓰지 않는다 — 원칙과 공개된 값만 참고해 새로 만든 CSS다.

## 붙이는 법
```
cp -r ../rules/docs/fonts ../rules/docs/pretendard.css ../rules/docs/style.css static/
```
```html
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<link rel="stylesheet" href="/static/pretendard.css">
<link rel="stylesheet" href="/static/style.css">
```
견본: `docs/preview.html`(사용자 화면, 모바일) · `docs/preview-admin.html`(관리 화면, 데스크톱). 클래스 쓰는 법은 견본 HTML을 그대로 보고 따라 한다.

## AI 티가 나는 화면 — 하지 않는다
- 회색 바탕 위에 그림자 카드를 잔뜩 띄우기 → **흰 바탕 + 굵은 회색 띠(`.gap16`)로 구획**
- 지표마다 ▲▼ %와 색 → 숫자 하나 + 비교는 회색 작은 글씨(`.note`)
- 이모지 · 그라디언트 · 컬러 아이콘 박스 남발 → 회색 원형 asset, 강조는 1곳만 brand
- 배너 · 뱃지 과다 → 뱃지는 상태가 바뀌는 항목에만, 배너 대신 `.notice` 한 줄
- 모든 버튼이 파랑 → 화면당 fill 1개, 나머지 `weak` / `dark weak`

## 원칙
1. **화면 제목은 문장이다.** "예약 현황"보다 "회의실 예약이 3건 있어요"(사용자 화면). 관리 화면은 명사형 제목 + 기간.
2. **위계는 크기 · 굵기 · 회색 단계로.** 색은 행동(brand)과 상태(성공 · 주의 · 위험)에만.
3. **목록이 기본 단위.** 정보는 `.row`(왼쪽 asset · 두 줄 텍스트 · 오른쪽 값 · chevron)로 쌓는다. 표는 열 비교가 필요할 때만.
4. **주된 행동은 화면 아래 하나.** 모바일은 `.bottom-cta`(보조는 왼쪽 `dark weak`, 주행동은 오른쪽 fill).
5. **말투는 "~해요"체, 짧게.** 오류는 원인 + 다음 행동: "선택한 회의실은 최대 12명까지 쓸 수 있어요."
6. **같은 색은 같은 뜻.** brand 파랑은 누를 수 있는 것에만 쓴다.
7. 라이트 · 다크 · 375px · 키보드 포커스 · 모션 감소를 모두 지원한다(CSS에 내장).

## 토큰
| 범주 | 값 |
|---|---|
| 회색 | grey50~900 (`#f9fafb` … `#191f28`), 글자는 text-1~4 의미 토큰으로만 |
| 브랜드 · 상태 | blue500 `#3182f6`, red500, green500, orange500 + 각 weak(반투명) |
| 글자 | t1 30/40 · t2 26/35 · t3 22/31 · t4 20/29 · **t5 17/25.5(본문)** · t6 15/22.5 · t7 13/19.5 · t8 12/18 |
| 여백 | 좌우 24px(`--gutter`), 구획 띠 16px, 목록 행 최소 64px |
| 버튼 | small 32 · medium 38 · large 48(기본) · xlarge 56, 반경 8/10/14/16, 누르면 0.96 축소 |
| 반경 | 입력 14, 시트 28, 관리 화면 그룹 16 |

## 컴포넌트
| 용도 | 클래스 |
|---|---|
| 사용자 화면 틀 | `.page` > `.navbar` · `.top`(`.sub-top` `.title` `.desc` `.amount`) |
| 구획 | `.gap16`(굵은 띠) · `.divider` · `.section-head` + `.text-btn` |
| 목록 행 | `.list` > `.row` (`.asset[.square][.brand]` `.texts` `.r-title` `.r-sub` `.right` `.r-value` `.icon.i-chevron`) |
| 키-값 | `dl.kv` |
| 버튼 | `.btn` + `weak` / `dark` / `dark weak` / `danger` · `small` `medium` `xlarge` `full` · 로딩 `aria-busy="true"` |
| 하단 행동 | `.bottom-cta` > `.inner` > `.btn` |
| 입력 | `.field` > `label` + `.input` + `.help`, 오류 `.field.error` |
| 선택 | `.tabs`(밑줄) · `.segmented`(Apple) · `.chips` > `.chip[aria-pressed]` |
| 상태 | `.badge` + `brand` `success` `caution` `danger` · `.notice` · `.progress > i` |
| 비어 있음 · 로딩 | `.empty` · `.skel` |
| 알림 · 시트 | `.toast` · `dialog.sheet` (`.handle` `.s-title` `.s-desc` `.actions`) |
| 관리 화면 틀 | `.shell` > `.sidebar`(`.side-item[aria-current=page]`) + `.main` > `.main-head` `.toolbar` `.search` |
| 관리 화면 내용 | `.metrics` > `.metric` · `.group`(inset grouped 목록) · `.table-wrap` > `.table` (`.r` 숫자 오른쪽 정렬, `th[aria-sort]`) |

## 체크리스트 (마무리 전 1분)
- [ ] 화면 제목이 사용자의 질문에 답하는 문장인가
- [ ] fill 버튼이 화면에 1개인가
- [ ] 그림자 카드 대신 띠 · 그룹으로 구획했나
- [ ] 숫자에 고정폭(`.num` / `.r`)이 적용됐나
- [ ] 빈 상태 · 로딩 · 오류 문구가 "~해요"체로 있나
- [ ] 375px에서 넘침 없음, 다크 모드에서 읽힘

## 에이전트에게 UI를 맡길 때
```
UI는 ../rules/docs/STYLE.md 와 preview.html / preview-admin.html 구조를 따른다.
style.css 클래스만 쓰고 새 CSS는 최소로. "AI 티가 나는 화면" 항목은 하지 않는다.
화면 목적(사용자의 질문 한 문장): …  사용자: …  주된 행동: … (1개)
빈 상태 · 로딩 · 오류 문구까지 만든다.
```
