DOM은 문서 객체 모델(Document Object Model)의 준말이다. 이것은 HTML 문서의 객체 표현이고 외부를 향하는 자바스크립트와 같은 HTML 요소의 연결 지점이다. 트리의 최상위 객체는 문서이다.

DOM은 마크업과 1:1의 관계를 맺는다.

- 브라우저들은 사용자가 띄운 웹 문서를 구성과 내용에 맞게 객체화한다.
- 각 요소(element)별로 구조화한다.
- 이 요소들은 상, 하위 구조나 병렬 구조로 체계화된다.
- 웹 문서에 대한 모든 내용을 담고있는 객체이다.
- DOM은 JS를 통해 dynamic하게 변경 가능하다.
- DOM은 HTML 문서를 node tree로 나타낸다.
- NODE : 트리 구조에서 데이터 상,하위 계층을 나타내는 위치의 항목.

## DOM(Document Object Model)

DOM은 도큐먼트 객체 모달(DOM: Document Object Model) 이다. Document는 문서이고 Object는 객체로 번역이 된다. 그리고 Model은 말 그데로 모델 이다. 문서 객체 모델로 번역을 할 수 있다. _문서 객체란 이나 같은 HTML문서의 태그들을 JavaScript가 이용할 수 있는 객체(object)로 만들면 그것을 문서 객체라고 한다_. 여기에 Model을 붙였는데 Model이라는 영어 단어에는 모형, 주형이라는 의미도 있고 모듈이라는 의미도 있다. 비슷하게 여기서는 문서 객체를 ‘인식하는 방식’이라고 해석할 수 있다. 조금 더 명확하게 DOM을 정의해보면, DOM은 넓은 의미로 *웹 브라우저가 HTML 페이지를 인식하는 방식*을 의미한다. 조금 좁은 의미로 보면 *document 객체와 관련된 객체의 집합*을 의미할 수도 있다. 이제 DOM을 보게 되면 웹 브라우저가 html 페이지를 인식하는 방식을 이야기 하거나 문서 객체(document object)와 관련된 객체의 집합에 관한 이야기라는 것을 쉽게 추측할 수 있을것디.

DOM is a collection of functions and attributes / data that we use to create JavaScript programs that we can call APIs (Application Programming Interface). DOM can be used in HTML, XM and SVG. DOM is not only used for JavaScript programming but can be used for other programming as well.

Inside the document object, we will find the functions and attributes that we can use to manipulate the HTML document.

DOM has a structure in the form of a tree we can call DOMtree.

we can access more specific HTML elements by using some of the functions below.

- getElementById() function to select elements based on attributes id.
- getElementByName() function to select elements based on attributes name.
- getElementByClassName() function to select elements based on attributes class.
- getElementByTagName() function to select elements by tag name.
- getElementByTagNameNS() function to select elements by tag name.
- querySelector() function to select elements based on query.
- querySelectorAll() function to select elements based on query.
  and others.

In the above method there is a single return value of the HTML element. In addition, there are also those that return multiple elements from an HTML file which is commonly referred to as an HTMLCollection. Because of all method above belongs to the document object, so don’t forget to prefix all calls method-method above with syntax document.

### node

tree 구조에서 root 노드를 포함한 모든 개개의 개체를 node라고 표현한다. head, body, title, script, h1, select, button, checkbox 등의 태그뿐 아니라 태그 안의 텍스트나 속성 등도 모두 node에 한다. 이중 HTML 태그를 요소노드(Element Node)라고 부르고 요소 노드 안에 있는 글자를 Text 노드(Text Node)라고 부르기도 한다.

노드의 종류

W3C HTML DOM 표준에 따르면, HTML 문서의 모든 것은 노드이다.

- 문서 노드(document node) : HTML 문서 전체를 나타내는 노드
- 요소 노드(element node) : 모든 HTML 요소는 요소 노드이며, 속성 노드를 가질 수 있는 유일한 노드
- 속성 노드(attribute node) : 모든 HTML 요소의 속성은 속성 노드이며, 요소 노드에 관한 정보를 가지고 있으나 - 해당 요소 노드의 자식 노드(child node)에: 는 포함되지 않는다
- 텍스트 노드(text node) : HTML 문서의 모든 텍스트는 텍스트 노드
- 주석 노드(comment node) : HTML 문서의 모든 주석은 주석 노드

### JavaScript로 문서객체 생성

문서 객체가 생성되는 방식은 두 가지로 나누어 볼 수 있다. 하나는 웹 브라우저가 HTML 페이지에 적혀 있는 태그를 읽으면 생성하는 것이다. 이런 과정을 정적으로 문서 객체를 생성한다고 말한다. 단순히 적혀져 있는 그대로 문서객체가 생성되는 것을 표현한 것이다.

반대로 원래 HTML 페이지에 없던 문서객체를 JavaScript를 이용해서 생성할 수 있다. 이런 과정을 동적으로 문서객체를 생성한다고 한다. 따라서 JavaScript로 문서객체를 생성한다는 것은 처음에는 HTML 페이지에 없던 문서객체를 동적으로 생성하는 것이 된다.

let element = document.createElement(tagName[, options]);

### Document Fragment

사실 React에서<Fragment>의 개념은 어렵지 않게 접할 수 있다. 최상위 노드를 하나만 둬야하는 경우가 많다보니 Wrapper로 종종 쓰게 되기 때문이다(물론 그냥 <div>로 감싸는 사람도 있지만.). 하지만 이는 리액트에 한정된 개념이 아니라 JavaScript에 존재하는 개념이라는 것을 알게 되었다. 성능 최적화를 위해서 활용될 수 있다고 하니 공부해두자.

**Document Fragment를 만드는 방법**

<div> 엘리먼트를 만들고자 할 때 아래와 같이 작성하면 된다는 것을 알 것이다.

```js
var element = document.createElement('div');
```

Document Fragment를 만들 때에도 비슷하다. 하지만, 빈 태그(즉, React의 JSX로 치면 <> </>)인 셈이니, 인자로는 아무 것도 넣지 않는다.

```js
var documentFragment = document.createDocumentFragment();
```

이렇게 만들어진 Document Fragment는 DOM트리 내부에 존재하는 게 아니라 메모리상에만 따로 존재하게 된다. DOM에다가 바로 작업을 하는 게 아니라, 본격적인 DOM 조작에 앞서 잠시 보관해두는 껍데기인 것이다. 노드 조각이라고도 한다.

**Document Fragment를 활용한 성능 최적화**
어떤 때에, 왜 Document Fragment가 유용하게 쓰일 수 있다는 걸까?

DOM객체는 트리구조로 되어있기 때문에, 특정 엘리먼트에 접근하는 것을 줄일수록 좋다. Document Fragment는 DOM트리와 별개로 존재하므로 접근 속도가 빠르다.
Reflow는 성능에 영향을 미치는 주요 요인중 하나로, Reflow를 줄일수록 좋다. Document Fragment를 이용해서 작업을 모아놨다가 한번에 DOM에 적용한다면 Reflow를 최소화할 수 있을 것이다.

## BOM(Browser Object Model)

웹 서비스 개발은 브라우저와 밀접한 관련이 있다. 모든 서비스는 사실 웹 브라우저를 바탕으로 실행이 되기 때문이다. 이 *브라우저와 관련된 객체들의 집합을 브라우저 객체 모델(BOM: Browser Object Model)*이라고 부른다. 이 브라우저 객체 모델(BOM)을 이용해서 Browser와 관련된 기능들을 구성하게된다. *DOM은 이 BOM 의 한 부분*이다. 브라우저 객체 모델(BOM)의 최상위 객체는 window라는 객체이다. DOM은 이 window 객체의 하위 객체이다

BOM is a Browser Object Model, which is a _window object_ supported by all browsers representing a browser window consisting of _navigator, history, screen, location and document objects_ which are children of windows. BOM can function to check an event from windows with window.addEventListener and can perform manipulation using window.innerHeight and window.innerWidth.

BOM can give special commands to the browser, for example, we use special attributes in the browser, you can make it using browser.

Method _alert(), prompt(), consol.log()_
