# Type

자바스크립트의 모든 값은 데이터 타입을 갖는다. ECMAScript 표준(ECMAScript 2015 (6th Edition), 이하 ES6)은 7개의 데이터 타입을 제공한다

- 원시 타입 (primitive data type)

  - boolean
  - null
  - undefined
  - number
  - string
  - symbol (ES6에서 추가)

- 객체 타입 (object/reference type)
  - object

## 불변성 (Immutability)

_원시 타입의 값 자체의 내용을 변경할 수 있는 방법은 없습니다._ 이런 성질을 불변성(immutability)이라고 하고, "JavaScript의 원시 값은 불변(immutable)이다"라고 말합니다.

예를 들면, 문자열을 변형하는 메소드는 모두 기존 문자열의 내용을 바꾸는 것이 아니라 새 문자열을 반환합니다. 다른 원시 타입의 메소드들도 마찬가지입니다.

```js
const str = 'JavaScript string is immutable!';

str.replace('!', '?'); // 'JavaScript string is immutable?'
str.slice(0, 10); // 'JavaScript'
str.toUpperCase(); // 'JAVASCRIPT STRING IS IMMUTABLE!'

console.log(str); // JavaScript string is immutable!
```

_변수에 저장된 원시 타입의 값을 바꾸려면, 오직 변수에 다른 값을 대입하는 방법밖에 없습니다._

_원시 타입을_ 인수로 해서 함수를 호출할 때에는, 원본이 변경될지도 모른다는 걱정을 할 필요가 없습니다. _값이 불변일 뿐더러, 애초에 함수 호출 시에는 값이 복사되어서 전달되기 때문에 원본을 변경할 수 있는 방법이 아예 없습니다._

**객체의 경우**를 생각해보면, 객체 자체의 내용을 변경할 수 있는 방법이 얼마든지 많이 있습니다. 따라서 _객체는 가변(mutable)입니다._

_가변인 값은 어디서 어떻게 변경될지 알 수 없습니다._ 변경되지 말아야 할 객체가 있다면, 정말로 변경되지 않도록 신경 써서 코드를 작성해야 합니다. 그러나 객체가 정말로 변경되지 않았는지를 확인하는 일은 쉽지 않아서, 때때로 객체의 가변성 때문에 프로그래밍이 어려워지기도 합니다.

객체의 가변성 때문에 어려움을 겪고 있다면, 두 가지 해결책을 시도해볼 수 있습니다.

먼저 *Object.freeze*의 사용을 고려해볼 수 있습니다. Object.freeze는 객체를 얼려서 속성의 추가/변경/삭제를 막습니다.

```js
const obj = { prop: 1 };

Object.freeze(obj);

// 모두 무시됩니다.
obj.prop = 2;
obj.newProp = 3;
delete obj.prop;

console.log(obj); // { prop: 1 }
```

다만 Object.freeze를 호출한다고 해서 객체 안에 있는 객체까지 얼려버리지는 않으므로, 중첩된 객체에는 Object.freeze를 사용하기가 조금 까다롭습니다. 그리고, 다음에 소개할 방법과 비교하면 여러모로 편의성이 떨어집니다.

다음으로 *Immutable.js 같은 라이브러리의 사용*을 고려해보세요. 이런 라이브러리들은 Object.freeze처럼 객체를 정말로 얼려버리지는 않지만, 객체를 마치 불변인 것처럼 다룰 수 있는 방법을 제공합니다. 다시 말하면, 이 객체들은 (문자열의 예에서 봤던 것처럼) 메소드를 통해 내용이 조금이라도 변경되면 아예 새로운 객체를 반환합니다. 즉, 내용이 달라지면 참조 역시 달라지게 되어 객체의 내용이 변경되었는지를 확인하는 작업이 아주 쉬워집니다.
