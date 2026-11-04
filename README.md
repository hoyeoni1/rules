# rules

Codex와 작업할 때 쓰는 규칙 모음. **받아오기만 한다** — 작업물은 push · 업로드 · 외부 전송 금지, 커밋은 로컬에만.

## 시작할 때 (한 번)
```bash
git clone https://github.com/hoyeoni1/rules ../rules
cp ../rules/AGENTS.md ../rules/PLAN.md ../rules/templates/DESIGN.md ../rules/templates/HANDOFF.md .
```
AGENTS.md가 이미 있으면 cp 대신 `cat ../rules/AGENTS.md >> AGENTS.md`

## 진행 방법
**STEP 1부터 순서대로.** 붙여 넣을 필요 없이 Codex에 이렇게만 친다:
```
STEP 1
STEP 4 R2 / 파일: app/service.py, tests/ / 제약: C1, C3 / 테스트: pytest -q
STEP 5 R2
STEP 6   ← 리뷰는 두 번째 세션에서
```
Codex가 `PROMPTS.md`에서 해당 지시문을 찾아 따른다. 빈칸(R번호 · 파일 · 제약 · 테스트 명령)은 **내가 정해서** 같이 친다 — 이게 내 판단이 드러나는 부분이다.
체크는 작업 폴더의 **`PLAN.md` 맨 위 "진행 체크"** 에서 한다 (번호가 같다).

| STEP | 할 일 | 같이 쓰는 파일 |
|---|---|---|
| 1 | 시작: 요구사항 · 데이터 요약 · 정의 필요 목록 | PLAN.md |
| 2 | 담당자 확인 (내가 직접) | PLAN.md 정의, DESIGN.md 제약 표 |
| 3 | 설계 | DESIGN.md |
| 4 → 5 → 6 | R마다 반복: 맡기기 → 설명 받기 → 리뷰 | PLAN.md 요구사항 · AI 오류 |
| 7 | 검증 · 규모 | HANDOFF.md 성능 표 |
| 8 | 마무리 (새 기능 금지) | HANDOFF.md → QA.md |

그 외 파일: `AGENTS.md` Codex가 자동으로 읽음 · `QA.md` 질문에 답할 때 (결론 → 근거 → 검증 → 한계) · `PLAYBOOK.md` 질문이 막힐 때 · `docs/STYLE.md` 화면 필요할 때

## 꼭 지킬 3가지
1. 결정할 때마다 PLAN.md에 한 줄 (결정 / 이유 / 버린 대안)
2. AI가 틀린 것 2건 이상 기록
3. "해줘" 금지 — 범위 · 제약 · 테스트 명령을 같이 준다

---
Pretendard: SIL OFL 1.1 (`docs/fonts/OFL.txt`)
