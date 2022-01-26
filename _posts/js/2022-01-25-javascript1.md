---
title: "Javascript 기초"
excerpt: "변수, 연산자, 조건문, 반복문, 함수"
last_modified_at: 2022-01-25T18:03:16-19:00
categories:
  - Javascript
tags:
  - Javascript
  - WEB
toc: true
toc_sticky: true
toc_label: "Javascript"
---

## 자바스크립트

자바스크립트는 사용자의 마우스 조작에 따라 해당 이미지를 교체하거나 이미지 애니메이션, 폼 양식처리, 마우스나 키보드의 다양한 이벤트 처리등 동적인 웹을 위하여 사용됩니다.


## 변수

```javascript
var a;
let b;
const c;
a = 3;
b = 6
c = 7;
```

위와 같이 자바스크립트의 변수에는 let, var, const가 있습니다. const는 말그대로 상수로써 값을 초기화하면 변경할 수 없습니다. 그렇다면 let과 var의 차이는 무엇일까요?
<br>

### 변수의 스코프

- 전역변수

코드 전체에서 사용할 수 있는 변수입니다.

- 지역변수

해당 코드블록에서만 사용할 수 있는 변수입니다. 블록은 대부분 {} 로 나눠집니다.
<br>

```javascript
var str1 = 'var';
let str2 = 'let';

console.log(this.str1);
console.log(this.str2);

function run() {
  console.log(this.str1);
  console.log(this.str2);
}

run();
```

![image](https://user-images.githubusercontent.com/72953874/151108074-75c79009-e441-4fb9-8929-bc136676ea5c.png)

this는 window를 가리킵니다. 따라서 this.변수를 사용하게 되면 전역변수를 가리키게 됩니다. 사진을 보시면 var은 출력이 되지만 this.str2는 undefined로 출력되지 않는 것을 볼 수 있습니다. var은 전역변수이며 let은 전역변수가 아닙니다.
따라서 되도록이면 let을 사용하는 것을 권장한다고 하네요ㅎㅎ

<br>

### 변수타입

|제목|내용|
|---|---|
|숫자형|정수, 실수, 지수 표현등 모든 숫자 형태의 데이터를 표현하는 자료형|
|문자형|문자, 숫자, 기호, 특수문자의 모음을 작음 따옴표, 큰 따옴표로 감싸서 표현하는 자료형|
|불리언형|참(true)/거짓(false) 두가지 값 만을 가지는 자료형|
|심볼형|ES6에서 추가된 자료형으로 뒤에서 설명하겠습니다.|
|null|빈 값을 의미합니다. 변수는 선언되었지만 값이 초기화 되지 않은 상태입니다.|
|undefined|변수 자체가 선언되지 않은 것입니다.|

숫자형, 문자형, 불리언형, null, defined는 다들 아실 것같고, 심볼형에 대해서 알아봅시다.
<br>

#### 심볼

```javascript
let symbol1 = Symbol('key');
let symbol2 = Symbol('key');

console.log(typeof(symbol1));
console.log(symbol1 == symbol2);

let obj = {};
obj[symbol1] = 'value';
obj[symbol2] = 'value';

console.log(obj[symbol1] === 'value');
console.log(obj[symbol2] === 'value');
console.log(obj[symbol1] === obj[symbol2]);
```

![image](https://user-images.githubusercontent.com/72953874/151116878-3be869b7-d56f-4f14-bb72-222f7cba8967.png)

심볼은 문자열 인자를 받아 고유한 키 값을 생성합니다. 같은 인자를 넘겨도 다른 키 값이 생성되기 때문에 실행할 때마다 다른 값이 필요할 때 사용할 수 있습니다.
<br>

### 배열

```javascript

let colors = ["빨강", "노랑", "파랑"];

```

배열은 위와 같이 하나의 변수로 여러 개의 데이터 값을 저장할 수 있는 데이터형입니다.

<br>




### 자료형의 변환

자료형의 변환, 또는 형 변환, 타입 캐스팅이라고 합니다.


|연산자|우선순위|형 변환 규칙|
|---|---|---|
|+|문자열|문자열 + 문자열은 문자열 합치기<br> 문자열 + 숫자인 경우 숫자 -> 문자열로 변환<br>|
|-,*,/|숫자|숫자로 형 변환이 가능한 경우 모든 경우에 문자열 -> 숫자로 변환<br> 문자열 -> 숫자형 변환이 불가능 한 경우에는 NaN을 반환|

<br>

|제목|내용|
|---|---|
|parseInt()|정수형으로 강제 형 변환|
|parseFloat()|실수형으로 강제 형 변환|
|toString()|문자열로 강제 형 변환|

<br>



## 연산자

### 산술연산자

- 더하기(+)

- 빼기(-)

- 곱하기(*)

- 나누기(/)

- 나머지(%)

- 제곱(**)

- 증가,감소(++/--)

### 비교연산자

- 값이 같음(==)

- 값이 다름(!=)

- 값과 타입이 같음(===)

- 값이나 타입이 다름(!==)

### 논리연산자

- AND(&&)

- OR(||)

- NOT(!)

## 조건문

- if문

```javascript
if (조건절1){
  참 실행구문
} else if(조건절2){
  참 실행구문
} else {
  거짓 실행구문
}
```
<br>

- switch문

```javascript
switch (조건변수){
  case 조건절1:
    실행구문1;
    break;
  case 조건절2:
    실행구문2;
    break;
  default:
    나머지 실행구문3
    break;
}
```

스위치의 경우 조건이 true일시 해당 실행구문부터 아래로 전부 실행하기 때문에 break를 써줘서 해당 실행구문만 실행하도록 해야합니다. <br>
break문이 무엇인지는 아래서 설명드리겠습니다.

<br>

## 반복문

- for문

```javascript
for(시작값; 조건문; 간격조건){
  실행구문
}
```

<br>

- while문

```javascript
while(조건식) {
  문장1;
  문장2;
}
```

<br>

- do while문

```javascript

do {
  문장1;
  문장2;
} while(조건문);

```
do while문은 일단 한번은 실행되고 난 후, 조건문을 확인하여 실행여부를 결정하지만 while문은 조건문을 확인하고 실행할지 말지 결정합니다. 즉, do while문은 어떤 경우라도 한번은 실행됩니다.

<br>

- break문

```javascript
for(let i=1; i<=5; i++){
  console.log(i);
  if (i===2) {
    break;
  }
}
```

![image](https://user-images.githubusercontent.com/72953874/151121851-1225a8b9-89fb-424f-9ea7-0e60033c3bb4.png)


위의 이미지를 보시면 for문과 console.log에 의해서 i는 1에서 5까지 출력돼야하지만 2까지밖에 출력되지 않았습니다. 왜그럴까요?<br>
break문에 의해서 i가 2일때 루프문을 빠져나왔기 떄문입니다. 이렇게 break는 루프를 빠져나갈때 사용됩니다.

<br>

- continue

```javascript
for(let i=1; i<=5; i++){
  if (i===2) {
    continue;
  }
  console.log(i);
}
```

![image](https://user-images.githubusercontent.com/72953874/151122193-c9469696-b4cc-4d76-a347-3a465ceeb59b.png)

이번에는 2만 제외하고 출력됐습니다. continue는 이렇게 하나의 반복을 건너뛰고 다음 반복을 실행하게 합니다.

<br>


## 함수

### 함수란?
컴퓨터 프로그래밍 언어에서 함수는 영어로 "function"이라고 합니다.. function은 '기능', '역할' 이라는 의미입니다.. 쉽게 말해 함수는 어떤 역할을 수행하는 것을 말합니다.

<br>

### 함수의 종류

- 내장함수

자바스크립트 자체에서 그 기능을 내장하고 있는 함수입니다. 예를들어 alert(), write(), Number() 같은 함수가 있습니다.
<br>
alert()함수<br>

![image](https://user-images.githubusercontent.com/72953874/151122814-3afe250c-39cc-4c54-b891-4066de75b7dc.png)
<br>

write()함수<br>
![image](https://user-images.githubusercontent.com/72953874/151122940-0c015ff4-6010-4ccb-9f76-6ae8ac00e0e9.png)

![image](https://user-images.githubusercontent.com/72953874/151122974-25c289a2-7c23-4113-a3ac-c5cd044829c1.png)
<br>
Number()함수
<br>
![image](https://user-images.githubusercontent.com/72953874/151123028-0a5b03c9-f5d7-4c5a-b3dd-c89a35e7ff76.png)




<br>
- 사용자 정의 함수

```javascript
function 함수명(){ //함수 정의
  함수 기능;
}

함수명(); //함수 호출
```

말 그대로 사용자가 스스로 정의해서 사용하는 함수입니다. 예를들어 안녕하세요를 출력해주는 함수를 만들어 봅시다.

```javascript
function printHello(){ //함수 정의
  console.log("안녕하세요");
}

printHello(); //함수 호출
```

![image](https://user-images.githubusercontent.com/72953874/151123398-c357b30f-c3b0-4316-9b37-8c01d579ff62.png)

이런식으로 사용 가능합니다!

<br>

### 매개변수

- 매개변수란?
함수에게 특정 데이터를 전달하기 위해 사용되는 것입니다.

- 사용예시
```javascript
function printHello(message){ 
  console.log(message);
}

let anything = "아이고 힘들다";
printHello(anything); 
```

![image](https://user-images.githubusercontent.com/72953874/151123650-68e57f90-561a-4f8c-b60f-2f9db794351e.png)

단순히 안녕하세요가 아닌, 매개변수로 전달한 문자열을 출력한 것을 보실 수 있습니다.

<br>

### 함수 값의 반환

자바스크립트에서 사용되는 함수는 변수와 마찬가지로 함수 자체가 값을 가질 수 있습니다. 백문이 불여일타! 한번 써봅시다.

```javascript
function printHello(num1){ 
  return num1 + 5;
}

let num = 3;
console.log(printHello(num));
```
![image](https://user-images.githubusercontent.com/72953874/151123993-4bf585a5-2482-4e66-95ee-5d987780443e.png)

printHello(num)이라는 함수가 8의 값을 갖네요?! 이처럼 함수값은 return으로 정해집니다. 매개변수로 받은 num의 값이 3이고 return이 num1 + 5 였으므로 3+5인 8을 갖게 되는 것 입니다.

<br>

### 익명함수
익명함수란 말 그대로 이름이 없는 함수를 의미하며 다음과 같은 형식으로 사용됩니다.


```javascript
let 변수명 = function() {
  문장1;
  문장2;
}

변수명();
```

역시 백문이 불여일타. 한번 사용해봅시다.

```javascript
let add = function(num1, num2) {
  return num1 + num2;
}

console.log(add(2, 4));
```

![image](https://user-images.githubusercontent.com/72953874/151124749-183375a1-33f7-4c2c-b579-995d5a6783db.png)

네.. 뭐 설명할 것도 없이 쉽죠??<br>
<br>
 물론 위에 설명한 내용들이 다는 아닙니다. for~of 문법도 있고 더 많은 내용들이 있으나 다 설명드릴 수는 없기에 모르는 것은 서치해가며 공부합시다!
<br>

 ## 참고문헌

![image](https://user-images.githubusercontent.com/72953874/151125239-2aa121d5-f6d4-4c4d-a371-1053cfce9746.png)

저자 어포스트 | 어포스트 | 2020.08.13<br>
페이지 442 | ISBN 9791197122804<br>
