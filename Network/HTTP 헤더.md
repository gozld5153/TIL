## HTTP 주요 헤더
***
> ### 요청(Request)에서 사용되는 헤더
#### From: 유저 에이전트의 이메일 정보
* 일반적으로 잘 사용하지 않음
* 검색 엔진에서 주로 사용
* 요청에서 사용    

<br/>

#### Referer: 이전 웹 페이지 주소
* 현재 요청된 페이지의 이전 웹 페이지 주소
* A => B로 이동하는 경우 B를 요청할 때 `referer: A`를 포함해서 요청
* `referer`를 사용하면 유입경로 수집 가능    

<br/>

#### User-Agent: 유저 에이전트 애플리케이션 정보      
* 클라이언트의 애플리케이션 정보(웹 브라우저 정보, 등등)
* 통계 정보
* 어떤 종류의 브라우저에서 장애가 발생하는지 파악 가능
* 예시
   + user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/
537.36 (KHTML, like Gecko) Chrome/86.0.4240.183 Safari/537.36     

<br/>

#### Host: 요청한 호스트 정보(도메인)
* 필수 헤더
* 하나의 서버가 여러 도메인을 처리해야 할 때 호스트 정보를 명시하기 위해 사용
* 하나의 IP 주소에 여러 도메인이 적용되어 있을 때 호스트 정보를 명시하기 위해 사용

<br/>

#### Origin: 서버로 POST 요청을 보낼 때 요청을 시작한 주소를 나타냄 
* 요청을 보낸 주소와 받는 주소가 다르면 CORS 에러가 발생한다.
* 응답 헤더의 Access-Control-Allow-Origin과 관련

<br/>

#### Authorization: 인증 토큰(ex JWT)을 서버로 보낼 때 사용하는 헤더
* "토큰의 종류(Basic, barer, token) + 실제 토큰 문자"를 전송
* ex
   + Authorization: "Basic YWxhZGRpbjpvcGVuc2VzYW1l"

   <br/>

> ### 응답(Response)에서 사용되는 헤더
#### Server: 요청을 처리하는 ORIGIN 서버의 소프트웨어 정보
+ Server: Apache/2.2.22 (Debian)
+ Server: nginx

<br/>

#### Date: 메시지가 발생한 날짜와 시간
+ Date: Tue, 15 Nov 1994 08:12:31 GMT

<br/>

#### Location: 페이지 리디렉션
+ 웹 브라우저는 3xx 응답의 결과에 `location` 헤더가 있으면, `location` 위치로 리다이렉트(자동이동)
+ 201(Created): `Location` 값은 요청에 의해 생성된 리소스 URI
+ 3xx(Redirection): Location 값은 요청을 자동으로 리디렉션하기 위한 대상 리소스를 가리킴

<br/>

#### Allow: 허용 가능한 HTTP 메서드
+ 405(Method Not Allowed)에서 응답에 포함
+ Allow: GET, HEAD, PUT

<br/>

#### Retry-After: 유저 에이전트가 다음 요청을 하기까지 기다려야 하는 시간 
+ 503(Service Unavailable): 서비스가 언제까지 불능인지 알려줄 수 있음
+ Retry-After: Fri, 31 Dec 2020 23:59:59 GMT(날짜 표기)
+ Retry-After: 120(초 단위 표기)