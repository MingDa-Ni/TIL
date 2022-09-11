# HTML - Basic
## 2022-09-11 Sun

### 문서의 구조
   1. 웹 페이지 제목
   ```
   <title>웹 페이지 제목</title>
   ```

   2. 글자가 깨지는 경우
  
  * 글자는 0과 1로 저장되기 때문에, 어떻게 저장할 지에 관한 버전이 여러가지이다.
  * 웹 브라우저에게 웹 페이지를 이 방식으로 열라고 지시할 때
   ```
   <meta charset="utf-8">
   ```

  - charset의 char은 `캐릭터`를, set은 `집합`을 가리킨다.

   3. 본문과 머리
  * HTML의 본문은 `<body>`라는 태그로 묶기로 약속했다.
  * 본문을 설명하는 태그는 `<head>`로 묶기로 약속했다. 
  * HTML의 모든 태그는 `<head>`와 `<body>` 위의 `<html>` 태그 아래에 놓인다.
   ```
   <html>
    <head>
      <title>MINDA2-HTML</title>
      <meta charset="utf-8">
    </head>
    <body>
      ... 생략 ...
    <body>
  </html>
  ```

### HTML의 사용 설명서
 * W3C에서 권고하는 W3C Recommendation이라는 `html specification(HTML 설명서)`

### 링크
 * HTML의 약자인 `HyperText Markup Language`의 HyperText가 가리키는 것
 * 정보의 바다에 정박한다는 anchor의 첫 글자를 딴 `<a>`
 * 링크를 걸고 싶은 곳을 `<a>` 태그로 감싸면 된다.
```
<a>밍다니의 하루 (MingHa)</a>
```
  1. 주소를 걸지 않았기 때문에 링크가 걸리지 않는다.
  2. 하이퍼텍스트의 첫 글자 h와 값을 참조하라는 의미의 ref를 따서 `href`라는 속성에 지정한다.
```
<a href="https://blog.naver.com/clava735"> 밍다니의 하루 (MingHa)</a>
```
 * 링크를 클릭했을 때 `새 탭에서 열리게` 만들고 싶다면
```
<a href="https://blog.naver.com/clava735" target="_blank"> 밍다니의 하루 (MingHa)</a>
```
 * 링크를 클릭하기 전에 `툴팁처럼 무엇인가`를 알려주고 싶다면
```
<a href="https://blog.naver.com/clava735" target="_blank" title="Minda blog"> 밍다니의 하루 (MingHa)</a>
```