https://velog.io/@yaytomato/%ED%94%84%EB%A1%A0%ED%8A%B8%EC%97%90%EC%84%9C-%EC%95%88%EC%A0%84%ED%95%98%EA%B2%8C-%EB%A1%9C%EA%B7%B8%EC%9D%B8-%EC%B2%98%EB%A6%AC%ED%95%98%EA%B8%B0

https://kunkunwoo.tistory.com/211

https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-JWTjson-web-token-%EB%9E%80-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC#JWT_(JSON_Web_Token)

## Cookie

쿠키는 *Key-Value 형식의 문자열 덩어리*이다.

클라이언트가 어떠한 웹사이트를 방문할 경우, 그 사이트가 사용하고 있는 서버를 통해 *클라이언트의 브라우저에 설치*되는 작은 기록 정보 파일이다.

각 사용자마다의 브라우저에 정보를 저장하니 고유 정보 식별이 가능한 것이다.

1.  브라우저(클라이언트)가 서버에 요청(접속)을 보낸다.
2.  서버는 클라이언트의 요청에 대한 응답을 작성할 때, 클라이언트 측에 저장하고 싶은 정보를 응답 헤더의 Set-Cookie에 담는다.
3.  이후 해당 클라이언트는 요청을 보낼 때마다, 매번 저장된 쿠키를 요청 헤더의 Cookie에 담아 보낸다.
    서버는 쿠키에 담긴 정보를 바탕으로 해당 요청의 클라이언트가 누군지 식별하거나 정보를 바탕으로 추천 광고를 띄우거나 한다.

_Cookie 방식의 단점_

가장 큰 단점은 *보안에 취약*하다는 점이다.
요청 시 쿠키의 값을 그대로 보내기 때문에 유출 및 조작 당할 위험이 존재한다.
쿠키에는 *용량 제한*이 있어 많은 정보를 담을 수 없다.
웹 브라우저마다 쿠키에 대한 지원 형태가 다르기 때문에 *브라우저간 공유가 불가능*하다.
쿠키의 사이즈가 커질수록 *네트워크에 부하*가 심해진다.

## Session

이러한 쿠키의 보안적인 이슈 때문에, 세션은 비밀번호 등 클라이언트의 민감한 인증 정보를 브라우저가 아닌 *서버 측에 저장*하고 관리한다.

서버의 메모리에 저장하기도 하고, 서버의 로컬 파일이나 데이터베이스에 저장하기도 한다.

핵심 골자는 민감한 정보는 클라이언트에 보내지말고 서버에서 모두 관리한다는 점이다.

*세션 객체*는 Key에 해당하는 SESSION ID와 이에 대응하는 Value로 구성되어 있다.
Value에는 세션 생성 시간, 마지막 접근 시간 및 User가 저장한 속성 등 이 Map 형태로 저장된다.

1. 유저가 웹사이트에서 로그인하면 세션이 서버 메모리(혹은 데이터베이스) 상에 저장된다.
   이때, 세션을 식별하기 위한 Session Id를 기준으로 정보를 저장한다.
2. 서버에서 브라우저에 쿠키에다가 Session Id를 저장한다.
3. 쿠키에 정보가 담겨있기 때문에 브라우저는 해당 사이트에 대한 모든 Request에 Session Id를 쿠키에 담아 전송한다.
4. 서버는 클라이언트가 보낸 Session Id 와 서버 메모리로 관리하고 있는 Session Id를 비교하여 인증을 수행한다.

_Session 방식의 단점_

쿠키를 포함한 요청이 외부에 노출되더라도 세션 ID 자체는 유의미한 개인정보를 담고 있지 않는다.
그러나 해커가 세션 ID 자체를 탈취하여 클라이언트인척 위장할 수 있다는 한계가 존재한다. (이는 서버에서 IP특정을 통해 해결 할 수 있긴 하다)
서버에서 세션 저장소를 사용하므로 요청이 많아지면 서버에 부하가 심해진다.

## Token

토큰 기반 인증 시스템은 클라이언트가 서버에 접속을 하면 서버에서 해당 클라이언트에게 인증되었다는 의미로 '토큰'을 부여한다.

이 토큰은 유일하며 토큰을 발급받은 클라이언트는 또 다시 서버에 요청을 보낼 때 요청 헤더에 토큰을 심어서 보낸다.

그러면 서버에서는 클라이언트로부터 받은 토큰을 서버에서 제공한 토큰과의 일치 여부를 체크하여 인증 과정을 처리하게 된다.

_기존의 세션기반 인증은 서버가 파일이나 데이터베이스에 세션정보를 가지고 있어야 하고 이를 조회하는 과정이 필요하기 때문에 많은 오버헤드가 발생한다_.

하지만 토큰은 세션과는 달리 서버가 아닌 클라이언트에 저장되기 때문에 메모리나 스토리지 등을 통해 세션을 관리했던 서버의 부담을 덜 수 있다.

*토큰 자체에 데이터가 들어있기 때문에 클라이언트에서 받아 위조되었는지 판별*만 하면 되기 떄문이다.

토큰은 앱과 서버가 통신 및 인증할때 가장 많이 사용된다.

왜냐하면 웹에는 쿠키와 세션이 있지만 앱에서는 없기 때문이다.

[서버 기반 vs 토큰 기반]

_서버(세션) 기반 인증 시스템_

서버의 세션을 사용해 사용자 인증을 하는 방법으로 서버측(서버 램 or 데이터베이스)에서 사용자의 인증정보를 관리하는 것을 의미한다.
그러다 보니, 클라이언트로부터 요청을 받으면 클라이언트의 상태를 계속에서 유지(Stateful) 해놓고 사용한다.
이는 사용자가 증가함에 따라 성능의 문제를 일으킬 수 있으며 확장성이 어렵다는 단점을 지닌다.

_토큰 기반 인증 시스템_

이러한 단점을 극복하기 위해서 "토큰 기반 인증 시스템"이 나타났다.
인증받은 사용자에게 토큰을 발급하고, 로그인이 필요한 작업일 경우 헤더에 토큰을 함께 보내 인증받은 사용자인지 확인한다.
이는 *서버 기반 인증 시스템과 달리 상태를 유지하지 않으므로 Stateless한 특징*을 가지고 있다.

1. 사용자가 아이디와 비밀번호로 로그인을 한다.
2. 서버 측에서 사용자(클라이언트)에게 유일한 토큰을 발급한다.
3. 클라이언트는 서버 측에서 전달받은 토큰을 쿠키나 스토리지에 저장해 두고, 서버에 요청을 할 때마다 해당 토큰을 HTTP 요청 헤더에 포함시켜 전달한다.
4. 서버는 전달받은 토큰을 검증하고 요청에 응답한다.
   **토큰에는 요청한 사람의 정보가 담겨있기에 서버는 DB를 조회하지 않고 누가 요청하는지 알 수 있다.**

_Token 방식의 단점_

쿠키/세션과 다르게 토큰 자체의 데이터 길이가 길어, 인증 요청이 많아질수록 네트워크 부하가 심해질수 있다.
Payload 자체는 암호화되지 않기 때문에 유저의 중요한 정보는 담을 수 없다.
_토큰을 탈취당하면 대처하기 어렵다. (따라서 사용 기간 제한을 설정하는 식으로 극복한다)_

## JWT(JSON Web Token)

JWT(JSON Web Token)란 인증에 필요한 정보들을 암호화시킨 *JSON 토큰*을 의미한다.

그리고 JWT 기반 인증은 JWT 토큰(Access Token)을 HTTP 헤더에 실어 서버가 클라이언트를 식별하는 방식이다

JWT는 JSON 데이터를 Base64 URL-safe Encode 를 통해 인코딩하여 직렬화한 것이며, 토큰 내부에는 위변조 방지를 위해 개인키를 통한 전자서명도 들어있다.

따라서 사용자가 *JWT를 서버로 전송하면 서버는 서명을 검증하는 과정을 거치게 되며 검증이 완료되면 요청한 응답*을 돌려준다.

JWT는 유저를 인증하고 식별하기 위한 토큰(Token)기반 인증이다. *토큰*은 세션과는 달리 *서버가 아닌 클라이언트에 저장*되기 때문에 메모리나 스토리지 등을 통해 세션을 관리했던 서버의 부담을 덜 수 있다. JWT의 핵심적인 특징은 *토큰 자체에 사용자의 권한 정보나 서비스를 사용하기 위한 정보가 포함(Self-contained)*된다는 것이다. 데이터가 많아지면 토큰이 커질 수 있으며 토큰이 한 번 발급된 이후 사용자의 정보를 바꾸더라도 토큰을 재발급하지 않는 이상 반영되지 않는다.

_JWT를 사용하면 RESTful 과 같은 무상태(Stateless)인 환경에서 사용자 데이터를 주고 받을 수 있게된다._ 세션(Session)을 사용하게 될 경우에는 쿠키 등을 통해 식별하고 서버에 세션을 저장했지만 JWT 와 같은 토큰을 클라이언트에 저장하고 요청시 단순히 HTTP 헤더에 토큰을 첨부하는 것만으로도 단순하게 데이터를 요청하고 응답을 받아올 수 있다.

**JWT 구조**

JWT는 . 을 구분자로 나누어지는 세 가지 문자열의 조합이다.

. 을 기준으로 좌측부터 Header, Payload, Signature를 의미한다.

_Header_ 에는 JWT에서 사용할 타입과 해시 알고리즘의 종류가 담겨있으며, _Header_ 는 서버에서 첨부한 사용자 권한 정보와 데이터가 담겨있다. 마지막으로 _Header_ 에는 Header, Payload 를 Base64 URL-safe Encode 를 한 이후 Header 에 명시된 해시함수를 적용하고, 개인키(Private Key)로 서명한 전자서명이 담겨있다.

전자서명에는 비대칭 암호화 알고리즘을 사용하므로 암호화를 위한 키와 복호화를 위한 키가 다르다. 암호화(전자서명)에는 개인키를, 복호화(검증)에는 공개키를 사용한다.

Header와 Payload는 단순히 인코딩된 값이기 때문에 제 3자가 복호화 및 조작할 수 있지만, _Signature는 서버 측에서 관리하는 비밀키가 유출되지 않는 이상 복호화할 수 없다._
따라서 *Signature는 토큰의 위변조 여부를 확인*하는데 사용된다.

1. 사용자가 ID, PW를 입력하여 서버에 로그인 인증을 요청한다.
2. 서버에서 클라이언트로부터 인증 요청을 받으면, Header, PayLoad, Signature를 정의한다.
   Hedaer, PayLoad, Signature를 각각 Base64로 한 번 더 암호화하여 JWT를 생성하고 이를 쿠키에 담아 클라이언트에게 발급한다.
3. 클라이언트는 서버로부터 받은 JWT를 로컬 스토리지에 저장한다. (쿠키나 다른 곳에 저장할 수도 있음)
   API를 서버에 요청할때 Authorization header에 Access Token을 담아서 보낸다.
4. 서버가 할 일은 클라이언트가 Header에 담아서 보낸 JWT가 내 서버에서 발행한 토큰인지 일치 여부를 확인하여 일치한다면 인증을 통과시켜주고 아니라면 통과시키지 않으면 된다.
5. 인증이 통과되었으므로 페이로드에 들어있는 유저의 정보들을 select해서 클라이언트에 돌려준다.
6. 클라이언트가 서버에 요청을 했는데, 만일 액세스 토큰의 시간이 만료되면 클라이언트는 리프래시 토큰을 이용해서
   서버로부터 새로운 엑세스 토큰을 발급 받는다.

_토큰 인증 신뢰성을 가지는 이유_

정리하자면, *서버는 토큰 안에 들어있는 정보가 무엇인지 아는게 중요한 것이 아니라 해당 토큰이 유효한 토큰인지 확인하는 것이 중요*하기 때문에, 클라이언트로부터 받은 JWT의 헤더, 페이로드를 서버의 key값을 이용해 시그니처를 다시 만들고 이를 비교하며 일치했을 경우 인증을 통과시킨다.

JWT은 서명(인증)이 목적이다.

JWT는 Base64로 암호화를 하기 때문에 디버거를 사용해서 인코딩된 JWT를 1초만에 복호화할 수 있다.
복호화 하면 사용자의 데이터를 담은 Payload 부분이 그대로 노출되어 버린다. 그래서 페이로드에는 비밀번호와 같은 민감한 정보는 넣지 말아야 한다.
그럼 토큰 인증 방식 자체가 빛 좋은 개살구라고 생각할수도 있지만, _토큰의 진짜 목적은 정보 보호가 아닌, 위조 방지이다._
바로 위에서 소개했듯이, 시그니처에 사용된 비밀키가 노출되지 않는이상 데이터를 위조해도 시그니처 부분에서 바로 걸러지기 때문이다.

JWT 장점

_Header와 Payload를 가지고 Signature를 생성하므로 데이터 위변조를 막을 수 있다._
인증 정보에 대한 별도의 저장소가 필요없다.
JWT는 토큰에 대한 기본 정보와 전달할 정보 및 토큰이 검증됬음을 증명하는 서명 등 필요한 모든 정보를 자체적으로 지니고 있다.
클라이언트 인증 정보를 저장하는 세션과 다르게, 서버는 무상태(StateLess)가 된다.
확장성이 우수하다.
토큰 기반으로 다른 로그인 시스템에 접근 및 권한 공유가 가능하다. (쿠키와 차이)
OAuth의 경우 Facebook, Google 등 소셜 계정을 이용하여 다른 웹서비스에서도 로그인을 할 수 있다.
모바일 어플리케이션 환경에서도 잘 동작한다. (모바일은 세션 사용 불가능)

_서버에서 가장 피해야 할 것은 데이터베이스 조회이다._
서버 자체가 죽는 경우도 있지만, 대부분 DB가 터져서 서버도 같이 죽는 경우가 허다하기 때문이다.
이런 점에서, _JWT 토큰은 DB조회를 안해도 되는 장점을 가지고 있다는 점이다._
만일 payload에 유저이름과 유저등급 을 같이 두고 보내면, 서버에서는 유저이름을 가지고 DB를 조회해서 유저 등급을 얻지않아도 바로 원하는 정보를 취할수 있다.

JWT 단점

쿠키/세션과 다르게 _JWT는 토큰의 길이가 길어, 인증 요청이 많아질수록 네트워크 부하가 심해진다_.
Payload 자체는 암호화되지 않기 때문에 유저의 중요한 정보는 담을 수 없다.
토큰을 탈취당하면 대처하기 어렵다.

JWT의 Access Token / Refresh Token 방식

https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-Access-Token-Refresh-Token-%EC%9B%90%EB%A6%AC-feat-JWT

다만 이 JWT도 탈취의 위험성이 있기 때문에, 그대로 사용하는것이 아닌 Access Token, Refresh Token 으로 이중으로 나누어 인증을 하는 방식을 현업에선 취한다.

## Password - hash and salt

https://st-lab.tistory.com/100

해싱과 암호화는 일상에서는 어느정도 통용되지만, *암호학적*으로 본다면 차이가 있다. 가장 큰 차이는 **'방향성'**이다. 단방향, 즉 복호화가 불가능하는 하다는 것이고 이를 *'해싱'*이라 부른다. 반면에 '암호화(Encryption)'는 해싱하고는 다르다. _'암호화'는 '양방향'이다_. 즉, 암호화를 하면 역으로 복호화도 가능한 것이다.

단방향 해시 함수는 어떤 수학적 연산(또는 알고리즘)에 의해 *원본 데이터를 매핑시켜 완전히 다른 암호화된 데이터로 변환*시키는 것을 의미한다. 이 변환을 해시라고 하고, 해시에 의해 *암호화된 데이터를 다이제스트(digest)*라고 한다.

대표적으로 아래와 같은 알고리즘들이 있다.
SHA
MD
HAS
WHIRLPOOL

그중 가장 대표적인 해시 알고리즘인 _SHA-256_ 을 통해 123456 을 해싱하면 다음과 같이 나온다.

8d969eef6ecad3c29a3a629280e686cf0c3f5d5a86aff3ca12020c923adc6c92

이렇게 사용자로부터 입력받은 정보를 그대로 저장하는게 아니라 해싱을 해서 저장하는 것이다.
그러면 DB를 털어 저런 값을 얻었다고 한들 기존 원래 패스워드를 유추하기 힘들게 된다.

**단방향 해시 함수의 한계점**

1. *동일한 메시지는 동일한 다이제스트*를 갖는다.

앞서 위의 123456 을 SHA-256 을 통해 다이제스트를 얻었다. 분명 123456 의 다이제스트는 원래의 password 인 123456 을 유추하기 어렵다. 그러나 123456 에 대한 다이제스트는 항상 같은 값을 얻는다는 것, 즉 값이 변하지 않는 것이 큰 문제점이다.

여러분이 해커(공격자)라고 가정해볼 때 해싱된 메시지의 원문을 얻기 위해서 가장 편한 방법은 무엇일까?

그 것은 바로 그동안 해커들이 여러 값들을 대입해보면서 얻었던 다이제스트들을 모아놓은 리스트에서 찾아보는 것이다. 이러한 다이제스트들의 테이블을 우리는 *레인보우 테이블(Rainbow Table)*이라고 한다.

2. 무차별 대입 공격 (브루트포스)

*해시 함수의 경우 원래 빠른 데이터 검색을 위한 목적*으로 설계된 것이다. 그렇다보니 해시 함수를 써도 원문의 다이제스트는 금방 얻어진다. 바로 이 점이 문제점인데, 우리가 다이제스트를 빠르게 얻을 수 있는 것과 동일하게 해커도 똑같이 빠르게 값을 얻을 수 있다는 것이다. 즉, 해커는 무작위의 데이터들을 계속 대입해보면서 얻은 다이제스트와 해킹할 대상의 다이제스트를 계속 비교를 해보는 것이다.

**단방향 해시 함수 보완하기**

가장 유명한 방법으로는 *키-스트레칭*과 *솔트*가 있다. u

1. 해시 함수 여러 번 수행하기 [키 스트레칭 _ Key Stretching]

우리가 패스워드를 저장할 때 가장 쉽게 생각 할 수 있는 방법이다.
다이제스트를 한 번 더 SHA-256 에 돌리는 것이다.
즉, 브루트포스를 최대한 무력화 하기위한 방법인 것이다.

2. 솔트 (Salt)

여러번 돌리더라도 결국 몇 번 돌렸는지 횟수만 알면 상징성 있는 대표 문자열들을 추려서 대입해보면 적어도 공격하는 입장에서는 조금이나마 찾는데 시간을 줄이고, 각 횟수별 다이제스트가 Rainbow table 에 있을 확률이 높기 때문이다. 또한 같은 비밀번호를 사용하는 사용자들이 있다면 하나의 결과를 갖고도 다수 사용자의 password 를 알아내는 것이나 마찬가지다. 이를 방지하기 위해 도입한 것이 바로 솔트다.

_솔트란 해시함수를 돌리기 전에 원문에 임의의 문자열을 덧붙이는 것을 말한다._ 단어 뜻 그대로 원문에 임의의 문자열을 붙인다는 의미의 소금친다(salting) 는 것이다.

즉, 같은 패스워드를 사용하더라도 salting 된 문자열은 서로 다르기 때문에 각 사용자의 다이제스트는 서로 다른 값으로 저장될 것이다.

_해커가 123456의 다이제스트를 갖고 있다고 하더라도 레인보우테이블에서 비교하기 어렵게 만드는 것이다._
설령 사용자의 고유 솔트를 알았다고 한들, 해당 솔트와 결합하여 임의의 문자열을 무차별 대입을 해보아야 하기 때문에 공격하는 사람 입장에서는 곤란하게 만들 수 밖에 없다.

솔트의 가장 큰 목적은 해당 *솔트의 레인보우 테이블 새로 생성하여 만들기 위해서는 엄청나게 큰 데이터를 필요로 하기 때문에 자연스럽게 레인보우 테이블 생성을 방지하는 역할*을 해주기도 한다.
