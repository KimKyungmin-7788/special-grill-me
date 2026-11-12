# special-grill-me

계획, 결정, 아이디어를 한 번에 한 질문씩 집요하게 인터뷰해서 다듬고, 그 결과를 개발 도구(Claude Code, Codex)에 넘길 문서로 만들어 주는 Claude 스킬입니다. 채팅창에서 쓰도록 만들었습니다.

A Claude skill that grills you about a plan one question at a time, then turns the decisions into a PRD or a handoff set for Claude Code and Codex. The skill is written in Korean.

## 무엇을 하나요

1. **인터뷰** — 한 번에 질문 하나만 묻습니다. 질문마다 선택지 2~4개를 주고 추천안을 첫 번째에 둡니다. 다른 결정을 가장 많이 막고 있는 질문부터 묻습니다.
2. **정리와 확인** — 더 물을 것이 없으면 정해진 결정을 목록으로 보여주고 맞는지 확인받습니다.
3. **산출물 선택** — 확인이 끝나면 무엇을 만들지 고릅니다.
   - 요약만
   - PRD 한 장
   - 개발 인계 세트 (앱, 웹, 도구처럼 개발할 대상일 때)

찾아볼 수 있는 사실은 스킬이 직접 찾고, 결정은 사용자가 합니다. 판단하기 어려워 맡긴 결정은 기록에 '추천안에 맡김'으로 따로 표시됩니다.

## 개발 인계 세트

인터뷰 결과를 개발 도구가 실제로 읽는 자리에 나눠 담습니다.

| 산출물 | 담는 것 |
|---|---|
| PRD.md | 무엇을, 왜, 누구를 위해 만드는지와 성공 기준 |
| AGENTS.md | 매번 지킬 규칙, 기술 스택, 문서 위치 |
| CLAUDE.md | AGENTS.md를 불러오는 한 줄과 Claude Code 전용 규칙 |
| DEVELOPMENT.md | 배포와 운영, 데이터, 개발 단계와 단계별 완료 확인 방법 |
| DESIGN.md | 화면 규칙, 분위기, 화면 목록 |
| 시작 프롬프트 | 개발 도구에 처음 붙여넣는 글 |

- 문서는 폴더째 zip 하나로 전달합니다.
- 시작 프롬프트는 파일이 아니라 채팅에 코드박스로 제시합니다. 복사해서 개발 도구에 바로 붙여넣으면 됩니다.
- 새 프로젝트면 압축을 푼 폴더가 그대로 프로젝트 폴더가 됩니다.
- 기존 프로젝트에 기능을 추가하는 경우에는 기존 지침 파일을 덮어쓰지 않도록, 합칠 조각(AGENTS-add.md)만 만듭니다.
- 인터뷰에서 정하지 않은 것은 지어내지 않습니다. 실행 명령어처럼 프로젝트를 세팅해야 알 수 있는 칸은 비워 두고 개발 도구가 채우게 합니다.

## 설치

**Claude 앱(채팅)** — `skills/special-grill-me` 폴더를 zip으로 묶어 스킬로 올립니다. zip을 열었을 때 맨 위에 `special-grill-me` 폴더가 있어야 합니다.

**Claude Code** — `skills/special-grill-me` 폴더를 `~/.claude/skills/` 아래에 복사합니다.

SKILL.md 하나만 가져가면 안 됩니다. 인계 세트를 만들 때 `references/handoff-templates.md`를 읽기 때문에 폴더째로 설치해야 합니다.

## 사용법

채팅에서 `/special-grill-me`라고 입력하거나 "이 계획 grill me 해줘"처럼 말한 뒤, 다듬고 싶은 계획을 설명합니다.

## 폴더 구성

```
skills/special-grill-me/
  SKILL.md                         인터뷰 진행과 마무리 규칙
  references/handoff-templates.md  인계 문서 템플릿과 시작 프롬프트 틀
```

## 원작과 라이선스

이 스킬은 Matt Pocock의 [mattpocock/skills](https://github.com/mattpocock/skills)에 있는 grill-me와 grilling 스킬을 한국어로 고쳐 하나로 합치고, 채팅창 진행 방식과 개발 인계 세트를 더한 것입니다.

MIT 라이선스로 공개합니다. 원작의 저작권 표시는 [LICENSE](./LICENSE)에 함께 실려 있습니다.
