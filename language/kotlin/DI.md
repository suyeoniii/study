## 의존성 주입 (Dependency Injection)

### 방법

1. Field (필드 주입)
   ```kt
   @Service
    class UserService {
        @Autowired
        private lateinit var userRepository: UserRepository
        ... // Business Logic
    }
   ```
2. Constructor (생성자 주입)

   ```kt
   @Service
    class UserService(private val userRepository: UserRepository) {
    ... // Business Logic
    }
   ```

   - 생성자에 주입할 객체를 파라미터로 작성
   - 생성자가 하나일 경우 @Autowired 어노테이션 생략 가능

3. Setter

   ```kt
    @Service class UserService {
        private var userRepository: UserRepository

        @Autowired
        fun setRepository(userRepository: UserRepository) {
            this.userRepository = userRepository
        }
    }
   ```

### Field vs Constructor vs Setter

- 생성자 주입이 가장 권장됨
- 불변성: Field, Setter의 경우 mutable한 `var` 사용, Contructor는 `final`로 선언됨
- 필드 주입은 스프링 프레임워크에 종속됨
- 생성자 주입은 스프링 프레임워크를 넘어서 안정성이 보장됨
- 생성자 주입은 생성자를 통해 모든 의존성을 주입받기때문에 의존성 관리가 용이함

#### 참고자료

https://jobc.tistory.com/198
