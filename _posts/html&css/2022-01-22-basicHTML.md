---
title: "HTML 기초"
excerpt: "기초적인 HTML을 알아보자"
last_modified_at: 2022-01-24T18:35:16-20:00
categories:
  - HTML&CSS
tags:
  - HTML
  - HyperText Markup Language
  - Web Basic
toc: true
toc_sticky: true
toc_label: "HTML 기초"
---
## HTML이란?
우리는 하루에도 수백개의 웹 페이지를 드나든다. 그 웹페이지를 구성하는 코드중 하나가 바로 HTML입니다. <strong>HTML(Hypertext Markup Language)은 웹 페이지와 그 내용을 구조화하기 위해 사용되는 코드</strong> 즉, 컨텐츠의 구조를 정의하는 마크업 언어입니다.<br>
그래서 다수의 사람들은 HTML은 프로그래밍 언어가 아니라고 말하기도 하죠!


## 기본 태그

그렇다면 이제 HTML의 기본적인 태그들에 대해서 알아보자.

- 굵은 글자
```html
<strong> 내용 </strong>
```

- 밑줄
```html
<u> 내용 </u>
```

- 제목 태그들
```html
<h1> 내용 </h1>
<h2> 내용 </h2>
<h3> 내용 </h3>
<h4> 내용 </h4>
<h5> 내용 </h5>
<h6> 내용 </h6>
```

- 줄바꿈
```html
<br>
<p> 내용 </p>
<p style="margin-top:40px;"> 내용 </p>
```
위 두 태그의 차이는 br태그는 단순한 줄바꿈이고 p태그는 paragraph 단락 변경입니다.<br>
단락을 어떤 방식으로 나눌 것인지 p태그는 3번째 줄과 같이 css를 첨가하여 스타일을 변경할 수 있습니다. 

- 이미지
```html
<img src="이미지 경로" width="100%">
```
이미지 태그 또한 css를 첨가하여 이미지 크기를 조절할 수 있습니다.<br>
이렇게 src나 width같은 것들을 <strong>속성(attribute)</strong>이라고 하는데 이들은 <strong>태그가 태그의 이름만으로는 정보가 부족할 때 사용합니다.</string>

- 목차
```html
<img src="이미지 경로" width="100%">
```