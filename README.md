# rules

AI 코딩 에이전트(Codex)와 타임박스 웹앱 작업을 할 때 쓰는 개인 작업 규칙. 코드는 없고, 규칙 · 문서 뼈대 · 지시문 · UI 스타일만 있다.

## 바로 쓰기

### 1. 가져오기 (작업 폴더 안에서)
```bash
git clone https://github.com/hoyeoni1/rules ../rules

# AGENTS.md가 이미 있으면 덮어쓰지 않고 뒤에 붙인다
if [ -f AGENTS.md ]; then cat ../rules/AGENTS.md >> AGENTS.md; else cp ../rules/AGENTS.md .; fi
cp ../rules/PLAN.md ../rules/templates/DESIGN.md ../rules/templates/HANDOFF.md .
git add AGENTS.md PLAN.md DESIGN.md HANDOFF.md && git commit -m "docs: 작업 규칙 · 계획 뼈대"
```
상위 폴더에 쓸 수 없으면 작업 폴더 안에 받고, 커밋에 섞이지 않게 제외한다:
```bash
git clone https://github.com/hoyeoni1/rules .rules && echo ".rules/" >> .git/info/exclude
# 이후 ../rules 대신 .rules 경로를 쓴다 (AGENTS.md 안의 ../rules 도 .rules 로 바꾼다)
```
UI가 필요하면: `cp -r ../rules/docs/fonts ../rules/docs/pretendard.css ../rules/docs/style.css <정적 파일 폴더>/` 후 `docs/STYLE.md` 를 따른다.

### 2. 진행 (비율은 전체 시간 기준)
| 비중 | 할 일 | 쓰는 것 |
|---|---|---|
| 10% | 요구사항 · 데이터 읽기, 질문 목록 | `PROMPTS.md` 1 |
| 15% | 요구사항 확인 질문 → 합의를 **시각과 함께** 기록 | `PLAYBOOK.md` 2, DESIGN 3 제약 표 |
| 10% | 설계 확정 | `PROMPTS.md` 2 |
| 40% | 기능 하나씩: 맡기기 → 테스트 → 리뷰 → 커밋 | `PROMPTS.md` 3 · 4 · 5 |
| 15% | 검증 · 규모 측정 | `PROMPTS.md` 6, `PLAYBOOK.md` 5 |
| 10% | HANDOFF, 질문 리허설, 1장 요약 — **새 기능 금지** | `PROMPTS.md` 8, `QA.md` |

### 3. 손으로 지키는 것 3가지
1. **결정할 때마다 PLAN.md에 한 줄** — 결정 / 이유 / 버린 대안. 합의는 상대 · 시각까지.
2. **AI가 틀린 것 최소 2건 기록** — 무엇이 / 어떻게 발견 / 어떻게 수정.
3. **"해줘" 한 줄로 맡기지 않는다** — 범위 · 제약 · 완료 기준(테스트 명령)을 같이 준다. 받아들이기 전에 설명을 듣고(`PROMPTS.md` 5) 내가 이해한 것만 커밋한다.

막히면: 같은 오류 3번이면 범위를 줄이고 PLAN "한계"에 적고 넘어간다.

## 파일
- `AGENTS.md` — 에이전트가 자동으로 읽는 작업 규칙 (정의 우선 · 작은 범위 · 구조 경계 · 사람 기준 검증 · 기능 단위 커밋 · 보고 형식)
- `PROMPTS.md` — 단계별로 붙여 넣는 지시문 (시작 · 설계 · 위임 · 리뷰 · 설명 받기 · 규모 · 마무리)
- `PLAN.md` — 요구사항 · 정의 · 결정 로그 · AI 오류 · 검증 · 실행 방법 · 한계
- `PLAYBOOK.md` — 진행 순서 · 요구사항 확인 질문 · 예외 케이스 · 검증 · 성능 · 판단 원칙
- `QA.md` — 작업 직후 기술 질문 대비: 질문 8유형 · 답변 틀 · 리허설 프롬프트 · 1장 요약
- `templates/` — DESIGN.md, HANDOFF.md
- `docs/STYLE.md`, `docs/style.css`, `docs/pretendard.css` — 운영 수준 UI (Pretendard 번들 · 토스/Apple 원칙 · 라이트/다크), 견본 `docs/preview.html` · `docs/preview-admin.html`

## 라이선스
Pretendard: SIL Open Font License 1.1 (`docs/fonts/OFL.txt`)
