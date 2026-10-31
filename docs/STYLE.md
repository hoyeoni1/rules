# STYLE — 운영 수준 UI (Pretendard · Apple/Toss 톤)

의존성 없는 CSS 한 벌. 디자인 토큰 → 컴포넌트 순서로 되어 있고, 라이트/다크 · 모바일 · 접근성까지 포함한다.

## 붙이는 법
```
cp -r ../rules/docs/fonts ../rules/docs/pretendard.css ../rules/docs/style.css static/
```
```html
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<link rel="stylesheet" href="/static/pretendard.css">
<link rel="stylesheet" href="/static/style.css">
```
폰트는 저장소에 번들(오프라인 동작). 견본: `docs/preview.html`을 브라우저로 연다.

## 톤 원칙
1. **여백이 위계를 만든다.** 선 · 그림자보다 간격. 카드 안 24px, 카드 사이 16px, 섹션 사이 24px+
2. **한 화면 한 목적.** 제목 한 줄로 이 화면의 질문을 말한다 ("이번 주 처리 현황")
3. **숫자가 주인공.** 핵심 지표 3~4개를 `.stats` 맨 위에, 단위는 작게
4. **색은 의미에만.** 기본은 회색조 + 파랑 1색. 초록/주황/빨강은 상태 표시에만
5. **행동은 하나만 강조.** 화면당 primary 버튼 1개. 나머지는 secondary/tertiary
6. **말투는 짧고 정중하게.** "~했어요" 체. 오류는 원인 + 다음 행동 ("파일 형식이 달라요. CSV로 올려 주세요")
7. **빈 화면 · 로딩 · 오류도 디자인한다.** `.empty` · `.skeleton` · `.banner.danger`

## 토큰 (style.css 상단)
| 범주 | 값 |
|---|---|
| 색 | gray 50~900 · blue-500 `#3182f6` · green/orange/red 상태색 · 다크 모드 자동 |
| 글자 | display 32 / title1 26 / title2 22 / title3 19 / body 16 / sub 15 / caption 13 / micro 12, 자간 -0.01~-0.03em, `word-break:keep-all` |
| 간격 | 4pt 단위 4 · 8 · 12 · 16 · 20 · 24 · 32 · 40 · 48 |
| 반경 | 8 · 12 · 16 · 20 · full |
| 그림자 | sh-1(카드) · sh-2(떠 있는 것) · sh-3(모달 · 토스트) |
| 모션 | 180ms, `cubic-bezier(.2,.8,.2,1)`, 모션 감소 설정 존중 |

## 컴포넌트
| 용도 | 클래스 |
|---|---|
| 상단바(블러) | `.app-header` `.brand` `.spacer` |
| 레이아웃 | `.container` `.page-head` `.stack` `.grid-2` `.row` |
| 카드 | `.card` `.card-head` `.section-title` |
| 지표 | `.stats` > `.stat` (`.stat-label` `.stat-value` `.stat-delta.up/.down`) |
| 목록(토스형 행) | `.list` > `.list-item` (`.lead` `.body` `.title` `.meta` `.trail`) |
| 표 | `.table-wrap` > `.table`, 숫자 칸 `td.num` |
| 버튼 | `.btn` + `.secondary` `.tertiary` `.ghost` `.danger` / `.sm` `.lg` `.block` / 로딩 `aria-busy="true"` |
| 입력 | `.field` > `.label` + `.input` / `.select` / `.textarea` + `.help`, 오류 `.field.error` |
| 세그먼트 | `.segmented` > `button[aria-pressed]` |
| 필터 줄 | `.toolbar` |
| 상태 | `.badge.ok/.warn/.danger/.info/.neutral` · `.banner.info/.warn/.danger` · `.progress` |
| 로딩 · 빈 상태 | `.skeleton` · `.empty` |
| 알림 · 모달 | `.toast-area` > `.toast` · `dialog.sheet` (모바일에서 바텀시트) |
| 모바일 하단 CTA | `.bottom-cta` > `.btn.lg.block` |

## 화면 패턴
- **조회형(일반 사용자):** page-head → 검색 `.input` → 결과 `.card` 1개 → 관련 `.list`
- **관리형(관리자):** page-head → `.toolbar`(필터 · 세그먼트) → `.stats` → 문제 항목 `.list` 또는 `.table` → 상세 `dialog.sheet`
- **입력형:** `.card` 안에 `.field` 세로 나열 → 하단 primary 1개 (모바일은 `.bottom-cta`)

## 체크리스트 (마무리 전 1분)
- [ ] primary 버튼이 화면당 1개인가
- [ ] 숫자에 `.num`(고정폭 숫자)이 적용됐나
- [ ] 빈 상태 · 로딩 · 오류 문구가 있나
- [ ] 375px 폭에서 가로 넘침이 없나 (표는 `.table-wrap`)
- [ ] 키보드 Tab으로 포커스 링이 보이나
- [ ] 다크 모드에서 글자가 읽히나

## 에이전트에게 UI를 맡길 때
```
UI는 ../rules/docs/STYLE.md 를 따른다. style.css 클래스만 쓰고 새 CSS는 최소로.
화면 목적: (한 줄). 사용자: (누구). 핵심 지표: (3개). 주요 행동: (1개).
빈 상태 · 로딩 · 오류 문구까지 만든다. 끝나면 375px · 1280px 폭에서 확인한다.
```
