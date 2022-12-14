# Array

배열은 JavaScript에 내장되어 있는 `자료구조`입니다. 배열은 `객체의 일종`이지만, 내부적으로 특별하게 취급되어 일반적인 객체들과는 다른 특징을 갖고 있습니다.

배열 안에 들어있는 값들을 요소(element) 혹은 항목(item)이라고 합니다. **객체와 배열의 가장 큰 차이점은, 배열의 각 요소 간에는 순서가 있다는 점입니다.**

배열은 Array 생성자의 인스턴스입니다. 그러니까, 배열의 프로토타입으로 `Array.prototype 객체`가 지정되어 있습니다.

## Array.of

일관적이지 못한 생성자의 동작방식 때문에, ES2015에 Array.of 정적 메소드가 추가되었습니다. Array 생성자를 사용할 때에는 1번 방식으로만 사용하고, 2번 방식의 코드를 작성할 때는 생성자 대신 Array.of 정적 메소드를 사용하세요.

```js
new Array(1, 2, 3); // 이렇게 하지 마세요!
Array.of(1, 2, 3); // 대신 이렇게 하세요.

// `Array.of` 정적 메소드는 인수가 하나이더라도 그 인수를 요소로 갖는 배열을 반환합니다.
Array.of(1); // [1]

// 생성자는 이런 용도로만 사용하세요.
new Array(1000); // [empty × 1000]
```
