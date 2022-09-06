#### Test

#### 테스트 실행시 datasource 설정

- test폴더에 별도의 resources-application.yml을 만들어서 datasource를 작성하면 실서버와 분리된 datasource 사용가능
- h2 사용시 실제 사용되는 h2와 별도로 테스트하기 위해 memory옵션을 주면 h2데이터베이스가 실행 중이 아니더라도 메모리 내에서 테스트 가능함
- application.yml

  ```yml
  spring:
  datasource:
      url: jdbc:h2:mem:test # 이렇게 설정하면 memory에서 돌아감
      username: sa
      password:
      driver-class-name: org.h2.Driver

  jpa:
      hibernate:
      ddl-auto: create
      properties:
      hibernate:
          # show_sql: true
          format_sql: true

  logging:
  level:
      org.hibernate.SQL: debug
  ```

- 위와 같이 h2를 mem으로 설정하면 memory에서 돌아가는데, spring boot에서 datasource 입력을 하지 않아도 기본으로 mem옵션이 붙어서 memory에서 돌아감
