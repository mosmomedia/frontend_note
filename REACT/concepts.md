## Virtual DOM

Virtual DOM (VDOM)은 UI의 이상적인 또는 “가상”적인 표현을 메모리에 저장하고 ReactDOM과 같은 라이브러리에 의해 “실제” DOM과 동기화하는 프로그래밍 개념입니다. 이 과정을 재조정이라고 합니다.

_기존에는 DOM(Document Object Model)을 조작해서 브라우저에 화면을 나타내는 형식이었다_. DOM 자체의 성능은 느리다고 할 수 없지만 매번 DOM 전체를 직접 접근하여 변화를 주면 HTML, CSS, JS파일 전체를 다시 리랜더링하기 때문에 느려질 수 밖에 없었다. 그래서 *리액트는 가상 DOM를 이용해서 실제 DOM를 조작하는 횟수를 줄여서 성능을 빠르게 개선*하였다.

리액트에서 가상 DOM을 이용하는 방식은 다음과 같다. *데이터가 변경*되면 리액트는 *가상 DOM를 다시 변경*한다. 그리고 *이전의 가상 DOM과 비교해서 변경된 부분*을 체크하고 **변경된 부분만 실제 DOM에 적용**한다. 이러한 리액트의 랜더링 방식은 DOM 전체를 매번 리랜더링했던 이전 방식의 비해 빠르며 *애플케이션의 규모가 클수록, 데이터의 변경이 많을수록 더 큰 힘을 발휘*한다.

데이터 변경 -> 가상 DOM 리랜더링 -> 이전 가상 DOM과 비교 -> 변경된 부분 실제 DOM에 적용

## Fundamentals of React

**Components**: Components are the fundamental building elements of each React application, and most applications include a few components. A part is a user interface element. React divides the user interfaces into distinct, reusable components that might be taken care of independently.

It utilizes two sorts of components :

· _Functional Components_: These components are otherwise called stateless components since they have no state of their own. As props, they might extricate data from different components (properties).

· _Class Components_: These components have a distinct render function for returning JSX to the screen and may keep and control their state. Since they can have a state, they are in some cases named stateful components.

**State**: The state object is a built-in React object that stores information or data about the part. A part’s state can change over the long run, and when it works out, the part should be re-rendered. The part’s state might change as a result of user activity or framework-generated occasions, and these progressions affect the way of behaving of the part.

**Properties (Props)**: Properties are abbreviated as props. It’s a built-in React object that saves the worth of a label’s attributes and functions in basically the same manner as HTML attributes. It permits you to send data starting with one part and then onto the next similarly as arguments are passed in a function.

## JSX

JSX(Javascript + xml)는 자바스크립트에 대한 확장 구문으로서, 리액트에서 element(요소)를 제공해 줍니다. 장점은 매우 다양합니다. 단순히 개발자가 마크업 코드에 익숙하다면, 그것만으로도 JSX를 통해 컴포넌트를 구성하는 데 쉽게 적응할 수 있다는 장점이 있습니다.
