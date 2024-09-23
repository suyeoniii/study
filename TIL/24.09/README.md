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

`11`

- [MySQL에서 SQL 문장 가독성 향상](https://yozm.wishket.com/magazine/detail/2758/) 읽음

  - DISTINCT는 함수처럼 괄호붙여서 사용하는거 지양하기, 결과가 똑같으므로
  - A LEFT JOIN B 사용 시, 드리븐 테이블(A)에 대한 조건은 where 절에 명시하면 inner join처럼 동작함. on 절에 명시해야함
  - 페이징을 위한 limit n m 사용 시, order by 절 명시하기
  - group by 절에 명시되지 않은 컬럼을 select절에서 참조하는 경우 집계함수 사용 (의도에 맞게)
  - AND, OR 조건을 사용할 때, 괄호로 묶어주기
  - 데이터 건수 조회는 count(\*) 사용하기

- [exposed](https://github.com/JetBrains/Exposed) - Jetbrains 개발한 kotlin ORM 라이브러리
  - 사용법 정도 간단히 훓어봄. 나중에 개인 프로젝트에 적용해보면 좋을 듯

`20`

- 요즘 프론트엔드쪽 역량을 더 키워보고 싶다는 생각을 해서, 디자인 시스템에 대해 찾아봄
- [잘 쓰이는 디자인 시스템을 위한 여정](https://medium.com/29cm/%EC%9E%98-%EC%93%B0%EC%9D%B4%EB%8A%94-%EB%94%94%EC%9E%90%EC%9D%B8-%EC%8B%9C%EC%8A%A4%ED%85%9C%EC%9D%84-%EC%9C%84%ED%95%9C-%EC%97%AC%EC%A0%95-7c4fe03f32b7)
  - MFA (Micro Frontend Architecture) 라는 개념을컨퍼런스에서 얼핏 들어봤었는데, 줄여서 MFA라고 하네 (인증하는 MFA 인줄)
  - Headless UI - 스타일이 없는 UI 라이브러리
    - Headless UI 도입을 통해 상태 관리, 동작 구현 리소스 줄일 수 있었음, ark-ui 사용
- [플랫폼 팀 없는 오픈 소스 기반의 디자인 시스템 구축 회고](https://tech.inflab.com/20240224-design-system/)
  - 스토리북, mantine, 피그마 플러그인 등 사용
  - 내용이 많아서 다 이해하진 못했음
- 디자인 시스템
  - 디자인 시스템의 핵심은 공통 컴포넌트 관리에 있는 것 같다고 느낌
  - 디자이너와 개발자 사이 소통 비용을 줄일 수 있음
  - 주로 사용하는 툴은 무엇일지 조사해봐야할 듯
- 인프런 - Real Mysql 1 강의 조금 들음 (char vs varchar)
  - 길이 명시할 때 적히는 숫자 varchar(255) 이런게 바이트 크기인지, 문자 길이인지 헷갈렸었는데 문자 길이이고, 영어냐 한글이냐 이모지냐에 따라 디스크에 저장되는 저장공간(바이트)의 차이가 있는 것

`23`

- `Good first issue`: 오픈소스 프로젝트에서 새로운 기여자들이 쉽게 참여할 수 있는 이슈
- neovim 써보고 싶어서 설치만 했음. 뭐부터 해야할지 모르겠는데, 다음에 차차 진행할 예정
- [요즘IT - 검색엔진 최적화(SEO)란?](https://yozm.wishket.com/magazine/detail/1540/)
  - 추후에 자체 블로그 개발할 때 적용할 수 있을 듯
