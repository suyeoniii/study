## SQL Injection

### 종류

#### Normal SQL Injection

논리적 취약점을 이용한 기법

OR 1=1 -- 구문 등을 넣어 로그인을 성공시키거나, 모든 값을 조회하도록 한다.

#### Error based SQL Injection

에러를 발생시키는 구문을 넣어 에러 로그가 노출되게 하여 DB 구조, 컬럼명 등을 노출시켜 공격에 이용함

#### UNION Sql Injection

union 문을 입력하여 모든 데이터를 조회하도록함

#### Blind SQL Injection

에러메세지가 보이지 않는 경우 서버의 반응을 이용하여 참, 거짓을 판별한다.
값을 넣고 뒤에 SLEEP(2) 등을 넣어 SLEEP이 되는지에 따라 참, 거짓 여부를 판별한다.

### 예방 방법

1. 입력값 검증
2. Error message 노출하지 않기
3. prepared statement 사용하기
