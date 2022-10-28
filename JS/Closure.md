# Closure

자신을 포함하고 있는 외부함수보다 내부함수가 더 오래 유지되는 경우, `외부 함수 밖에서 내부함수가 호출되더라도 외부함수의 지역 변수에 접근` 할 수 있는데 이러한 `함수`를 **클로저(Closure)**라고 부른다.

즉, 클로저는 반환된 `내부함수`가 `자신이 선언됐을 때의 환경(Lexical environment)인 스코프를 기억`하여 자신이 선언됐을 때의 환경(스코프) 밖에서 호출되어도 그 환경(스코프)에 접근할 수 있는 함수를 말한다. 이를 조금 더 간단히 말하면 `클로저는 자신이 생성될 때의 환경(Lexical environment)을 기억하는 함수`라고 말할 수 있겠다.

클로저에 의해 참조되는 외부함수의 변수 즉 `outerFunc 함수의 변수 x를 자유변수(Free variable)`라고 부른다. 클로저라는 이름은 자유변수에 함수가 닫혀있다(closed)라는 의미로 의역하면 `자유변수에 엮여있는 함수`라는 뜻이다.

```js
function add5(x) {
	let five = 5;

	return function add(x) {
		return x + five++;
	};
}

const result = add5();

console.log(result(0)); // 5
console.log(result(0)); // 6
console.log(result(0)); // 7
```

## Usage

1. 상태 유지
   클로저가 가장 유용하게 사용되는 상황은 현재 상태를 기억하고 변경된 최신 상태를 유지하는 것이다.
2. 전역 변수의 사용 억제
3. 정보 은닉

<!--  -->

바깥 스코프에 있는 변수를 가져다 사용하는 *함수*와, 변수가 저장되는 *저장소*를 **클로저(closure)**라고 부릅니다.

클로저의 성질을 통해 *고차 함수를 흥미로운 방식으로 활용*할 수 있습니다.

1. 고차 함수의 인수로 함수를 넘길 때, 해당 함수에서 바깥 스코프에 있는 변수를 사용할 수 있습니다.

```js
const people = [
	{ name: '윤아준', age: 19 },
	{ name: '신하경', age: 20 },
];

function peopleOlderThan(people, threshold) {
	return people.filter((person) => person.age > threshold);
}

peopleOlderThan(people, 19); // [ { name: '신하경', age: 20 } ]
```

2. 특정한 방식으로 동작하는 함수를 만들어내는 고차 함수를 작성할 수 있습니다.

```js
function makeAdder(x) {
	return function (y) {
		return x + y;
	};
}

[1, 2, 3].map(makeAdder(2)); // [3, 4, 5]
```

3. 때때로 클로저의 성질은 데이터를 숨기고 정해진 방법을 통해서만 데이터에 접근할 수 있도록 제한을 두는 데 활용되기도 합니다.1

```js
function makeCounter(x = 1) {
	return function () {
		return x++;
	};
}

// `x`를 직접 변경할 수 있는 방법이 없습니다!

const counter = makeCounter();
console.log(counter()); // 1
console.log(counter()); // 2
```

```js
function personFactory(initialAge) {
	let age = initialAge;
	return {
		getOlder() {
			age++;
		},
		getAge() {
			return age;
		},
	};
}
// `age`를 직접 변경할 수 있는 방법이 없습니다!
```

근래의 JavaScript 디버거는 클로저에 어떤 값이 들어있는지를 보여주는 기능을 포함하고 있습니다.
