# 작업 기록

## 완료된 작업

### XP 구조 수정 (완료)
- [x] DEF에 todayFeedCount: 0, lastFeedDate: null 추가
- [x] load()에 todayFeedCount, lastFeedDate 반영
- [x] openFeed() — 하루 3회 제한 체크
- [x] confirmFeed() — +8 → +3, 카운터 증가
- [x] EVENTS 24개 xp 값 상향 (+15~+25)
- [x] balloonRelease() — +10 → +15
- [x] closeSortDone() — +12 → +18
- [x] addTreeLeaf() — +15 → +10

### 이벤트 중복 방지 (완료)
- [x] seenEvents[] 배열 추가
- [x] maybeEvent() — 미봤던 이벤트만 필터링, 전부 본 경우 리셋

### 나뭇잎 달기 나무 SVG 개선 (완료)
- [x] 대칭 → 비대칭 cubic bezier 곡선으로 재설계
- [x] 좌우 가지 각도 비대칭 (40° vs 65°)
- [x] 4단계 굵기 테이퍼링

### Supabase 인증 강화 (완료)
- [x] doLogin() — try/catch 추가, data.user 체크, G.name 게이트
- [x] doSignUp() — try/catch 추가, 모든 경로에서 G.name 확인 후 enterAfterAuth() 호출

---

## 현재 아키텍처

### 미니게임 4종
| 게임 | 함수 | XP |
|------|------|----|
| 감정 먹이주기 | openFeed / confirmFeed | +3 (하루 3회) |
| 마음 풍선 불기 | openBalloon / balloonRelease | +15 |
| 생각 분리수거 | openSort / closeSortDone | +18 |
| 나뭇잎 달기 | openTree / addTreeLeaf | +10 (나무 완성 시) |

### EVENTS xp 변환표 (확정)
| 단계 | xp 값 |
|------|-------|
| 1단계 3개 | 15, 15, 16 |
| 2단계 3개 | 16, 17, 16 |
| 3단계 3개 | 17, 18, 17 |
| 4단계 3개 | 18, 19, 18 |
| 5단계 3개 | 20, 21, 21 |
| 6단계 3개 | 19, 19, 20 |
| 7단계 3개 | 22, 23, 22 |
| 8단계 3개 | 24, 25, 25 |

### G 객체 DEF (최종)
```javascript
const DEF = {
  lv:1, xp:0,
  name: null, charColorIdx: null,
  lastPlayed:null, lastCheckin:null,
  lastEventDate:null, todayEventCount:0,
  lastFeedDate:null,  todayFeedCount:0,
  emotions:[],
  profile:{ w:0,c:0,i:0,g:0,d:0,s:0,cl:0,df:0 },
  type:null,
  decor:{ wall:0, light:0, prop:0 },
  diary:[],
  seenEvents:[],
  trees:[],
  currentTree: null,
};
```
