## 처리율 제한 장치의 설계

- 처리율 제한 장치란 클라이언트 또는 서비스가 보내는 트래픽의 처리율을 제어하기 위한 장치
- 특정 기간 내에 전송되는 클라이언트의 요청 횟수를 제한

### 도입 시 장점

- Dos 공격에 의한 자원 고갈 방지
- 비용 절감
- 서버 과부하 방지

### 1단계 : 문제 이해 및 설계 범위 확정

요구사항

- 설정된 처리율을 초과하는 요청은 거부
- 낮은 응답시간: 이 처리율 제한 장치는 HTTP 응답시간에 나쁜 영향을 주면 안됨
- 가능한 적은 메모리 사용
- 분산형 처리율 제한: 하나의 처리율 제한 장치를 여러 서버나 프로세스에서 공유할 수 있어야함
- 예외 처리: 요청이 제한되었음을 사용자에게 보여주기
- 높은 결함 감내성: 제한 장치에 장애가 생기더라도 전체 시스템에 영향을 주어서는 안됨

### 2단계 : 개략적 설계안 제시 및 동의 구하기

#### 처리율 제한 장치는 어디에 둘 것인가?

- 클라이언트 or 서버
- 클라이언트에 두는 방법 - 클라이언트의 요청은 쉽게 위변조될 수 있음
- 서버에 두는 방법
- 미들웨어에 두는 방법 (API 게이트웨이)
- 처리율 제한 장치를 구현하기에 충분한 인력이 없다면 상용 API 게이트웨이 사용

#### 처리율 제한 알고리즘

##### 토큰 버킷 알고리즘

- 토큰 버킷 알고리즘은 토큰을 버킷에 담아두고, 토큰을 소비하는 방식으로 동작
- 토큰 버킷은 지정된 용량을 갖는 컨테이너
- 사전 설정된 양의 토큰이 주기적으로 버킷에 추가됨
- 토큰이 꽉찬 버킷에는 토큰이 더 추가되지 않음
- 각 요청은 처리될 때마다 하나의 토큰을 사용함
- 요청이 도착하면 버킷에 충분한 토큰이 있는지 검사
- 충분한 토큰이 없으면 요청을 거부
- 2개의 인자를 사용: 버킷 크기, 토큰 공급률
- API 엔드포인트마다 별도의 버킷을 둔다
- IP 주소별로 처리율을 제한해야한다면 IP 주소마다 버킷을 할당
- 시스템의 처리율을 초당 10000개 요청으로 제한하고 싶다면, 모든 요청이 하나의 버킷을 공유하도록 해야함

장단점

- 구현이 쉬움
- 메모리 사용측면에서 효율적
- 짧은 시간에 집중되는 트래픽도 처리 가능
- 버킷 크기과 토큰 공급률 인자를 적절하게 튜닝하는게 까다로움

##### 누출 버킷 알고리즘

- 누출 버킷 알고리즘은 토큰을 버킷에 담아두고, 토큰을 소비하는 방식으로 동작
- 토큰 버킷 알고리즘 과는 요청 처리율이 고정되어 있다는 차이가 있음
- FIFO 방식으로 동작
- 2개의 인자: 버킷 크기, 처리율

장단점

- 큐의 크기가 제한되어 있어서 메모리 사용량 측면에서 효율적
- 고정된 처리율을 갖고 있어서 안정적 출력이 필요한 경우 적합
- 단시간에 많은 트래픽이 몰리는 경우 최신 요청들이 버려짐
- 버킷 크기와 처리율을 적절하게 튜닝하는게 까다로움
  Q. 처리율이 고정?

##### 고정 윈도 카운터 알고리즘

- 타임라인을 고정된 간격의 윈도로 나누고, 각 윈도마다 카운터를 붙임
- 요청이 도착하면 현재 윈도의 카운터를 1 증가시킴
- 이 카운터의 값이 사전에 설정된 임계치에 도달하면 새로운 요청은 새 윈도가 열릴 때까지 버려짐

장단점

- 메모리 효율이 좋음
- 이해하기 쉬움
- 윈도가 닫히는 시점에 카운터를 초기화하는 방식은 특정한 트래픽 패턴을 처리하는데 적합함 (?)
- 윈도의 경계 부근에 순간적으로 많은 트래픽이 집중될 경우, 윈도에 할당된 양보다 더 많은 요청이 처리될 수 있음

##### 이동 윈도 로깅 알고리즘

- 고정 윈도 카운터 알고리즘의 단점을 보완한 알고리즘
- 요청의 타임스탬프를 추적함
- 타임 스탬프는 보통 레디스의 정렬집합 같은 캐시에 보관
- 새 요청이오면 만료된 타임스탬프 제거
- 만료된 타임스탬프는 현재 윈도의 시작 시점보다 이전에 도착한 요청을 의미
- 새 요청의 타임스탬프를 로그에 추가함
- 로그의 크기가 허용치보다 같거나 작으면 요청을 시스템에 전달함, 아니면 버림
- 1:00:50이 삭제되지 않는 이유?

장단점

- 어느 순간의 윈도를 보더라도 허용되는 요청의 개수는 시스템 처리율의 한도를 넘지 않음 ?
- 다량의 메모리 사용함. 거부된 요청의 타임스탬프도 보관하기 때문

##### 이동 윈도 카운터 알고리즘

- 고정 윈도 알고리즘과 이동 윈도 로깅 알고리즘을 결합한 것
- 처리율 제한 장치의 한도가 분당 7개 요청
- 이전 1분동안 5개의 요청, 현재 1분동안 3개의 요청이 왔다고 가정
- 현재 1분의 30% 시점에 도착한 새 요청의 경우 현재 윈도에 몇개의 요청이 온 것으로 보고 처리해야할지?
- 현재 1분간의 요청 수 + 이전 1분간의 요청 수 \* 이동 윈도와 직전 1분이 겹치는 비율 ?
- 계산 결과 3 + 5 \* 70% = 6.5개의 요청이 도착한 것으로 간주
- 내림하면 6

장단점

- 이전 시간대의 평균 처리율에 따라 현재 윈도의 상태를 계산하므로 짧은 시간에 몰리는 트래픽도 잘 대응함
- 메모리 효율지 좋음
- 직전 시간대에 도착한 요청이 균등하게 분포되어 있다는 가정한 상태에서 추정치를 계산하기때문에 다소 느슨함

##### 개략적인 아키텍처

- 카운터는 어디에 보관할 것인가?
  - 메모리상에서 동작하는 캐시가 바람직함
  - 빠르고, 만료정책 지원함
  - 레디스로 구현한다면 INCR과 EXPIRE 명령어를 사용
  - INCR: 카운터를 1 증가시킴
  - EXPIRE: 카운터를 만료시킴
- 클라이언트의 요청을 처리하는 미들웨어
- 처리율 제한 장치는 레디스의 지정 버킷에서 카운터를 가져와서 한도에 도달했는지 아닌지 확인
- 한도에 도달하면 HTTP 상태 코드 429를 반환
- 한도에 도달하지 않으면 요청을 처리하고 카운터를 증가

### 3단계 : 상세 설계

#### 처리율 제한 규칙

- 트래픽의 처리율을 제한하는 규칙
- 예) 마케팅 메세지의 하루 최대치 5회
- 예) 클라이언트가 분당 5회 이상 로그인 할 수 없음

#### 처리율 초과 트래픽의 처리

- HTTP 상태 코드 429 반환
- 나중에 처리하기 위해 큐에 보관 (주문 등)

#### 상셰 설계

#### 분산 환경에서의 처리율 제한 장치 구현

##### 성능 최적화

### 4단계 : 마무리

- 처리율 제한을 구현하는 여러 알고리즘, 장단점을 살펴봄
- 경성 또는 연성 처리율 제한
- 다양한 계층에서의 처리율 제한
- 처리율 제한을 회피하는 방법

### 추가 참고자료

https://mahdie-asiyaban.medium.com/implementing-scalable-rate-limiting-in-a-distributed-environment-with-lua-scripts-and-redis-sorted-3d743ab8734a

### 참고문헌
