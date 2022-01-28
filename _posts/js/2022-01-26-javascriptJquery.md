---
title: "Javascript Jquery"
excerpt: "Jquery에 대해서 알아보자"
last_modified_at: 2022-01-28T12:03:16-13:00
categories:
  - Javascript
tags:
  - Javascript
  - Jquery
toc: true
toc_sticky: true
toc_label: "Javascript"
---

## 제이쿼리란?

<a href="https://jquery.com">제이쿼리</a> 홈페이지에 따르면 jQuery는 빠르고 작고 기능이 풍부한 JavaScript 라이브러리입니다. 여러 브라우저에서 작동하는 사용하기 쉬운 API를 사용하여 HTML 문서 탐색 및 조작, 이벤트 처리, 애니메이션 및 Ajax와 같은 작업을 훨씬 더 간단하게 만듭니다.
<hr>

## 제이쿼리의 기능

1. DOM 요소들을 선택하는 제이쿼리 선택자

JQuery("선택자") 혹인 $("선택자")의 형식입니다.

2. DOM 트리와 요소를 조작하는 제이쿼리 메소드

'$("선택자").이벤트()' 형식입니다.

3. 웹 페이지에서 발생되는 이벤트를 처리하는 제이쿼리 이벤트

'$("선택자").메소드()' 형식입니다.<br>


## 제이쿼리의 기본 구조

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Hello World!</title>
  <script src="http://code.jquery.com/jquery-latest.min.js"></script> <!-- 제이쿼리 불러오기 -->
</head>
<body>
  <p>단락입니다.</p>
  <button>배경 색상 변경하기</button>

  <script>
    $("button").click(function(){
      $("p").css("background-color", "yellow");
    });
  </script>
</body>
</html>
```

![image](https://user-images.githubusercontent.com/72953874/151486181-288bcd3c-ad53-4814-b527-233d4524c68c.png)
![image](https://user-images.githubusercontent.com/72953874/151486188-7d62a307-3136-473a-b3cc-8f2aec01b516.png)

'$()'은 제이쿼리 함수, css()는 제이쿼리 메소드, click()은 제이쿼리 이벤트입니다.

<br>

## $(document).ready()

- 제이쿼리 코드 적용 오류

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Hello World!</title>
  <script src="http://code.jquery.com/jquery-latest.min.js"></script> <!-- 제이쿼리 불러오기 -->
  <script>
    $("button").click(function(){
      $("p").css("background-color", "yellow");
    });
  </script>
</head>
<body>
  <p>단락입니다.</p>
  <button>배경 색상 변경하기</button>

</body>
</html>
```
위의 코드로 변경하여 다시 실행하면 버튼을 눌러도 배경색이 바뀌지 않습니다. 왜일까요? 제이쿼리 코드가 먼저 실행된 후, body 영역에 있는 p태그와 button태그가 자바스크립트 엔진에 로드되기 때문에 그 전에 실행된 jquery 코드에서는 p와 button태그를 인지할 수 없기 때문입니다.
<br>
<br>
위와 같은 문제를 방지하기 위해 $(document).ready()를 사용합니다.

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Hello World!</title>
  <script src="http://code.jquery.com/jquery-latest.min.js"></script> <!-- 제이쿼리 불러오기 -->
  <script>
    $(document).ready(function(){
      $("button").click(function(){
      $("p").css("background-color", "yellow");
    });
    });
    
  </script>
</head>
<body>
  <p>단락입니다.</p>
  <button>배경 색상 변경하기</button>

</body>
</html>
```

이제 정상 작동하는 것을 확인할 수 있습니다.$(document)는 페이지를 나타내는 제이쿼리 객체이며, ready()는 페이지가 준비되었을때 함수를 실행하도록 합니다. 따라서 DOM요소가 모두 자바스크립트 엔진에 다 로드되어 준비가 되었을때 실행됩니다.

<br>

## HTML 조작을 위한 메소드들

|메소드|역할|
|---|---|
|text()|선택된 HTML요소의 텍스트 내용을 가져오거나 설정한다.|
|html()|선택된 HTML요소의 HTML 태그를 포함한 내용을 가져오거나 설정한다.|
|val()|선택된 HTML요소의 폼 요소의 속성 값을 가져오거나 설정한다.|
|arrt()|선택된 HTML요소의 요소의 속성 값을 가져오거나 설정한다.|

<br>

|메소드|역할|
|---|---|
|append()|선택된 HTML요소의 제일 끝에 새로운 요소를 추가한다.|
|prepend()|선택된 HTML요소의 제일 앞에 새로운 요소를 삽입한다.|
|before()|선택된 HTML요소의 바로 앞에 새로운 요소를 삽입한다.|
|after()|선택된 HTML요소의 바로 뒤에 새로운 요소를 삽입한다.|
|remove()|선택된 HTML요소를 삭제한다.|
<br>

## CSS 조작을 위한 메소드들

|메소드|역할|
|---|---|
|addClass()|선택된 HTML요소에 class 속성을 추가한다.|
|removeClass()|선택된 HTML요소로부터 class 속성을 삭제한다.|
|css()|선택된 HTML요소에 css속성을 설정하거나 속성 값을 가져온다.|



<br>

이렇게 간단하게 제이쿼리에 대해 알아보았습니다. 다 설명하기엔 너무 길고, 쓸데없는 내용이 많을 것 같아서 간략하게 소개만 했습니다. 제이쿼리 선택자의 경우에도 위에 설명한 것만 있는 것이 아니라 그룹 선택자, 자식/후손 선택자 등등 여러가지가 있습니다. 따라서 경우에 따라 필요할 때 직접 찾아서 사용해 보시길 바랍니다. 감사합니다.
<br> 

## 참고문헌

![image](https://user-images.githubusercontent.com/72953874/151288663-06e5edaa-1585-4511-8413-b4e23b264bb2.png)

저자 황재호 | 인포앤북 | 2021.11.01<br>
페이지 464 | ISBN 9791192038001