# Scope

The scope is a policy that manages the `accessibility of variables`.

The code block of `if, for, while statements` also create a scope.

The inner scope can access the variables of its outer scope.

스코프는 `참조 대상 식별자를 찾아내기 위한 규칙`이다. 자바스크립트는 이 규칙대로 식별자를 찾는다.

- 전역 스코프 (Global scope)
  코드 어디에서든지 참조할 수 있다.
- 지역 스코프 (Local scope or `Function-level scope`)
  함수 코드 블록이 만든 스코프로 함수 자신과 하위 함수에서만 참조할 수 있다.

자바스크립트는 타 언어와는 달리 특별한 시작점(Entry point)이 없어서 위 코드와 같이 전역에 변수나 함수를 선언하기 쉽다.

C언어의 경우 main 함수가 시작점이 되기 때문에 대부분은 코드는 main 함수 내에 포함된다. C언어의 경우 전역 변수를 선언하기 위해서는 의도적으로 main 함수 밖에 변수를 선언하여야 한다.

## Module scope

Looking from another angle, the scope is an encapsulation mechanism for code blocks, functions, and modules.

window and document, for example, are global variables supplied by the browser. In a Node environment, you can access process object as a global variable.

## Lexical Scope

Lexical scoping means that the accessibility of variables is determined statically by the position of the variables within the nested `function scopes`: the inner function scope can access variables from the outer function scope.

Moreover, `the innerFunc() is a closure` because it captures the variable outerVar from the lexical scope.

자바스크립트는 `함수 레벨 스코프`(function-level scope)를 따른다. 함수 레벨 스코프란 함수 코드 블록 내에서 선언된 변수는 함수 코드 블록 내에서만 유효하고 함수 외부에서는 유효하지 않다(참조할 수 없다)는 것이다.

단, ECMAScript 6에서 도입된 `let keyword를 사용하면 블록 레벨 스코프`를 사용할 수 있다.

변수명이 중복된 경우, 지역변수를 우선하여 참조한다.
중첩 스코프는 가장 인접한 지역을 우선하여 참조한다

var - function level scope
let, const - block level scope

`동적 스코프`는 함수를 `어디서 호출`하였는지에 따라 상위 스코프를 결정하는 것이고
`렉시컬 스코프`는 함수를 `어디서 선언`하였는지에 따라 상위 스코프를 결정하는 것이다.

`자바스크립트는 렉시컬 스코프를 따르므로 함수를 선언한 시점에 상위 스코프가 결정된다. 함수를 어디에서 호출하였는지는 스코프 결정에 아무런 의미를 주지 않는다.`

var x = 1 vs y = 1

변수가 아니라 단지 프로퍼티인 y는 delete 연산자로 삭제할 수 있다. 전역 변수는 프로퍼티이지만 delete 연산자로 삭제할 수 없다.

전역변수 사용을 억제하기 위해,` 즉시 실행 함수`(IIFE, Immediately-Invoked Function Expression)를 사용할 수 있다. 이 방법을 사용하면 전역변수를 만들지 않으므로 라이브러리 등에 자주 사용된다. 즉시 실행 함수는 즉시 실행되고 그 후 전역에서 바로 사라진다.

## Var 키워드로 선언된 변수

1. 함수 레벨 스코프(Function-level scope)

   - 함수의 코드 블록만을 스코프로 인정한다. 따라서 전역 함수 외부에서 생성한 변수는 모두 전역 변수이다. 이는 전역 변수를 남발할 가능성을 높인다.
   - for 문의 변수 선언문에서 선언한 변수를 for 문의 코드 블록 외부에서 참조할 수 있다.

2. var 키워드 생략 허용

   - 암묵적 전역 변수를 양산할 가능성이 크다.

3. 변수 중복 선언 허용

   - 의도하지 않은 변수값의 변경이 일어날 가능성이 크다.

4. 변수 호이스팅
   - 변수를 선언하기 이전에 참조할 수 있다.

# Scope Chain

스코프의 개념은 대부분의 언어에 존재하지만, ES5까지의 Javascript는 특이하게도 오직 함수에 의해서만 스코프가 생성된다.

scope chain

식별자의 유효범위를 안에서 바깥으로 차례로 검색해나는 것
이를 가능하게 하는 것이 outerEnvironmentReference이다.

선언하다라는 행위가 실제로 일어날 수 있는 시점은 콜 스택 상에서 어떤 실행 컨텍스트가 활성화된 상태일 때뿐이다.모든 코드는 실행 컨텍스트가 활성화 상태일 때 실행되기 때문이다.
