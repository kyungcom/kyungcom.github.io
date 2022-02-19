---
title: "Node.js http서버"
excerpt: "Node.js로 http서버를 만들어보자"
last_modified_at: 2022-02-19T16:03:16-23:59
categories:
  - Node.js
tags:
  - Node.js
  - Web
  - server
toc: true
toc_sticky: true
toc_label: "Node.js http서버"
---

## 서버와 클라이언트
- 서버는 클라이언트가 요청을 보내면 요청에 따른 응답을 해줍니다.
- 따라서 요청이 왔을 때 무슨 작업을 해야할지 정의해주는 이벤트 리스너를 등록해줘야합니다.
<br>

### node로 http서버 만들기

```javascript
const http = require('http');

http.createServer((req,res) => {
  res.writeHead(200, { 'Content-Type': 'text/html; charset=utf-8'});
  res.write('<h1>Hello Node!</h1>');
  res.end('<p>Hello Server!</p>');
})
.listen(8080, () => {
  console.log('8080포트에서 대기 중입니다!');
});
```

- createServer 메서드 뒤에 listen 메서드를 붙이고 클라이언트에 공개할 포트 번호와 포트 연결 완료 후 실행될 콜백 함수를 넣습니다.
- res객체는 res.writeHead와 res.write, res.end 메서드가 있습니다.
- res.writeHead는 응답에 대한 정보를 기록하는 메서드입니다.
- res.write는 클라이언트로 보낼 데이터입니다.
- res.end는 응답을 종료하는 메서드입니다.

<br>

![image](https://user-images.githubusercontent.com/72953874/154795081-0cc215a2-2f46-4518-8668-89fb50f5bbec.png)

- localhost는 현재 컴퓨터의 내부 주소를 가리킵니다. 외부에서는 접근 불가능합니다.
- 포트는 서버 내에서 프로세스를 구분하는 번호입니다. http의 경우 보통 80번입니다.

<br><br>

- listen메서드에 콜백함수를 넣는 대신, listening이벤트 리스터를 붙여도 됩니다.

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/html; charset=utf-8'});
  res.write('<h1>Hello Node!</h1>');
  res.end('<p>Hello Server!</p>');
});

server.listen(8080);

server.on('listening', () => {
  console.log('8080번 포트에서 대기중입니다.');
});

server.on('error', (error) => {
  console.error(error);
});
```

<br><br>

### Rest

1. Rest란?
- REpresentational State Transfer의 줄임말이며, 서버의 자원을 정의하고 자원에 대한 주소를 지정하는 방법을 가리킵니다.

2. HTTP 요청 메서드
- GET: 서버 자원을 가져오고자 할 때 사용합니다. 요청의 본문에 데이터를 넣지않고 쿼리스트링을 사용합니다.
- POST: 서버에 자원을 새로 등록하고자 할 때 사용합니다. 요청의 본문에 새로 등록할 데이터를 넣어 보냅니다.
- PUT: 서버의 자원을 요청에 들어있는 것으로 치환하고자 할 때 사용합니다.요청의 본문에 치환할 데이터를 넣어 보냅니다.
- PATCH: 서버 자원의 일부만 수정하고자 할 때 사용합니다.요청의 본문에 일부 수정할 데이터를 넣어 보냅니다.
- DELETE: 서버의 자원을 삭제하고자 할 때 사용합니다. 본문에 데이터를 넣지 않습니다.
- OPTIONS: 요청을 하기 전에 통신 옵션을 설명하기 위해 사용합니다.


## 참고문헌

![image](https://user-images.githubusercontent.com/72953874/151500796-1e8c34c5-23fb-45d0-bbc7-20693430e9d7.png)

저자 조현영 | 길벗 |2020.07.25
페이지 756 | ISBN 9791165212308|개정 2판