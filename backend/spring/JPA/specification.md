## JPA Specification

- JPA에서 제공하는 Criteria API
- 쿼리를 코드로 작성 할 수 있음

specification 사용할 repository 설정

```java
public interface StockRepository extends JpaRepository<Stock, Long>, JpaSpecificationExecutor<Stock> {
}
```

specification 작성 예제

```java
public class CustomerSpecs {

  public static Specification<Customer> isLongTermCustomer() {
    return (root, query, builder) -> {
      LocalDate date = LocalDate.now().minusYears(2);
      return builder.lessThan(root.get(Customer_.createdAt), date);
    };
  }

  public static Specification<Customer> hasSalesOfMoreThan(MonetaryAmount value) {
    return (root, query, builder) -> {
      // build query here
    };
  }
}
```

specification 사용 예제

```java
List<Customer> customers = customerRepository.findAll(isLongTermCustomer());
```

이런식으로 spec을 repository 함수에 넣어서 사용가능

### QueryDSL과 비교

- JPA Specification은 JPA에서 제공하고, QueryDSL은 정식제공은 아니지만 Hibernate 등에서 사용가능한 오픈소스 형태로 제공됨
- 실무에서는 JPA specification의 경우 join이 들어가거나, 조건이 복잡해지면 코드가 복잡해지므로 QueryDSL 또는 다른 방법을 더 권장함

#### 참고자료

- https://docs.spring.io/spring-data/jpa/reference/jpa/specifications.html
- https://www.inflearn.com/questions/16685/specification-%EB%8C%80%EB%B9%84-querydsl%EC%9D%98-%EC%9E%A5%EC%A0%90%EC%9D%B4-%EC%96%B4%EB%96%A4%EA%B2%83%EC%9D%B4-%EC%9E%88%EC%9D%84%EA%B9%8C%EC%9A%94
