## Lock

### DB 충돌상황을 개선할 수 있는 방법

1. 데이터를 수정할 때 Lock을 걸고 Lock이 걸려있지 않은 경우에먼 수정할 수 있게하기
2. 수정할 때, 내가 먼저 이 값을 수정했다고 명시해서 다른 사람이 동일 조건으로 수정할 수 없게 하는 것

### 비관적 Lock (Pessimistic Lock)

- 트랜잭션을 이용하여 충돌을 예방하는 방법
- Repeatable Read 또는 Serializable 수준의 격리성 제공
- 트랜잭션이 시작될 때 Shared Lock 또는 Exclusive Lock을 설정
- Shared Lock이 걸려있으면 write를 하기 위해서 Exclusive Lock을 얻어야햐는데 Shared Lock이 다른 트랜잭션에 의해 설정되어있으면 Lock을 얻지 못해서 대기
- 수정하기 위해서는 해당 트랜잭션을 제외한 모든 트랜잭션이 종료되어야함

### 낙관적 Lock (Optimistic Lock)

- A를 B로 업데이트할 때, 값이 A인 데이터를 B로 수정한다고 명시하기
- A라는 값이 다른 값으로 변경되었다면 수정은 이루어지지 않음
- 주로 version이라는 컬럼을 추가해서 사용함
- 어플리케이션 레벨에서 수행

### 비교

- 낙관적 Lock은 트랜잭션을 사용하지 않기때문에 비관적 Lock보다 성능이 좋음
- 낙관적 Lock은 충돌을 해결하기 위해 Application 레벨에서 직접 롤백처리 해줘야하고, 비관적 Lock은 트랜잭션을 롤백하면 됨
- 충돌이 많이 예상되거나 충돌이 발생했을 때 비용이 많이 들거라 생각되는 곳에서는 비관적 Lock을 사용하는 것이 좋음

#### 참고자료

[link](https://sabarada.tistory.com/175)
