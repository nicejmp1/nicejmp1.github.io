---
layout: post
title: javascript 이벤트객체 (마우스 속성)
date: 2024-05-04 12:20 +0900
description: javascript
image: ../assets/img/post/javascript02.png
category: javascript
tags: javascript 
published: true
sitemap: true
---

# javascript 마우스 속성 

안녕하세요! 오늘은 마우스 속성 이벤트 메서드에 대해 알아보도록 하겠습니다.
<br>

## clientX : 브라우저 기준
>clientX는 마우스 이벤트(MouseEvent) 객체의 속성으로, 브라우저 창의 왼쪽 상단 모서리를 기준으로 마우스 포인터의 X 좌표를 나타냅니다. 화면 전체를 기준으로 한 위치가 아니라, 현재 표시되고 있는 뷰포트(뷰포트 스크롤 위치를 고려하지 않은 기준)에서의 위치를 제공합니다.

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>clientX Example</title>
</head>
<body>
    <h1>Move the Mouse Around</h1>
    <p>Mouse X Position: <span id="mouseX"></span></p>

    <script>
        const mouseXDisplay = document.getElementById("mouseX");

        window.addEventListener("mousemove", (event) => {
            mouseXDisplay.textContent = event.clientX;
        });
    </script>
</body>
</html>


clientX는 마우스 이벤트(MouseEvent) 객체의 속성으로, 브라우저 창의 왼쪽 상단 모서리를 기준으로 마우스 포인터의 X 좌표를 나타냅니다. 화면 전체를 기준으로 한 위치가 아니라, 현재 표시되고 있는 뷰포트(뷰포트 스크롤 위치를 고려하지 않은 기준)에서의 위치를 제공합니다.

주요 특징
뷰포트(스크롤 위치를 고려하지 않은 브라우저 창의 현재 보기 영역) 기준으로 마우스 포인터의 X 좌표를 반환합니다.
이벤트 객체에서 직접 접근할 수 있습니다.
사용 예제
다음은 마우스 움직임에 따라 마우스 포인터의 X 좌표를 표시하는 간단한 예제입니다.

HTML 코드
html
코드 복사
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>clientX Example</title>
</head>
<body>
    <h1>Move the Mouse Around</h1>
    <p>Mouse X Position: <span id="mouseX"></span></p>

    <script>
        const mouseXDisplay = document.getElementById("mouseX");

        window.addEventListener("mousemove", (event) => {
            mouseXDisplay.textContent = event.clientX;
        });
    </script>
</body>
</html>

clientX vs pageX vs screenX
clientX: 브라우저 창 기준의 X 좌표
pageX: 페이지 전체 기준의 X 좌표 (스크롤 포함)
screenX: 모니터 화면 기준의 X 좌표

````

## ClientY : 브라우저 기준
>clientY는 마우스 이벤트(MouseEvent) 객체의 속성으로, 브라우저 창의 위쪽 상단 모서리를 기준으로 마우스 포인터의 Y 좌표를 나타냅니다. 즉, 브라우저 뷰포트 내에서 마우스 포인터의 세로 위치를 반환합니다.

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Mouse Coordinates Example</title>
</head>
<body>
    <h1>Move the Mouse Around</h1>
    <p>clientY: <span id="clientY"></span></p>
    <p>pageY: <span id="pageY"></span></p>
    <p>screenY: <span id="screenY"></span></p>

    <script>
        const clientYDisplay = document.getElementById("clientY");
        const pageYDisplay = document.getElementById("pageY");
        const screenYDisplay = document.getElementById("screenY");

        window.addEventListener("mousemove", (event) => {
            clientYDisplay.textContent = event.clientY;
            pageYDisplay.textContent = event.pageY;
            screenYDisplay.textContent = event.screenY;
        });
    </script>
</body>
</html>

주요 특징
뷰포트 기준으로 마우스 포인터의 Y 좌표를 반환합니다.
이벤트 객체에서 직접 접근할 수 있습니다.
````

## offsetX : 요소를 기준
>offsetX는 마우스 이벤트(MouseEvent) 객체의 속성 중 하나로, 마우스 이벤트가 발생한 요소를 기준으로 수평 위치를 나타냅니다. 이 값은 이벤트가 발생한 요소 내에서 마우스 포인터의 수평 위치를 픽셀 단위로 반환합니다. 간단히 말해 이벤트가 발생한 요소의 좌측 경계선에서부터 마우스 포인터까지의 거리를 나타냅니다.

````html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>offsetX 예제</title>
  <style>
    .box {
      width: 300px;
      height: 300px;
      background-color: lightblue;
      border: 2px solid navy;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 18px;
      font-weight: bold;
    }
  </style>
</head>
<body>

  <div class="box" id="box">
    Click inside me!
  </div>

  <script>
    const box = document.getElementById('box');

    box.addEventListener('click', function (event) {
      const offsetX = event.offsetX;
      const offsetY = event.offsetY;
      box.textContent = `X: ${offsetX}, Y: ${offsetY}`;
    });
  </script>

</body>
</html>

관련된 속성
offsetY: 클릭된 요소 내에서 수직 위치를 반환합니다.
clientX / clientY: 뷰포트 기준 좌표.
pageX / pageY: 페이지 기준 좌표.

````

## offsetY : 요소를 기준
>offsetY는 offsetX와 마찬가지로 마우스 이벤트(MouseEvent) 객체의 속성 중 하나로, 마우스 이벤트가 발생한 요소를 기준으로 수직 위치를 나타냅니다. offsetY는 이벤트가 발생한 요소 내에서 마우스 포인터의 수직 위치를 픽셀 단위로 반환합니다. 다시 말해 이벤트가 발생한 요소의 상단 경계선에서부터 마우스 포인터까지의 거리를 나타냅니다.

````html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>offsetY 예제</title>
  <style>
    .box {
      width: 300px;
      height: 300px;
      background-color: lightgreen;
      border: 2px solid darkgreen;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 18px;
      font-weight: bold;
    }
  </style>
</head>
<body>

  <div class="box" id="box">
    Click inside me!
  </div>

  <script>
    const box = document.getElementById('box');

    box.addEventListener('click', function (event) {
      const offsetX = event.offsetX;
      const offsetY = event.offsetY;
      box.textContent = `X: ${offsetX}, Y: ${offsetY}`;
    });
  </script>

</body>
</html>

관련된 속성
offsetX: 클릭된 요소 내에서 수평 위치를 반환합니다.
clientX / clientY: 뷰포트 기준 좌표.
pageX / pageY: 페이지 기준 좌표.

````

## pageX : 페이지 기준
>pageX는 마우스 이벤트(MouseEvent) 객체의 속성 중 하나로, 문서(document)를 기준으로 마우스 이벤트가 발생한 위치의 수평 좌표를 나타냅니다. 이 값은 페이지의 좌측 경계에서부터 마우스 포인터까지의 수평 거리를 픽셀 단위로 반환합니다.

````html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>pageX 예제</title>
  <style>
    .box {
      width: 300px;
      height: 300px;
      margin-top: 800px; /* 페이지 스크롤을 확인하기 위한 여백 */
      background-color: lightcoral;
      border: 2px solid darkred;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 18px;
      font-weight: bold;
    }
  </style>
</head>
<body>

  <div class="box" id="box">
    Click inside me!
  </div>

  <script>
    const box = document.getElementById('box');

    box.addEventListener('click', function (event) {
      const pageX = event.pageX;
      const pageY = event.pageY;
      box.textContent = `PageX: ${pageX}, PageY: ${pageY}`;
    });
  </script>

</body>
</html>

````

## pageY : 페이지 기준
>pageY는 MouseEvent 객체의 속성 중 하나로, 문서(document)를 기준으로 마우스 이벤트가 발생한 위치의 수직 좌표를 나타냅니다. 이 값은 페이지의 상단 경계에서부터 마우스 포인터까지의 수직 거리를 픽셀 단위로 반환합니다.

````html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>pageY 예제</title>
  <style>
    .box {
      width: 300px;
      height: 300px;
      margin-top: 800px; /* 페이지 스크롤을 확인하기 위한 여백 */
      background-color: lightcoral;
      border: 2px solid darkred;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 18px;
      font-weight: bold;
    }
  </style>
</head>
<body>

  <div class="box" id="box">
    Click inside me!
  </div>

  <script>
    const box = document.getElementById('box');

    box.addEventListener('click', function (event) {
      const pageX = event.pageX;
      const pageY = event.pageY;
      box.textContent = `PageX: ${pageX}, PageY: ${pageY}`;
    });
  </script>

</body>
</html>

````

## screenX : 디바이스 기준
>screenX는 마우스 이벤트(MouseEvent) 객체의 속성 중 하나로, 마우스 이벤트가 발생한 위치의 수평 좌표를 전체 화면(screen)을 기준으로 나타냅니다. 즉, 화면의 좌측 경계에서부터 마우스 포인터까지의 수평 거리를 픽셀 단위로 반환합니다.

````html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>screenX 예제</title>
  <style>
    .box {
      width: 300px;
      height: 300px;
      background-color: lightblue;
      border: 2px solid navy;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 18px;
      font-weight: bold;
    }
  </style>
</head>
<body>

  <div class="box" id="box">
    Click inside me!
  </div>

  <script>
    const box = document.getElementById('box');

    box.addEventListener('click', function (event) {
      const screenX = event.screenX;
      const screenY = event.screenY;
      box.textContent = `ScreenX: ${screenX}, ScreenY: ${screenY}`;
    });
  </script>

</body>
</html>

````

## screenY : 디바이스 기준
>screenY는 마우스 이벤트(MouseEvent) 객체의 속성 중 하나로, 마우스 이벤트가 발생한 위치의 수직 좌표를 전체 화면(screen)을 기준으로 나타냅니다. 이 값은 화면의 상단 경계에서부터 마우스 포인터까지의 수직 거리를 픽셀 단위로 반환합니다

````html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>screenY 예제</title>
  <style>
    .box {
      width: 300px;
      height: 300px;
      background-color: lightgreen;
      border: 2px solid darkgreen;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 18px;
      font-weight: bold;
    }
  </style>
</head>
<body>

  <div class="box" id="box">
    Click inside me!
  </div>

  <script>
    const box = document.getElementById('box');

    box.addEventListener('click', function (event) {
      const screenX = event.screenX;
      const screenY = event.screenY;
      box.textContent = `ScreenX: ${screenX}, ScreenY: ${screenY}`;
    });
  </script>

</body>
</html>

````

#### 다음시간에 계속...
![image](https://github.com/nicejmp1/nicejmp1.github.io/assets/163364733/90a41f22-19d3-4d17-b649-016d5880fa98)
