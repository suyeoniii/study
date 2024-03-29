## Optimizer

### Optimizer란

데이터를 기반으로 최적의 실행계획을 결정해주는 것

### 쿼리 실행 과정

1. 파싱
   - sql문을 mysql이 이해할 수 있도록 쪼개어 파스트리에 저장
2. 최적화 및 실행 계획 수립 단계
   - 불필요한 조건 제거, 복잡한 연산 단순화
   - 여러 테이블의 조인이 있는 경우 어떤 순서로 테이블을 읽을지 결정
   - 각 테이블에서 사용된 조건과 인덱스 정보를 통해 사용할 인덱스 결정
   - 각 레코드를 임시테이블에 넣고 가공해야하는지 결정
3. 처리
   - 스토리지 엔진에서 레코드를 읽어오고, mysql 엔진에서 레코드를 조인, 정렬 하는 작업 수행

### 종류

#### 규칙 기반 최적화

- 테이블 레코드 수, 선택도 등을 고려하지 않고 optimizer에 내장된 우선순위로 결정
- 같은 쿼리에 대해 같은 실행계획을 수립
- 현재 대부분의 DBMS에서 사용하지 않음

#### 비용 기반 최적화

- 쿼리를 처리하기 위한 여러 방법을 만들고, 각 작업의 비용, 통계 정보를 활용하여 실행계획별 비용을 산출한다.
- 가장 적은 비용의 실행계획을 선택하여 실행
- mysql 등 대부분의 RDBMS에서 채택

### 기본 데이터 처리

#### 풀 테이블 스캔

- 데이터 수가 적어서 인덱스를 읽는 것보다 풀 테이블 스캔이 나은 경우
- 조건에 사용할 인덱스가 없는 경우
- 조건 일치 레코드가 너무 많은 경우
- InnoDB의 경우 연속된 페이지가 읽히면 백그라운드 스레드에 의해 리드어헤드(Read ahead)를 통해 필요할 것 같은 페이지를 요청이 오기전에 미리 버퍼 풀에 가져다 둔다. (풀 테이블 스캔, 풀 인덱스 스캔 모두)

#### 참고자료

https://willseungh0.tistory.com/161
https://jaehoney.tistory.com/193
