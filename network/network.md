## Network

### 인터넷 주소창에 daum.net을 쳤을 때 일어나는 과정

1. URL 해석/파싱 -> 프로토콜, 도메인, 포트
2. HSTS - 브라우저는 이 리스트에 우리가 요청한 웹사이트가 존재하는지 확인하고 존재하면 HTTP대신 HTTPS 프로토콜 사용
3. DNS서버에 도메인(https://daum.net)의 IP 주소 요청
4. 라우터를 이용해 접속하려는 네트워크로 가는 최적 경로 찾기
5. IP 주소를 MAC 주소로 변환 (APR)
6. TCP를 사용해 서버 연결 (3-way handshaking)
7. 웹 브라우저가 웹 서버에 페이지 요청
8. 웹 서버에서 응답
9. 브라우저에 HTML 컨텐트 렌더링

#### 참고자료

https://aws.amazon.com/ko/blogs/korea/what-happens-when-you-type-a-url-into-your-browser/
https://1-7171771.tistory.com/134
