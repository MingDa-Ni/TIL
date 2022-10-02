# HTML - Basic
## 2022-10-02 Sun

### 파일로 쪼개 정리 정돈

* 서로 연관된 코드를 파일로 묶어 그루핑
* 전환 버튼을 다른 홈페이지에도 적용해야 한다.
```
<input type="button" value="night" onclick="
  nightDayHandler(this);
">
```
* 모든 페이지에 버튼을 붙여넣는다.
  - 버튼 동작에 공통적으로 들어가는 코드를 colors.js 파일을 만들어 붙여넣는다.
  - 이때, `.js` 폴더에 `<script>` 태그는 뺀다.
  - 페이지마다 `<script src="colors.js"></script>`로 동일 코드를 대신한다.
```
<head>
  <title>WEB1 - HTML</title>
  <meta charest="utf-8">
  <script src="colors.js"></script>
  <link rel="stylesheet" href="style.css"/>
</head>
```
* 파일 쪼개기의 장점
  - `모든 코드를 복사할 필요 없이` 간단하게 colors.js 파일을 포함시키면 된다.
  - 작성한 `코드 재사용`이 쉽다.
  - `가독성`이 좋아지며, `코드가 명확`해질 뿐 아니라 `코드의 의미를 파일 이름을 통해` 확인할 수 있다.
  - 한 번 다운로드한 파일은 웹 브라우저가 저장해놓기`(캐시파일)` 때문에 트래픽 절감에 도움된다.
  - 훨씬 빠르게 화면을 표시할 수 있다.
  
### 라이브러리와 프레임워크

* 다른 사람이 `이미 만든 부품으로` 빠르게 조립하는 것이 오늘날의 소프트웨어다.

* 라이브러리
  - 부품이 되는 소프트웨어를 잘 정리정돈해서 `재사용하기 쉽게` 되어 있는 장소
  - 라이브러리를 가져와서 사용하는 것
  - jQuery : 라이브러리 중 가장 유명한 곳
  - CDN : Content Delivery Network

* 프레임워크
  - 공통적으로 필요한 부분과 `기획 의도에 따라 달라지는 부분`이 있어 `수정`해야 하는 반제품
  - 프레임워크 안에 들어가서 작업

### jQuery

* CDN
  - 라이브러리를 내려받아 프로젝트에 포함시키고 업로드하면 돈이 든다.
  - 많은 라이브러리는 CDN을 통해 서버에 파일을 보관하고, 사용자는 src 속성을 통해 가져가는 방식을 취한다.
```
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
```
* jQuery
  - 처리해야 할 태그가 여러 가지 있을 때 jQuery를 이용하면 반복문을 통해 처리하지 않아도 된다.
```
var Links = {
  setColor: function(color) {
    var alist = document.querySelectorAll('a');
    var i = 0;
    while(i<alist.length) {
      alist[i].style.color = color;
      console.log(alist[i]);
      i = i + 1;
    }
  }
}
```

```
var Links = {
  setColor: function(color) {
    $('a').css('color', color);
  }
}
```
* `$('a')`는 이 `웹 페이지에 있는 모든 <a> 태그를 jQuery로 제어하겠다`라는 뜻이다.
  - 검색창에 jQuery css를 검색
  ```
  $('a').css('color', color);
  ```

* 자바스크립트와 jQuery
  - jQuery가 훨씬 더 `직관적`이다.
  - `새로운 언어가 아니며` 자바스크립트를 통해 css()라는 함수를 미리 만들어주었다.
  
