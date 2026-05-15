# 신나는 자기이해 — 프로젝트 가이드

## 프로젝트 개요
에릭슨 심리사회 발달 이론 기반 캐릭터 육성 게임.
사용자가 매일 감정을 입력하면 캐릭터가 성장하고, 16가지 빛 유형 중 하나로 최종 형태가 결정됨.

## 파일 구조
- `index.html` — 단일 파일 게임 (HTML + CSS + JS 통합)
- `CLAUDE.md` — 이 파일
- `plan.md` — 작업 계획 및 기록

## 핵심 규칙
- **아이보리 톤 디자인** 절대 유지 (CSS :root 변수 기준)
- 기능 추가 시 기존 코드 수정 최소화, 추가 방식 우선
- 이미지 파일 금지 — CSS/SVG 전용
- localStorage key: `snj`

## 주요 데이터 구조 (G 객체)
| 필드 | 설명 |
|------|------|
| lv, xp | 레벨·경험치 |
| name, charColorIdx | 캐릭터 이름·무지개 색 인덱스 |
| emotions[] | 감정 기록 |
| profile | 감정 성향 프로파일 (w/c/i/g/d/s/cl/df) |
| type | 16가지 빛 유형 키 |
| decor | 방 꾸미기 설정 |
| diary[] | 감정 일기 |
| seenEvents[] | 이미 본 이벤트 title |
| todayEventCount, lastEventDate | 하루 이벤트 횟수 |
| todayFeedCount, lastFeedDate | 하루 먹이주기 횟수 |
| trees[], currentTree | 나뭇잎 달기 게임 데이터 |

## XP 구조
| 행동 | XP |
|------|----|
| 감정 체크인 | +5 |
| 감정 먹이주기 (하루 최대 3회) | +3 |
| 이벤트 시뮬레이션 | +15~+25 (단계별) |
| 마음 풍선 불기 | +15 |
| 생각 분리수거 | +18 |
| 나뭇잎 달기 (나무 완성) | +10 |

## 배포
- GitHub: https://github.com/cozycactus01/ma
- Vercel: https://ma-cozycactus.vercel.app/
