
# HTML5 Canvas with Video

---

## 캔버스에 비디오 불러오기

Canvas API의 CanvasRenderingContext2D.drawImage()를 통해 이미지를 불러올 수 있다.  
이 때 이미지로 사용가능한 데이터 타입은 아래와 같다.

- HTMLImageElement
- SVGImageElement
- **HTMLVideoElement**
- HTMLCanvasElement

캔버스에서 비디오를 사용할 때는 비디오의 캡쳐된 이미지를 불러오게 된다.  
따라서 실시간으로 비디오가 캔버스 위에 보여지게 하고 싶다면 setInterval()을 사용해 캔버스의 이미지를 계속 갱신해야 한다.

```javascript
function showVideo() {
  setInterval(() => {
    ctx.drawImage(video, 0, 0, video.videoWidth, video.videoHeight);
  }, 20);
}
```

---
  
##  비디오 이벤트 사용하기
만약 play이벤트가 발생한 순간 캔버스에서 비디오를 불러오려고 한다면 오류가 발생할 수 있다.  
아직 비디오 이미지가 생성되지 않았기 때문이다. 비디오 이벤트는 아래와 같은 순서로 발생한다.  
1. play
2. loadstart
3. durationchange
4. loadedmetadata
5. loadeddata
6. canplay
7. progress

canplay 이벤트가 발생했을 때 비로소 비디오를 사용할 수 있게 된다.  
```javascript
function showVideo() {
  setInterval(() => {
    ctx.drawImage(video, 0, 0, video.videoWidth, video.videoHeight);
  }, 20);
}

video.addEventListner('canplay', showVideo);
```

---
  
## 비디오 크기에 맞춰 캔버스 조정하기

캔버스의 width, height 속성은 따로 입력하지 않았을 경우 300x150px이 기본값이다.  
아래와 같이 비디오 크기에 맞춰 캔버스의 크기를 조정할 수 있다.
```javascript
function showVideo() {
  const {videoWidth: width, videoHeight: height} = video;
  canvas.width = width;
  canvas.height = height;
  
  setInterval(() => {
    ctx.drawImage(video, 0, 0, width, height);
  }, 20);
}
```

---

## 캡쳐된 이미지 저장하기

캔버스를 이용해 비디오 캡쳐 이미지를 저장할 수 있다.
```javascript
function saveCaptureImage() {
  const image = {
    title: 'capture.jpeg',
    url: canvas.toDataURL('image/jpeg', 0.8)
  }

  captureImage.innerHTML = `
    <a href=${image.url} title=${image.title} download=${image.title}>
      <img src=${image.url} alt=${image.title}>
    </a>
  `;
}
```

---

## 비디오에 필터 효과 주기

캔버스를 활용해 비디오 이미지의 rgb 픽셀값을 조정해 다양한 효과를 줄 수 있다.  
CanvasRenderingContext2D.getImageData()를 통해 얻은 rgba 값이 들어있는 배열의 값을 조정하면 된다.

- 붉은 필터 씌우기
```javascript
function redScreen() {
  const pixels = ctx.getImageData(0, 0, video.videoWidth, video.videoHeight);
  for (let i = 0; i <= pixels.data.length; i+=4) {
    pixels.data[i+1] = 0; // GREEN
    pixels.data[i+2] = 0; // BLUE
  }
  ctx.putImageData(pixels, 0, 0);
}
```

- RGB Split Effect
```javascript
function rgbSplit() {
  const pixels = ctx.getImageData(0, 0, video.videoWidth, video.videoHeight);
  for (let i = 0; i <= pixels.data.length; i+=4) {
    pixels.data[i] = pixels.data[i+100]; // RED
    pixels.data[i+1] = pixels.data[i+1+400]; // GREEN
    pixels.data[i+2] = pixels.data[i+2+700]; // BLUE
  }
  ctx.putImageData(pixels, 0, 0);
}
```
