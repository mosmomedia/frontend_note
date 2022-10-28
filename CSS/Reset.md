https://velog.io/@teo/2022-CSS-Reset-%EB%8B%A4%EC%8B%9C-%EC%8D%A8%EB%B3%B4%EA%B8%B0

```css
* {
	margin: 0;
	padding: 0;
	font: inherit;
	color: inherit;
}
*,
:after,
:before {
	box-sizing: border-box;
	flex-shrink: 0;
}
:root {
	-webkit-tap-highlight-color: transparent;
	-webkit-text-size-adjust: 100%;
	text-size-adjust: 100%;
	cursor: default;
	line-height: 1.5;
	overflow-wrap: break-word;
	-moz-tab-size: 4;
	tab-size: 4;
}
html,
body {
	height: 100%;
}
img,
picture,
video,
canvas,
svg {
	display: block;
	max-width: 100%;
}
button {
	background: none;
	border: 0;
	cursor: pointer;
}
a {
	text-decoration: none;
}
table {
	border-collapse: collapse;
	border-spacing: 0;
}
```

*{margin:0; padding:0; font:inherit; color:inherit;}
margin, padding, font, color를 초기화 시켜줍니다. 대부분의 Reset은 여기에 치중되어 있고 Reset의 크기가 커지는 것을 원하지 않아서 *을 사용하였습니다. 예전과 달리 최신 브라우저의 \* 성능은 문제가 없는 수준이기에 조금 더 간결한 형태의 Reset을 원했습니다.

font:inherit는 버튼이나 Input등의 글자가 고유의 시스템 글자로 되는 문제가 있어 현재 글자와 동일하게 보이기 위해서 추가하였습니다.

color:inherit의 경우 a나 input, textarea의 글자색을 그대로 쓸 수 있게 하기 위해서 추가하였습니다.

\*, :after, :before {box-sizing:border-box; flex-shrink:0;}
box-sizing을 border-box로 바꾸는것은 작업을 훨씬 더 편리하게 만들어 줍니다. 최초 박스 모델이었던 content-box는 paddig과 border가 정해진 content-width 바깥으로 만들어지는 구조였습니다.

하지만 width가 auto일 경우에는 부모의 크기를 따라가면서 안쪽으로 padding과 border가 만들어지는 방식이었습니다. 이 점도 충분히 혼란스러운데 대부분의 디자인 툴이 width에서 안쪽으로 padding을 잡는식으로 되다 보니 padding이나 border가 생기면 그에 맞게 계속 계산을 하는게 불편하기 때문에 🔥 최근에 나온 border-box가 default로 설정되는 것은 바람직하다고 생각합니다.

또한 flex-shrink:0 역시 default가 1이 아니라 0이 되어야 한다고 생각합니다. 가급적 원본의 컨텐츠가 잘리지 않고 크기대로 나와주는 것이 좋다고 생각합니다.

:root {... overflow-wrap:break-word;word-break:break-word; ... }
-webkit-tap-highlight-color: 모바일에 클릭시 검은색 영역이 사라집니다.

-webkit-text-size-adjust: 모바일에서도 원래의 폰트 크기대로 출력됩니다.

👍 overflow-wrap:break-word;word-break:break-word;을 :root에 걸어두면 띄어쓰기가 없이 글자를 입력하면 wrap이 되지 않고 삐져나가는 일이 사라집니다.

img, picture, video, canvas, svg {display: block; max-width:100%;}
이미지나 비디오가 글자 취급인 inline으로 되어 있어서 외부에서 엘리먼트를 감싸다 보면 꼭 하단에 4px씩의 여백이 생기곤 합니다. 대부분의 미디어 컨텐츠는 block 취급을 받는게 낫습니다. max-width:100%는 CSS가 AWESOME하지 않게 하도록 하기 위함입니다. (삐져나가는 거 금지)
