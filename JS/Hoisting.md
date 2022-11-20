<!-- 실행 컨텍스트 -->

# Hoisting

호이스팅(Hoisting)이란, _var 선언문이나 function 선언문_ 등을 해당 *스코프의 선두*로 옮긴 것처럼 동작하는 특성을 말한다.

_즉, 자바스크립트는 모든 선언문(var, let, const, function, function\*, class)이 선언되기 이전에 참조 가능하다._

선언 단계(Declaration phase)
변수를 실행 컨텍스트의 변수 객체(Variable Object)에 등록한다. 이 변수 객체는 스코프가 참조하는 대상이 된다.

초기화 단계(Initialization phase)
변수 객체(Variable Object)에 등록된 변수를 위한 공간을 메모리에 확보한다. 이 단계에서 변수는 undefined로 초기화된다.

할당 단계(Assignment phase)
undefined로 초기화된 변수에 실제 값을 할당한다.

var 키워드로 선언된 변수는 선언 단계와 초기화 단계가 한번에 이루어진다. *즉, 스코프에 변수를 등록(선언 단계)하고 메모리에 변수를 위한 공간을 확보한 후, undefined로 초기화(초기화 단계)한다.* 따라서 변수 선언문 이전에 변수에 접근하여도 스코프에 변수가 존재하기 때문에 에러가 발생하지 않는다. 다만 undefined를 반환한다. 이후 변수 할당문에 도달하면 비로소 값이 할당된다. 이러한 현상을 변수 호이스팅(Variable Hoisting)이라 한다.

즉, 코드가 실행 되기 전에 자바스크립트의 엔진은 이미 실행 컨텍스트에 속한 변수명들을 모두 알고 있게 되는 셈이다.

엔진의 실제 동작 방식 대신에 자바스크립트 엔진은 식별자들을 최상단으로 끌어올려놓은 다음, 실제 코드를 실행한다 라고 생각해도 코드 해석에 문제되는 것이 없기 때문이다.

중요한 점은, 자바스크립트 엔진이 실제로 변수를 끌어올리지는 않지만, 편의상 끌어올리는 것으로 간주하자는 것이다.

변수의 경우 정의부만 호이스팅 되지만, `함수는 함수 전체가 호이스팅 된다`.

## Order of declarations

```js
var hosted = function () {
	console.log('hi');
};
```

It’s a little twisted, but a variable assignment takes precedence over a function declaration, and a function declaration takes precedence over a variable declaration. What it means in practice is that if you declare and assign a variable and then create a function with the same name the variable will be a type of variable, not a function.

It is the javascript engine that defines all var and function declarations to undefined in the creation phase during the global exection context. And becuase of that _it is available in the meomory as undefined and we won't get any errors_ if we trying to use the variable before it has been declared.
