## Etc

### 복제 (Replication)

- Master 서버와 Slave 서버를 둠
- 데이터 백업, 부하분신을 위해 사용
- Master DB에서 삽입, 수정, 삭제를 작업을 하고 변경된 데이터를 Slave에게 전달해주고, Slave DB는 데이터 조회 작업을 주로 담당함
- Master 서버에 장애가 생겼을 경우 Slave 서버가 대신 역할을 수행할 수 있음

### select시 많은 열과 많은 데이터 행 중에 어떤게 더 효율적일까?

많은 열이 있는 경우, 인덱스를 효과적으로 사용하기 어려움
따라서 주로 더 많은 열이 있는 데이터가 덜 효율적임

#### 참고자료

https://server-talk.tistory.com/240
