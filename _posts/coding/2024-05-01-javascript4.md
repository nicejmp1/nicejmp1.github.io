---
layout: post
title: javascript 문자열객체
date: 2024-05-01 13:20 +0900
description: javascript
image: ../assets/img/post/javascript02.png
category: javascript
tags: javascript 
published: true
sitemap: true
---

# Javascript 문자열 객체 종류 알아보기!!

안녕하세요! 오늘은 javascript 문자열 객체가 무엇인지에 대해 간단한 설명과 예시를 통해 알려드리겠습니다.

## .includes() 
>includes() 메서드는 문자열 포함 여부를 검색하여, 불린(true, false)을 반환합니다.

includes() 함수는 JavaScript에서 배열이나 문자열에서 특정 요소나 문자열이 존재하는지 확인할 때 사용합니다. <br>

이 함수는 요소나 문자열이 존재하면 true
존재하지 않으면 false를 반환합니다. <br>

````javascript
{
        const sentence = "Hello, world!";
        console.log(sentence.includes("world"));  // true
        console.log(sentence.includes("bye"));    // false                                        
}
````

## .indexOf()
> indexOf() 메서드는 문자열을 검색하여, 주어진 값과 일치하는 첫 번째 위치값(index)을 반환 합니다.

indexof() 함수는 JavaScript의 JavaScript의 문자열과 배열에서 사용되는 메서드로,
특정 요소 또는 문자가 처음 나타나는 위치를 반환합니다. <br>

````javascript
{
        const sentence = "Hello, welcome to the world of JavaScript!";
        const index1 = sentence.indexOf('e');
        console.log(index1); // 출력: 1 ('e'가 인덱스 1 위치에 있음)     
        
        // 문자열에서 부분 문자열 "world"의 첫 번째 등장 위치 찾기
        const text = "The quick brown fox jumps over the lazy dog.";
        const index2 = text.indexOf("fox");
        console.log(index2); // 출력: 16 ('fox' 부분 문자열이 인덱스 16 위치에 있음)

        // 배열에서 숫자 3의 첫 번째 등장 위치 찾기
        const numbers = [1, 2, 3, 4, 5, 3, 2, 1];
        const index3 = numbers.indexOf(3);
        console.log(index3); // 출력: 2 (숫자 3이 인덱스 2 위치에 있음)
}
````

## .match() 
> match() 메서드는 문자열(정규식)을 검색하고, 문자열(배열)을 반환합니다.

javaScript: String.prototype.match는 문자열에서 정규식 패턴을 찾습니다. <br>
Python: re.match는 문자열의 시작 부분에서 정규식 패턴을 찾습니다. <br>
ust, Swift, Kotlin: 패턴 매칭을 위한 키워드로 다양한 조건에 따라 표현식을 분기합니다 <br>

````javascript
{
    fun main() {
        val number = 2
        
        when (number) {
                1 -> println("One")
                2 -> println("Two")
                3 -> println("Three")
                else -> println("Other")
        }
        }
        // 출력: Two

        let number = 3

    switch number {
    case 1:
        print("One")
    case 2:
        print("Two")
    case 3:
        print("Three")
    default:
        print("Other")
    }
    // 출력: Three

}
````

## .replace() 
> replace() 메서드는 문자열에서 특정 문자열을 교체하여, 새로운 문자열을 반환합니다.

JavaScript: `String.prototype.replace`는 문자열 내 특정 패턴을 다른 문자열로 교체합니다. <br>

````javascript
 //JavaScript: String.prototype.replace
        // 단순 문자열 대체
        console.log("Hello, world!".replace("world", "everyone")); // "Hello, everyone!"
        
        // 정규식 사용
        console.log("Hello, World!".replace(/world/i, "everyone")); // "Hello, everyone!"
````
<br>

Python: `str.replace`는 문자열 내 모든 일치하는 부분을 다른 문자열로 교체합니다.
<br>

````python
   //Python: str.replace
    # 단순 문자열 대체
    text = "Hello, world!"
    print(text.replace("world", "everyone"))  # "Hello, everyone!"

    # 정규식 사용
    import re
    text = "Hello, world!"
    print(re.sub(r'world', 'everyone', text))  # "Hello, everyone!"
````

## .search()
> search() 메서드는 문자열(정규식)을 검색하고, 위치값(숫자)을 반환합니다.

JavaScript: `String.prototype.search`는 문자열에서 정규식 패턴을 찾아 인덱스를 반환합니다.
찾는 패턴이 없을 경우 `-1`을 반환합니다.
<br>

````javascript
    //JavaScript: String.prototype.search
    // 패턴 일치
    console.log("Hello, world!".search(/world/)); // 7
    
    // 패턴 불일치
    console.log("Hello, world!".search(/everyone/)); // -1
````
<br>

Python: `re.search`는 문자열에서 정규식 패턴과 일치하는 첫 부분을 반환합니다.
찾는 패턴이 없을 경우 `None`을 반환합니다.
<br>

````python
    //Python: re.search
    import re

    # 패턴 일치
    match = re.search(r'world', "Hello, world!")
    if match:
        print(match) # re.Match object; span=(7, 12), match='world'
    
    # 패턴 불일치
    match = re.search(r'everyone', "Hello, world!")
    if not match:
        print("Pattern not found")  # Pattern not found
````

## .slice()
> slice() 메서드는 문자열에서 시작 위치에서 종료 위치 값을 추출하여, 새로운 문자열을 반환 합니다.

JavaScript: `Array.prototype.slice`와 `String.prototype.slice`는 배열 또는 문자열의 일부를 추출합니다.
<br>

````javascript
 //JavaScript: Array.prototype.slice와 String.prototype.slice
    // 배열
    const letters = ['a', 'b', 'c', 'd'];
    console.log(letters.slice(1, 3)); // ['b', 'c']

    // 문자열
    const text = "Hello, world!";
    console.log(text.slice(7, 12)); // "world"
````
<br>

Python: `list[start:end]`, `str[start:end]`는 리스트 또는 문자열의 일부를 슬라이스합니다. <br>

````python
    //python: 리스트 및 문자열 슬라이싱
    # 리스트
    letters = ['a', 'b', 'c', 'd']
    print(letters[1:3])  # ['b', 'c']
    
    # 문자열
    text = "Hello, world!"
    print(text[7:12])  # "world"
````

## .substring()
> substring() 메서드는 문자열에서 시작 위치에서 종료 위치 값을 추출하여, 새로운 문자열을 반환 합니다.

JavaScript: `String.prototype.substring`은 문자열의 일부를 추출합니다.
종료 인덱스는 포함되지 않습니다.
음수 인덱스는 자동으로 `0`으로 변환됩니다.
인덱스 순서는 시작과 종료 인덱스에 상관없이 자동 정렬됩니다. <br>

````javascript
//JavaScript: String.prototype.substring
    const text = "Hello, world!";

    // 시작과 종료 인덱스 순서 상관 없이 추출
    console.log(text.substring(7, 12)); // "world"
    console.log(text.substring(12, 7)); // "world"
    
    // 음수 인덱스는 0으로 처리
    console.log(text.substring(-3, 5)); // "Hello"
````
<br>

Python: `str[start:end]`는 문자열의 일부를 슬라이스합니다.
음수 인덱스를 지원하여 문자열의 끝에서부터 슬라이스 가능합니다.
종료 인덱스는 포함되지 않습니다. <br>

````python
    Python: 문자열 슬라이싱 (str[start:end])
    text = "Hello, world!"

    # 시작과 종료 인덱스에 따라 슬라이싱
    print(text[7:12])  # "world"
    
    # 음수 인덱스 사용
    print(text[-6:-1])  # "world"        
````
<br>

## .split()
> split() 메서드는 문자열을 구분자로 구분하고, 여러 개의 문자열(배열)을 반환합니다.

JavaScript: `String.prototype.split`은 문자열을 구분자를 기준으로 나누어 배열을 생성합니다.
구분자가 없을 경우 전체 문자열이 하나의 요소로 반환됩니다. <br>

````javascript
   //JavaScript: String.prototype.split
    // 구분자로 나누기
    console.log("Hello, world!".split(", ")); // ["Hello", "world!"]
    
    // 최대 분할 횟수 지정
    console.log("a,b,c,d".split(",", 2)); // ["a", "b"]
    
    // 구분자 없이 분할 시 전체 문자열이 하나의 요소로 반환
    console.log("Hello".split()); // ["Hello"]
````

Python: `str.split`은 문자열을 구분자로 나누어 리스트를 생성합니다.
구분자가 없을 경우 공백을 기준으로 분할됩니다.
<br>

````python
    Python: str.split
    # 구분자로 나누기
    print("Hello, world!".split(", "))  # ["Hello", "world!"]
    
    # 최대 분할 횟수 지정
    print("a,b,c,d".split(",", 2))  # ["a", "b"]
    
    # 구분자 없이 분할 시 공백을 기준으로 분할
    print("Hello world!".split())  # ["Hello", "world!"]
````

## .trim()
> trim 메서드는 문자열의 앞/뒤 공백을 제거하고, 새로운 문자열을 반환합니다.

JavaScript: `String.prototype.trim`은 문자열의 양 끝에 있는 공백을 제거합니다.
중간의 공백은 그대로 유지합니다. <br>

````javascript
    //JavaScript: String.prototype.trim
    const text = "   Hello, world!   ";
    console.log(text.trim()); // "Hello, world!"
````
<br>

Python: `str.strip`은 문자열의 양 끝에 있는 공백을 제거합니다.
<br>

````python
    //Python: str.strip, str.lstrip, str.rstrip
    text = "   Hello, world!   "
    print(text.strip())  # "Hello, world!"
    print(text.lstrip())  # "Hello, world!   "
    print(text.rstrip())  # "   Hello, world!"
````

#### 다음시간에 계속...
![image](https://github.com/nicejmp1/nicejmp1.github.io/assets/163364733/90a41f22-19d3-4d17-b649-016d5880fa98)
