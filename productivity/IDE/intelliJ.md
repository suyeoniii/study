# IntelliJ

Preference - keymap 참고

### 공통

- `⌘ + ⇧ +` ➡️ 커서기준 오른쪽 단어들 포커스

- `cmd + L` 현재 줄 선택

### intelliJ

- `command + ,` preference 열기

- `⌘ + N` Generate

- `⌥ + ⌘ + M` Extract Method - 함수로 추출하기
- `⌥ + ⌘ + P` Extract Parameter - 함수의 파라미터로 추출하기
- `⌥ + ⌘ + V` Extract Variable 변수화
- `⌘ + ⇧ + T` Choose Test Subject - 테스트파일에서 테스트할 대상이 되는 파일로 이동할 수 있음 or Create Test
- `⌥` + `enter` 도움말
- `F2` 이 파일에서 오류나는 위치로 이동
- `⌘` + `⇧` + enter 보기중에서 그냥 enter를 누르면 세미콜론이 안들어가지만, 이 키를 누르면 들어감
- `⌥` + ↩️ ? - 개선
- `⌘ +` E 코드 히스토리 조회
- `^ + R` Run
- `^ + D` Debug 모드로 실행
- `⌥ + ⌘ + N` Inline variable
- `⇧` + `F6` rename 한번에
- `^` + `O` Select Method to Override/Implement
- `Shift + Shift` 전체 검색
- `⌘ + Shift + a` 액션 검색 (Refactor 등)
- `⌘ + Shift + o` 파일 찾기
- `⌘ + e` 최근 열었던 파일 리스트
- `⌘ + [` 이전 포커스로 이동
- `⌘ + ]` 다음 포커스로 이동

### 단축어

psvm타이핑 + enter main 코드 생성

```kotlin
public static void main(String[] args) {

}
```

sout + enter키

```java
System.out.println("")
```

### 디버깅

- 코드 라인 좌측을 클릭해서 `Break point` 생성
- Break point에 `우클릭`하면 `Condition` 설정해서 조건에 따라 Break 걸기 가능
- break시 할 수 있는 동작
  - resume: 다음 break point로 이동 `⌥ + ⌘ + R`
  - step over: 다음 라인으로 이동 `F8`
  - step into: 함수 내부로 이동 `F7`
  - force step into: 함수 내부로 이동 (설정과 상관없이 전부 확인) `⇧ + F7`
  - step out: 함수 밖으로 이동 (라인을 실행하고) `⇧ + F8`
  - drop frame: 함수 밖으로 이동 (라인을 실행하지 않고)
  - run to cursor: 커서가 있는 라인까지 실행 `⌥ + F9`

#### 참고자료

- https://jojoldu.tistory.com/149
