## Collection

데이터의 집합, 그룹을 의미함

Collection 인터페이스가 존재하며 상위 3개 클래스 List, Set, Queue로 분류된다.
Map 인터페이스는 Collection을 상속받고 있지는 않지만 Collection으로 분류한다.

### Set

순서를 유지하지 않는 데이터의 집합. 데이터의 중복이 허용되지 않음

- HashSet: 빠른 접근 속도, 순서 예측 불가
- TreeSet: 정렬방법을 지정할 수 있음

### List

순서가 있는 데이터의 집합. 데이터의 중복을 허용함

- LinkedList: 양방향 포인터 구조. 데이터 삽입, 삭제가 빈번한 경우 위치 정보만 수정하면 된다는 장점
- Vector: 자동으로 동기화 처리가 일어나 성능이 좋지않아 잘 사용하지 않음
- ArrayList: 단방향 포인터 구조. 각 데이터에 대한 인덱스를 가지고 있어 조회 성능이 좋음

### Queue

FIFO (First In First Out) 구조

- PriorityQueue: 우선순위에 따라 객체를 처리할 때 사용

### Map

키, 값의 쌍으로 이루어진 데이터 집합
순서는 유지되지 않으며 키의 경우 중복을 허용하지 않음

- HashTable: HashMap보다 느리지만 동기화 지원. null 불가능
- HashMap: 중복과 순서가 허용되지 않음. null 가능
- TreeMap: 정렬된 순서대로 키, 값을 저장하여 검색이 빠름

#### 참고자료

https://gangnam-americano.tistory.com/41
