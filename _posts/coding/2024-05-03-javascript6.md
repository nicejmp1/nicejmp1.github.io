---
layout: post
title: javascript 이벤트객체 (마우스 포인터))
date: 2024-05-03 11:20 +0900
description: javascript
image: ../assets/img/post/javascript02.png
category: javascript
tags: javascript 
published: true
sitemap: true
---

# javascript 마우스 포인터

안녕하세요! 오늘은 javascript 마우스 포인터 이벤트 메서드에 대해 알아보도록 하겠습니다.
<br>

## addEventListerner("mousedown") : 마우스 버튼을 클릭했을 때
>addEventListener("mousedown")는 사용자가 마우스 버튼을 눌렀을 때 발생하는 이벤트를 처리하기 위한 메서드입니다. 이 이벤트는 마우스 버튼을 눌렀을 때 즉시 발생하며, 마우스 버튼을 떼는 순간 발생하는 mouseup 이벤트와 짝을 이룹니다.

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Mousedown Left Click Only</title>
</head>
<body>
    <h1 id="heading">Press Left Mouse Button Only</h1>

    <script>
        const heading = document.getElementById("heading");

        heading.addEventListener("mousedown", (event) => {
            if (event.button === 0) {
                console.log("Left mouse button pressed!");
            } else {
                console.log("Other mouse button pressed!");
            }
        });
    </script>
</body>
</html>

마우스 버튼 값
마우스 버튼 값은 다음과 같이 정의됩니다:

0: 왼쪽 버튼
1: 가운데 버튼
2: 오른쪽 버튼
3: 뒤로 가기 버튼(일부 마우스에 해당)
4: 앞으로 가기 버튼(일부 마우스에 해당)
````

## addEventListerner("mouseup") : 마우스 버튼을 떼는 경우
>addEventListener("mouseup")는 사용자가 마우스 버튼을 누른 후 떼는 순간에 발생하는 이벤트를 처리하기 위한 이벤트 리스너입니다. 이 이벤트는 mousedown 이벤트와 쌍을 이루며, 두 이벤트를 함께 사용하여 클릭 또는 드래그 동작을 처리할 수 있습니다.

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Mouseup Event Example</title>
</head>
<body>
    <h1 id="heading">Press and Release the Mouse Button</h1>

    <script>
        const heading = document.getElementById("heading");

        heading.addEventListener("mouseup", (event) => {
            console.log("Mouse button released!");
            console.log(`Button: ${event.button}`); // 0: Left, 1: Middle, 2: Right
        });
    </script>
</body>
</html>

마우스 버튼 값
마우스 버튼 값은 다음과 같이 정의됩니다:

0: 왼쪽 버튼
1: 가운데 버튼
2: 오른쪽 버튼
3: 뒤로 가기 버튼(일부 마우스에 해당)
4: 앞으로 가기 버튼(일부 마우스에 해당)
예제: 왼쪽 버튼 클릭에만 반응
다음 예제는 왼쪽 마우스 버튼이 떼어질 때만 반응하도록 합니다.

````
<br>
예제1. 특정 요소에서 마우스 드래그 구현

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Draggable Element Example</title>
    <style>
        #draggable {
            width: 100px;
            height: 100px;
            background-color: lightblue;
            position: absolute;
            cursor: grab;
        }
    </style>
</head>
<body>
    <h1>Drag the Box</h1>
    <div id="draggable"></div>

    <script>
        const draggable = document.getElementById("draggable");
        let isDragging = false;
        let offsetX, offsetY;

        draggable.addEventListener("mousedown", (event) => {
            isDragging = true;
            offsetX = event.clientX - draggable.getBoundingClientRect().left;
            offsetY = event.clientY - draggable.getBoundingClientRect().top;
            draggable.style.cursor = "grabbing";
        });

        document.addEventListener("mousemove", (event) => {
            if (isDragging) {
                draggable.style.left = `${event.clientX - offsetX}px`;
                draggable.style.top = `${event.clientY - offsetY}px`;
            }
        });

        document.addEventListener("mouseup", () => {
            isDragging = false;
            draggable.style.cursor = "grab";
        });
    </script>
</body>
</html>

````
<br>
예제2 : 클릭 동작 구현

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Click Example</title>
    <style>
        #clickable {
            width: 200px;
            height: 100px;
            background-color: lightgreen;
            border: 1px solid black;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <h1>Click the Box</h1>
    <div id="clickable">Click Me!</div>

    <script>
        const clickable = document.getElementById("clickable");
        let isMouseDown = false;

        clickable.addEventListener("mousedown", (event) => {
            isMouseDown = true;
            console.log("Mouse button pressed down");
        });

        clickable.addEventListener("mouseup", (event) => {
            if (isMouseDown && event.button === 0) {
                console.log("Mouse button released and clicked");
                alert("Box clicked!");
            }
            isMouseDown = false;
        });
    </script>
</body>
</html>

````

## addEventListerner("mousemove) : 마우스를 움직이는 경우
>addEventListener("mousemove")는 사용자가 마우스를 움직일 때 발생하는 이벤트를 처리하기 위한 메서드입니다. 이 이벤트는 사용자가 마우스를 움직일 때마다 지속적으로 발생합니다.

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Mousemove Event Example</title>
</head>
<body>
    <h1>Move the Mouse Around</h1>

    <script>
        window.addEventListener("mousemove", (event) => {
            console.log(`Mouse position: (${event.clientX}, ${event.clientY})`);
        });
    </script>
</body>
</html>

마우스 좌표 값
mousemove 이벤트 객체의 속성을 사용하여 마우스 위치를 얻을 수 있습니다.

clientX: 브라우저 창을 기준으로 한 마우스의 x 좌표
clientY: 브라우저 창을 기준으로 한 마우스의 y 좌표
screenX: 모니터 화면을 기준으로 한 마우스의 x 좌표
screenY: 모니터 화면을 기준으로 한 마우스의 y 좌표
````
<br>
예제1 : 특정 요소의 내부 좌표

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Mousemove Inside Element Example</title>
    <style>
        #container {
            width: 400px;
            height: 200px;
            background-color: lightblue;
            position: relative;
            border: 1px solid black;
            margin-top: 50px;
        }
    </style>
</head>
<body>
    <h1>Move the Mouse Inside the Box</h1>
    <div id="container"></div>

    <script>
        const container = document.getElementById("container");

        container.addEventListener("mousemove", (event) => {
            const rect = container.getBoundingClientRect();
            const x = event.clientX - rect.left;
            const y = event.clientY - rect.top;
            console.log(`Mouse inside container: (${x}, ${y})`);
        });
    </script>
</body>
</html>

````
<br>
예제2 : 마우스 트레일 효과

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Mouse Trail Effect</title>
    <style>
        .trail {
            width: 10px;
            height: 10px;
            background-color: red;
            border-radius: 50%;
            position: absolute;
            pointer-events: none;
            opacity: 0.8;
            transition: transform 0.1s;
        }
    </style>
</head>
<body>
    <h1>Mouse Trail Effect</h1>

    <div class="trail" id="trail1"></div>
    <div class="trail" id="trail2"></div>
    <div class="trail" id="trail3"></div>

    <script>
        const trails = [document.getElementById("trail1"), document.getElementById("trail2"), document.getElementById("trail3")];
        let index = 0;

        window.addEventListener("mousemove", (event) => {
            const trail = trails[index];
            trail.style.transform = `translate(${event.clientX}px, ${event.clientY}px)`;
            index = (index + 1) % trails.length;
        });
    </script>
</body>
</html>

````
<br>
예제3 : 드래그 앤 드롭 구현

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Drag and Drop Example</title>
    <style>
        #draggable {
            width: 100px;
            height: 100px;
            background-color: lightgreen;
            position: absolute;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <h1>Drag the Box</h1>
    <div id="draggable"></div>

    <script>
        const draggable = document.getElementById("draggable");
        let isDragging = false;
        let offsetX, offsetY;

        draggable.addEventListener("mousedown", (event) => {
            isDragging = true;
            offsetX = event.clientX - draggable.getBoundingClientRect().left;
            offsetY = event.clientY - draggable.getBoundingClientRect().top;
            draggable.style.cursor = "grabbing";
        });

        window.addEventListener("mousemove", (event) => {
            if (isDragging) {
                draggable.style.left = `${event.clientX - offsetX}px`;
                draggable.style.top = `${event.clientY - offsetY}px`;
            }
        });

        window.addEventListener("mouseup", () => {
            isDragging = false;
            draggable.style.cursor = "pointer";
        });
    </script>
</body>
</html>
````

## addEventListerner("mouseenter") : 요소위에 포인터 요소 위치가 있을 때
>addEventListener("mouseenter")는 사용자가 마우스 커서를 특정 요소 위로 이동했을 때 발생하는 이벤트를 처리하기 위한 이벤트 리스너입니다. 이 이벤트는 mouseover 이벤트와 유사하지만, 자식 요소로 이벤트가 전파되지 않는다는 차이점이 있습니다. 즉, mouseenter 이벤트는 이벤트 버블링을 발생시키지 않습니다.

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Mouseenter Event Example</title>
</head>
<body>
    <h1 id="heading">Hover over this text!</h1>

    <script>
        const heading = document.getElementById("heading");

        heading.addEventListener("mouseenter", () => {
            console.log("Mouse entered the heading!");
        });
    </script>
</body>
</html>

````
<br>
비교 예제
<br>
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Mouseenter vs Mouseover Example</title>
    <style>
        .container {
            width: 200px;
            height: 200px;
            background-color: lightblue;
            margin-bottom: 20px;
            border: 1px solid black;
            position: relative;
        }

        .inner {
            width: 100px;
            height: 100px;
            background-color: lightgreen;
            position: absolute;
            top: 50px;
            left: 50px;
        }
    </style>
</head>
<body>
    <h1>Mouseenter vs Mouseover</h1>
    <div class="container" id="container">
        Outer
        <div class="inner" id="inner">Inner</div>
    </div>

    <script>
        const container = document.getElementById("container");
        const inner = document.getElementById("inner");

        container.addEventListener("mouseenter", () => {
            console.log("Mouse entered the outer container!");
        });

        container.addEventListener("mouseover", () => {
            console.log("Mouse over the outer container!");
        });

        inner.addEventListener("mouseenter", () => {
            console.log("Mouse entered the inner box!");
        });

        inner.addEventListener("mouseover", () => {
            console.log("Mouse over the inner box!");
        });
    </script>
</body>
</html>
````
<br>
예제 : 마우스 오버 효과

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Mouse Enter Effect</title>
    <style>
        .hoverable {
            width: 200px;
            height: 100px;
            background-color: lightgreen;
            margin: 10px;
            border: 1px solid black;
            transition: background-color 0.3s, transform 0.3s;
        }

        .hoverable:hover {
            background-color: yellow;
        }

        .hover-effect {
            background-color: yellow;
            transform: scale(1.1);
        }
    </style>
</head>
<body>
    <h1>Mouse Enter Effect</h1>
    <div class="hoverable" id="box1">Hover over me</div>
    <div class="hoverable" id="box2">Hover over me too</div>

    <script>
        const box1 = document.getElementById("box1");
        const box2 = document.getElementById("box2");

        box1.addEventListener("mouseenter", () => {
            box1.classList.add("hover-effect");
        });

        box1.addEventListener("mouseleave", () => {
            box1.classList.remove("hover-effect");
        });

        box2.addEventListener("mouseenter", () => {
            box2.classList.add("hover-effect");
        });

        box2.addEventListener("mouseleave", () => {
            box2.classList.remove("hover-effect");
        });
    </script>
</body>
</html>

````
예제 : 마우스 커서 진입 시 툴팁 표시

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Tooltip Example</title>
    <style>
        #tooltip {
            display: none;
            position: absolute;
            background-color: black;
            color: white;
            padding: 5px;
            border-radius: 5px;
            font-size: 12px;
            z-index: 1000;
        }

        .hoverable {
            display: inline-block;
            padding: 10px;
            margin: 10px;
            background-color: lightblue;
            border: 1px solid black;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <h1>Tooltip Example</h1>
    <div class="hoverable" id="hoverable1" data-tooltip="This is a tooltip 1!">Hover over me 1</div>
    <div class="hoverable" id="hoverable2" data-tooltip="This is a tooltip 2!">Hover over me 2</div>

    <div id="tooltip"></div>

    <script>
        const tooltip = document.getElementById("tooltip");

        function showTooltip(event) {
            const tooltipText = event.target.getAttribute("data-tooltip");
            if (tooltipText) {
                tooltip.textContent = tooltipText;
                tooltip.style.display = "block";
                tooltip.style.left = `${event.pageX + 10}px`;
                tooltip.style.top = `${event.pageY + 10}px`;
            }
        }

        function hideTooltip() {
            tooltip.style.display = "none";
        }

        const hoverableElements = document.querySelectorAll(".hoverable");

        hoverableElements.forEach((element) => {
            element.addEventListener("mouseenter", showTooltip);
            element.addEventListener("mousemove", showTooltip);
            element.addEventListener("mouseleave", hideTooltip);
        });
    </script>
</body>
</html>

````

## addEventListerner("mouseleave") : 요소 위에 포인터 요소 위치가 벗어났을때
>addEventListener("mouseleave")는 사용자가 마우스 커서를 특정 요소에서 벗어날 때 발생하는 이벤트를 처리하기 위한 이벤트 리스너입니다. 이 이벤트는 mouseout 이벤트와 유사하지만, mouseleave 이벤트는 이벤트 버블링을 발생시키지 않습니다.

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Mouseleave Event Example</title>
</head>
<body>
    <h1 id="heading">Hover over this text and leave!</h1>

    <script>
        const heading = document.getElementById("heading");

        heading.addEventListener("mouseleave", () => {
            console.log("Mouse left the heading!");
        });
    </script>
</body>
</html>

````

## addEventListerner("mouseover") : 요소위에 포인터 요소 위치가 있을 때
>addEventListener("mouseover")는 사용자가 마우스 커서를 특정 요소 위로 가져갈 때 발생하는 이벤트를 처리하기 위한 이벤트 리스너입니다. 이 이벤트는 mouseenter 이벤트와 유사하지만, 자식 요소로 이벤트가 전파된다는 차이점이 있습니다. 즉, 마우스가 요소 위에 있거나 요소의 자식 위에 있을 때마다 mouseover 이벤트가 발생합니다.

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Mouseover Event Example</title>
</head>
<body>
    <h1 id="heading">Hover over this text!</h1>

    <script>
        const heading = document.getElementById("heading");

        heading.addEventListener("mouseover", () => {
            console.log("Mouse over the heading!");
        });
    </script>
</body>
</html>

````

## addEventListerner("mouseout") : 요소 위에 포인터 요소 위치가 벗어 났을 때
>addEventListener("mouseout")는 사용자가 마우스 커서를 특정 요소에서 벗어날 때 발생하는 이벤트를 처리하기 위한 이벤트 리스너입니다. 이 이벤트는 mouseleave 이벤트와 유사하지만, mouseout 이벤트는 자식 요소로 이벤트가 전파된다는 차이점이 있습니다.

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Mouseout Event Example</title>
</head>
<body>
    <h1 id="heading">Hover over this text and leave!</h1>

    <script>
        const heading = document.getElementById("heading");

        heading.addEventListener("mouseout", () => {
            console.log("Mouse left the heading!");
        });
    </script>
</body>
</html>

````

#### 다음시간에 계속...
![image](https://github.com/nicejmp1/nicejmp1.github.io/assets/163364733/90a41f22-19d3-4d17-b649-016d5880fa98)
