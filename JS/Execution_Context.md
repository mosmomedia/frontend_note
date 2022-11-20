https://junilhwang.github.io/TIL/Javascript/Domain/Execution-Context/#_2-%E1%84%89%E1%85%B5%E1%86%AF%E1%84%92%E1%85%A2%E1%86%BC-%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%
A6%E1%86%A8%E1%84%89%E1%85%B3%E1%84%90%E1%85%B3-%E1%84%80%E1%85%AE%E1%84%89%E1%85%A5%E1%86%BC

<!-- # 호이스팅, 스택, this -->

# 실행 컨텍스트

자바스크립트 엔진은 코드를 실행하기 위하여 실행에 필요한 여러가지 정보를 알고 있어야 한다. `실행에 필요한 여러가지 정보`란 아래와 같은 것들이 있다.

- 변수 : 전역변수, 지역변수, 매개변수, 객체의 프로퍼티
- 함수 선언
- 변수의 유효범위(Scope)
- this

실행 컨텍스트가 생성되면 자바스크립트 엔진은 실행에 필요한 여러 정보들을 담을 객체를 생성한다. 이를 Variable Object(VO / 변수 객체)라고 한다. Variable Object는 코드가 실행될 때 엔진에 의해 참조되며 코드에서는 접근할 수 없다.

Variable Object는 아래의 정보를 담는 객체이다.

- 변수
- 매개변수(parameter)와 인수 정보(arguments)
- 함수 선언(`함수 표현식은 제외`)

스코프 체인은 식별자 중에서 객체(전역 객체 제외)의 프로퍼티가 아닌 식별자, 즉 변수를 검색하는 메커니즘이다.
식별자 중에서 `변수가 아닌 객체의 프로퍼티(물론 메소드도 포함된다)를 검색하는 메커니즘은 프로토타입 체인`(Prototype Chain)이다.

자바스크립트는 실행 컨텍스트가 활성화되는 시점에 다음과 같은 현상이 발생한다.

- `호이스팅`이 발생한다(선언된 변수를 위로 끌어올린다)
- 외부 환경 정보를 구성한다
- `this` 값을 설정한다.

## 실행 컨텍스트의 생성 과정

1. 전역 코드에의 진입

컨트롤이 실행 컨텍스트에 진입하기 이전에 유일한 전역 객체(Global Object)가 생성된다. 전역 객체는 단일 사본으로 존재하며 이 객체의 프로퍼티는 코드의 어떠한 곳에서도 접근할 수 있다. 초기 상태의 전역 객체에는 빌트인 객체(Math, String, Array 등)와 BOM, DOM이 설정되어 있다.

- 1. 스코프 체인의 생성과 초기화

- 2. Variable Instantiation(변수 객체화) 실행
  <!--  Variable Instantiation(변수 객체화)는 아래의 순서로 Variable Object에 프로퍼티와 값을 set한다. (반드시 1→2→3 순서로 실행된다.) -->

  - 1. (Function Code인 경우) 매개변수(parameter)가 Variable Object의 프로퍼티로, 인수(argument)가 값으로 설정된다.

  - 2. 대상 코드 내의 함수 선언(함수 표현식 제외)을 대상으로 함수명이 Variable Object의 프로퍼티로, 생성된 함수 객체가 값으로 설정된다.(함수 호이스팅)

  - 3. 대상 코드 내의 변수 선언을 대상으로 변수명이 Variable Object의 프로퍼티로, undefined가 값으로 설정된다.(변수 호이스팅)
    <!--  -->

  - 1.  함수 선언은 Variable Instantiation 실행 순서 2.와 같이 선언된 함수명 foo가 Variable Object(전역 코드인 경우 Global Object)의 프로퍼티로, 생성된 함수 객체가 값으로 설정된다.

    - 생성된 함수 객체는 [[Scopes]] 프로퍼티를 가지게 된다. [[Scopes]] 프로퍼티는 함수 객체만이 소유하는 내부 프로퍼티(Internal Property)로서 함수 객체가 실행되는 환경을 가리킨다. 따라서 현재 실행 컨텍스트의 스코프 체인이 참조하고 있는 객체를 값으로 설정한다. 내부 함수의 [[Scopes]] 프로퍼티는 자신의 실행 환경(Lexical Enviroment)과 자신을 포함하는 외부 함수의 실행 환경과 전역 객체를 가리키는데 이때 자신을 포함하는 외부 함수의 실행 컨텍스트가 소멸하여도 [[Scopes]] 프로퍼티가 가리키는 외부 함수의 실행 환경(Activation object)은 소멸하지 않고 참조할 수 있다. 이것이 클로저이다.

    - 함수선언식의 경우, 변수 객체(VO)에 함수표현식과 동일하게 함수명을 프로퍼티로 함수 객체를 할당한다는 것이다. 단, 함수선언식은 변수 객체(VO)에 함수명을 프로퍼티로 추가하고 즉시 함수 객체를 즉시 할당하지만 함수 표현식은 일반 변수의 방식을 따른다. 따라서 함수선언식의 경우, 선언문 이전에 함수를 호출할 수 있다. 이러한 현상을 함수 호이스팅(Function Hoisting)이라 한다.

  - 2. 변수 선언은 Variable Instantiation 실행 순서 3.과 같이 선언된 변수명( x )이 Variable Object의 프로퍼티로, undefined가 값으로 설정된다.

    - var 키워드로 선언된 변수는 선언 단계와 초기화 단계가 한번에 이루어진다. 다시 말해 스코프 체인이 가리키는 변수 객체에 변수가 등록되고 변수는 undefined로 초기화된다. 따라서 변수 선언문 이전에 변수에 접근하여도 Variable Object에 변수가 존재하기 때문에 에러가 발생하지 않는다. 다만 undefined를 반환한다. 이러한 현상을 변수 호이스팅(Variable Hoisting)이라한다.

- 3. this value 결정

  - 변수 선언 처리가 끝나면 다음은 this value가 결정된다. this value가 결정되기 이전에 this는 전역 객체를 가리키고 있다가 함수 호출 패턴에 의해 this에 할당되는 값이 결정된다. 전역 코드의 경우, this는 전역 객체를 가리킨다.

  - 전역 컨텍스트(전역 코드)의 경우, Variable Object, 스코프 체인, this 값은 언제나 전역 객체이다.

# Summary

- 실행 컨텍스트는 실행할 코드에 제공할 환경 정보들을 모아놓은 객체이다.
  전역 공간에서 자동으로 생성되는 전연 컨텍스트
  eval함수
  함수 실행에 의한 컨텍스트
- 실행 컨텍스트 객체는 활성화 되는 시점에 VariableEnviroment, LexcialEnvrionment, ThisBinding의 세 가지 정보를 수집한다.
- 실행 컨텍스트를 생서할 때 VariableEnvironment와 LexicalEnvironment가 동일한 내용으로 구성된다.
- LexicalEnvironment는 함수 실행 도중에 변경되는 사항이 즉시 반영된다.

- LexicalEnvironment와 VariableEnvironment는 다음과 environmentRecord와 outerEnvironmentReference로 구성돼 있다.

  1. environmentRecord는 매개변수 식별자, 변수 식별자, 선언한 함수의 식별자 등을 수집한다.

  - 이것 때문에 호이스팅이라는 개념이 사용된다.
  - 호이스팅은 코드 해석을 좀 더 수월하게 하기 위해 environmentRecord의 수집 과정을 추상화한 개념이다.
  - 변수 선언부와 함수 선언문에 호이스팅이 발생한다.
  - 함수 표현식을 사용할 경우 함수의 선언부만 호이스팅이 발생한다.

  2. outerEnvironmentReference는 상위(직전) 컨텍스트의 LexcicalEnviroment 정보를 참조한다.

  - 이것 때문에 스코프가 형성되고, 스코프 체인을 통해 상위 컨텍스트에 접근할 수 있다.
  - 스코프는 변수의 유효범위를 말한다.
