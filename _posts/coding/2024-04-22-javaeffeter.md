---
layout: post
title: 자바스크립트 기능 살펴보기
date: 2024-04-22 16:00 +0900
description: 자바스크립트 기능으로 마우스 스크롤 효과 만들기
image: ../assets/img/PARALAX.jpg
category: 이펙터, 스크롤효과, 자바스크립트 
tags: 이펙터  
published: true
sitemap: true
---

# PARALLAX scroll 효과 파해치기 

안녕하세요 오늘 배울 자바스크립트 기능 중 GSAP를 이용한 마우스 스크롤 효과 만들기 입니다. <br>

먼저 기본적인 레이아웃 부터 짜고 시작하도록 하겠습니다.

````html
<body>
    <div id="wrap">
        <header id="header">
            <div class="header__inner">
                <h1><a href="index.html">Parallax Effect</a><em> 01</em></h1>
                <p>GSAP scrollTrigger - 애니메이션 기본 효과</p>

                <div class="link">
                    <ul>
                        <li><a href="mouse01.html">mouse</a></li>
                    </ul>
                </div>
            </div>
        </header>
        <!-- //header -->

        <main id="main">
            <div class="main__inner">
                <section id="section01">
                    <span class="num">01</span>
                    <div class="img"></div>
                </section>
                <!-- //section01-->
                <section id="section02">
                    <span class="num">02</span>
                    <div class="img"></div>

                </section>
                <!-- //section02-->
                <section id="section03">
                    <span class="num">03</span>
                    <div class="img"></div>

                </section>
                <!-- //section03 -->
                <section id="section04">
                    <span class="num">04</span>
                    <div class="img"></div>

                </section>
                <!-- //section04-->
                <section id="section05">
                    <span class="num">05</span>
                    <div class="img"></div>

                </section>
                <!-- //section05-->
                <section id="section06">
                    <span class="num">06</span>
                    <div class="img"></div>

                </section>
                <!-- //section06-->
                <section id="section07">
                    <span class="num">07</span>
                    <div class="img"></div>

                </section>
                <!-- //section07-->
                <section id="section08">
                    <span class="num">08</span>
                    <div class="img"></div>

                </section>
                <!-- //section08-->
                <section id="section09">
                    <span class="num">09</span>
                    <div class="img"></div>

                </section>
                <!-- //section09 -->
            </div>

        </main>
````

간단하게 스크롤을 내릴때마다 나타나는 효과를 배울것이기 때문에 간단하게 구조를 짜고 시작하도록하겠습니다.<br>

먼저 스크립트를 짜기전 https://gsap.com/ GSAP 사이트에서 스크립트를 가져오도록 하겠습니다.<br>

Get GSAP 클릭 후 <br>
![alt text](image-1.png)

CDN -> ScrollTrigger 클릭 후 나오는 스크립트를 추가해야 GSAP 기능을 이용 할 수 있습니다. <br>

먼저 첫번째 기능은 to, from에 대해 알아보도록 하겠습니다.

### To, From

````javascript
 // 01   to, from
        gsap.to("#section01 .img", {
            duration: 2,
            x: 500,
            rotation: 360,
            borderRadius: 100
        });
````

구체적으로 코드는 다음과 같은 동작을 합니다 <br>

<b> 선택자</b>: #section01 .img는 ID가 section01인 요소 내부에 있는 클래스명 img를 가진 모든 요소를 대상으로 합니다.<br>

<b> duration </b>:  2는 애니메이션의 지속 시간을 2초로 설정합니다. <br>
x: 500은 선택한 요소를 수평으로 500픽셀 만큼 이동시킵니다.<br>
<b> rotation</b>: 360은 요소를 360도 회전합니다. 이것은 한 바퀴 도는 효과를 만듭니다. <br>
<b> borderRadius</b>: 100은 요소의 모든 모서리의 경계 반경을 100픽셀로 설정하여 더 둥근 모양을 만듭니다. <br>

이 코드를 통해 지정된 요소는 오른쪽으로 500픽셀 이동하면서 한 바퀴 돌고, 모서리가 둥글게 변하는 애니메이션을 2초 동안 수행합니다.<br>

### Trigger 효과

>GSAP의 scrollTrigger 효과는 웹페이지에서 스크롤 위치에 따라 애니메이션을 시작하거나 멈추게 할 수 있게 해주는 기능입니다. 이를 통해 사용자가 특정 요소에 도달했을 때 동적인 시각 효과를 실행시킬 수 있어 인터랙티브한 웹 경험을 제공합니다

````javascript
   // 02 : trigger 
        gsap.to("#section02 .img", {
            duration: 3,
            x: 500,
            rotation: 360,
            borderRadius: 100,

            // 화면에 보이면 바로 움직입니다.
            scrollTrigger: {
                trigger: "#section02 .img"
            }
        });
````

코드의 구체적인 설명은 다음과 같습니다<br>

scrollTrigger: 이 속성을 통해 애니메이션이 트리거되는 조건을 설정합니다. <br>

trigger: #section02 .img로 설정되어 있으며, 이는 애니메이션이 시작되는 트리거 요소가 동일한 #section02 .img임을 의미합니다. 즉, 해당 요소가 화면에 보이는 순간 애니메이션 시작됩니다. <br>

이 설정을 통해, 웹 페이지를 스크롤하여 #section02 .img 요소가 화면에 보일 때, 해당 요소는 오른쪽으로 500픽셀 이동하면서 한 바퀴 돌고 모서리가 둥글게 변하는 3초 동안의 애니메이션을 실행합니다. <br>

### ToggleActions : 상황별 애니메이션 처리 
>GSAP의 `scrollTrigger`에서 `toggleActions` 옵션은 스크롤 위치에 따라 애니메이션의 네 가지 가능한 행동(시작, 끝, 뒤로 시작, 뒤로 끝)을 정의합니다. 이를 통해 요소가 화면에 들어오거나 나갈 때 다른 애니메이션 효과를 적용할 수 있어 풍부한 사용자 경험을 제공합니다.

````javascript
   gsap.to("#section03 .img", {
            duration: 4,
            x: 500,
            rotation: 360,
            borderRadius: 100,

            // onEnter, onLeave, onEnterBack, onLeaveBack
            // keywords for each action: "play", "pause", "resume", "reset", "restart", "complete", "reverse", and "none"
            scrollTrigger: {
                trigger: "#section03 .img",
                toggleActions: "play none reverse none"
            }
        })
````

scrollTrigger와 toggleActions를 통해 스크롤 위치에 따른 애니메이션 동작을 조정합니다. 각 구성 요소에 대한 설명은 다음과 같습니다<br>

trigger: #section03 .img는 애니메이션의 트리거 요소로 지정되어 있습니다. <br>

toggleActions: play none reverse none은 스크롤 이벤트에 따라 다른 행동을 지정합니다. <br>

##### toggleActions 옵션의 각 키워드
play: 요소가 화면에 처음 등장할 때 애니메이션을 실행합니다. <br>
none: 요소가 화면에서 사라질 때 아무런 액션을 취하지 않습니다.<br>
reverse: 요소가 화면으로 다시 들어올 때 (뒤로 스크롤할 때)  애니메이션을 역방향으로 실행합니다. <br>
none: 요소가 화면에서 완전히 벗어났을 때 (뒤로 스크롤한 후) 아무런 액션을 취하지 않습니다. <br>


### Start, End : 애니메이션 시작, 끝 조절

>GSAP의 scrollTrigger에서 start와 end 속성은 애니메이션의 시작과 종료가 발생하는 스크롤 위치를 지정합니다. 이를 사용하면 페이지의 특정 지점에서 애니메이션을 정확하게 시작하거나 종료시킬 수 있어, 애니메이션의 흐름을 세밀하게 제어할 수 있습니다.

````javascript
    // 04 : start, end : 애니메이션 시작, 끝 조절
        gsap.to("#section04 .img", {
            duration: 5,
            x: 500,
            rotation: 360,
            borderRadius: 100,

            scrollTrigger: {
                trigger: "#section04 .img",
                toggleActions: "play reverse none none",
                markers: false,
                start: "top 50%",
                end: "bottom 20%"
            }
        })
````

각 코드의 해석은 다음고 같습니다. <br>

trigger: #section04 .img로 설정되어 있으며, 이는 애니메이션의 트리거 요소를 지정합니다. <br>

toggleActions: play reverse none none은 스크롤 이벤트에 따라 다른 행동을 지정합니다. 요소가 화면에 들어오면 play, 뒤로 스크롤할 때는 reverse, 나머지 상황에서는 아무 행동도 취하지 않습니다.<br>

markers: false는 스크롤 트리거 지점을 시각적으로 표시하지 않음을 의미합니다. <br>

start: top 50%는 요소의 상단이 뷰포트의 중간 (50%)에 도달했을 때 애니메이션이 시작됨을 의미합니다. <br>

end: bottom 20%는 요소의 하단이 뷰포트 하단으로부터 20% 위치에 도달했을 때 애니메이션이 종료됨을 의미합니다.<br>

이 설정은 사용자가 페이지를 스크롤하면서 요소가 특정 위치에 도달할 때 애니메이션이 실행되고, 또 다시 해당 위치를 벗어나면 애니메이션이 역방향으로 실행되도록 합니다.

### Scrub 효과
>GSAP의 `scrollTrigger` 속성 중 `scrub` 옵션은 스크롤 동작에 따라 애니메이션의 진행 상태를 연결합니다. 만약 `scrub`을 설정하면, 사용자가 스크롤하는 동안 애니메이션은 스크롤 위치에 따라 부드럽게 진행되거나 역행합니다. 이는 스크롤을 할 때마다 애니메이션이 사용자의 스크롤 속도와 방향에 맞춰 실시간으로 조절되어, 매우 동적이고 상호작용적인 효과를 만들어냅니다.

````javascript
   gsap.to("#section05 .img", {
            duration: 5,
            x: 500,
            rotation: 360,
            borderRadius: 100,

            scrollTrigger: {
                trigger: "#section05 .img",
                markers: false,
                start: "top 50%",
                end: "bottom 10%",
                scrub: true // 0.5 | true | number
            }
        })
````

trigger: #section05 .img는 애니메이션의 트리거 요소로 지정됩니다.
markers: false는 스크롤 트리거 지점을 시각적으로 표시하지 않음을 의미합니다. <br>

start: top 50%는 요소의 상단이 뷰포트의 중간 (50%)에 도달했을 때 애니메이션이 시작됨을 의미합니다.<br>

end: bottom 10%는 요소의 하단이 뷰포트 하단으로부터 10% 위치에 도달했을 때 애니메이션이 종료됨을 의미합니다. <bt>

scrub: true로 설정되어 있으며, 이는 사용자가 스크롤하는 동안 애니메이션 진행이 스크롤과 연동되어 실시간으로 조절됨을 의미합니다. 이 옵션은 스크롤을 멈추면 애니메이션도 해당 위치에서 멈춥니다. <br>

이 설정으로 인해, #section05 .img 요소는 사용자가 스크롤하는 동안 실시간으로 오른쪽으로 이동하고 회전하며, 모서리가 둥글어지는 애니메이션을 보여줍니다. 사용자의 스크롤에 따라 애니메이션의 속도와 방향이 변화하여, 매우 상호작용적인 효과를 제공합니다.

### pin 효과

>GSAP의 scrollTrigger 속성 중 pin 옵션은 선택된 요소를 스크롤 시 일정 구간 동안 화면에 고정하는 효과를 제공합니다. 이를 사용하면 특정 요소가 사용자가 지정한 시작점(start)과 종료점(end) 사이에서 스크롤하는 동안 고정되어, 다른 콘텐츠는 그 뒤로 스크롤되면서 지나갑니다. 이 기능은 긴 페이지에서 중요한 정보를 강조하거나 독창적인 애니메이션 시퀀스를 생성하는 데 유용합니다.

````javascript
     gsap.to("#section06 .img", {
            duration: 2,
            x: 500,
            rotation: 360,
            borderRadius: 100,

            scrollTrigger: {
                trigger: "#section06 .img",
                start: "top 50%",
                end: "bottom 200px",
                scrub: true,
                pin: true,
                markers: false
            }
        });
````

trigger: #section06 .img는 애니메이션의 트리거 요소로 지정됩니다. <br>

start: top 50%는 요소의 상단이 뷰포트의 중간 (50%)에 도달했을 때 애니메이션이 시작됨을 의미합니다. <br>

end: bottom 200px는 요소의 하단이 뷰포트 하단에서 200픽셀 위에 위치할 때 애니메이션이 종료됨을 의미합니다. <br>

scrub: true로 설정되어 있으며, 이는 사용자가 스크롤하는 동안 애니메이션 진행이 스크롤과 연동되어 실시간으로 조절됨을 의미합니다. <br>

pin: true는 이 요소를 스크롤 동안 특정 구간에서 화면에 고정시키는 옵션입니다. <br>

markers: false는 스크롤 트리거 지점을 시각적으로 표시하지 않음을 의미합니다. <br>

이 설정으로 인해, #section06 .img 요소는 사용자가 페이지를 스크롤할 때 뷰포트 중간에 도달하면 고정되고, 동시에 오른쪽으로 이동하며 회전하고 모서리가 둥글어지는 애니메이션을 수행합니다. 이 요소는 스크롤을 계속하면서도 화면에 고정되어 있는 동안 애니메이션이 계속 조정됩니다.

### toggleClass
> toggleClass 옵션은 className과 targets 두 부분으로 구성됩니다. className은 추가하거나 제거할 CSS 클래스의 이름이며, targets은 이 클래스 변경을 적용할 요소를 지정합니다.
클래스는 scrollTrigger가 활성화되는 특정 스크롤 포인트에서 추가되고, 비활성화될 때 제거될 수 있습니다. 이를 통해 스크롤에 따라 요소의 시각적 표현을 변경하는 다양한 효과를 적용할 수 있습니다.

````javascript
        gsap.to("#section07 .img", {
            duration: 2,
            x: 500,
            rotation: 360,
            borderRadius: 100,

            scrollTrigger: {
                trigger: "#section07 .img",
                start: "top center",
                end: "bottom 200px",
                scrub: true,
                toggleClass: "active",
                markers: false,
                id: "box7"
            }
        });
````

trigger: #section07 .img는 애니메이션의 트리거 요소로 지정됩니다.
start: top center는 요소의 상단이 뷰포트 중앙에 도달했을 때 애니메이션이 시작됨을 의미합니다.<br>

end: bottom 200px는 요소의 하단이 뷰포트 하단에서 200픽셀 위에 위치할 때 애니메이션이 종료됨을 의미합니다. <br>

scrub: true로 설정되어 있으며, 이는 사용자가 스크롤하는 동안 애니메이션 진행이 스크롤과 연동되어 실시간으로 조절됨을 의미합니다. <br>

toggleClass: active로 설정되어 있으며, 이는 요소가 스크롤 트리거 조건을 만족할 때 'active' 클래스를 추가하고, 조건을 벗어날 때 제거합니다. 이 클래스를 통해 요소의 스타일 변화를 적용할 수 있습니다. <br>

markers: false는 스크롤 트리거 지점을 시각적으로 표시하지 않음을 의미합니다. <br>

id: box7는 스크롤 트리거의 식별자로, 디버깅이나 특정 스크롤 트리거를 찾을 때 유용하게 사용할 수 있습니다. <br>

이 설정을 통해, #section07 .img 요소는 사용자가 스크롤할 때 지정된 위치에서 애니메이션을 시작하고, 특정 구간에서는 스타일 변경이 일어나며, 스크롤 위치에 따라 실시간으로 애니메이션 속도와 방향이 조절됩니다.

### callback 
>scrollTrigger에서 콜백 함수는 스크롤 이벤트가 발생할 때 추가적인 자바스크립트 함수를 실행할 수 있도록 해주는 기능입니다. 이를 통해 특정 스크롤 위치에서 필요한 추가 작업을 할 수 있으며, 스크롤 트리거의 상태에 따라 다양한 행동을 취할 수 있습니다.

#### 주요 콜백 함수
>onEnter: 요소가 뷰포트로 진입할 때 실행됩니다.
onLeave: 요소가 뷰포트를 벗어날 때 실행됩니다.
onEnterBack: 요소가 뷰포트로 다시 진입할 때 (반대 방향에서 스크롤 할 때) 실행됩니다.
onLeaveBack: 요소가 뷰포트를 반대 방향으로 벗어날 때 실행됩니다.
onUpdate: 스크롤 위치가 변경될 때마다 실행됩니다.

````javascript
  gsap.to("#section08 .img", {
            duration: 2,
            x: 500,
            rotation: 360,
            borderRadius: 100,

            scrollTrigger: {
                trigger: "#section08 .img",
                start: "top center",
                end: "bottom 200px",
                scrub: true,
                markers: true,
                // onEnter: () => { console.log("onEnter") },
                // onLeave: () => { console.log("onLeave") },
                // onEnterBack: () => { console.log("onEnterBack") },
                // onLeaveBack: () => { console.log("onLeaveBack") },

                onUpdate: (self) => { console.log("onUpdate", self.progress.toFixed(3)) },
                onToggle: (self) => { console.log("onToggle", self.isActive) },
            }
        })
````

trigger: #section08 .img는 애니메이션의 트리거 요소로 지정됩니다.
start: top center는 요소의 상단이 뷰포트 중앙에 도달했을 때 애니메이션이 시작됨을 의미합니다. <br>

end: bottom 200px는 요소의 하단이 뷰포트 하단에서 200픽셀 위에 위치할 때 애니메이션이 종료됨을 의미합니다. <br>

scrub: true로 설정되어 있으며, 이는 사용자가 스크롤하는 동안 애니메이션 진행이 스크롤과 연동되어 실시간으로 조절됨을 의미합니다. <br>

markers: true는 스크롤 트리거 지점을 시각적으로 표시하도록 설정되어 있습니다. <br>

onUpdate: 스크롤이 업데이트될 때마다 실행되는 콜백 함수로, 스크롤의 진행 정도를 콘솔에 로깅합니다. 여기서 self.progress.toFixed(3)는 스크롤 진행 상태의 정밀한 값을 3자리 소수점으로 표시합니다. <br>

onToggle: 스크롤 트리거의 활성 상태가 변경될 때마다 실행되는 콜백 함수로, 현재 활성 상태를 콘솔에 로깅합니다. 여기서 self.isActive는 스크롤 트리거가 활성화되어 있는지의 여부를 나타냅니다. <br>

이 설정을 통해, #section08 .img 요소는 사용자가 스크롤할 때 지정된 위치에서 애니메이션을 시작하며, 스크롤 위치에 따라 실시간으로 애니메이션 속도와 방향이 조절되고, 스크롤 이벤트에 따라 추가적인 정보가 콘솔에 로깅됩니다<br>

#### 다음시간에 계속...
![image](https://github.com/nicejmp1/nicejmp1.github.io/assets/163364733/90a41f22-19d3-4d17-b649-016d5880fa98)
