# 24.09

`09`

- [코드래빗](https://coderabbit.ai/?ref=futuretools.io)이라는 AI 코드리뷰 툴이 괜찮다길래 무료 평가판 등록함

`10`

- [자바 가독성 높이는 법](https://yozm.wishket.com/magazine/detail/2682/) 읽음

  - for(i) 대신 for-each 사용
    - off-by-one 에러 방지 (인데스 경계값 오류)
  - 변수는 사용할 때 선언하기
  - Null 대신 Optional 사용
    - Optional을 사용할 경우, 해당 객체의 값이 없을 수도 있다는 것을 명시적으로 표현 가능
    - Optional 사용이 표준화 되어있지 않다면, null인지 체크를 해줘야함
  - 인터페이스 사용하기
    - List 인터페이스를 구현한게 ArrayList, LinkedList 등
    - Set 인터페이스를 구현한게 HashSet, TreeSet 등
    - 메소드 내용에 따라 인터페이스를 사용해도 괜찮다면, 구현체 대신 인터페이스에 의존하게 하면 다른 구현체도 사용이 가능하니 좋을 것 같고, 구현체를 꼭 사용해야 하는 경우에는 구현체를 사용하도록 하면 됨

- Query DSL vs Kotlin JDSL
  - https://spoqa.github.io/2024/05/03/transfer-jdsl.html
  - 프로젝트에서 필터를 이용한 검색 기능을 개발해야해서, QueryDSL 도입을 검토해보았음
  - Kotlin을 사용하기때문에 Kotlin JDSL도 있는데, QueryDSL을 사용하려면 kapt라는 도구를 사용해주어야하는데, 새로운 기능 지원이 중단되고, 유지보수만 진행될 예정이라해서 kapt 대신 KSP를 앞으로 더 사용하게 될 것 같음
  - 하지만 QueryDSL은 KSP를 아직 지원하지 않으므로, 다른 대체재로 Kotlin JDSL 선택
  - Kotlin JDSL은 라인 개발팀에서 만든 라이브러리군
- MutableList
  - 변경 가능한 리스트
  - kotlin에서 사용되는 리스트 타입
- Tidy First? - 2장에서 `코드정리시점`까지 읽음
  - 보호 구문
  - 안 쓰는 코드 `이해완료`
  - 대칭으로 맞추기
  - 새로운 인터페이스로 기존 루틴 부르기
  - 읽는 순서 `이해완료`
  - 응집도를 높이는 배치 `이해완료`
  - 설명하는 변수 `이해완료`
  - 설명하는 상수 `이해완료`
  - 명시적인 매개변수
  - 비슷한 코드끼리
  - 도우미 추출 `이해완료`
  - 하나의 더미 `이해완료`
  - 설명하는 주석 `이해완료`
  - 불필요한 주석 지우기 `이해완료`
  - 여기까진 몇개 이해안되는 것도 있지만, 쉬운편이었고 2장은 명쾌하게 이해되지 않는 부분이 좀 있어서 다시 읽어봐야할 듯
- javascript 불변성 관련해서 찾아보다가 찾은 정리잘 된 블로그 글

  - [자바스크립트에서 불변성(Immutability)이란](https://sustainable-dev.tistory.com/156)
    - 원시 타입은 불변한다
      - 메모리영역 안에서 변경이 불가능하며, 변수에 할당할 때 새로운 값이 만들어져 할당된다
    - 객체와 배열은 불변하지 않다
      - 새로운 값이 만들어지지 않고, 직접 변경이 가능하다
    - 배열도 object type이므로 불변하지만, 불변성을 유지하기 위해 스프레드 연산자나 Object.assign을 사용하기도 한다
    - `const`는 값에 대한 참조가 할당되고 나면, 변경할 수 없는 것이지 값 자체가 불변하는 것은 아니다

- kotlin - Private set
  - 외부에서 setter를 사용하지 못하게 하기 위해 사용
  ```
  var count: Int = 0
        private set
  ```
- [kotlin - Companion object](../../language/kotlin/companion-object.md)
  - 예전에 정리해둔 내용이 있어서 다시 읽어봄
  - `클래스의 멤버 변수는 인스턴스 생성시에 생성됨. 공통으로 사용되는 경우 companion object 안에 정의하면, 클래스 로딩 시 생성됨` <- 이게 핵심인듯
