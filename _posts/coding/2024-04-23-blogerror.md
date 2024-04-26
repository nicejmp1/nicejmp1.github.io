---
layout: post
title: github블로그 에러 잡기
date: 2024-04-23 16:00 +0900
description: github블로그 에러 고치기
image: ../assets/img/post/error.png
category: Github error blog jekyll
tags: error 
published: true
sitemap: true
---

# Gitgub 블로그 Error 잡기

안녕하세요.. 블로그 빌드 에러로 한동안 고생좀 하다가 고치게 되어 저랑 같은 증상으로 블로그가 안되는 분들도 계실거라 생각해 고치는 방법을 알려드리도록 하겠습니다.<br>

먼저 저를 속 썩였던 에러들을 보여 드리도록 하겠습니다. <br>

![image](https://github.com/nicejmp1/nicejmp1.github.io/assets/163364733/89756ebe-0b03-4cb0-9bb8-bf4b9c3ae34f)<br>

자꾸 commit을 하게되면 해당 사진 처럼
build 오류가 발생 하였었습니다. <br>

github 폴더를 삭제하고 다시 설치해도 똑같은 증상이 나가기에 어떻게 해야 할지 감도 잡히지가 않았습니다.<br>

그러던 도중 좋은 포스팅을 찾게 되었는데 그 방법대로 하니 build가 되는 것입니다...

### 해결방안 

1. 아래와 같이 settings- pages -Build and deploymen 에서 소스를 github Action으로 변경합니다.

![image-2](https://github.com/nicejmp1/nicejmp1.github.io/assets/163364733/b7f94046-5029-4b29-bff4-b4bd5155264c)

2. 변경하게되면 Jekyll 라는게 생기게 되는데 거기서 Configure를 클릭합니다.

![image-3](https://github.com/nicejmp1/nicejmp1.github.io/assets/163364733/efc807ef-2c3f-4a69-bda6-7bfff1a8e025)

3. 그 이후 별도의 수정 없이 Commit Change 를 선택 후 <br>

![image-4](https://github.com/nicejmp1/nicejmp1.github.io/assets/163364733/2d909005-46a9-492c-a08e-f23af771ee4c)

4. Commit changes 버튼을 눌러줍니다.

![image-5](https://github.com/nicejmp1/nicejmp1.github.io/assets/163364733/4ae9f978-664d-4b9b-ab75-5e9fd4cd16f9)

이렇게 되면 에러가 해결된것을 확인 할 수 있게 되었습니다.
![image-6](https://github.com/nicejmp1/nicejmp1.github.io/assets/163364733/c0dfde8b-17d6-4b1e-849d-d428330e4159)



정말 간단하게 이슈가 해결되서 어이가 없었지만 덕분에 블로그를 다시 쓸 수 있게 되었습니다.<br>

여러분들은 이런 에러가 나오지 않고 잘 사용하셨으면 좋겠습니다..

#### 다음시간에 계속...
![image](https://github.com/nicejmp1/nicejmp1.github.io/assets/163364733/90a41f22-19d3-4d17-b649-016d5880fa98)
