# programs — 사전등록 기반 작은 도구 개발 템플릿 (pre-registered small-tool workflow)

프로그램 하나 = 폴더 하나 = 로컬 git 저장소 하나.

## 흐름
아이디어 → 사전등록(PREREG) → MVP → 측정 → 판정 → 발전 / 보류

| 단계 | 하는 일 | 완료 기준(이게 있어야 다음 단계) |
|---|---|---|
| 0. 아이디어 | 출처·문제·쓸 사람 한 줄씩 | `README.md`에 문제/사용자/출처 3줄, 이미 있는 코드·도구 확인 결과 1줄 |
| 1. 사전등록 | 성공 기준·측정법·시험 대상을 **결과 보기 전에** 고정 | `PREREG.md` 작성 + 커밋(커밋 시각 = 고정 시각). 이후 기준 변경은 `## 변경` 절에 날짜·이유로만 추가 |
| 2. MVP | 기준을 시험할 수 있는 최소 기능 | `python3 -I <tool>.py --help` 동작, `tests/` 1개 이상 통과, 외부 코드 실행 0 |
| 3. 측정 | PREREG의 시험 대상에 실제로 돌림 | 원시 결과를 `results/<날짜>.*`에 저장(요약이 아니라 출력 원본), 무엇을 센 숫자인지 명시 |
| 4. 판정 | PREREG 기준 대비 PASS/FAIL | `PREREG.md` `## 판정` 절: 기준별 PASS/FAIL + "규칙 밖 판단" 따로 |
| 5. 발전/보류 | 다음 버전 PREREG 또는 보류 사유 | 발전: 새 PREREG 버전(v2). 보류: 사유·재개 조건을 카드 결정 로그에 |

## 규칙
- Python 표준 라이브러리 우선. 외부 패키지가 필요하면 README에 이유를 적는다.
- 다운로드한 외부 코드는 실행하지 않는다(텍스트로만 읽음).
- 판정은 착지로만. rc=0·HTTP 200은 자기보고.
- 삭제는 휴지통으로. 외부 게시·설정 변경은 사람 승인 후.
- 커밋 메시지 끝: `Co-Authored-By: Claude Sonnet 5.5 <noreply@anthropic.com>`
- 단계가 끝나면 프로젝트 기록(카드)을 그날 갱신.

## 새 프로그램 시작
```sh
cd <작업 폴더>
cp -R _template <이름> && cd <이름> && git init -q
# README.md·PREREG.md 채우고 → git add -A && git commit -m "prereg: <이름> v1"
```

## 목록
| 이름 | 단계 | 판정 | 비고 |
|---|---|---|---|
| repo-sniff | 4. 판정 | PASS 6 / FAIL 1 (기대 등록 오류) | GitHub 저장소 위험 점검 |
| vault-doctor | 4. 판정 | PASS 7 / FAIL 0 (정의 위반 1 정정) | Obsidian 볼트 점검, 읽기 전용 |

---
## English
A folder-per-tool template: idea → pre-registration (`PREREG.md`, committed before results) → MVP → measurement (raw output in `results/`) → PASS/FAIL verdict → next version or shelve.
Start a new tool: `cp -R _template <name> && cd <name> && git init`.

## License
MIT
