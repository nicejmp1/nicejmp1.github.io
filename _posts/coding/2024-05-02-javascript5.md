---
layout: post
title: javascript 이벤트객체
date: 2024-05-02 16:20 +0900
description: javascript
image: ../assets/img/post/javascript02.png
category: javascript
tags: javascript 
published: true
sitemap: true
---

# Javascript 이벤트 객체

안녕하세요! 오늘은 javascript로 많이 활용하는 이벤트 객체에 대해 설명 해드리도록 하겠습니다.

## addEventListerner("click") : 클릭했을 때
>addEventListener("click")는 자바스크립트에서 DOM 요소에 특정 이벤트 리스너를 추가하는 데 사용되는 메서드입니다. 이 메서드를 사용하면 사용자가 HTML 요소를 클릭했을 때 실행될 함수를 지정할 수 있습니다.

````javascript
// 버튼 요소 가져오기
const button = document.getElementById("myButton");

// 클릭 이벤트 리스너 추가
button.addEventListener("click", function() {
    alert("Button clicked!");
});
````

화살표 함수 사용 <br>
더 최신의 화살표 함수를 사용한 버전은 다음과 같습니다.

````javascript
// 클릭 이벤트 리스너 추가 (화살표 함수 사용)
button.addEventListener("click", () => {
    alert("Button clicked!");
});

````

매개변수를 받는 이벤트 리스너 <br>
이벤트 객체는 이벤트 리스너의 첫 번째 인자로 전달됩니다. 이 객체를 통해 이벤트와 관련된 다양한 정보를 얻을 수 있습니다.

````javascript
button.addEventListener("click", (event) => {
    console.log("Event type: ", event.type);
    console.log("Mouse position: ", event.clientX, event.clientY);
});

````



## addEventListerner("dblclick") : 더블 클릭했을 떄
>addEventListener("dblclick")는 click 이벤트와 유사하지만, HTML 요소를 빠르게 두 번 연속 클릭할 때 발생하는 dblclick 이벤트를 처리하는 방법입니다.

````javascript
// 버튼 요소 가져오기
const button = document.getElementById("myButton");

// 더블 클릭 이벤트 리스너 추가
button.addEventListener("dblclick", function() {
    alert("Button double-clicked!");
});
````
<br>
화살표 함수 사용 <br>
화살표 함수를 사용한 버전은 다음과 같습니다.

````javascript
button.addEventListener("dblclick", () => {
    alert("Button double-clicked!");
});

````
<br>
매개변수를 받는 이벤트 리스너 <br>
이벤트 객체를 사용하여 이벤트와 관련된 추가 정보를 얻을 수 있습니다.

````javascript
button.addEventListener("dblclick", (event) => {
    console.log("Event type: ", event.type);
    console.log("Mouse position: ", event.clientX, event.clientY);
});

````

## addEventListerner("load") : 문서 로딩이 끝났을 떄
> addEventListener("load")는 페이지가 완전히 로드되었을 때 실행될 함수를 지정하는 이벤트 리스너입니다. 이 이벤트는 문서 및 그 안의 모든 하위 리소스(이미지, 스크립트, 스타일시트 등)가 완전히 로드된 후 발생합니다.

````javascript
window.addEventListener("load", function() {
    console.log("All resources finished loading!");
});

화살표 함수 사용
window.addEventListener("load", () => {
    console.log("All resources finished loading!");
});
````
<br>

DOMContentLoaded vs. Load <br>

DOMContentLoaded: DOM 요소가 모두 로드되었을 때 발생하지만, 스타일시트와 이미지 등의 리소스는 완전히 로드되지 않을 수 있습니다. <br>
load: 전체 문서 및 모든 외부 리소스가 완전히 로드되었을 때 발생합니다.

````javascript
document.addEventListener("DOMContentLoaded", () => {
    console.log("DOM fully loaded and parsed");
});

window.addEventListener("load", () => {
    console.log("All resources finished loading!");
});
````

## addEventListerner("DOMContentLoaded") : 문서 초기 HRML이 완전히 로고되고 파싱 됬을떄
>addEventListener("DOMContentLoaded")는 문서의 초기 HTML이 완전히 로드되고 파싱되었을 때 실행되는 이벤트 리스너입니다. 이 이벤트는 스타일시트나 이미지 등의 외부 리소스가 아직 로드되지 않았을 때 발생하지만, DOM을 조작하기 위한 요소들이 모두 로드되었으므로 DOM 조작이 가능해집니다.

````javascript
document.addEventListener("DOMContentLoaded", function() {
    console.log("Initial HTML document fully loaded and parsed!");
});

화살표 함수 사용
document.addEventListener("DOMContentLoaded", () => {
    console.log("Initial HTML document fully loaded and parsed!");
});

````
<br>
DOMContentLoaded vs. Load <br>
DOMContentLoaded: 문서의 HTML이 파싱되어 DOM 트리가 생성된 후 바로 발생하며, 스타일시트 및 이미지 등의 외부 리소스는 완전히 로드되지 않은 상태일 수 있습니다.
load: 문서의 모든 외부 리소스(스타일시트, 이미지 등)가 완전히 로드된 후 발생합니다

````javascript
document.addEventListener("DOMContentLoaded", () => {
    console.log("DOM fully loaded and parsed");
});

window.addEventListener("load", () => {
    console.log("All resources finished loading!");
});

````

## addEventListerner("error") : 문서가 정확히 로딩되지 않았을떄
>addEventListener("error")는 문서 로드 또는 스크립트 실행 중 오류가 발생했을 때 실행될 이벤트 핸들러를 지정하는 방법입니다. 이 이벤트 리스너를 통해 다양한 오류 상황을 처리하고, 오류 정보를 수집하거나 사용자에게 알림을 줄 수 있습니다.

````javascript
window.addEventListener("error", function(event) {
    console.error("JavaScript error: ", event.message);
    console.error("Source: ", event.filename, "Line: ", event.lineno, "Column: ", event.colno);
    console.error("Error object: ", event.error);
});

//화살표 함수 사용

window.addEventListener("error", (event) => {
    console.error("JavaScript error: ", event.message);
    console.error("Source: ", event.filename, "Line: ", event.lineno, "Column: ", event.colno);
    console.error("Error object: ", event.error);
});

````

## addEventListerner("scroll") : 스크롤 했을 떄
>addEventListener("scroll")는 사용자가 문서를 스크롤할 때 발생하는 이벤트를 처리하는 데 사용되는 메서드입니다. 이 이벤트는 윈도우 또는 특정 요소에서 스크롤이 발생할 때마다 실행됩니다.

````javascript
const scrollable = document.getElementById("scrollable");

scrollable.addEventListener("scroll", function() {
    console.log(`Scrollable Div Scroll Position: ${scrollable.scrollTop}`);
});

// 화살표 함수 사용
scrollable.addEventListener("scroll", () => {
    console.log(`Scrollable Div Scroll Position: ${scrollable.scrollTop}`);
});

// 디바운싱
function debounce(func, wait) {
    let timeout;
    return function(...args) {
        clearTimeout(timeout);
        timeout = setTimeout(() => func.apply(this, args), wait);
    };
}

const logScrollPosition = debounce(() => {
    console.log(`Window Scroll Position: ${window.scrollY}`);
}, 200);

window.addEventListener("scroll", logScrollPosition);

// 스로틀링
function throttle(func, limit) {
    let lastFunc;
    let lastRan;
    return function(...args) {
        const context = this;
        if (!lastRan) {
            func.apply(context, args);
            lastRan = Date.now();
        } else {
            clearTimeout(lastFunc);
            lastFunc = setTimeout(() => {
                if ((Date.now() - lastRan) >= limit) {
                    func.apply(context, args);
                    lastRan = Date.now();
                }
            }, limit - (Date.now() - lastRan));
        }
    };
}

const logScrollPositionThrottle = throttle(() => {
    console.log(`Window Scroll Position: ${window.scrollY}`);
}, 200);

window.addEventListener("scroll", logScrollPositionThrottle);

````

## addEventListerner("resize") : 브라우저 사이즈가 변경 됬을 떄
>addEventListener("resize")는 브라우저 윈도우의 크기가 조정될 때마다 발생하는 이벤트를 처리하는 메서드입니다. 이 이벤트는 사용자가 창 크기를 변경할 때마다 발생합니다.

````javascript
window.addEventListener("resize", function() {
    console.log(`Window size: ${window.innerWidth} x ${window.innerHeight}`);
});

//화살표 함수 사용
window.addEventListener("resize", () => {
    console.log(`Window size: ${window.innerWidth} x ${window.innerHeight}`);
});

// 디바운싱
function debounce(func, wait) {
    let timeout;
    return function(...args) {
        clearTimeout(timeout);
        timeout = setTimeout(() => func.apply(this, args), wait);
    };
}

const logResizeDebounce = debounce(() => {
    console.log(`Window size: ${window.innerWidth} x ${window.innerHeight}`);
}, 200);

window.addEventListener("resize", logResizeDebounce);

// 스로틀링
function throttle(func, limit) {
    let lastFunc;
    let lastRan;
    return function(...args) {
        const context = this;
        if (!lastRan) {
            func.apply(context, args);
            lastRan = Date.now();
        } else {
            clearTimeout(lastFunc);
            lastFunc = setTimeout(() => {
                if ((Date.now() - lastRan) >= limit) {
                    func.apply(context, args);
                    lastRan = Date.now();
                }
            }, limit - (Date.now() - lastRan));
        }
    };
}

const logResizeThrottle = throttle(() => {
    console.log(`Window size: ${window.innerWidth} x ${window.innerHeight}`);
}, 200);

window.addEventListener("resize", logResizeThrottle);

````

## addEventListerner("selectatart") : 텍스트 선택을 시작했을 때 
>addEventListener("selectstart")는 텍스트를 선택하려고 할 때 발생하는 이벤트를 처리하는 이벤트 리스너입니다. 사용자가 텍스트 선택을 시작하는 순간에 이 이벤트가 발생하며, 주로 사용자가 텍스트 선택을 방지하거나 선택 행동을 커스터마이징하려는 경우에 사용됩니다.

````javascript
element.addEventListener("selectstart", callback);

```` 
간단한 예제 

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Select Start and Prevent Example</title>
    <style>
        .selectable {
            padding: 10px;
            border: 1px solid black;
            margin-bottom: 10px;
        }

        .noSelect {
            padding: 10px;
            border: 1px solid black;
            user-select: none;
        }
    </style>
</head>
<body>
    <h1>Select Start Event Example</h1>

    <div class="selectable" id="selectable">
        Try selecting this text!
    </div>

    <div class="noSelect" id="noSelect">
        You cannot select this text!
    </div>

    <script>
        const selectable = document.getElementById("selectable");
        const noSelect = document.getElementById("noSelect");

        selectable.addEventListener("selectstart", (event) => {
            console.log("Text selection started in the selectable element!");
        });

        noSelect.addEventListener("selectstart", (event) => {
            event.preventDefault();
            console.log("Text selection prevented in the no-select element!");
        });
    </script>
</body>
</html>

````

#### 다음시간에 계속...
![image](https://github.com/nicejmp1/nicejmp1.github.io/assets/163364733/90a41f22-19d3-4d17-b649-016d5880fa98)
