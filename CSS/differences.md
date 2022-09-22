# display: none vs opacity: 0 vs visibility: hidden

There are three common CSS properties to make an element invisible:

_display: none_
_opacity: 0_
_visibility: hidden_

## Differences

display: none doesn't take space when the element is rendered. The other ways still take the space normally.

The browser will not response to any events of element which uses either display: none or visibility: hidden. The visibility: hidden style behaves like a combination of opacity: 0 and pointer-events: none.

Regarding the accessibility, opacity: 0 is the only property which makes the element accessible in the tab order, and the element's content can be read by screen readers.

Applying display: none or opacity: 0 will effect on child elements. visibility: hidden, on the other hand, doesn't change the visibility of any children.

It's worth noting that if you want to measure the size of element, then you can't use display: none at all.

As mentioned in the first difference, an element with display: none doesn't take any space on the page. Hence, all properties related to the element size, such as clientHeight, clientWidth, height, offsetHeight, offsetWidth, scrollHeight, scrollWidth and width are zero.

All properties returned by the getBoundingClientRect() method are zero as well.

Similarly, an element with visibility: hidden will have empty inner text (equivalent with the innerText property).
