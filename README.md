# rules

AI 코딩 에이전트(Codex)와 일할 때 쓰는 개인 작업 규칙. 코드는 없고, 규칙과 문서 뼈대만 있다.

- `AGENTS.md` — 에이전트가 자동으로 읽는 작업 규칙 (정의 우선 · 작은 범위 · 사람 기준 검증 · 기능 단위 커밋 · 보고 형식)
- `PLAN.md` — 요구사항 · 정의 · 결정 로그 · AI 오류 · 검증 · 한계 뼈대

- `PLAYBOOK.md` — 타임박스 진행 순서 · 요구사항 확인 질문 · 예외 케이스 · 검증 · 성능 · 대규모 점검
- `templates/` — DESIGN.md, HANDOFF.md
- `docs/STYLE.md`, `docs/style.css`, `docs/pretendard.css` — 운영 수준 UI (Pretendard 번들 · 토스/Apple 원칙 · 라이트/다크), 견본 `docs/preview.html` · `docs/preview-admin.html`

## 사용
```
git clone https://github.com/hoyeoni1/rules ../rules
cp ../rules/AGENTS.md ../rules/PLAN.md ../rules/templates/DESIGN.md .
# UI: cp -r ../rules/docs/fonts ../rules/docs/pretendard.css ../rules/docs/style.css static/
```

## 라이선스
Pretendard: SIL Open Font License 1.1 (`docs/fonts/OFL.txt`)
