## Elastic Beanstalk + Github actions + Docker 로 CI/CD

<img src='../image/eb-docker-deploy.png'/>

### Docker

#### Dockerfile 작성

```docker
FROM openjdk:17-alpine
CMD ["./gradlew", "clean", "build"]
ARG JAR_FILE_PATH=build/libs/sharp-0.0.1-SNAPSHOT.jar
COPY ${JAR_FILE_PATH} app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]
```

#### 참고자료

[link](https://taetoungs-branch.tistory.com/202)
