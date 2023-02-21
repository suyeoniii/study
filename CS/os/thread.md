## Thread (스레드)

### 스레드란?

프로세스 내에서 실행되는 흐름의 단위
하나의 프로세스는 기본적으로 하나의 스레드를 가지고 있으며, 여러 스레드를 동시에 가질 수도 있다. (멀티스레드)
별도의 register, stack을 가지며, 나머지는 프로세스내 다른 스레드와 공유한다.

### 장점

- 하나의 프로세스 내의 자원을 공유하기 때문에 프로세스에 비해 자원 할당 비용 및 Context Switching 비용이 적게 든다.
- 다중 스레드의 경우 일부 스레드의 처리가 지연되더라도 다른 스레드에서 작업을 처리할 수 있음
- 프로세스 간의 통신은 IPC가 필요하지만, 스레드는 공유 주소 공간 (데이터, 힙) 을 사용하여 데이터 교환 가능
- 프로세스를 생성하여 자원을 할당하는 시스템 콜이 줄어듬

### 단점

- 하나의 스레드에서 발생한 문제가 프로세스 전반에 영향을 미칠 수 있음
- 자원을 공유하기 때문에 동기화 문제가 발생할 수 있음

#### 참고자료

https://cocoon1787.tistory.com/849