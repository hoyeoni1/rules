# rules

Codex와 작업할 때 쓰는 규칙 모음. **받아오기만 한다** — 작업물은 push · 업로드 · 외부 전송 금지, 커밋은 로컬에만.

## 시작할 때 (한 번)
```bash
git clone https://github.com/hoyeoni1/rules ../rules
cp ../rules/AGENTS.md ../rules/PLAN.md ../rules/templates/DESIGN.md ../rules/templates/HANDOFF.md .
```
AGENTS.md가 이미 있으면 cp 대신 `cat ../rules/AGENTS.md >> AGENTS.md`

## 언제 어떤 파일
| 언제 | 파일 | 어떻게 |
|---|---|---|
| 항상 | `AGENTS.md` | Codex가 알아서 읽음. 내가 열 필요 없음 |
| 요구사항 받자마자 | `PROMPTS.md` 1 | 붙여 넣기 → 요구사항 목록 · "정의 필요" 목록 받음 |
| 담당자에게 물을 때 | `PLAYBOOK.md` 2 | 질문 은행에서 골라 묻기. 안 알려주면 질문을 바꿔서 |
| 답을 받았을 때 | `PLAN.md` · `DESIGN.md` 3 | 내가 직접 한 줄: 기준 · 값 · 누구 HH:MM |
| 설계할 때 | `PROMPTS.md` 2 | 붙여 넣기 → DESIGN.md 채워짐 |
| 기능 만들 때 (반복) | `PROMPTS.md` 3 → 5 → 4 | 맡기기 → 설명 듣기 → 리뷰 → 커밋 |
| AI가 틀렸을 때 · 결정했을 때 | `PLAN.md` | AI 오류 / 결정 로그에 한 줄 |
| 다 만들고 검증할 때 | `PROMPTS.md` 6 | 규모 ×10 · ×100 측정 |
| 마지막 10% (새 기능 금지) | `PROMPTS.md` 8 → `QA.md` | HANDOFF 채우기 → 질문 리허설 → 1장 요약 |
| 질문에 답할 때 | `QA.md` | 결론 → 근거 → 검증 → 한계 |
| 화면 필요할 때 | `docs/STYLE.md` | Codex에게 "docs/STYLE.md 따라라" |

## 꼭 지킬 3가지
1. 결정할 때마다 PLAN.md에 한 줄 (결정 / 이유 / 버린 대안)
2. AI가 틀린 것 2건 이상 기록
3. "해줘" 금지 — 범위 · 제약 · 테스트 명령을 같이 준다

같은 오류 3번이면 범위 줄이고 PLAN "한계"에 적고 넘어간다.

---
Pretendard: SIL OFL 1.1 (`docs/fonts/OFL.txt`)
