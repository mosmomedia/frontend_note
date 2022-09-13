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
