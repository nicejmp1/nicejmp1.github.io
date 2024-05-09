---
layout: post
title: javascript 이벤트객체 (마우스 드래그)
date: 2024-05-05 10:20 +0900
description: javascript
image: ../assets/img/post/javascript02.png
category: javascript
tags: javascript 
published: true
sitemap: true
---

# javascript 마우스 드래그

안녕하세요! 오늘은 마우스 드래그 이벤트메서드에 대해 설명해드리겠습니다.

## addEventListener("drag") : 드래그 중인 경우
> "drag" 이벤트는 HTML5에서 제공되는 드래그 앤 드롭 기능의 일부로, 사용자가 요소를 드래그할 때 지속적으로 발생합니다. addEventListener를 사용하여 특정 요소에 drag 이벤트를 추가할 수 있습니다.

<이벤트 흐름> <br>
1. 드래그가 시작되면 dragstart 이벤트가 발생합니다. <br>
2. 드래그 중에 마우스가 이동할 때마다 drag 이벤트가 발생합니다. <br>
3. 드래그가 종료되면 dragend 이벤트가 발생합니다. <br>
<br>

<드래그 앤 드롭 관련 주요 이벤트> <br>
- dragstart: 드래그 시작 시 발생 <br>
- drag: 드래그하는 동안 지속적으로 발생 <br>
- dragend: 드래그 종료 시 발생 <br>
- dragenter: 드래그 대상 영역에 진입 시 발생 <br>
- dragover: 드래그 대상 영역 위에 있을 때 - 지속적으로 발생 <br>
- dragleave: 드래그 대상 영역을 벗어날 때 발생 <br>
- drop: 드래그 대상 영역에 드롭 시 발생 <br>

````css
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Drag Event 예제</title>
  <style>
    .draggable {
      width: 100px;
      height: 100px;
      background-color: lightcoral;
      border: 2px solid darkred;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 16px;
      font-weight: bold;
      cursor: grab;
    }

    .dropzone {
      width: 300px;
      height: 300px;
      background-color: lightblue;
      border: 2px solid navy;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 16px;
      margin-top: 20px;
    }
  </style>
</head>
<body>

  <div class="draggable" id="draggable" draggable="true">Drag me!</div>
  <div class="dropzone" id="dropzone">Drop zone</div>

  <script>
    const draggable = document.getElementById('draggable');
    const dropzone = document.getElementById('dropzone');

    draggable.addEventListener('dragstart', function (event) {
      event.dataTransfer.setData('text/plain', event.target.id);
      draggable.style.backgroundColor = 'darkred';
    });

    draggable.addEventListener('drag', function (event) {
      console.log(`Dragging... (${event.pageX}, ${event.pageY})`);
    });

    draggable.addEventListener('dragend', function () {
      draggable.style.backgroundColor = 'lightcoral';
    });

    dropzone.addEventListener('dragover', function (event) {
      event.preventDefault(); // 드래그 허용
    });

    dropzone.addEventListener('drop', function (event) {
      event.preventDefault();
      const draggableId = event.dataTransfer.getData('text/plain');
      const draggableElement = document.getElementById(draggableId);
      dropzone.appendChild(draggableElement);
      console.log('Dropped!');
    });
  </script>

</body>
</html>
````

## addEventListener("dragstart") : 드래그를 시작한 경우
>dragstart 이벤트는 HTML5 드래그 앤 드롭 기능의 일부로, 사용자가 요소를 드래그하기 시작할 때 발생합니다. 이를 통해 드래그 시작 시 특정 동작을 수행할 수 있습니다. 이벤트 핸들러 내에서는 드래그되는 데이터(dataTransfer)를 설정하거나 스타일을 변경하는 등의 작업을 수행할 수 있습니다.

````css
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>dragstart 이벤트 예제</title>
  <style>
    .draggable {
      width: 100px;
      height: 100px;
      background-color: lightcoral;
      border: 2px solid darkred;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 16px;
      font-weight: bold;
      cursor: grab;
      margin-right: 10px;
    }

    .dropzone {
      width: 300px;
      height: 300px;
      background-color: lightblue;
      border: 2px solid navy;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 16px;
    }

    .container {
      display: flex;
    }
  </style>
</head>
<body>

  <div class="container">
    <div class="draggable" id="draggable1" draggable="true">Drag me 1!</div>
    <div class="draggable" id="draggable2" draggable="true">Drag me 2!</div>
  </div>
  <div class="dropzone" id="dropzone">Drop zone</div>

  <script>
    const draggables = document.querySelectorAll('.draggable');
    const dropzone = document.getElementById('dropzone');

    draggables.forEach(draggable => {
      draggable.addEventListener('dragstart', function (event) {
        event.dataTransfer.setData('text/plain', event.target.id);
        event.target.style.backgroundColor = 'darkred';
        console.log(`Drag started for ${event.target.id}`);
      });

      draggable.addEventListener('dragend', function (event) {
        event.target.style.backgroundColor = 'lightcoral';
        console.log(`Drag ended for ${event.target.id}`);
      });
    });

    dropzone.addEventListener('dragover', function (event) {
      event.preventDefault(); // 드래그 허용
    });

    dropzone.addEventListener('drop', function (event) {
      event.preventDefault();
      const draggableId = event.dataTransfer.getData('text/plain');
      const draggableElement = document.getElementById(draggableId);
      dropzone.appendChild(draggableElement);
      console.log(`Dropped ${draggableId}`);
    });
  </script>

</body>
</html>

````

<이벤트 흐름> <br>
- dragstart: 드래그 시작 <br>
- drag: 드래그 진행 중 지속적으로 발생 <br>
- dragend: 드래그 종료 <br>
- dragenter: 드래그 대상 영역에 진입 <br>
- dragover: 드래그 대상 영역 위에 있을 때 - 지속적으로 발생 <br>
- dragleave: 드래그 대상 영역을 벗어날 때 발생 <br>
- drop: 드래그 대상 영역에 드롭될 때 발생 <br>

## addEventListener("dragend") : 드래그 끝난 경우
>dragend 이벤트는 HTML5 드래그 앤 드롭 기능의 일부로, 사용자가 요소를 드래그한 후 마우스 버튼을 놓을 때 발생합니다. 이를 통해 드래그 작업이 끝났을 때 특정 동작을 수행할 수 있습니다.

````html

<!-- <!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>dragend 이벤트 예제</title>
  <style>
    .draggable {
      width: 100px;
      height: 100px;
      background-color: lightcoral;
      border: 2px solid darkred;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 16px;
      font-weight: bold;
      cursor: grab;
      margin-right: 10px;
    }

    .dropzone {
      width: 300px;
      height: 300px;
      background-color: lightblue;
      border: 2px solid navy;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 16px;
    }

    .container {
      display: flex;
    }
  </style>
</head>
<body>

  <div class="container">
    <div class="draggable" id="draggable1" draggable="true">Drag me 1!</div>
    <div class="draggable" id="draggable2" draggable="true">Drag me 2!</div>
  </div>
  <div class="dropzone" id="dropzone">Drop zone</div>

  <script>
    const draggables = document.querySelectorAll('.draggable');
    const dropzone = document.getElementById('dropzone');

    draggables.forEach(draggable => {
      draggable.addEventListener('dragstart', function (event) {
        event.dataTransfer.setData('text/plain', event.target.id);
        event.target.style.backgroundColor = 'darkred';
        console.log(`Drag started for ${event.target.id}`);
      });

      draggable.addEventListener('dragend', function (event) {
        event.target.style.backgroundColor = 'lightcoral';
        console.log(`Drag ended for ${event.target.id}`);
      });
    });

    dropzone.addEventListener('dragover', function (event) {
      event.preventDefault(); // 드래그 허용
    });

    dropzone.addEventListener('drop', function (event) {
      event.preventDefault();
      const draggableId = event.dataTransfer.getData('text/plain');
      const draggableElement = document.getElementById(draggableId);
      dropzone.appendChild(draggableElement);
      console.log(`Dropped ${draggableId}`);
    });
  </script>

</body>
</html> -->

````

## addEventListener("dragenter") : 요소위치에 드래그 했을 떄
>dragenter 이벤트는 HTML5 드래그 앤 드롭 API의 일부로, 드래그된 요소가 드롭 대상 영역에 진입할 때 발생합니다. 이를 통해 드래그된 요소가 드롭 영역에 들어왔을 때의 동작을 정의할 수 있습니다.
<br>

````html
<!-- 
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>dragenter 이벤트 예제</title>
  <style>
    .draggable {
      width: 100px;
      height: 100px;
      background-color: lightcoral;
      border: 2px solid darkred;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 16px;
      font-weight: bold;
      cursor: grab;
      margin-right: 10px;
    }

    .dropzone {
      width: 300px;
      height: 300px;
      background-color: lightblue;
      border: 2px solid navy;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 16px;
    }

    .container {
      display: flex;
    }
  </style>
</head>
<body>

  <div class="container">
    <div class="draggable" id="draggable1" draggable="true">Drag me 1!</div>
    <div class="draggable" id="draggable2" draggable="true">Drag me 2!</div>
  </div>
  <div class="dropzone" id="dropzone">Drop zone</div>

  <script>
    const draggables = document.querySelectorAll('.draggable');
    const dropzone = document.getElementById('dropzone');

    draggables.forEach(draggable => {
      draggable.addEventListener('dragstart', function (event) {
        event.dataTransfer.setData('text/plain', event.target.id);
        event.target.style.backgroundColor = 'darkred';
        console.log(`Drag started for ${event.target.id}`);
      });

      draggable.addEventListener('dragend', function (event) {
        event.target.style.backgroundColor = 'lightcoral';
        console.log(`Drag ended for ${event.target.id}`);
      });
    });

    dropzone.addEventListener('dragenter', function (event) {
      event.preventDefault();
      dropzone.style.backgroundColor = 'darkblue';
      console.log('Drag entered drop zone');
    });

    dropzone.addEventListener('dragleave', function (event) {
      dropzone.style.backgroundColor = 'lightblue';
      console.log('Drag left drop zone');
    });

    dropzone.addEventListener('dragover', function (event) {
      event.preventDefault(); // 드래그 허용
    });

    dropzone.addEventListener('drop', function (event) {
      event.preventDefault();
      const draggableId = event.dataTransfer.getData('text/plain');
      const draggableElement = document.getElementById(draggableId);
      dropzone.appendChild(draggableElement);
      dropzone.style.backgroundColor = 'lightblue';
      console.log(`Dropped ${draggableId}`);
    });
  </script>

</body>
</html> -->

````

## addEventListener("dragover") : 요소 위치 위에 있을떄
> dragover 이벤트는 HTML5 드래그 앤 드롭 API의 일부로, 드래그된 요소가 드롭 영역 위에 있을 때 지속적으로 발생합니다. dragover 이벤트는 드롭을 허용하기 위해 event.preventDefault()를 반드시 호출해야 합니다.

````html
<!-- <html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>dragover 이벤트 예제</title>
  <style>
    .draggable {
      width: 100px;
      height: 100px;
      background-color: lightcoral;
      border: 2px solid darkred;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 16px;
      font-weight: bold;
      cursor: grab;
      margin-right: 10px;
    }

    .dropzone {
      width: 300px;
      height: 300px;
      background-color: lightblue;
      border: 2px solid navy;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 16px;
    }

    .container {
      display: flex;
    }
  </style>
</head>
<body>

  <div class="container">
    <div class="draggable" id="draggable1" draggable="true">Drag me 1!</div>
    <div class="draggable" id="draggable2" draggable="true">Drag me 2!</div>
  </div>
  <div class="dropzone" id="dropzone">Drop zone</div>

  <script>
    const draggables = document.querySelectorAll('.draggable');
    const dropzone = document.getElementById('dropzone');

    draggables.forEach(draggable => {
      draggable.addEventListener('dragstart', function (event) {
        event.dataTransfer.setData('text/plain', event.target.id);
        event.target.style.backgroundColor = 'darkred';
        console.log(`Drag started for ${event.target.id}`);
      });

      draggable.addEventListener('dragend', function (event) {
        event.target.style.backgroundColor = 'lightcoral';
        console.log(`Drag ended for ${event.target.id}`);
      });
    });

    dropzone.addEventListener('dragenter', function (event) {
      event.preventDefault();
      dropzone.style.backgroundColor = 'darkblue';
      console.log('Drag entered drop zone');
    });

    dropzone.addEventListener('dragleave', function (event) {
      dropzone.style.backgroundColor = 'lightblue';
      console.log('Drag left drop zone');
    });

    dropzone.addEventListener('dragover', function (event) {
      event.preventDefault(); // 드래그 허용
      dropzone.style.backgroundColor = 'darkblue';
      console.log('Drag over drop zone');
    });

    dropzone.addEventListener('drop', function (event) {
      event.preventDefault();
      const draggableId = event.dataTransfer.getData('text/plain');
      const draggableElement = document.getElementById(draggableId);
      dropzone.appendChild(draggableElement);
      dropzone.style.backgroundColor = 'lightblue';
      console.log(`Dropped ${draggableId}`);
    });
  </script>

</body>
</html> -->

````

## addEventListener("dragleave") : 요소의 위치 위에서 벗어 났을때
>addEventListener("dragleave")는 드래그 앤 드롭(Drag and Drop) 기능을 구현할 때 dragleave 이벤트를 처리하기 위해 사용됩니다. 이 이벤트는 사용자가 드래그 중인 요소가 특정 드롭 영역을 벗어날 때 발생합니다.

````html
<!-- <!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>dragleave 이벤트 예시</title>
    <style>
        .dropzone {
            width: 200px;
            height: 200px;
            border: 2px dashed #ccc;
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 20px;
            transition: background-color 0.3s;
        }

        .dropzone.hover {
            background-color: #e0e0e0;
        }
    </style>
</head>
<body>
    <h1>드래그 앤 드롭 예시</h1>
    <div class="dropzone" id="dropzone">
        드롭하세요
    </div>

    <script>
        // 드롭존 요소 가져오기
        const dropzone = document.getElementById('dropzone');

        // dragenter 이벤트: 드롭존에 들어올 때
        dropzone.addEventListener('dragenter', (event) => {
            event.preventDefault();
            dropzone.classList.add('hover');
        });

        // dragleave 이벤트: 드롭존에서 나갈 때
        dropzone.addEventListener('dragleave', (event) => {
            event.preventDefault();
            dropzone.classList.remove('hover');
            console.log('드래그 영역을 벗어났습니다.');
        });

        // dragover 이벤트: 드롭존 위에 있을 때
        dropzone.addEventListener('dragover', (event) => {
            event.preventDefault();
        });

        // drop 이벤트: 드롭이 이루어질 때
        dropzone.addEventListener('drop', (event) => {
            event.preventDefault();
            dropzone.classList.remove('hover');
            console.log('드롭이 이루어졌습니다.');
        });
    </script>
</body>
</html> -->

````

## addEventListener("drop") : 요소의 위치에 드롭했을 떄
>addEventListener("drop")는 드래그 앤 드롭(Drag and Drop) 기능을 구현할 때 drop 이벤트를 처리하기 위해 사용됩니다. drop 이벤트는 사용자가 드래그 중인 요소를 드롭 영역에 떨어뜨릴 때 발생합니다.

````html
<!-- <!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>drop 이벤트 예시</title>
    <style>
        .dropzone {
            width: 200px;
            height: 200px;
            border: 2px dashed #ccc;
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 20px;
            transition: background-color 0.3s;
        }

        .dropzone.hover {
            background-color: #e0e0e0;
        }
    </style>
</head>
<body>
    <h1>드래그 앤 드롭 예시</h1>
    <div class="dropzone" id="dropzone">
        드롭하세요
    </div>

    <script>
        // 드롭존 요소 가져오기
        const dropzone = document.getElementById('dropzone');

        // dragenter 이벤트: 드롭존에 들어올 때
        dropzone.addEventListener('dragenter', (event) => {
            event.preventDefault();
            dropzone.classList.add('hover');
        });

        // dragleave 이벤트: 드롭존에서 나갈 때
        dropzone.addEventListener('dragleave', (event) => {
            event.preventDefault();
            dropzone.classList.remove('hover');
        });

        // dragover 이벤트: 드롭존 위에 있을 때
        dropzone.addEventListener('dragover', (event) => {
            event.preventDefault();
        });

        // drop 이벤트: 드롭이 이루어질 때
        dropzone.addEventListener('drop', (event) => {
            event.preventDefault();
            dropzone.classList.remove('hover');
            
            // 드래그된 데이터를 가져오기
            const data = event.dataTransfer.getData('text/plain');
            console.log(`드롭된 데이터: ${data}`);
        });

        // 드래그 가능 요소 만들기
        document.addEventListener('DOMContentLoaded', () => {
            const draggableItem = document.createElement('div');
            draggableItem.textContent = '드래그할 요소';
            draggableItem.style.cursor = 'pointer';
            draggableItem.draggable = true;
            draggableItem.id = 'draggableItem';
            document.body.appendChild(draggableItem);

            // 드래그 시작 이벤트 처리
            draggableItem.addEventListener('dragstart', (event) => {
                event.dataTransfer.setData('text/plain', draggableItem.id);
            });
        });
    </script>
</body>
</html> -->

````
#### 다음시간에 계속...
![image](https://github.com/nicejmp1/nicejmp1.github.io/assets/163364733/90a41f22-19d3-4d17-b649-016d5880fa98)
