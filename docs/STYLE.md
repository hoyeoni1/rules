# STYLE — 10분 안에 깔끔한 UI

`style.css`를 그대로 복사해 `<link>`로 붙인다. 프레임워크 없이 클래스만 쓴다. 꾸미기보다 **읽히는 화면**이 목표다.

## 원칙
1. 화면 하나 = 질문 하나에 답한다 ("내 신청 상태는?", "어느 항목이 문제인가?")
2. **숫자가 주인공**: 핵심 지표 3~4개를 `.stats` 카드로 맨 위에
3. 표는 `.table`, 위험은 `.badge-danger`, 주의는 `.badge-warn`, 정상은 `.badge-ok`
4. 계산 기준을 화면에 한 줄(`.note`)로 보여준다 — 숫자만 있으면 안 믿는다
5. 필터 · 옵션은 `.toolbar`에 한 줄로. 값을 바꾸면 결과가 바로 바뀐다
6. 빈 상태 · 오류 상태도 문장으로 (`.empty`): "처리되지 않은 항목 3건 — 기준 범위 밖"
7. 모바일 폭(375px)에서 표는 가로 스크롤(`.table-wrap`)

## 레이아웃 뼈대
```html
<header class="topbar"><h1>제목</h1><span class="muted">기준일</span></header>
<main class="container">
  <div class="toolbar">select · input · button</div>
  <section class="stats">
    <div class="stat"><span class="stat-label">처리 건수</span><span class="stat-value">120 → 96</span></div>
  </section>
  <p class="note">권장 = … (계산식)</p>
  <div class="card"><div class="table-wrap"><table class="table">…</table></div></div>
</main>
```

## 사용자별 화면
- 일반 사용자: **내 것 하나** (검색 → 결과 카드)
- 관리자: **지표 → 문제 목록 → 상세** 순서
