## 피처 토글 (Feature toggle)

- 작성한 코드의 적용여부를 on/off 할 수 있도록 하는 것

```java
// isEnabled 함수는 서버 외부 설정에 따라, true / false중 하나를 반환
if (isEnabled("awesome-feature")) {
  provideAwesomeFeature();
} else {
  provideLegacyFeature();
}
```

- 위 예제의 경우 awesome-feature값이 true인 경우만 기능을 실행하게 할 수 있음
- 배포, 릴리즈를 분리할 수 있음
- 배포 = 인프라 관점에서 배포, 릴리즈 = 사용자에게 기능이 제공되는 것
- 최대한 운영과 비슷한 환경에서 테스트해볼 수 있음
- 문제 발생 시 기능토글을 Off하여 추가적인 영향을 없앨 수 있음
- 특정 사용자에게만 기능을 On 하여 QA를 더 편리하게할 수 있음
- `Trunk based development` 전략에서 유용함. 빠르게 feature 브랜치를 머지해야하는데, 아직 작업중인 기능도 기능토글을 이용해서 미리 배포해둘 수 있음

### 기능토글을 지원하는 tool

**Unleash**

- 기능 토글을 관리하는 페이지를 제공하고, 코드를 받아서 자체 인프라환경에 배포해서 사용할 수 있음
- 기능 토글의 전파가 빠름 (기본값 15초)

#### 참고자료

https://tech.mfort.co.kr/blog/2022-11-24-feature-toggle/
