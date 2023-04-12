## 스택 (Stack), 큐 (Queue)

### 스택

#### 특징

- 후입선출 (LIFO: Last-In First-Out)
- 삽입, 삭제가 리스트의 한쪽(top)에서만 이루어짐

#### 사용 사례

- 웹 브라우저 방문 기록 (뒤로가기)
- 실행 취소 (undo)
- 후위 표기법
- 함수 호출 스택 (Call Stack)

  ```js
  void foo() {
      int x = 5;
      bar();
  }

  void bar() {
      int y = 10;
  }

  int main() {
      foo();
      return 0;
  }
  ```

  ```bash
  bar() 프레임
  foo() 프레임
  main() 프레임
  ```

### 큐

#### 특징

- 선입선출 (FIFO: First-In First-Out)
- 삭제 연산은 앞쪽(front), 삽입 연산은 뒤쪽(rear)에서 이루어짐

#### 사용 사례

- 은행 업무
- 대기열 순서와 같은 우선순위 작업 예약
- 프로세스 관리
- 콜백 큐 (Callback Queue)

#### 참고자료

https://jud00.tistory.com/entry/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%EC%8A%A4%ED%83%9DStack%EA%B3%BC-%ED%81%90Queue%EC%97%90-%EB%8C%80%ED%95%B4%EC%84%9C-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90
