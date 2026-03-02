# 블로그 포스트 작성 (/write)

사용자 요청: $ARGUMENTS

## 개요

`/write`는 초안 작성부터 검수까지 에이전트 파이프라인으로 처리한다.

## 에이전트 파이프라인

1. `series-manager` — 시리즈 컨텍스트 파악
2. `outline-writer` — 이번 회차 개요 설계
3. `writer` — 초안 작성
4. `style-touch` — 문체 다듬기
5. `proofreader` — 기준 검수, 80점 이상이면 posts/에 저장

각 에이전트는 아래 파일을 참조한다:
- `CLAUDE.md`
- `docs/tone-and-manner.md`
- `series-plan.md`

## 저장 경로

drafts/0N-[제목]-draft.md
reviews/review-0N.md
posts/0N-[제목].md   ← proofreader 통과 시

## proofreader 통과 기준

- 서두: 질문 또는 결론으로 시작
- 이전 편과 다른 서두 패턴
- 금지 표현 없음
- 분량: 800~1500자
- 독자가 얻는 것 마지막에 명확히 전달

판정: 80점 이상 통과 / 미만 style-touch 재실행
