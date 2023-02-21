## HashMap

개념과 작동원리

### HashMap 이란

Map 자료구조는 <key, value>로 이루어져 있으며 중복되지 않는 key를 통해 value를 찾을 수 있다.
HashMap은 이 해시함수를 통해 key가 들어갈 위치를 구하고, 해당 위치에 key, value를 입력한다.
일반 배열에서 비어있는 위치를 찾는 시간복잡도는 `O(n)`이지만, 해시 함수를 통해 key가 들어갈 위치를 찾는 것은 `O(1)`이 된다. 해시 함수를 통해 나온 값에 바로 넣으면 되기 때문이다.

### 해시 충돌

해시함수를 사용할 때 일어날 수 있는 문제이다. 저장소보다 key의 개수가 많은 경우 해시함수를 통해 구한 위치가 중복될 수 있다. 이미 i번째 위치에 값이 있는데, 다른 key를 해시함수에 넣었을 때 i가 나올 수 있는 것이다.

#### 충돌 해결방법 (1)

`Open Addressing`

- 비어있는 다른 칸에 저장하는 방법이다. 비어있는 칸을 구하는 방법도 여러가지가 있다.
  - Linear Probing: 해시 충돌이 발생했을 때 그 위치에서부터 빈값을 찾을때까지 다음칸으로 이동하여 비어있는지 확인하는 방법이다.
  - Quadratic Probing: 충돌위치에 제곱을 한 위치에 데이터 저장
  - Double Hashing: 다른 해시함수를 한번 더 적용하여 나온 위치에 저장

두 방법 모두 배열의 크기가 key값 보다 작을 경우 결국 들어가지 못하는 key가 발생한다는 문제점이 있고, 1번의 경우 특정 위치에 군집이 생길 수 있다는 문제도 있다.

#### 충돌 해결방법 (2)

`Seperate Chaining`

- 이미 i번째 위치에 key가 존재한다면 그 위치에 Linked list를 만들어 넣어두고, key를 찾을 땐 해당 위치의 Linked list를 찾는 것이다.

### Java의 HashMap 구현 방법

- Java에서는 HashMap을 배열에 `Node<K, V>` 형식으로 저장하고 있다. 이 배열을 `버킷`이라고 한다.
- 버킷이 임계점(기본 75%) 이상 채워지면 버킷의 사이즈를 2배 늘린다. (첫번째 해결방법)
- 충돌 초기에는 Linked list 방식으로 충돌을 해결한다. (seperate chaining)
  - Node객체에는 `Node<K, V> next` 값이 존재하여 다음 Node를 알 수 있다.
- 충돌 횟수가 많아지면 Linked list 방식은 효율이 떨어지므로 `트리 (TreeNode)` 방식으로 변환한다.
- 트리형태로 바뀌었을 때 시간복잡도는 `O(log n)`이 된다. 따라서 Linked list보다 효율적이게 된다.

#### 왜 충돌이 많아지면 Linked list 방식에서 트리 형태로 바꾸는 것일까?

어떤 노드가 n번 충돌되어 n번째 Node의 next에 저장되면 해당 노드를 찾는데 `O(n)`이 걸리므로 충돌이 많아지면 많아질수록 효율이 떨어진다.
그렇기 때문에 일정 충돌 횟수를 넘기면 Red-Black 트리로 바꾸어 준다.
이 때 트리를 구성하기 위해 Node객체를 TreeNode 객체로 변환한다. (TreeNode는 Node를 상속하고 있으므로 Node에 일부 값이 추가된 것과 같다.)
TreeNode객체는 트리 구성에 필요한 parent, left, right, prev 값을 추가로 가진다.

#### 처음부터 Linked list가 아니라 트리 형태로 저장하면 안되는 걸까?

처음부터 트리로 저장하게 되면, 저장하는데 더 많은 메모리 공간을 필요로 하고 구현도 복잡해지는 단점이 있다.
반면 Linked list는 구현이 간단하며 저장 공간을 많이 필요로 하지않기 때문에 충돌이 적은 경우 Linked list로, 충돌이 많이 발생하는 경우에만 트리로 변환하는 것이 효율적이다.

#### 참고자료

https://lordofkangs.tistory.com/78
https://preamtree.tistory.com/20