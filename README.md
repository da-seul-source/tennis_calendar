# tennis_calendar

테니스 코트 일정 캘린더. `index.html` 한 장으로 동작하고, 데이터는 Firebase Firestore의 `events` 컬렉션에 저장된다.
(BSH-court-calendar에서 갈라져 나왔고, Firebase 프로젝트는 따로 쓴다.)

## 설정
1. `index.html`의 `firebaseConfig`를 새 Firebase 프로젝트 값으로 바꾼다.
2. `index.html`의 `MEMBERS`에 회원 명단을 적는다.
3. Firebase 콘솔 → Firestore Database → 규칙 탭에 `firestore.rules` 내용을 붙여 넣고 게시한다.
