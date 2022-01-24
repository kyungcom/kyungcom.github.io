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
text우리는 하루에도 수백개의 웹 페이지를 드나듭니다. 그 웹페이지를 구성하는 코드중 하나가 바로 HTML입니다. <strong>HTML(Hypertext Markup Language)은 웹 페이지와 그 내용을 구조화하기 위해 사용되는 코드</strong> 즉, 컨텐츠의 구조를 정의하는 마크업 언어입니다.<br>
그래서 다수의 사람들은 HTML은 프로그래밍 언어가 아니라고 말하기도 하죠!


## 기본 태그

그렇다면 이제 HTML의 기본적인 태그들에 대해서 알아봅시다.

- 굵은 글자

```html
<strong> 내용 </strong>
```


- 밑줄

```html
<u> 내용 </u>
```

- 제목

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
단락을 어떤 방식으로 나눌 것인지 p태그는 3번째 줄과 같이 css를 첨가하여 스타일을 변경할 수 있습니다. <br>

- 이미지

```html
<img src="이미지 경로" width="100%">
```

이미지 태그 또한 css를 첨가하여 이미지 크기를 조절할 수 있습니다.<br>
이렇게 src나 width같은 것들을 <strong>속성(attribute)</strong>이라고 하는데 이들은 <strong>태그가 태그의 이름만으로는 정보가 부족할 때 사용합니다.</strong><br>


- 이미지

```html
<img src="이미지 경로" width="100%">
```

<br>

- 목록 

```html
<li> 내용1 </li>
<li> 내용2 </li>
<li> 내용3 </li>
```

<br>

- 목록간 연관성을 구분하기 위한 태그

```html
<ul>
  <li> A와 관련된 내용1 </li>
  <li> A와 관련된 내용2 </li>
  <li> A와 관련된 내용3 </li>
</ul>

<ul>
  <li> B와 관련된 내용1 </li>
  <li> B와 관련된 내용2 </li>
  <li> B와 관련된 내용3 </li>
</ul>
```
이 ul태그는 무조건 위와같이 안에 li같은 태그(자식태그)를 가지고 있어야합니다. 서로 포함관게에 있을때   포함된 태그를 우리는 자식태그 라고 부릅니다.
<br>

- 목록에 숫자를 붙여주는 태그

```html
<ol>
  <li> A와 관련된 내용1 </li>
  <li> A와 관련된 내용2 </li>
  <li> A와 관련된 내용3 </li>
</ol>

<ol>
  <li> B와 관련된 내용1 </li>
  <li> B와 관련된 내용2 </li>
  <li> B와 관련된 내용3 </li>
</ol>
```
<br>글만 봐서는 이해가 되지 않을 것 같아 사진을 첨부하겠습니다.

![image](https://user-images.githubusercontent.com/72953874/150764739-c531e5ea-45ec-43c6-a50b-2edb16a3a9c8.png) <br>
위가 ol태그를 적용한 결과고 아래가 ul태그를 적용한 결과입니다. ol태그에만 목록 앞에 숫자가 붙은 것을 확인할 수 있습니다.

<br>

- 페이지 제목

```html
<title>페이지 이름</title>
```

![image](https://user-images.githubusercontent.com/72953874/150765356-311dc0f8-8dab-4cfe-a339-3aa831c4751f.png)

페이지를 열면 위에 보이는 제목을 나타내는 태그입니다.

<br>

- 한글 깨짐 방지를 위한 태그


```html
<meta charset="utf-8">
```

우리가 작성한 파일은 0과 1로 저장됩니다. 그런데 0과 1을 어떻게 저장할 것인지에 관한 여러가지 약속들이 있는데 그것에 맞춰 파일을 열기위한 코드 입니다.

<br>

- 본문을 설명을 묶는 태그

```html
<head>
  <title> 페이지 제목 </title>
  <meta charset="utf-8">
</head>
```

title태그나 meta태그처럼 페이지 내에 직접 본문으로 나타나지 않는 정보들은 head태그로 묶어 줍니다.

<br>

- 본문

```html
<body>
  <h1>제목</h1>
  <ul>
    <li>내용</li>
  <ul>
  ~~~~~~~ 내용<br>
</body>
```

위와 같이 말 그대로 페이지에 나타나는 모든 내용들은 body 태그로 묶어줍니다.

<br>

- 링크

```html
<a href="https://www.kyungcom.dev">이 글자를 누르면 이동합니다. </a>
```
앞서 언급했듯이 태그에는 속성들이 있는데 a태그는 어디로 이동할 것인지 나타내는 href와 새 탭에서 열 수 있도록 하는 target="_blank" 같은 속성 혹은 마우스 커서를 올리면 툴팁이 나타나게 하는 title="내용" 같은 속성들이 존재합니다.

<br>
<br>

마무리에 앞서 우리가 모든 태그를 다 기억하고 외워서 사용할 수는 없습니다. 헷갈리거나 모르는 태그가 나온다면 https://www.w3schools.com/html/ 같은 곳을 찾아보도록 합시다!

## 참고문헌
![image](https://user-images.githubusercontent.com/72953874/150768248-c1d7aece-4932-4d7a-903f-cbbfcf1ccea9.png)

생활코딩! HTML+CSS+자바스크립트<br>
저자 이고잉|위키북스 |2019.01.15<br>
ISBN 9791158391331