---
title: "Javascript 객체"
excerpt: "객체에 대해서 알아보자"
last_modified_at: 2022-01-27T12:03:16-13:00
categories:
  - Javascript
tags:
  - Javascript
  - Object
toc: true
toc_sticky: true
toc_label: "Javascript"
---

## 객체란?

자바스크립트는 객체 기반의 언어이며 자바스크립트를 이루고 있는 거의 모든 것이 객체입니다. 숫자, 문자열, 함수, 배열 등도 모두 객체를 기반으로 합니다.<br>
자바스크립트의 객체는 속성과 메소드로 구분되는데, 속성은 객체에 붙어있는 변수이며, 메소드는 객체에 붙어있는 함수입니다.<br>
하나의 객체는 데이터를 의미하는 속성과 데이터를 처리하는 기능을 가진 메소드의 집합이라고 할 수 있습니다.

```javascript
var person = {
  name: "kyungcom",
  age: 25,
  sayHello: function(){
    document.write(this.name+"님 안녕하세요!");
  }
};
```

<br>

## 객체의 종류

### 사용자 정의 객체

위의 코드와 같이 사용자가 객체를 정의하여 사용하는 객체를 말합니다.
<br>


- 객체 리터럴(객체 생성 방법1)

자바스크립트에서 객체를 생성하는 가장 간단한 방법이자 많이 사용되는 방법입니다. 리터럴이란 데이터 형에 들어가는 데이터 값 자체를 의미하고, 이 방식에서는 변수를 선언할 때와 유사하게 객체에 들어가는 속성과 메소드를 직접 정의합니다.
```javascript
var 객체명 = {
  키1:값1,  //속성
  키2:값2,  //속성

  메소드1:function() { //메소드
    자바스크립트 코드
  },
  메소드2:function() { //메소드
    자바스크립트 코드
  }
};
```

<br>

- 생성자 함수와 New 연산자(객체 생성 방법2)

1. 생성자 함수를 이용하여 객체의 타입을 정의한다. 생성자 함수의 첫 글자는 반드시 영문 대문자를 사용하도록 한다.

2. new를 이용하여 객체를 생성한다.

```javascript
function Car(company, model, year){
  this.company = company;
  this.model = model;
  this.year = year;
}

var car1 = new Car("테슬라", "모델s", 2021);
```

<br>

- 객체의 속성 접근법

1. 객체명.키
2. 객체명["키"]

```javascript
var car1 = {
  name:"모델S",
  age:1
};

console.log(car1.name);
console.log(car1["age"]);
```
![image](https://user-images.githubusercontent.com/72953874/151286546-f896b8f5-fb2c-4703-8a07-6e636703e208.png)

<br>

- for문에서의 객체 사용

```javascript
var car1 = {
  name:"모델S",
  age:1
};

for(var x in car1){
  console.log(car1[x]);
}
```
![image](https://user-images.githubusercontent.com/72953874/151286692-33120197-dcd7-428e-b7db-591278d1c585.png)


<br>

### 내장 객체

자바스크립트에 기본적으로 내장되어있는 객체를 말합니다. 예를들면 배열, 숫자, 문자열, 수학, 날짜 객체들이 있습니다.<br>
예전에 소개해드린 toString() 과 같은 것들이 Number객체의 메소드이며 굳이 자세히 설명하진 않겠습니다.

<br>

### 문서 객체 모델(DOM)

문서 객체 모델은 HTML의 문서 구조를 말합니다.<br>


- DOM의 기본 구조

DOM의 구조를 알아보기위해 간단한 HTML을 살펴보겠습니다.

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Hello World!</title>
</head>
<body>
  <div>안녕하세요</div>
  <p id="hello"></p>
</body>
</html>
```
![image](https://user-images.githubusercontent.com/72953874/151287668-9e46642e-72b5-4d60-b818-b5a6e33cbebd.png)

이해가 되시나요? 이렇게 트리모양으로 구성됩니다.<br>

- 요소 내용 삽입과 CSS 조작


```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Hello World!</title>
</head>
<body>
  <div>안녕하세요</div>
  <p id="hello"></p>
  <script>
    document.getElementById("hello").innerHTML = "안녕하세요";
    document.getElementById("hello").style.color = "red";
  </script>
</body>
</html>
```
![image](https://user-images.githubusercontent.com/72953874/151287864-5ed0d7be-b8d1-44d0-b858-830a9cf27ce9.png)
<br>

- DOM 이벤트

웹 브라우저에서 DOM의 요소에 마우스를 클릭하는 것과 같은 이벤트가 발생하면 원하는 자바스크립트 코드를 실행하도록 할 수 있다.<br>

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Hello World!</title>
  <script>
    function changeText(obj){
      obj.innerHTML = "클릭하셨네요";
    }
  </script>
</head>
<body>
  <div onclick="changeText(this)">안녕하세요</div>
</body>
</html>
```

![image](https://user-images.githubusercontent.com/72953874/151288254-7649966e-d0ec-4e26-b14b-b6173f7e77e8.png)
![image](https://user-images.githubusercontent.com/72953874/151288272-3c9bc810-62a9-47d0-af54-adf25b330e8e.png)


<br>


### 브라우저 객체 모델(BOM)

자바스크립트에서 브라우저를 다루는 데 필요한 객체의 모델. Window, Screen, Location, History, Navigator 등이 있습니다.<br>
여기서 자세히 알아보진 않겠습니다.

<br>


## 참고문헌

![image](https://user-images.githubusercontent.com/72953874/151288663-06e5edaa-1585-4511-8413-b4e23b264bb2.png)

저자 황재호 | 인포앤북 | 2021.11.01<br>
페이지 464 | ISBN 9791192038001