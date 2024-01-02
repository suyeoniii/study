## Fetch Type

- 엔티티간 연관관계가 있을 때, 하나의 엔티티에 연관된 다른 엔티티를 찾는 두가지 방법이 있음
- Lazy(지연), Eager(즉시)

### Lazy

- `FetchType.LAZY`
- 지연로딩으로 된 엔티티를 프록시 객체로 가져옴
- 이후 실제로 그 객체를 사용하려고 할 때 초기화됨
- XToMany의 기본 속성이 Lazy

### Eager

- `FetchType.EAGER`
- 엔티티 객체를 로딩할 때 연관된 엔티티들을 모두 join하여 가져옴
- XToOne의 기본 속성이 Eager

### Eager보다 Lazy 권장

- 즉시 로딩을 사용할 경우, join이 아닌 select SQL이 두번 나갈 수 있음
- join이 여러번 걸리면 성능문제 발생 가능
- JPQL에서 N+1 원인이됨

### 결론

- Lazy 옵션 사용하기
- N+1 문제 발생하면 fetch join, Entity Graph 등으로 해결하기

#### 참고자료

https://hello-backend.tistory.com/165
