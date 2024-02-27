## replace(), replaceAll()

### replace()

- 첫번째 인자로 찾을 문자열
- 두번째 인자로 바꿀 문자열

```java
String a = "무궁화. 삼천리. 화려강산. 대한사람. 대한으로. 길이. 보전하세 ";
a = a.replace(".", "/");
System.out.println(a);
//결과값 : 무궁화/ 삼천리/ 화려강산/ 대한사람/ 대한으로/ 길이/ 보전하세
```

### replaceAll()

- 첫번째 인자로 **정규식**
- 두번째 인자로 바꿀 문자열

```java
String a = "무궁화. 삼천리. 화려강산. 대한사람. 대한으로. 길이. 보전하세 ";
a = a.replace(".", "/");
System.out.println(a);
//결과값 : /////////////////////////////////////
```

- .(마침표)가 정규식에서 모든 문자열을 의미해서 정규식으로 인식되어 결과가 이러함

### replaceFirst()

- 찾은 첫번째 문자만 치환함

```java
String a = "무궁화. 삼천리. 화려강산. 대한사람. 대한으로. 길이. 보전하세 ";
a = a.replace(".", "/");
System.out.println(a);
//결과값 : 무궁화/ 삼천리. 화려강산. 대한사람. 대한으로. 길이. 보전하세
```

#### 참고자료

[link](https://coding-factory.tistory.com/128)
