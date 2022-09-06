## Docker

---

### 명령어 정리

#### 컨테이너 실행

```bash
docker run [OPTIONS] IMAGE[:TAG|@DIGEST] [COMMAND] [ARG...]

docker run ubuntu:18.04 # ubuntu
docker run -d -p 1234:6379 redis # redis
docker run -d -p 3306:3306 \
  -e MYSQL_ALLOW_EMPTY_PASSWORD=true \
  --name mysql \
  mysql:5.7 # mysql
```

##### option

`-d` detached mode (백그라운드 모드)
`-p` 호스트와 컨테이너의 포트 연결 (포워딩)
`-v` 호스트와 컨테이너의 디렉토리 연결 (마운트)
`-e` 컨테이너 내에서 사용할 환경변수 설정
`–name` 컨테이너 이름 설정
`–rm` 프로세스 종료시 컨테이너 자동 제거
`-it` -i와 -t를 동시사용, 터미널 입력을 위한 옵션
`–link` 컨테이너 연결 [컨테이너명:별칭]

#### 실행중인 컨테이너 확인

```bash
docker ps [OPTIONS]
docker ps # 실행중인 컨테이너 보여줌
docker ps -a # 존재하는 모든 컨테이너 보여줌
```

#### 컨테이너 중지

```bash
docker stop [OPTIONS] CONTAINER [CONTAINER...]
```

#### 컨테이너 삭제

```bash
docker rm [OPTIONS] CONTAINER [CONTAINER...]
```

#### 다운로드한 이미지 확인

```bash
docker images [OPTIONS] [REPOSITORY[:TAG]]
```

#### 이미지 다운

```bash
docker pull [OPTIONS] NAME[:TAG|@DIGEST]
```

#### 다운로드된 이미지 삭제

```bash
docker rmi [OPTIONS] IMAGE [IMAGE...]
```

#### 로그 보기

```bash
docker logs [OPTIONS] CONTAINER
docker logs --tail 10 ${WORDPRESS_CONTAINER_ID} # 끝 10개의 로그만 출력
docker logs -f ${WORDPRESS_CONTAINER_ID} # 실시간 로그 확인
```
