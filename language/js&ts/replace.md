## replace(), replaceAll()

### replace()

```js
let str = "apple, banana, orange, banana";
let replaced_str = str.replaceAll(/banana/, "tomato");
```

- 첫번째 발견한 문자열만 치환함

```js
let str = "apple, banana, orange, banana";
let replaced_str = str.replaceAll(/banana/g, "tomato");
```

- 정규표현식 뒤에 /g를 붙여서 전역으로 선언해주면, 모든 값을 치환해서 replaceAll처럼 사용 가능

### replaceAll()

```js
let str = "apple, banana, orange, banana";
let replaced_str = str.replaceAll("banana", "tomato"); // 찾을 문자열, 바꿀 문자열
```

```js
let str = "apple, banana, orange, banana";
let replaced_str = str.replaceAll(/banana/g, "tomato");
```

- 모든 일치하는 문자열을 치환
- 정규표현식 사용 시 /g를 붙여야함

### $

`$&`

- $를 사용해서 찾는 문자열 앞 뒤에 다른 값 붙일 때 유용

```js
str.replaceAll("찾는문자열", "??$&??");
```

```js
const str = "1345";
str.replaceAll("1", "0$&2"); // -> 012345
```

`$n`

- 괄호 안의 그루핑된 문자열을 조작할 때 사용

```js
const str = "홍길동";
str.replaceAll(/(홍)(길동)/g, "$2$1"); // -> 길동홍
```

- 첫번째 괄호가 $1이 되고, 두번째 괄호가 $2가 됨

### 인자 함수

- 바꿀 문자열 (2번째 인자) 대신 인자함수 사용 가능
- 단순히 문자를 바꿔주는 것보다 더 많은 재가공 방법 제공

제공하는 인자 (순서대로)

- match: 찾은 문자열
- p1, p2 ...: 괄호로 그루핑되어 매칭된 그룹 1, 2, ..N을 반환
- offset: 찾은 문자열의 시작위치 반한
- string: 전체 대상 문자열이 그대로 넘어감

```js
const str = "홍길동";
str.replaceAll("길", (s, found) => {
  console.log(str, found); // -> '길', 1
});
```

- 일반 문자열을 찾고있으므로 두번재 인자가 p1, p2.. 가 아니라 offset임

#### 참고자료

[link](https://apost.dev/1131/)
