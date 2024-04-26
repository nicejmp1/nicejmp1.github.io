---
layout: post
title: 자바스크립트
date: 2024-04-26 18:40 +0900
description: 자바스크립트 문재풀기
image: ../assets/img/post/javascript02.png
category: javascript
tags: javascript
published: true
sitemap: true
---

# javascript 문제 풀기

오늘은 자바스크립트를 얼마나 알고 있는지 알아보도록 하겠습니다. <br>

1. 
````javascript
{
        function func(){
            let a = [];
    
            for(i=1; i<=5; i++){
                a += [i];
            }
            console.log(a);
        }
        func();
}   
````
첫번째 문제는 쉬우니까 답만 알려드리도록 하겠습니다. <br>
정답 : 12345 <br>

2. 
````javascript
{
    const arr = [100, 200, 300, 400, 500];

    const text1 = arr.join("*");
    const text3 = arr.join("");
    const text4 = arr.join(" ");

    console.log(text1);
    console.log(text3);
    console.log(text4);
}
````
두번째 문제 같은 경우 text1 = arr에 join * 을 하게되었습니다.<br>
출력값을 확인해보면 100*200*300*400*500 이 출력됩니다. <br>

text3 arr에 ""을 추가함으로써 출력시 100200300400500이 나오게 됩니다. <br>

마지막으로 text4 arr에 " "을 추가함으로써 출력시 100 200 300 400 500  이 출력되게 됩니다. <br>

정답 : 100*200*300*400*500 <br>
      100200300400500 <br>
      100 200 300 400 500

3.  
````javascript
{
        let a, b = 10;

        for(let i=0; i<5; i++){
            a = i;
            b -= a;
        }
        console.log(a, b)
}
````
해당 코드의 풀이를 보면,<br>

````javascript
초기값: a = 0, b = 10
i = 0: a = 0, b = 10 - 0 = 10
i = 1: a = 1, b = 10 - 1 = 9
i = 2: a = 2, b = 9 - 2 = 7
i = 3: a = 3, b = 7 - 3 = 4
i = 4: a = 4, b = 4 - 4 = 0
````

이런식으로 a 는 1씩 증가하지만 b는 a의 값을 빼서 4,0이 되는것을 확인 할 수 있습니다. <br>

정답 : 4 , 0  <br>

4. 
````javascript
{
        function func(){
            let i = 20, j = 20, k = 30;
            i /= j;
            j -= i;
            k %= j;
    
            console.log(i);
            console.log(j);
            console.log(k);
        }
        func();
}
````

해당 코드를 살펴보면 i = 20 / 20을 한다는 뜻입니다. <br>
그렇게 해서 i 는 1이되면서 출력이 되고 j= 20 - i를 하는 것이기 떄문에 j는 19가 출력이됩니다. <br>

그렇게 K = 30 % j(19) 가되어서 나머지 값인 11이 출력이 됩니다. <br>

정답 : 1,19,11 <br>

5. 
````javascript
{       
        let k = 1;
        let temp;
        for(let i=0; i<=3; i++){
                temp = k;
                k++;
                console.log(temp + "번");
        }    
}
````

해당 코드를 살펴보면 for문이 총 0~3까지 반복될때 k++한다고 합니다. <br>

그 k는 temp에 저장이 되어 출력이 되므로, 1번,2번,3번,4번이 출력 됩니다. <br>

정답 : 1번, 2번, 3번, 4번<br>

6. 
````javascript
{
        let num1 = 3;
        let num2 = 7;
        if(++num1 > 5 || num2++ < 1){
                console.log(num1);
        }
        console.log(num2)
}
````

- ++num1: num1의 값을 1 증가시킨 후에 비교합니다. num1은 3에서 4가 되고, 다시 4에서 5가 됩니다. <br>

- ++num1 > 5: 이제 num1은 5이므로, 이 조건은 false입니다. <br>

- num2++ < 1: 이 부분은 실행되지 않습니다. 왜냐하면 JavaScript에서는 논리 연산자 || (OR)가 첫 번째 조건이 true일 때 두 번째 조건을 평가하지 않는 "단축 평가(short-circuit evaluation)" 방식을 사용하기 때문입니다.<br>

- 여기서 첫 번째 조건이 false이므로, 두 번째 조건이 평가되어야 하지만 num2++ < 1 조건은 num2가 7인 상태에서 false가 됩니다. <br>

- num2는 7에서 8로 증가합니다.

console.log(num1): if 문의 조건이 false이므로 이 줄은 실행되지 않습니다. <br>
console.log(num2): num2의 최종 값, 8을 출력합니다. <br>

정답 : 8 <br>

7. 
````javascript
{
        let num = [1, 5, 1, 2, 7, 5];
        for(let i=0; i<6; i++){
                if((i+2) % 2 == 0){
                        console.log(num[i]);
                }
        }
}
````
 해당 코드를 살펴보면 for문은 0~5까지 반복 하면서 i +2 % 2 == 0 이 참일 경우 출력하라고 합니다. <br>

처음 0은 +2 를하고 %2 를하였을때 나머지가 0 이므로 홀수를 제외한 짝수가 출력 되는것을 확인 할 수 있습니다. <br>

정답 : 1,1,7 <br>

8. 
````javascript
{
        let num = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

        for(let i=0; i<=9; i++){
                switch(num[i] % 2){
                        case 1:
                            console.log(num[i]);
                            break;
                        default:
                            console.log("*");
                }
        }
}
````
해당 코드를 살펴보면 i = 0~9까지 반복이 되면서 %2를 하여 case 1 즉 나머지가 1일경우 num[i] 값을 출력 하라 나와있고 아닐경우 "*"이 출력되게 하였습니다. <br>

즉 홀수 값들이 출력 되는 것을 확인 할 수 있습니다. <br>

정답 : *1*3*5*7*9 <br>

9. 
````javascript
{
        let cnt = 0;
        let sum = 0;
        for(let i=0; i<=7; i++){
                if(i%2 == 1){
                        cnt++;
                        sum += i;
                }
        }
        console.log(cnt + ", "+sum/2);
}
````

해당 코드를 살펴보면 전 문제랑 상당히 유사하다는 것을 알 수있습니다. <br>

i의 변수값이 0~7까지 반복되게 하면서 i%2 == 1 일 경우 cnt++ 하면서 sum에 +=i를 시켜달라는 것입니다.<br>

홀수일때 cnt++ 가 되며 i에 값이 sum 으로 들어가게 됩니다. <br>

1,3,5,7 총 4번 카운트가 되며 그 값을 더한 16을 나누기 2하게 됩니다. <br>

정답 : 4,8 <br>

10. 

````javascript
{
        let a=1, b=1, num;

        for(let i=0; i<6; i++){
            num = a + b;
            a = b;
            b = num;
        }
        console.log(num)
}
````

해당 코드는 피보나치 수열이라고 생각하시면 됩니다. <br>

- 변수 초기화: a와 b는 각각 피보나치 수열의 첫 번째 항과 두 번째 항의 값인 1로 초기화됩니다. num은 계산된 피보나치 수를 저장할 변수입니다. <br>

-for 루프 실행: 루프는 0부터 5까지 총 6번 반복됩니다.
각 반복에서, num은 a와 b의 합, 즉 현재 피보나치 항의 값을 계산합니다.<br>
a는 b의 값을 받고, b는 num의 값을 받습니다. 이것은 수열에서 다음 위치로 이동하는 것을 시뮬레이션합니다. <br>

- 출력: console.log(num)은 루프가 종료된 후, num의 값을 출력합니다. 이 값은 루프의 마지막 반복에서 계산된 피보나치 항입니다. <br>

정답 : 21

#### 다음시간에 계속...
![image](https://github.com/nicejmp1/nicejmp1.github.io/assets/163364733/90a41f22-19d3-4d17-b649-016d5880fa98)