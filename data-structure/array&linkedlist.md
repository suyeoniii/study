## Array, LinkedList

### Array

- element는 메모리에 연속적으로 저장됨 -> index 접근 용이
- 1, 2 ... N 차원
- 메모리는 Array가 선언되자마자 컴파일때 할당됨 (Static Memory Allocation)
- -> Stack 영역에 메모리 할당 이루어짐
- size는 array 선언 시점에 지정되어야함
- Random Access 지원 (index로 element 접근 가능)
- 삽입 및 삭제: 인덱스로 접근 후 삽입, 삭제 `O(1)` + 전체 배열 요소를 1씩 Shift `O(N)`
- 데이터 접근이 빈번한 경우 사용하면 유리함

### LinkedList

- 새로운 element의 메모리 위치 주소가 이전 node에 저장됨
- element는 메모리 어딘가에 저장됨
- Linear(Singly), Doubly, Circular linked list
- 메모리는 새 node가 추가될 때 런타임에 할당됨 (Dynamic Memory Allocation)
- -> Heap 영역에 메모리 할당 이루어짐
- size는 다양할 수 있음 (node가 추가될 때 변경될 수 있음)
- Sequential Access 지원 (element 접근시 순차적으로 찾아야함, O(N))
- 삽입 및 삭제: 위치 접근 후 삽입 및 삭제 `O(N)`, 맨 앞이나 뒤에서 삽입, 삭제한다면 `O(1)`
- 데이터 수정이 빈번한 경우 유리함

#### 참고자료

https://wooono.tistory.com/281
