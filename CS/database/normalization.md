## 정규화(Normalization)

### 정규화란?

이상현상이 있는 릴레이션을 분해하여 이상현상을 없애는 과정

### 장단점

`장점`

- 이상 현상 재거
- 확장, 변경에 용이하다.

`단점`

- 분해된만큼 Join 연산이 많아져 성능저하가 일어날 수 있다.

### 이상현상

- `삽입 이상` 튜플 삽입 시 특정 속성에 해당하는 값이 없어 null이 입력되는 현상
- `삭제 이상` 튜플 삭제 시 같이 저장된 다른 정보까지 삭제되는 현상
- `갱신 이상` 튜플 갱신 시 중복된 데이터의 일부만 갱신되어 데이터 불일치가 발생하는 현상

### 함수종속성

- 속성 A의 값에 따라 속성 B의 값이 정해지는 관계 (A->B)
- A는 결정자라고함

### 제1 정규형 (1NF)

각 컬럼의 값이 원자값(하나의 값)으로만 구성되어야 한다. (쪼개질 수 없는 값)

| 학생id | 과목id     |
| ------ | ---------- |
| 1      | C123       |
| 2      | C123, C124 |

2번째 행은 C123, C124 두개의 값을 가지기 때문에 1정규형에 맞지 않는다.

| 학생id | 과목id |
| ------ | ------ |
| 1      | C123   |
| 2      | C123   |
| 2      | C124   |

### 제2 정규형 (2NF)

제 1정규형이면서 기본키에 완전함수종속이어야 함.
|직원|기술|근무지|
|---|---|---|
|James|Node.js|마포구|
|James|Typescript|마포구|
|Ellie|Typescript|관악구|

각 행은 직원, 기술 컬럼에 의해 유일성이 보장된다. -> 직원, 기술은 복합키이다.
근무지는 직원, 기술 모두에 종속적인게 아닌 직원 컬럼에만 종속적이다.
-> 현재는 부분함수종속관계이다. 완전함수종속관계로 바꾸어야한다.

| 직원  | 근무지 |
| ----- | ------ |
| James | 마포구 |
| Ellie | 관악구 |

| 직원  | 기술       |
| ----- | ---------- |
| James | Node.js    |
| James | Typescript |
| Ellie | Typescript |

### 제3 정규형 (3NF)

제2 정규형이면서 이행적 함수 종속성을 제거한 정규형
이행적 함수 종속성: `X -> Y, Y -> Z` => `X -> Z`
|학생|지도교수|학과|
|---|---|---|
|James|P1|컴퓨터|
|Sandy|P2|컴퓨터|
|Ellie|P3|전자|

학생 -> 지도교수, 지도교수 -> 학과 관계를 가진다.
각각 다른 테이블로 분리해주어햐 한다.

| 학생  | 지도교수 |
| ----- | -------- |
| James | P1       |
| Sandy | P2       |
| Ellie | P3       |

| 지도교수 | 학과   |
| -------- | ------ |
| P1       | 컴퓨터 |
| P2       | 컴퓨터 |
| P3       | 전자   |

### BCNF

제 3 정규형을 만족하면서 모든 결정자가 후보키 집합에 속해야함

| 학생  | 과목 | 교수 |
| ----- | ---- | ---- |
| James | 자바 | P1   |
| Sandy | C++  | P2   |
| Ellie | C    | P3   |
| Ellie | C++  | P2   |
| Ellie | 자바 | P4   |

학생, 과목이 기본키이고, `학생,과목 -> 교수` 종속이 성립한다.
하지만 과목마다 교수가 다를 수 있으므로 `과목 -> 교수`는 성립하지 않는다.
반대로 `교수 -> 과목`은 성립한다.
이때 기본키가 아닌 교수가 결정자 역할을 하고있다.

| 학생  | 교수 |
| ----- | ---- |
| James | P1   |
| Sandy | P2   |
| Ellie | P3   |
| Ellie | P2   |
| Ellie | P4   |

| 교수 | 과목 |
| ---- | ---- |
| P1   | 자바 |
| P2   | C++  |
| P3   | C    |
| P2   | C++  |
| P4   | 자바 |

학생 -> 교수
교수 -> 과목

### 제4 정규형

BCNF를 만족하며 다치 종속이 없어야함

#### 다치종속

A->B 일떼 하나의 A값에 여러개의 B값이 존재하는것

A, B, C가 있고 A->B, A->C일때
A에 B, C가 여러개 종속됨
| 학생 | 과목 | 취미 |
| ----- | ---- | ---- |
| James | 자바 | 노래 |
| James | C++ | 독서 |
| Ellie | C | 운동 |
| Ellie | C++ | 독서 |

A->B, A->C로 분해해야함

| 학생  | 과목 |
| ----- | ---- |
| James | 자바 |
| James | C++  |
| Ellie | C    |
| Ellie | C++  |

| 학생  | 취미 |
| ----- | ---- |
| James | 노래 |
| James | 독서 |
| Ellie | 운동 |
| Ellie | 독서 |

두 테이블 모두 다치 종속성을 가지지만, 2개 이상의 컬럼이 한 컬럼에 다치 종속되지 않으므로 제4 정형을 만족

### 제5 정규형

제4 정규형을 만족하면서 조인 종속이 없고, 조인 연산을 했을 때 손실이 없는 것

연관성 없는 조인 시 다시 분해하면 손실이 발생한다.

개발자 - 자격증 - 언어를 연관시킨 경우 3개를 한번에 조인했다가 분해하면 손실이 발생한다.

개발자 - 자격증, 자격증 - 언어, 개발자 - 언어로 분해하면 조인했다가 다시 분해하여도 손실이 발생하지 않는다.

### 조인 종속

하나의 릴레이션을 여러 릴레이션으로 무손실 분해했다가 다시 결합할 수 있는 것

#### 참고자료

https://limkydev.tistory.com/163
https://rebro.kr/160
https://code-lab1.tistory.com/48
https://code-lab1.tistory.com/47
https://code-lab1.tistory.com/270
