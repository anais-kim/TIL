# Determining the diementions of the elements

https://developer.mozilla.org/ko/docs/Determining_the_dimensions_of_elements


## offsetWidth, offsetHeight
- 공간을 얼마나 차지하는지
- 스크롤바, 보더 포함
<img src="https://developer.mozilla.org/@api/deki/files/186/=Dimensions-offset.png">

## clientWidth, clientHeight
- 보이는 컨텐트의 크기
- 스크롤바, 보더 미포함
<img src="https://developer.mozilla.org/@api/deki/files/185/=Dimensions-client.png">

## offsetLeft, offsetTop
- offsetParent로부터의 상대적인 위치
- 만약 전체 viewPort에서의 절대적인 위치를 알고 싶다면 offsetParent를 거슬러 올라가 계산해야 함
```javascript
function calculateOffset(element, offset = {top: 0, left: 0}) {
  offset.top += element.offsetTop;
  offset.left += element.offsetLeft;

  return element.offsetParent? calculateOffset(element.offsetParent, offset) : offset;
}
```
