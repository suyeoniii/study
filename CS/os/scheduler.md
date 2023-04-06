## 스케줄러 (Scheduler)

- 한정적인 메모리를 여러 프로세스가 효율적으로 사용할 수 있도록 다음 실행시간에 실행할 프로세스를 선택하는 역할

### 스케줄러 종류

1. 장기 스케줄러 / 잡 스케줄러
   - 디스크와 매모리 사이 스케줄링 담당
   - 어떤 프로세스를 메모리에 할당하여 ready queue로 보낼지 결정
2. 단기 스케줄러 / CPU 스케줄러
   - 메모리와 CPU 사이 스케줄링 담당
   - 어떤 프로세스를 running 상태로 전환 시킬지 결정
3. 중기 스케줄러 / 스와퍼
   - 여유 공간 마련을 위해 프로세스를 통째로 메모리에서 디스크로 쫓아내는 역할

### 스케줄링 알고리즘

1. FCFS (First Come First Served)
   - 먼저 도착한 프로세스가 먼저 CPU 할당
   - 콘보이 현상 (Convoy Effect): burst time이 긴 프로세스가 먼저 도착해 다른 프로세스의 실행 시간이 전부 늦춰지는 현상
2. SJF (Shortest Job First)
   - burst time이 짧은 프로세스가 먼저 CPU 할당
   - 기아 (Starvation) 현상: burst time 짧은 프로세스가 계속 도착하여 우선순위가 낮은 burst time이 긴 프로세스가 계속해서 CPU를 할당받지 못하는 현상
3. SRT (Shortest Remaining Time First)
   - 남은 burst time이 더 짧은 프로세스에 CPU할당
   - Starvation 발생 가능
4. Priority Scheduling
   - 우선순위 높은 프로세스에 먼저 CPU 할당
   - 기아 현상, 무기한 봉쇄 발생가능
   - 에이징 기법: 먼저 도착한 프로세스가 나이를 계속 먹으며 우선순위가 올라가는 기법 적용가능
5. RR (Round Robin)
   - 프로세스간 동일한 할당시간만큼 순서대로 계속 CPU할당
   - CPU 할당 시간이 길 경우 FCFS랑 같아짐
6. Multilevel Queue
   - Background에서 돌아가는 프로세스에는 FCFS, Foreground에는 RR 알고리즘 적용
   - 큐 사이에 다른 CPU할당시간 적용
7. Multilevel Feedback Queue
   - 각 큐에 서로 다른 CPU 할당 시간 적용, 프로세스가 해당 시간 동안 작업을 다 처리하지 못하면 점점 긴 time quantum을 할당해주는 큐로 이동
   - Time Quantum이 짧은 큐의 우선순위가 높음
   - 기아 현상 발생 가능, Aging기법으로 해결 가능

### 선점 / 비선점 스케줄링 알고리즘

1. 비선점: FCFS, SJF
   - 모든 프로세스를 공정하게 처리
   - 문맥교환으로 인하 오버헤드 적음
   - burst time이 긴 프로세스로 인해 burst time이 짧은 프로세스가 기다리는 현상 생길 수 있음
2. 선점: SRT, RR, Priority, Scheduling, Multilevel Scheduling
   - 우선순위 높은 프로세스의 빠른 응답시간 보장
   - 프로세스간 문맥교환이 자주 발생
   - Starvation 발생 가능

#### 참고자료

https://dheldh77.tistory.com/entry/%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C-%EC%8A%A4%EC%BC%80%EC%A4%84%EB%9F%ACScheduler
