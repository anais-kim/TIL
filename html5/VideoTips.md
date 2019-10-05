### Video Customizing Tips

----

#### 1. You cannot autoplay video
- 사용자에게 원치 않는 동영상이 강제로 재생되는 것을 막기 위해 몇몇 브라우저들은 autoplay 기능을 제한하고 있다. 자바스크립트를 이용해 video.prototype.play() 메서드를 바로 실행하는 경우 역시 마찬가지이다.
- 만약 autoplay를 하고 싶다면, 오디오를 mute할 경우 가능하다. (트위터처럼)
- 사용자의 인터렉션이 발생했을 때 이벤트를 통해 재생시키는 방법이 가장 자연스럽다. (재생버튼을 클릭했을 때 재생, 스크롤 이벤트를 통해 비디오가 화면 안에 보여졌을 때 재생 등)

----

#### 2. You cannot hide default controls when is fullscreen
- 기본적으로 제공되는 비디오 컨트롤을 사용하지 않고 볼륨, 스킵 등을 커스터마이징 해서 구연할 경우 풀스크린 모드에서는 어려움이 생긴다. 풀스크린 모드에서는 기본 비디오 컨트롤이 강제되며 이것을 보이지 않게 할 좋은 방법은 없다.
- 가장 나은 방법은 비디오 자체를 풀스크린하는 것이 아니라, 비디오 바깥의 wrapper를 풀스크린 하는 것이다.
```javascript
function toggleFullscreen() {
  if (document.fullscreenElement === wrapper) {
    document.exitFullscreen();
  } else {
    wrapper.requestFullscreen();
  }
}
```
