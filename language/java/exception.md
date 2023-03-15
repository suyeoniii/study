## Checked Exception, Unchecked Exception

### 예외 (Exception)

프로그램 실행 중 예기치 않은 상황이 발생한 것

- Checked Exception
- Unchecked Exception

### Checked Exception

- RuntimeException의 하위 클래스가 아니면서 Exception 클래스의 하위 클래스
- 반드시 에러 처리를 해야하는 특징이 있음 (try/catch, throw)
- 예외 발생 시 트랜잭션 rollback X

### Unchecked Exception

- RuntimeException의 하위 클래스 (=실행 중 발생할 수 있는 예외)
- 체크 예외와 달리 에러 처리를 강제하지 않음
- 예외 발생 시 트랜잭션 rollback O

#### 참고자료

https://devlog-wjdrbs96.tistory.com/351
