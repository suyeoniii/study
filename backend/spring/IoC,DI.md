## IoC, DI

### IoC

Inversion of Control
제어의 역전

메소드나 객체의 호출작업을 개발자가 결정하는 것이 아니라, 외부에서 결정되는 것을 의미

```java
public class A {
   private B b;

   public A() {
      b = new B();
   }
}
```

```java
public class A {

   @Autowired
   private B b;
}
```

두번째의 경우 스프링 컨테이너가 직접 객체를 생성하여 해당 객체에 주입시켜줌
이 때 주입되는 객체는 스프링 컨테이너에 의해 관리되는 Bean이어야함

#### 장점

- 객체 간 결합도를 낮춤
- 유연한 코드 작성 가능
- 가독성 증진
- 코드 중복 방지
- 유지 보수 용이

### DI

Dependency Injection
의존 관계 주입

`의존성`: 의존대상 B가 변하면, 그것이 A에도 영향을 미친다.

객체(Bean)를 직접 생성하는게 아니라 외부에서 생성한 후 주입시켜주는 방식
모듈 간의 결합도를 낮추고 유연성을 높일 수 있음

#### 의존성 주입 방법

1. 생성자 주입 (추천)

   ```java
   public class A {
    private B b;

    public A(B b) {
        this.b = b;
    }
   }
   ```

2. Setter 주입

   ```java
   public class A {
    private B b;

    public void setB(B b) {
        this.b = b;
      }
   }
   ```

3. 인터페이스 주입

   ```java
   public interface BInjection {
    void inject(B b);
   }

   public A implements BInjection {
     private B b;

     @Override
     public void inject(B b) {
       this.b = b;
     }
   }
   ```

#### 참고자료

https://velog.io/@ohzzi/Spring-DIIoC-IoC-DI-%EA%B7%B8%EA%B2%8C-%EB%AD%94%EB%8D%B0
https://isoomni.tistory.com/entry/TISPRING-IOC-DI-%EC%A0%95%EC%9D%98-%EC%9E%A5%EC%A0%90
