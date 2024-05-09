---
layout: post
title: javascript 배열객체
date: 2024-04-30 20:20 +0900
description: javascript
image: ../assets/img/post/javascript02.png
category: javascript
tags: javascript 
published: true
sitemap: true
---

# Javascript 배열 객체 종류 알아보기!!

안녕하세요! 오늘은 javascript 에서 제일 많이 사용 되는 것중 배열객체에 어떤것이 쓰이는지에 대해 종류와 설명 그리고 간단한 예시를 알려드리겠습니다.

## find()
> find() 메서드는 주어진 판별 함수를 만족하는 첫번째 요소의 값을 반환 합니다.

JavaScript: `Array.prototype.find`는 배열에서 조건에 맞는 첫 번째 요소를 반환합니다. <br>
조건에 맞는 요소가 없으면 `undefined`를 반환합니다. <br>

````javascript
{
    JavaScript: Array.prototype.find
    const numbers = [1, 2, 3, 4];
    const result = numbers.find(num => num > 2);
    console.log(result); // 3
    
    const notFound = numbers.find(num => num > 10);
    console.log(notFound); // undefined
}
````

Python: `str.find`는 문자열에서 찾을 값의 첫 번째 인덱스를 반환합니다.
찾는 값이 없으면 `-1`을 반환합니다. <br>

````python
    Python: str.find
    text = "Hello, world!"
    index = text.find("world")
    print(index)  # 7
    
    index_not_found = text.find("everyone")
    print(index_not_found)  # -1
````

## forEach()
> forEach() 메서드는 주어진 함수 조건을 배열 요소 각각에 대해 실행하고, 그 결과를 반환합니다.

JavaScript: `Array.prototype.forEach`는 배열의 각 요소에 대해 콜백 함수를 실행합니다. 반환값은 없습니다. <br>

````javascript
    JavaScript: Array.prototype.forEach
    const numbers = [1, 2, 3];
    numbers.forEach(num => console.log(num * 2));
    // 출력: 2, 4, 6
````

Python: 컬렉션을 반복하기 위한 `for` 루프를 사용합니다. 리스트 컴프리헨션도 활용할 수 있습니다.  <br>

````python
   Python: 컬렉션을 반복하기 위한 for 루프
    # 일반적인 for 루프
    for num in [1, 2, 3]:
        print(num * 2)
    # 출력: 2, 4, 6
    
    # 리스트 컴프리헨션
    result = [num * 2 for num in [1, 2, 3]]
    print(result)
    # 출력: [2, 4, 6]
````

## map()
>map() 메서드는 주어진 함수를 호출하고, 그 결과를 모아서 만든 새로운 배열을 반환 합니다.

JavaScript: `Array.prototype.map`은 배열의 각 요소에 대해 콜백 함수를 실행하고 결과를 새로운 배열로 반환합니다. 원본 배열은 변경되지 않습니다. 
<br>

````javascript
// JavaScript: Array.prototype.map
    const numbers = [1, 2, 3];
    const doubled = numbers.map(num => num * 2);
    console.log(doubled); // [2, 4, 6]
    console.log(numbers); // [1, 2, 3]
````

Python: `map`은 각 요소에 함수를 적용하여 새로운 맵 객체를 반환합니다. 리스트 컴프리헨션을 활용할 수도 있습니다. <br>

````python
    // Python: map
    numbers = [1, 2, 3]
    doubled = list(map(lambda x: x * 2, numbers))
    print(doubled)  # [2, 4, 6]
    print(numbers)  # [1, 2, 3]
    
    # 리스트 컴프리헨션을 활용한 방법
    doubled = [num * 2 for num in numbers]
    print(doubled)  # [2, 4, 6]
````

## includes()
>includes() 메서드는 배열 포함 여부를 검색하여, 불린(true,false)을 반환합니다.

JavaScript: `Array.prototype.includes`와 `String.prototype.includes`는 배열 또는 문자열에 특정 값이 포함되어 있는지 여부를 확인합니다. 
대소문자를 구분하며, 문자열은 부분 일치 확인이 가능합니다.
<br>

````javascript
    // JavaScript: Array.prototype.includes와 String.prototype.includes
    // 배열의 값 포함 여부 확인
    const numbers = [1, 2, 3];
    console.log(numbers.includes(2)); // true
    console.log(numbers.includes(5)); // false
    
    // 문자열의 부분 일치 확인
    const text = "Hello, world!";
    console.log(text.includes("world")); // true
    console.log(text.includes("World")); // false
````

Python: `in` 연산자는 컬렉션 또는 문자열에 특정 값이 포함되어 있는지 여부를 확인합니다.
대소문자를 구분하며, 부분 일치 확인이 가능합니다.
<br>

````python
    // Python: in 연산자
    # 리스트의 값 포함 여부 확인
    numbers = [1, 2, 3]
    print(2 in numbers)  # true
    print(5 in numbers)  # false
    
    # 문자열의 부분 일치 확인
    text = "Hello, world!"
    print("world" in text)  # true
    print("World" in text)  # false
````

## indexOf() 
>indexOf() 메서드는 배열을 검색하고, 위치값(숫자)을 반환합니다.

JavaScript: `Array.prototype.indexOf`와 `String.prototype.indexOf`는 배열 또는 문자열에서 특정 값의 첫 번째 인덱스를 반환합니다.
찾을 값이 없으면 `-1`을 반환합니다.
<br>

````javascript
   // JavaScript: Array.prototype.indexOf와 String.prototype.indexOf
    // 배열에서 특정 값 찾기
    const numbers = [1, 2, 3, 2];
    console.log(numbers.indexOf(2)); // 1
    console.log(numbers.indexOf(2, 2)); // 3
    console.log(numbers.indexOf(5)); // -1
    
    // 문자열에서 특정 값 찾기
    const text = "Hello, world!";
    console.log(text.indexOf("world")); // 7
    console.log(text.indexOf("World")); // -1
````

Python: `str.index`는 문자열에서 특정 값의 첫 번째 인덱스를 반환합니다.
찾을 값이 없으면 `ValueError` 예외를 발생시킵니다.
리스트에서는 `index()` 메서드를 사용할 수 있습니다.
<br>

````python
 // Python: str.index와 list.index
    # 문자열에서 특정 값 찾기
    text = "Hello, world!"
    try:
        index = text.index("world")
        print(index)  # 7
    except ValueError:
        print("Value not found")
    
    # 리스트에서 특정 값 찾기
    numbers = [1, 2, 3, 2]
    try:
        index = numbers.index(2)
        print(index)  # 1
    except ValueError:
        print("Value not found")
````

## join()
> join() 메서드는 배열의 요소를 추가하여, 하나의 문자열로 반환합니다.

JavaScript: `Array.prototype.join`은 배열의 모든 요소를 문자열로 결합하여 반환합니다. 구분자를 지정하지 않으면 기본값 `,`를 사용합니다.
<br>

````javascript
    // JavaScript: Array.prototype.join
    const letters = ['a', 'b', 'c'];

    // 구분자를 지정하여 결합
    console.log(letters.join('-')); // "a-b-c"
    console.log(letters.join('')); // "abc"
    
    // 구분자를 지정하지 않으면 기본값 `,` 사용
    console.log(letters.join()); // "a,b,c"
````

Python: `"구분자".join`은 문자열, 리스트, 튜플 등의 컬렉션 요소를 결합하여 문자열로 반환합니다. 구분자를 지정하지 않으면 예외가 발생합니다.
<br>

````python
    // Python: "구분자".join
    letters = ['a', 'b', 'c']

    # 구분자를 지정하여 결합
    print('-'.join(letters))  # "a-b-c"
    print(''.join(letters))  # "abc"
    
    # 구분자가 없으면 예외 발생
    try:
        print(''.join())  # TypeError 발생
    except TypeError:
        print("구분자를 지정해야 합니다.")
````

## push()
> push() 메서드는 배열 끝에 요소를 추가하고, 배열의 새로운 길이 값을 반환합니다.

JavaScript: `Array.prototype.push`는 배열의 끝에 하나 이상의 요소를 추가하고 배열의 새 길이를 반환합니다. 추가된 후 배열의 새 길이를 반환합니다.
<br>

````javascript
  // JavaScript: Array.prototype.push
    const numbers = [1, 2, 3];

    // 단일 요소 추가
    const newLength = numbers.push(4);
    console.log(numbers); // [1, 2, 3, 4]
    console.log(newLength); // 4
    
    // 다중 요소 추가
    numbers.push(5, 6);
    console.log(numbers); // [1, 2, 3, 4, 5, 6]
````

Python: `list.append`와 `list.extend`는 리스트에 요소를 추가합니다.
`append`: 단일 요소를 리스트의 끝에 추가합니다.
`extend`: 다른 리스트나 컬렉션의 모든 요소를 리스트의 끝에 추가합니다.
<br>

````python
   // Python: list.append와 list.extend
    numbers = [1, 2, 3]

    # 단일 요소 추가 (append)
    numbers.append(4)
    print(numbers)  # [1, 2, 3, 4]
    
    # 다중 요소 추가 (extend)
    numbers.extend([5, 6])
    print(numbers)  # [1, 2, 3, 4, 5, 6]
````
<br>

## slice()
> slice() 메서드는 배열 시작 위치에서 종료 위치 값을 추출하여, 새로운 배열을 반환합니다.

JavaScript: `Array.prototype.slice`와 `String.prototype.slice`는 배열 또는 문자열의 일부를 추출하여 새로운 배열 또는 문자열을 생성합니다.
종료 인덱스는 포함되지 않습니다.
<br>

````javascript
    // JavaScript: Array.prototype.slice와 String.prototype.slice
    // 배열에서 부분 추출
    const numbers = [1, 2, 3, 4];
    const slicedNumbers = numbers.slice(1, 3);
    console.log(slicedNumbers); // [2, 3]
    
    // 문자열에서 부분 추출
    const text = "Hello, world!";
    const slicedText = text.slice(7, 12);
    console.log(slicedText); // "world"
````

Python: `list[start:end]`, `str[start:end]`는 리스트 또는 문자열의 일부를 슬라이스하여 새로운 리스트 또는 문자열을 생성합니다.
종료 인덱스는 포함되지 않습니다.
음수 인덱스를 사용하여 끝에서부터 슬라이스할 수 있습니다.
<br>

````python
    // Python: 리스트 및 문자열 슬라이싱 (list[start:end], str[start:end])
    # 리스트에서 부분 추출
    numbers = [1, 2, 3, 4]
    sliced_numbers = numbers[1:3]
    print(sliced_numbers)  # [2, 3]
    
    # 문자열에서 부분 추출
    text = "Hello, world!"
    sliced_text = text[7:12]
    print(sliced_text)  # "world"
    
    # 음수 인덱스를 사용하여 끝에서부터 추출
    sliced_text_negative = text[-6:-1]
    print(sliced_text_negative)  # "world"
````
<br>

## splice()
> splice() 메서드는 배열의 기존 요소를 삭제 또는 교체하거나 새 요소를 추가하여 배열의 내용을 변경합니다.

JavaScript: `Array.prototype.splice`는 배열에서 특정 인덱스에 있는 요소를 추가하거나 제거합니다. 반환값은 제거된 요소를 담은 배열입니다.
<br>

````javascript
    // JavaScript: Array.prototype.splice
    // 특정 인덱스에서 두 개의 요소 제거
    const numbers = [1, 2, 3, 4];
    const removed = numbers.splice(1, 2);
    console.log(removed); // [2, 3]
    console.log(numbers); // [1, 4]

    // 특정 인덱스에 요소 추가
    numbers.splice(1, 0, 2, 3);
    console.log(numbers); // [1, 2, 3, 4]
````

Python: `list`에는 `splice`에 해당하는 내장 메서드가 없으나, 슬라이싱을 통해 대체할 수 있습니다.
<br>

````python
    // Python: 리스트 및 문자열 슬라이싱 (list[start:end], str[start:end])
    # 리스트에서 부분 추출
    numbers = [1, 2, 3, 4]
    sliced_numbers = numbers[1:3]
    print(sliced_numbers)  # [2, 3]
    
    # 문자열에서 부분 추출
    text = "Hello, world!"
    sliced_text = text[7:12]
    print(sliced_text)  # "world"
    
    # 음수 인덱스를 사용하여 끝에서부터 추출
    sliced_text_negative = text[-6:-1]
    print(sliced_text_negative)  # "world"
````
<br>

## sort()
> sort() 메서드는 배열의 요소를 적적한 위치에 정렬한 후, 그 배열을 반환합니다.

JavaScript: `Array.prototype.sort`는 배열을 제자리에서 정렬하고 정렬된 배열을 반환합니다.
비교 함수를 제공하지 않을 경우 요소를 문자열로 변환하여 유니코드 순서로 정렬합니다.
비교 함수를 사용하여 사용자 정의 정렬이 가능합니다.
<br>

````javascript
 // JavaScript: Array.prototype.sort
    // 기본 정렬 (유니코드 순서)
    const numbers = [3, 1, 4, 2];
    const sortedNumbers = numbers.sort();
    console.log(sortedNumbers); // [1, 2, 3, 4]
    console.log(numbers); // [1, 2, 3, 4]
    
    // 비교 함수를 사용한 사용자 정의 정렬
    const customSortedNumbers = numbers.sort((a, b) => a - b);
    console.log(customSortedNumbers); // [1, 2, 3, 4]
````
<br>

Python: `list.sort` 메서드와 `sorted` 함수는 리스트를 정렬합니다.
`list.sort`는 리스트를 제자리에서 정렬하며, 반환값은 `None`입니다.
`sorted` 함수는 정렬된 새 리스트를 반환합니다.
비교 함수를 사용하여 사용자 정의 정렬이 가능합니다. 
<br>

````python
    // Python: list.sort와 sorted
    # 리스트 제자리 정렬
    numbers = [3, 1, 4, 2]
    numbers.sort()
    print(numbers)  # [1, 2, 3, 4]
    
    # 새 리스트로 정렬
    sorted_numbers = sorted([3, 1, 4, 2])
    print(sorted_numbers)  # [1, 2, 3, 4]
    
    # 사용자 정의 정렬 (내림차순)
    custom_sorted_numbers = sorted([3, 1, 4, 2], reverse=True)
    print(custom_sorted_numbers)  # [4, 3, 2, 1]
````

#### 다음시간에 계속...
![image](https://github.com/nicejmp1/nicejmp1.github.io/assets/163364733/90a41f22-19d3-4d17-b649-016d5880fa98)
