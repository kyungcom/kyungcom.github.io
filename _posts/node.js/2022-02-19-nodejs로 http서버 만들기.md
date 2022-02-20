---
title: "Node.js http서버"
excerpt: "Node.js로 http서버를 만들어보자"
last_modified_at: 2022-02-20T16:03:16-23:59
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

### 쿠키와 세션

1. 쿠키란?
서버가 클라이언트가 누구인지 기억하기 위해서 키-값 쌍으로 이루어진 데이터들을 클라이언트에 보내고, 클라이언트는 요청시에 쿠키를 보내 자신이 누구인지 알리는 데 사용됩니다.
<br> 쿠키는 요청의 헤더에 담겨 전송됩니다.

- 쿠키명 = 쿠키값: 기본적인 쿠기의 값입니다.
- Expires= 날짜: 만료 기한입니다. 기본값은 클라이언트가 종료될 때 까지 입니다.
- Max-age=초: 해당 초가 지나면 쿠키가 제거됩니다.
- Domain=도메인명: 쿠키가 전송될 도메인을 특정할 수 있습니다.
- Path=URL: 쿠키가 전송될 URL을 특정할 수 있습니다.
- Secure:HTTPS일 경우에만 쿠키가 전송됩니다.
- HttpOnly:설정 시 자바스크립트에서 쿠키에 접근할 수 없습니다.

2. 세션이란?
- 쿠키에는 세션에 접근을 위한 키를 보내고, 그 키를 이용하여 서버 내에 세션을 조회하여 사용자를 확인하는 방법
<br>

- 예시

```javascript
const http = require('http');
const fs = require('fs').promises;
const url = require('url');
const qs = require('querystring');

const parseCookies = (cookie = '') =>
  cookie
    .split(';')
    .map(v => v.split('='))
    .reduce((acc, [k, v]) => {
      acc[k.trim()] = decodeURIComponent(v);
      return acc;
    }, {});

const session = {};

http.createServer(async (req, res) => {
  const cookies = parseCookies(req.headers.cookie);
  if (req.url.startsWith('/login')) {
    const { query } = url.parse(req.url);
    const { name } = qs.parse(query);
    const expires = new Date();
    expires.setMinutes(expires.getMinutes() + 5);
    const uniqueInt = Date.now();
    session[uniqueInt] = {
      name,
      expires,
    };
    res.writeHead(302, {
      Location: '/',
      'Set-Cookie': `session=${uniqueInt}; Expires=${expires.toGMTString()}; HttpOnly; Path=/`,
    });
    res.end();
  // 세션쿠키가 존재하고, 만료 기간이 지나지 않았다면
  } else if (cookies.session && session[cookies.session].expires > new Date()) {
    res.writeHead(200, { 'Content-Type': 'text/plain; charset=utf-8' });
    res.end(`${session[cookies.session].name}님 안녕하세요`);
  } else {
    try {
      const data = await fs.readFile('./cookie2.html');
      res.writeHead(200, { 'Content-Type': 'text/html; charset=utf-8' });
      res.end(data);
    } catch (err) {
      res.writeHead(500, { 'Content-Type': 'text/plain; charset=utf-8' });
      res.end(err.message);
    }
  }
})
  .listen(8085, () => {
    console.log('8085번 포트에서 서버 대기 중입니다!');
  });
```
<br><br>

### https와 http2

1. https란?
웹 서버에 SSL 암호화를 추가한 모듈입니다. GET이나 POST요청을 할 때 오가는 데이터를 암호화해서 중간에 다른 사람이 요청을 가로채더라도 내용을 볼 수 없습니다.<br>
https를 이용하려면 인증기관에소 인증서를 구입해야합니다.

```javascript
const https = require('https');
const fs = require('fs');

https.createServer({
  cert: fs.readFileSync('도메인 인증서 경로'),
  key: fs.readFileSync('도메인 비밀키 경로'),
  ca: [
    fs.readFileSync('상위 인증서 경로'),
    fs.readFileSync('상위 인증서 경로'),
  ],
}, (req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/html; charset=utf-8' });
  res.write('<h1>Hello Node!</h1>');
  res.end('<p>Hello Server!</p>');
})
  .listen(443, () => {
    console.log('443번 포트에서 서버 대기 중입니다!');
  });
```

<br><br>

2. http2란?
HTTP/2는 Multiplexed Streams를 이용하여 Connection 한 개로 동시에 여러 개의 메시지를 주고 받을 수 있으며 응답은 순서에 상관없이 Stream으로 주고 받습니다. HTTP/1.1의 Connection Keep-Alive, Pipelining의 개선 버전이라 보면 됩니다.<br>

```javascript
const http2 = require('http2');
const fs = require('fs');

http2.createSecureServer({
  cert: fs.readFileSync('도메인 인증서 경로'),
  key: fs.readFileSync('도메인 비밀키 경로'),
  ca: [
    fs.readFileSync('상위 인증서 경로'),
    fs.readFileSync('상위 인증서 경로'),
  ],
}, (req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/html; charset=utf-8' });
  res.write('<h1>Hello Node!</h1>');
  res.end('<p>Hello Server!</p>');
})
  .listen(443, () => {
    console.log('443번 포트에서 서버 대기 중입니다!');
  });
```

<br><br>

### cluster

- 싱글 프로세스로 동작하는 노드가 cpu의 코어를 모두 사용할 수 있게 해주는 모듈입니다.

## 참고문헌

![image](https://user-images.githubusercontent.com/72953874/151500796-1e8c34c5-23fb-45d0-bbc7-20693430e9d7.png)

저자 조현영 | 길벗 |2020.07.25
페이지 756 | ISBN 9791165212308|개정 2판