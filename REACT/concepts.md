## Virtual DOM

Virtual DOM (VDOM)은 UI의 이상적인 또는 “가상”적인 표현을 메모리에 저장하고 ReactDOM과 같은 라이브러리에 의해 “실제” DOM과 동기화하는 프로그래밍 개념입니다. 이 과정을 재조정이라고 합니다.

_기존에는 DOM(Document Object Model)을 조작해서 브라우저에 화면을 나타내는 형식이었다_. DOM 자체의 성능은 느리다고 할 수 없지만 매번 DOM 전체를 직접 접근하여 변화를 주면 HTML, CSS, JS파일 전체를 다시 리랜더링하기 때문에 느려질 수 밖에 없었다. 그래서 *리액트는 가상 DOM를 이용해서 실제 DOM를 조작하는 횟수를 줄여서 성능을 빠르게 개선*하였다.

리액트에서 가상 DOM을 이용하는 방식은 다음과 같다. *데이터가 변경*되면 리액트는 *가상 DOM를 다시 변경*한다. 그리고 *이전의 가상 DOM과 비교해서 변경된 부분*을 체크하고 **변경된 부분만 실제 DOM에 적용**한다. 이러한 리액트의 랜더링 방식은 DOM 전체를 매번 리랜더링했던 이전 방식의 비해 빠르며 *애플케이션의 규모가 클수록, 데이터의 변경이 많을수록 더 큰 힘을 발휘*한다.

데이터 변경 -> 가상 DOM 리랜더링 -> 이전 가상 DOM과 비교 -> 변경된 부분 실제 DOM에 적용

**왜 Virutal DOM 을 쓰는거야?**

_DOM에 변화가 생기면_, 렌더트리를 재생성하고 (그러면 모든 요소들의 스타일이 다시 계산됩니다) 레이아웃을 만들고 페인팅을 하는 과정이 다시 *반복*되는거죠.

복잡한 SPA(싱글 페이지 어플리케이션) 에서는 DOM 조작이 많이 발생해요. 그 뜻은 그 변화를 적용하기 위해 브라우저가 많이 연산을 해야한단 소리고, 전체적인 프로세스를 *비효율적*으로 만듭니다.

자, 이 이부분에서 Virtual DOM 이 빛을 발합니다! 만약에 뷰에 변화가 있다면, 그 변화는 실제 DOM 에 적용되기전에 가상의 DOM 에 먼저 적용시키고 그 최종적인 결과를 실제 DOM 으로 전달해줍니다. 이로써, 브라우저 내에서 발생하는 *연산의 양을 줄이면서 성능이 개선*되는 것 이지요.

_DOM 조작의 실제 문제는 각 조작이 레이아웃 변화, 트리 변화와 렌더링을 일으킨다는겁니다._ 그래서, 예를 들어 여러분이 30개의 노드를 하나 하나 수정하면, 그 뜻은 30번의 (잠재적인) 레이아웃 재계산과 30번의 (잠재적인) 리렌더링을 초래한다는 것이죠.

Virtual DOM 은 그냥 뭐 엄청 새로운것도 아니고, 그냥 *DOM 차원에서의 더블 버퍼링*이랑 다름이 없는거에요. 변화가 일어나면 그걸 오프라인 DOM 트리에 적용시키죠. 이 DOM 트리는 렌더링도 되지 않기때문에 연산 비용이 적어요. 연산이 끝나고나면 그 최종적인 변화를 실제 DOM 에 던져주는거에요. 딱 한번만 한는거에요. 모든 변화를 하나로 묶어서. 그러면, 레이아웃 계산과 리렌더링의 규모는 커지겠지만, 다시 한번 강조하자면 딱 한번만 하는거에요. 바로 이렇게, 하나로 묶어서 적용시키는것이, 연산의 횟수를 줄이는거구요.

사실, 이 과정은 Virtual DOM 이 없이도 이뤄질수 있어요. 그냥, 변화가 있을 때, 그 변화를 묶어서 DOM fragment 에 적용한 다음에 기존 DOM 에 던져주면 돼요.

그러면, _Virtual DOM이 해결 하려고 하는건 무엇이냐?_ 그 DOM fragment를 관리하는 과정을 수동으로 하나하나 작업 할 필요 없이, *자동화하고 추상화*하는거에요. 그 뿐만 아니라, 만약에 이 작업을 여러분들이 직접 한다면, *기존 값 중 어떤게 바뀌었고 어떤게 바뀌지 않았는지 계속 파악*하고 있어야하는데 (그렇지 않으면 수정 할 필요가 없는 DOM 트리도 업데이트를 하게 될 수도 있으니까요), 이것도 Virtual DOM 이 이걸 *자동*으로 해주는거에요. 어떤게 바뀌었는지 , 어떤게 바뀌지 않았는지 알아내주죠.

마지막으로, DOM 관리를 Virtual DOM 이 하도록 함으로써, 컴포넌트가 DOM 조작 요청을 할 때 다른 컴포넌트들과 상호작용을 하지 않아도 되고, 특정 DOM 을 조작할 것 이라던지, 이미 조작했다던지에 대한 정보를 공유 할 필요가 없습니다. 즉, _각 변화들의 동기화 작업을 거치지 않으면서도 모든 작업을 하나로 묶어줄 수 있다는거죠._

## Fundamentals of React

**Components**: Components are the fundamental building elements of each React application, and most applications include a few components. A part is a user interface element. React divides the user interfaces into distinct, reusable components that might be taken care of independently.

It utilizes two sorts of components :

· _Functional Components_: These components are otherwise called stateless components since they have no state of their own. As props, they might extricate data from different components (properties).

· _Class Components_: These components have a distinct render function for returning JSX to the screen and may keep and control their state. Since they can have a state, they are in some cases named stateful components.

**State**: The state object is a built-in React object that stores information or data about the part. A part’s state can change over the long run, and when it works out, the part should be re-rendered. The part’s state might change as a result of user activity or framework-generated occasions, and these progressions affect the way of behaving of the part.

**Properties (Props)**: Properties are abbreviated as props. It’s a built-in React object that saves the worth of a label’s attributes and functions in basically the same manner as HTML attributes. It permits you to send data starting with one part and then onto the next similarly as arguments are passed in a function.

## JSX

*JSX(Javascript + xml)는 자바스크립트에 대한 확장 구문으로서, 리액트에서 element(요소)를 제공*해 줍니다. 장점은 매우 다양합니다. 단순히 개발자가 마크업 코드에 익숙하다면, 그것만으로도 JSX를 통해 컴포넌트를 구성하는 데 쉽게 적응할 수 있다는 장점이 있습니다.

## import & webpack

import 를 하는 것은, 우리가 *webpack*을 사용하기에 가능한 작업입니다. 이렇게 불러오고나면 나중에 프로젝트를 빌드하게 됐을 때 웹팩에서 파일의 확장자에 따라 다른 작업을 하게 됩니다. CSS 파일을 불러오게되면, 나중에 프로젝트에서 사용한 프로젝트를 한 파일에 모두 결합해주는 작업을 진행하고, 자바스크립트 파일을 불러오게되면 모든 코드들이 제대로 로딩되게끔 순서를 설정하고 하나의 파일로 합쳐주죠. (나중에 다뤄볼 얘기지만 규칙에 따라 여러 파일로 분리해서 저장하는것도 가능합니다.) 그리고, svg 처럼 사전에 따로 설정을 되지 않은 확장자의 경우, 그냥 파일로서 불러온다음에 나중에 특정 경로에 사본을 만들어주게되고, 해당 사본의 경로를 텍스트로 받아오게 됩니다.

## 꼭 닫혀야 하는 태그

태그는 꼭 닫혀있어야 합니다. <div> 태그를 열었으면, </div> 를 통하여 태그를 꼭 닫아주어야 합니다. 우리가 html 에서 input 이나 br 태그를 작성 할 때 태그를 안닫을때도 있는데요, 똑같이 리액트에서 하시면 이런 오류를 겪에 될 테니 참고하세요.

## 감싸져 있는 엘리먼트

두개 이상의 엘리먼트는 무조건 하나의 엘리먼트로 감싸져있어야 합니다. 한번, 다음과 같이 코드를 작성해보세요.
