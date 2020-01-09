# docker 예제
## 환경
```shell
[~/day01/simpleweb] # node --version
v13.3.0
```

## `node express` 기초

> `./simpleweb/package json`
```json
{
    "dependencies": {
        "express": "*"
    },
    "scripts": {
        "start": "node index.js"
    }
}

```

> `./simpleweb/index.js`
```js
const express = require('express');
const app = express();

app.get('/', (req, res) => {
    res.send('Hi, there!');
});

app.listen(8080, () => {
    console.log('listening on port 8080');
});
```

## node package 설치
`npm install` 명령어 만으로 `package.json` 을 조회하여 패키지 및 의존성 패키지까지 함께 설치됨
```shell
[~/day01/simpleweb] # npm install
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN simpleweb No description
npm WARN simpleweb No repository field.                   kages in 4.605s
npm WARN simpleweb No license field.
added 50 packages from 37 contributors and audited 126 packages in 4.605s
found 0 vulnerabilities
```

## console 에서 webserver 실행
```shell
[~/day01/simpleweb] # npm start

> @ start ~/day01/simpleweb
> node index.js

listening on port 8080

```

```shell
# docker ps
CONTAINER ID        IMAGE                     COMMAND                  CREATED             STATUS              PORTS                    NAMES
b181c5331252        ppojin/simpleweb:latest   "docker-entrypoint.s…"   3 minutes ago       Up 3 minutes        0.0.0.0:9000->8080/tcp   clever_morse
# curl http://localhost:8080/


StatusCode        : 200
StatusDescription : OK
Content           : Hi, there!
RawContent        : HTTP/1.1 200 OK
                    Connection: keep-alive
                    Content-Length: 10
                    Content-Type: text/html; charset=utf-
                    8
                    Date: Tue, 07 Jan 2020 05:01:07 GMT
                    ETag: W/"a-VUVkH3QcE6VHXLkL5R4PgVIefU
                    E"
                    X-Powered-By: Express...
Forms             : {}
Headers           : {[Connection, keep-alive], [Content-L
                    ength, 10], [Content-Type, text/html;
                     charset=utf-8], [Date, Tue, 07 Jan 2
                    020 05:01:07 GMT]...}
Images            : {}
InputFields       : {}
Links             : {}
ParsedHtml        : mshtml.HTMLDocumentClass
RawContentLength  : 10
```

```shell
[~/day01/simpleweb/] # docker build -t ppojin/simpleweb:latest .
```

## docker 로 webserver 실행
```shell
# docker run -t -p 9000:8080 ppojin/simpleweb:latest

> @ start /
> node index.js

listening on port 8080

```

```shell
# curl http://localhost:9000/


StatusCode        : 200
StatusDescription : OK
Content           : Hi, there!
RawContent        : HTTP/1.1 200 OK
                    Connection: keep-alive
                    Content-Length: 10
                    Content-Type: text/html; charset=utf-8
                    Date: Tue, 07 Jan 2020 06:20:25 GMT
                    ETag: W/"a-VUVkH3QcE6VHXLkL5R4PgVIefUE"
                    X-Powered-By: Express...
Forms             : {}
Headers           : {[Connection, keep-alive], [Content-Length, 10], [Content-Type, text/html; charset=utf-8], [Date, Tue, 07 Jan 20
                    20 06:20:25 GMT]...}
Images            : {}
InputFields       : {}
Links             : {}
ParsedHtml        : mshtml.HTMLDocumentClass
RawContentLength  : 10

```