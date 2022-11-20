https://velog.io/@hustle-dev/JS-%EB%A9%B4%EC%A0%91%EB%8C%80%EB%B9%84-%EA%B0%9C%EB%85%90%EC%A0%95%EB%A6%AC

### Node.js

Node.js: 자바스크립트를 브라우저 이외의 환경에서 동작시킬 수 있는 런타임 환경(비동기 IO와 단일 스레드 이벤트루프 지원 → SPA에 적합)

### JS와 ECMAScript

ECMAScript는 프로그래밍 문법의 핵심을 담당하고 자바스크립트는 일반적으로 프로그래밍 언어이면서도 클라이언트 사이드 Web API(DOM, BOM, XMLHttpRequest, Fetch)등을 아우르는 개념

JS특징

웹 브라우저에서 동작하는 유일한 언어
멀티 패러다임 언어
프로토타입 기반 객체지향 언어
구형브라우저를 위한 바벨과 같은 트랜스파일러(컴파일러) 사용

컴파일: 한 언어로 작성된 소스 코드를 다른 언어로 변환

트랜스파일: 한언어로 작성된 소스 코드를 비슷한 수준의 추상화를 가진 다른 언어로 변환

# 연산자

비교연산자
==(데이터 타입 바꾸어서 비교)
===(타입과 값도 같은 경우 true, 그러나 NaN은 false반환)
Obejct.is 메서드(+0과 -0 true로 나옴)
삼항 조건 연산자
삼항 조건 연산자 표현식은 값으로 평가할 수 있는 표현식인 문이다.

typeof 연산자
피연산자의 데이터 타입을 문자열로 반환 → 그러나 null과 array를 반환하지 않음.(이를 통해 완전하게 객체의 타입이 무엇인지 확인하는것은 어려움

# 단축평가

<!-- https://velog.io/@najiexx/JavaScript-%EB%8B%A8%EC%B6%95-%ED%8F%89%EA%B0%80 -->

논리곱 연산자와 논리합 연산자는 피연산자 타입을 Boolean 값으로 변환하지 않고 그대로 반환하는 것

옵셔널 체이닝 연산자
?. 좌항이 null 또는 undefined이면 undefined를 반환하고 그렇지 않으면 우항의 프로퍼티 값 참조

널 병합 연산자
?? 좌항이 null 또는 undefined 이면 우항의 피연산자를 반환하고 그렇지 않으면 좌항의 피연산자를 반환한다.

isNaN과 Number.isNaN
isNaN(is not a number)은 숫자인지 아닌지를 판별하는 것

Number.isNaN(is NaN)은 NaN 그 자체인지 아닌지를 판별
