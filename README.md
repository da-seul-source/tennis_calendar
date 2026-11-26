# tennis_calendar

개인용 테니스 코트 일정 캘린더. `index.html` 한 장으로 동작하고, 데이터는 Firebase Firestore의 `events` 컬렉션에 저장된다.
(BSH-court-calendar에서 갈라져 나왔고, Firebase 프로젝트는 따로 쓴다.)

## 화면
- 큰 월간 달력 + 고른 날의 일정 카드. 위쪽 토글로 '다가오는 일정' 목록으로 바꿔 볼 수 있다.
- 카드: 테니스장·코트 번호(주정보), 유형, 캔볼(내가 챙길 때만 공 아이콘), 시간, 참석자, 정산 상태.
- 정산
  - 내 코트: 참석자 이름을 눌러 정산 받음(✓) 표시. 다 받으면 '정산 완료'.
  - 남 코트: '정산 전' 버튼을 눌러 '정산 완료'로.
- 금액: (코트비 + 캔볼 값) ÷ 참석 인원, 10원 단위 올림. 캔볼 가져온 사람은 캔볼 값을 빼고 낸다.
  카드에 내 코트면 '1인 금액'을 보여 준다. 남 코트는 계산 없이 '내가 낼 돈'만 적는다 (myDue).
- 인원: 여/남 정원. 남는 자리는 카드에 빈자리로 보인다 (대기 없음).
- 종류: 코트(코트비 나눠 내기) / 행사(클럽·교류전·대회, 1인 참가비, 주최에게 정산).
- 카드를 누르면 수정·삭제, 오른쪽 아래 버튼으로 등록.

## 일정 문서 필드
`date, start, end, place, court, gameType, capF, capM, capacity, memo, courtFee, ballPrice, participants[{id,name,gender,at}], mine, host, ball, ballOwner, paid[이름], myPaid, kind(court|club), clubTag, feeMode, entryFee, createdAt`

## 설정
1. `index.html`의 `firebaseConfig`를 Firebase 프로젝트 값으로 바꾼다.
2. `index.html`의 `ME`에 캘린더 주인 이름을 적는다.
3. Firebase 콘솔 → Firestore Database → 규칙 탭에 `firestore.rules` 내용을 붙여 넣고 게시한다.
