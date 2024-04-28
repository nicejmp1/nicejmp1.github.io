---
layout: post
title: 자바스크립트
date: 2024-04-25 20:00 +0900
description: 자바스크립트 문재풀기2
image: ../assets/img/post/javascript02.png
category: javascript
tags: javascript
published: true
sitemap: true
---

# javascript 문제풀기 2

저번시간에 이어 자바스크립트 문제 풀어보도록 하겠습니다.
<br>


#### 1
````javascript
{
        let a, b, result;
        a = 7, b = 4
        result = a | b;
    
        console.log(result)
}
````

해당 코드를 보면 두 변수 a 외 4에 각각 숫자값 7과 4를 할당한 뒤, 비트 or얀산자 (|)를 사용하여 두 수의 비트 연산을 수행합니다. <br>

비트 OR 연산자는 두 대응되는 비트가 적어도 하나라도 1이면 결과 비트를 1로 설정합니다. 이를 각 비트별로 수행합니다. 7과 4를 이진수로 표현하면 다음과 같습니다 <br>

7은 이진수로 0111 <br>
4는 이진수로 0100 <br>
각 비트별로 OR 연산을 수행하면 다음과 같습니다 <br>

첫 번째 비트: 0 OR 0 = 0 <br>
두 번째 비트: 1 OR 1 = 1 <br>
세 번째 비트: 1 OR 0 = 1 <br>
네 번째 비트: 1 OR 0 = 1 <br>

따라서, 0111 OR 0100은 0111이 되고, 이는 십진수로 7입니다. 결과적으로 console.log(result)는 7을 출력합니다. <br>

정답 : 7 
<br>

#### 2
````javascript
{
        function solution(a, b, c){
                let answer = "YES", max;
                let total = a + b + c;
        
                if(a > b) max = a;
                else max = b;
                if(c > max) max = c;
                if(total-max <= max) answer = "NO"; 
                
                return answer;
        }
    
        console.log(solution(53, 93, 107));
}
````
해당 코드를 보면 살펴보게 되면 <br>

- 변수 정의 및 초기화

answer: 초기 값으로 "YES"를 가집니다. 이는 입력된 값들이 삼각형을 만들 수 있다고 가정하는 것입니다. <br>
max: 가장 긴 변을 저장할 변수입니다. <br>
total: 세 변의 합을 저장합니다. <br>

- 가장 긴 변 찾기
a, b, c 세 값 중 가장 큰 값을 찾아 max에 저장합니다. 먼저 a와 b를 비교하고, 그 결과와 c를 비교하여 최대값을 결정합니다 <br>

- 삼각형 조건 판단
total - max는 가장 긴 변을 제외한 나머지 두 변의 합입니다. 이 값이 max보다 작거나 같다면, 세 변으로 삼각형을 만들 수 없습니다. 이 경우 answer를 "NO"로 변경합니다. <br>

- 결과 반환
answer 값을 반환합니다. 삼각형을 만들 수 있다면 "YES", 아니면 "NO"입니다. <br>

total = 253 (53 + 93 + 107)
max를 찾기 위해 먼저 53과 93을 비교하고, 그 중 더 큰 값 93과 107을 비교하여 max = 107로 결정됩니다.<br>

total - max = 253 - 107 = 146
146은 107보다 크므로 이 숫자들로 삼각형을 만들 수 있고, 함수는 "YES"를 반환합니다. <br>

정답 : YES
<br>

#### 3

````javascript
{
        function solution(a, b, c){
                let answer;
                if(a < b) answer = a;
                else answer = b;
                if(c <= answer) answer = c; 
                return answer;
        }
        console.log(solution(15, 12, 11));
}
````

해당 코드를 살펴보면 다음과 같습니다. 
<br>

처음에 a (15)와 b (12)를 비교합니다. 12가 더 작으므로 answer = 12로 설정됩니다. <br>

다음으로 c (11)와 현재 answer (12)를 비교합니다. 11이 더 작으므로 answer = 11로 업데이트됩니다. <br>

최종적으로 answer 값인 11이 반환됩니다. 이는 제공된 세 값 중 최소값입니다. <br>

정답 : 11

#### 4

````javascript
{
        function solution(day, arr){
                let answer = 0;
                for(let x of arr){
                        if(x % 10 == day) answer++;
                }
                return answer;
        }
        
        arr = [25, 23, 11, 47, 53, 17, 33, 40];
        console.log(solution(0, arr));
}
````

해당 코드를 살표보면 다음과 같습니다. 
<br>

answer: 조건에 맞는 숫자의 개수를 세기 위한 카운터로, 0으로 초기화됩니다. <br>

for(let x of arr): 배열 arr의 각 요소 x에 대하여 반복합니다. <br>

if(x % 10 == day): 각 숫자 x의 일의 자리를 10으로 나눈 나머지를 구하고, 이 값이 day와 같은지 비교합니다.
<br>

예를 들어, x가 25이고 day가 5라면, 25 % 10은 5이므로 조건에 맞습니다.
<br>

카운터 증가
조건에 맞는 경우 answer의 값을 1 증가시킵니다.
<br>

결과 반환
모든 배열 요소의 검사가 끝나면 answer 값을 반환합니다. 이 값은 일의 자리가 day와 일치하는 숫자의 총 개수입니다.
<br>

- arr = [25, 23, 11, 47, 53, 17, 33, 40] 배열이 주어지고, solution(0, arr)를 호출합니다.
- 여기서 day는 0입니다.
- 각 숫자의 일의 자리를 확인하면, 40만이 일의 자리가 0입니다.
- 따라서, answer는 1이 증가되어 최종적으로 1이 반환됩니다.

정답 : 1

#### 5

````javascript
{
        let a, b, result;
        a = 7, b = 4
        result = a & b;
    
        console.log(result);
}
````

해당 코드를 살펴보면 다음과 같습니다.
<br>

비트 AND 연산자는 두 대응되는 비트가 모두 1일 경우 결과 비트를 1로 설정합니다. 그렇지 않으면 결과 비트는 0이 됩니다. 7과 4를 이진수로 표현하면 다음과 같습니다 <br>

7은 이진수로 0111 <br>
4는 이진수로 0100 <br>
각 비트별로 AND 연산을 수행하면 다음과 같습니다 <br>

첫 번째 비트: 0 AND 0 = 0 <br>
두 번째 비트: 1 AND 1 = 1 <br>
세 번째 비트: 1 AND 0 = 0 <br>
네 번째 비트: 1 AND 0 = 0 <br>
따라서, 0111 AND 0100은 0100이 되고, 이는 십진수로 4입니다. 결과적으로 console.log(result)는 4를 출력합니다. <br>

정답 : 4

#### 6

````javascript
{
        let a = 6, b = 9, c = 3, result;
        result = ++a + b++ + ++c;
    
        console.log(result);
        console.log(a+b+c);
}
````
해당 코드를 살펴보면 다음과 같습니다.
<br>


result = ++a + b++ + ++c; <br>

++a: a를 먼저 1 증가시키므로 a는 7이 됩니다.<br>

b++: b의 현재 값 9를 사용하고, 표현식 평가 후 b를 1 증가시킵니다. 따라서 이 연산 후 b는 10이 됩니다. <br>

++c: c를 먼저 1 증가시키므로 c는 4가 됩니다. <br>

따라서 계산은 7 + 9 + 4가 되어 result = 20.
결과 출력:
console.log(result); 는 20을 출력합니다.
<br>

console.log(a+b+c);는 각 변수의 최종 값을 더한 결과를 출력합니다: <br>
a = 7 <br>
b = 10 <br>
c = 4 <br>
7 + 10 + 4 = 21 <br>

정답: 20,21

#### 7

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

- b는 10으로 초기화됩니다.
- a는 선언만 되고 초기화되지 않습니다 (undefined 상태).
- 반복문 실행 (for loop):
- i는 0부터 시작하여 5 미만일 동안 반복됩니다 (0, 1, 2, 3, 4).
- 각 반복마다 다음을 수행합니다:
- a = i: a는 현재의 i 값으로 설정됩니다.
- b -= a: b에서 a의 값을 빼고 그 결과를 b에 저장합니다.
- 각 반복 단계에서의 b의 값 변화:
- i = 0: b -= 0 → b = 10 - 0 = 10
- i = 1: b -= 1 → b = 10 - 1 = 9
- i = 2: b -= 2 → b = 9 - 2 = 7
- i = 3: b -= 3 → b = 7 - 3 = 4
- i = 4: b -= 4 → b = 4 - 4 = 0
- 최종 출력:
- console.log(a, b)는 a와 b의 최종 값을 출력합니다. - a는 마지막 반복에서 4로 설정되었고, b는 0이 됩니다.

정답 : 4,0

#### 8

````javascript
{
        let num = 10;
        num += 2;
        num -= 3;
        num *= 5;
        num /= 5;
        num %= 9;
        
        console.log(num)
}
````

- 변수 초기화:
- num = 10: 변수 num을 10으로 설정합니다.
- 연산 수행:
- num += 2: num에 2를 더하면 num은 12가 됩니다.
- num -= 3: num에서 3을 빼면 num은 9가 됩니다.
- num *= 5: num에 5를 곱하면 num은 45가 됩니다.
- num /= 5: num을 5로 나누면 num은 9가 됩니다.
- num %= 9: num을 9로 나눈 나머지를 계산하면 num은  0이 됩니다.
- 결과 출력:
- console.log(num): 최종적으로 num의 값인 0을 - 콘솔에 출력합니다.

정답 : 0

#### 9

````jasvascript
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

#### 10

````javascript
{
        let data = [10, 6, 7, 9, 3];
        let temp;
    
        for(let i=0; i<4; i++){
            for(let j=i+1; j<5; j++){
                if(data[i] > data[j]){
                    temp = data[i];
                    data[i] = data[j];
                    data[j] = temp;
                }
            }
        }
    
        console.log(data) 
}
````

해당 코드를 살펴보면 오른차순인지 내림차순인지 파악하는 문제 입니다. <br>

- 변수 초기화:
- data = [10, 6, 7, 9, 3]: 정렬할 데이터 배열입니다.
- temp: 요소들을 교환할 때 사용할 임시 저장 변수입니다.
- 이중 반복문을 사용한 정렬:
- 외부 반복문: for(let i = 0; i < 4; i++)는 배열의 - 길이 - 1만큼 반복합니다. 배열의 모든 요소를 한 번씩 - 점검하기 위함입니다.
- 내부 반복문: for(let j = i + 1; j < 5; j++)는 - i의 다음 위치에서 시작하여 배열의 끝까지 반복합니다. - 이는 각 요소를 그 이후의 요소들과 비교하기 위함입니다.
- 조건 검사 및 요소 교환:
- if(data[i] > data[j]): 만약 현재 요소가 비교하는 - 요소보다 크면, 두 요소의 위치를 교환합니다.
- 교환 로직:
- temp = data[i]: 현재 요소를 임시 변수에 저장합니다.
- data[i] = data[j]: 비교 요소를 현재 요소 위치에 - 저장합니다.
- data[j] = temp: 임시 변수의 값을 비교 요소 위치에 - 저장합니다.
- 결과 출력:
- 반복문이 모두 완료된 후 console.log(data)를 - 호출하여 정렬된 배열을 출력합니다.

정답 : [3,6,7,9,10]

#### 다음시간에 계속...
![image](https://github.com/nicejmp1/nicejmp1.github.io/assets/163364733/90a41f22-19d3-4d17-b649-016d5880fa98)