# HTTP의 이해

- HTTP(Hypertext Transfer Protocol)
  - 웹서버와 사용자간의 통신규약
  - OSI 7계층
    - 응용 : HTTP
    - 표현
    - 세션
    - 전송 : TCP,UDP - port number
    - 네트워크 : IP address
    - 데이터링크 : MAC address
    - 물리

- HTTP와 HTTPS의 차이(TLS)
  - HTTPS : Hypertext Transfer Protocol Secure
  - HTTPS는 모든 데이터를 암호화해서 전송
  - HTTPS는 SSL(Secure Socket Layer)/ TLS(Transfer Protocol Secure) 전송기술 사용
  - TCP, UDP와 같은 통신에 안전한 계층(layer)을 추가하는 방식
  - 이 기술의 구현을 위해 웹 서버에 설치하는 것이 SSL/TLS 인증서 (TLS는 SSL의 개선 버전)

- 클라이언트-서버 모델
  - 서비스 요청자인 클라이언트와 서비스 제공자인 서버로 이루어진 구조
  - 웹사이트 : 웹브라우저(클라이언트) - 웹서버(서버)

- stateless와 stateful
  - stateless : 서버에서 Client의 이전 상태를 기록하지 않음, Client가 상태정보를 모두 관리해야함, 서버가 매 요청마다 상태정보를 전달받아야함, UDP, HTTP
  - stateful : 서버에서 Client의 이전 상태를 기록함, TCP

- HTTP Cookie와 HTTP Session
  - 클라이언트의 인증을 유지하기 위해 쿠키와 세션을 사용
  - 쿠키 : Client에서 관리됨, 사용자 인증 유효 시간 명시, 유효시간동안 브라우저를 끄더라도 인증 유지됨
  - 세션 : 일정 시간동안 같은 사용자의 요청을 하나의 상태로 보고 그 상태를 유지시키는 기술
  - 1. 사용자가 로그인 request / 2. 서버에서 DB 조회검증으로 유효한 사용자일 경우 세션 ID를 생성해 response header에 포함시켜 응답
  - 3. 사용자는 서버에서 세션 ID를 받아 쿠키에 저장 후 쿠키를 request header에 포함시켜 요청 / 4. 서버에서는 쿠키를 받아 세션 저장소에서 검증 후 데이터 반환

- HTTP 메시지 구조
  - HTTP 요청(Request)와 응답(Response)
    - multipart/form-data : 파일을 보내기 위해 사용하는 mime type
  - HTTP 요청 메서드(HTTP request methods)
    - 멱등성 : 여러번 연산해도 결과가 달라지지 않음 ( GET, PUT, DELETE는 멱등성 보장 O/ POST는 멱등성 보장 X)
  - HTTP 응답 상태 코드(HTTP response status code)
    - 서버의 처리 결과는 응답 메시지의 상태 코드(status code)를 보고 파악 가능
  - 2XX : 성공 / 3XX : 리다이렉션(완전한 처리를 위해 추가 동작 필요) / 4XX : 클라이언트 에러 / 5XX : 서버에러
