## Key

### index

데이터 검색을 위해 사용

### Primary Key (PK)

- null을 허용하지 않음
- unique
- PK컬럼은 테이블내에서 행을 식별할 수 있는 고유값을 가짐

#### 단일키

테이블이 하나의 PK를 가지는 것

#### 복합키

테이블이 여러 PK를 가지는 것

#### 단일키 vs 복합키

복합키 설정시

- 다른 테이블에서 FK를 설정할 때 복합키를 모두 FK로 가져야함
- 여러 컬럼이 PK로 설정되어있기 때문에, WHERE 조건에 하나의 PK만 적용하면 인덱스가 사용되지 않음

=> 가능하면 단일키를 사용하는 것이 더 좋음

### Unique Key

- 고유한 값으로 이루어진 index
- null 허용 가능
- 테이블 당 여러개 가질 수 있음

### Foreign Key (FK)

다른 테이블의 PK를 참조하는 column
Join조건으로의 역할을 함

#### Options

- RESTRICT: 값의 변경, 삭제를 제한함
- CASCADE: 상태 key값도 변경, 삭제함
- SET NULL: 변경, 삭제시 fk값을 null로 변경
- NO ACTION: mysql에서는 RESTRICT옵션과 동일
- SET DEFAULT: 변경, 삭제시 default 값으로 변경

#### 참고자료

https://jins-dev.tistory.com/entry/MySQL-%EC%97%90%EC%84%9C-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-Key-%EC%9D%98-%EC%A0%95%EC%9D%98%EC%99%80-%EC%A2%85%EB%A5%98%EB%93%A4%EC%97%90-%EB%8C%80%ED%95%98%EC%97%AC
