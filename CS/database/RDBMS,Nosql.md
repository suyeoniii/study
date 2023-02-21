## RDBMS, Nosql

### RDBMS

관계형 데이터베이스 관리 시스템

#### 특징

- 테이블간 관계를 나타내는데 외래키를 이용함
- 외래키로 테이블간 join이 가능함
- 정해진 스키마에 데이터를 저장하므로 명확한 데이터 구조를 가짐 -> 유연성 낮음
- join으로 인한 복잡한 쿼리가 만들어질 수 있음
- scale up만 가능함 (하나의 서버의 용량을 올리는)

### Nosql

관계형 데이터베이스가 아님

#### 특징

- 테이블간 관계를 정의하지 않음
- 명확한 데이터 구조를 보장하지 않음
- 스키마에 맞추어 데이터를 관리하지 않아도 되기때문에 확장성이 좋음
- 데이터 중복이 발생할 수 있으며, 데이터가 변경될 경우 모든 컬렉션에서 수행해야함

#### 종류

##### Key-value Database

- key, value 형태이며 value에는 여러 형태의 데이터를 담을 수 있음
- Redis, Riak, AWS DynamoDB 등

##### Document Database

- Key, Document 형태로 저장됨
- Document는 계층적 형태를 가지는 객체와 유사함
- 객체 - 관계 매핑이 필요하지 않으며 검색에 최적화되어 있다.
- MongoDB, CouthDB 등

##### Wide Column Database

- 키는 Row, Column-family, Column-name을 가짐
- 연관된 데이터는 같은 Column-family에 속하고, 각자 Column-name을 가짐
- HBase, Hypertable 등

##### Graph Database

- Node, Edge, Property와 함께 그래프 구조로 데이터를 표현하고 저장함
- 관계형 모델이라고 할 수 있음
- 연관된 데이터를 추천해주는 추천엔진, 패턴 인식 등으로 적합
- Neo4J 등

### RDBMS, NoSql 각각 언제 사용해야할까?

- RDBMS는 데이터 구조가 변경될 일이 적으며, 데이터 변경이 자주 일어나는 경우
- Nosql은 정확한 데이터 구조를 알 수 없고, 중복이 발생할 수 있으므로 데이터 update가 자주 일어나지 않은 경우 좋음
- Scale out이 필요할 수 있는 시스템에 좋음 (서버를 여러대 추가하여 부하 분산)

#### 참고자료

https://khj93.tistory.com/entry/Database-RDBMS%EC%99%80-NOSQL-%EC%B0%A8%EC%9D%B4%EC%A0%90
