HTTP의 특징 중의 하나는 *비연결성(Connectionless)*과 *비상태성(Stateless)*이다.

모든 요청(Request)마다 연결과 해제의 과정을 거치면서, 연결 상태를 유지 하지 않고, 연결 해제 후에도 상태 정보를 저장하지 않는다

- 이것은 서버 자원을 크게 절약한다
- 흔히들 사용하는 쿠키(cookie)와 세션(session)은 HTTP 프로토콜의 특징이자 약점을 보완하기 위해 사용한다

HTTP의 특징에는 다음과 같은 것들이 있다.

- 서버와 클라이언트에 의해 해석이 된다.
- TCP/IP를 이용한 응용 프로토콜이다.
- 비연결성 프로토콜이다.
- 무상태성(Statelessness)을 띤다.

HTTP는 비연결성 프로토콜이며 무상태성을 띤다. 따라서 HTTP는 연결을 유지하지 않은 채 요청(request)와 응답(response)를 처리하고, 응답을 해준 후에는 연결을 끊어버린다(비연결성). 또한 HTTP는 이전 연결에 대한 정보를 유지하고 있지 않다(무상태성).

그렇기 때문에 HTTP 통신은 자원의 낭비를 줄이고 성능을 높일 수 있었지만, 서로 다른 요청 간 상태를 유지시켜 줄 수 없다. 따라서 상태 유지를 위한 별도의 수단으로 쿠키나 세션(혹은 URL 재작성)을 이용해야한다.

### HTTP 프로토콜?

웹에서 데이터를 주고받기 위한 일종의 규약이다.

HTTP 프로토콜은 상태를 가지고 있지 않다. 따라서 이전 데이터 요청과 다음 데이터 요청이 완전히 분리되어 독립적으로 관리할 수 있다.

이와 같은 이점으로 당장 받은 요청 이외의 정보를 추가적으로 관리할 필요가 없어지고, 다수의 요청 및 서버의 부하를 줄일 수 있는 성능의 향상을 가져왔다.

HTTP 프로토콜은 일반적으로 TCP/IP 통신 위에서 동작하며 기본 포트는 80번이다.

## HTTP 상태코드

2xx - 성공

200번대의 상태 코드는 대부분 성공을 의미한다.

200 : GET 요청에 대한 성공
204 : No Content. 성공했으나 응답 본문에 데이터가 없음
205 : Reset Content. 성공했으나 클라이언트의 화면을 새로 고침 하도록 권고
206 : Partial Conent. 성공했으나 일부 범위의 데이터만 반환

3xx - 리다이렉션

300번대 상태 코드는 대부분 클라이언트가 이전 주소로 데이터를 요청하여 서버에서 새로운 URL로 리다이렉트를 유도하는 경우이다.

301 : Moved Permanently, 요청한 자원이 새 URL에 존재
303 : See Other, 요청한 자원이 임시 주소에 존재
304 : Not Modified, 요청한 자원이 변경되지 않았으므로 클라이언트에서 캐싱된 자원을 사용하도록 권고. ETag와 같은 정보를 활용하여 변경 여부를 확인

4xx - 클라이언트 에러

400번대 상태 코드는 대부분 클라이언트의 코드가 잘못된 경우이다. 없는 자원을 요청했거나 요청 권한 등이 잘못된 경우에 발생한다.

400 : Bad Request, 잘못된 요청
401 : Unauthorized, 권한 없이 요청. Authorization 헤더가 잘못된 경우
403 : Forbidden, 서버에서 해당 자원에 대해 접근 금지
404 : Not found, 요청한 자원이 서버에 없음
405 : Method Not Allowed, 허용되지 않은 요청 메서드
409 : Conflict, 최신 자원이 아닌데 업데이트하는 경우. ex) 파일 업로드 시 버전 충돌

5xx - 서버 에러

500번대 상태 코드는 서버 쪽에서 오류가 난 경우이다.

501 : Not Implemented, 요청한 동작에 대해 서버가 수행할 수 없는 경우
503 : Service Unavailable, 서버가 과부하 또는 유지 보수로 내려간 경우

## HTTP/2

Pros:

Multiple HTTP connection calls (HTTP/1 supports only 6);
A server can push an event to a client;
Compress headers;
More secure

Cons:

Server push can be abused;
Can be slower if LB (Load Balancer) supports HTTP/1 and server HTTP/2
