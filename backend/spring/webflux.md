## Webflux

### 관련 용어

- 동기: 호출과 응답이 동시에 이루어지는 것
- 비동기: 호출과 응답이 동시에 이루어지지 않는 것
- 블로킹: 함수 호출 후 응답을 받기까지 멈춰있는 상태
- 논블로킹: 함수 호출 후 응답 받기를 기다리지 않고 다음 작업을 실행하는 상태

### Spring MVC

- 동기, 블로킹 방식
- 사용자 요청마다 스레드를 생성하므로 동시에 많은 요청이 들어오면 처리하지 못하는 문제(Thread Pool Hell)가 있음
  -> Thread pool size를 잘 조절해야함

### Spring Webflux

Spring 5, Spring Boot 2 부터 추가됨

- 비동기, 논블로킹 방식
- Reactive Programming (반응형 프로그래밍)
- 이벤트 루프
- 모든 코드가 논블로킹하게 동작해야 의미가 있다 -> 특정 구간에서 블로킹이 발생하면 mvc처럼 thread pool hell 현상 발생 가능

### Webflux와 MVC 차이

Spring MVC

- 동기적인 방식
- 블로킹 방식
- 명령형 프로그래밍
- JDBC, JPA 지원

Webflux

- 비동기적인 방식
- 논블로킹 방식
- 반응형 프로그래밍
- 반응형 라이브러리 지원

### mono, flux

Spring webflux에서 사용하는 reacttive library는 Reactor이다.
Reactor는 Reactive Streams의 구현체이고 mono, flux는 Reactor 객체이다.
둘의 차이는 결과를 보낼 때 처리하는 데이터 개수

mono: 0~1개의 데이터 전달
flux: 0~N개의 데이터 전달

#### 더 알아볼것

- 반응형 프로그래밍

#### 참고자료

https://pearlluck.tistory.com/726
https://devuna.tistory.com/108
https://devuna.tistory.com/120
https://pearlluck.tistory.com/712
