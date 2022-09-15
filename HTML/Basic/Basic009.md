# HTML - Basic
## 2022-09-15 Thu

### CSS 프로퍼티 검색

* 웹 페이지의 제목을 크기 조정과 가운데 정렬
  1. 모든 CSS를 외울 수 없기 때문에 검색 엔진 검색
  2. `css text size property` 키워드 검색
  3. CSS font-size property
```
  div.a {
    font-size: 15px;
  }
  div.b {
    font-size: 1arge;
  }
  div.c {
    font-size: 150%;
  }
```
   4. font-size를 이용한 글자 크기 변경
```
  <style>
  h1 {
    font-size: 45px;
  }
  </style>
```
- px는 `컴퓨터에서 사용하는 단위`이다.
 
  1. `css text center property` 키워드 검색
  2. CSS text-align Property
```
  div.a {
    text-align: center;
  }
  div.b {
    text-align: left;
  }
  div.c {
    text-align: right;
  }
  div.c {
    text-align: justify;
  }
```
   4. text-align을 이용한 텍스트 가운데 정렬
```
  h1 {
    font-size: 45px;
    text-align: center;
  }
```
* 모든 프로퍼티를 암기하는게 아니라 `검색`하는 능력을 키우자
  
### CSS 선택자

* 모든 `<a>` 태그를 검은색으로 바꾸고, 방문한 적 있던 페이지를 회색으로 머물고 있는 페이지는 빨간색으로 표시
```
    <ol>
      <li><a href="1.html" style="color:gray;">HTML</a></li>
      <li><a href="2.html" style="color:gray;">CSS</a></li>
      <li><a href="3.html">JavaScript</a></li>
    </ol>
```
  1. 위의 코드는 `style="color:gray;" 이라는 중복이 발생`한다. 두 텍스트를 같은 그룹으로 묶고, `class라는 HTML 속성을 지정`해야 한다.
```
    <ol>
      <li><a href="1.html" class="saw">HTML</a></li>
      <li><a href="2.html" class="saw">CSS</a></li>
      <li><a href="3.html">JavaScript</a></li>
    </ol>
```
  2. `class""와 "saw"`는 HTML이다. "saw"라는 class 값을 가지고 있는 모든 태그 중 class값을 갖고 있는 모든 태그에 'gray' 색상을 지정하는 것이다.
```
<style>
  a {
    color: black;
    text-decoration: none;
  }
  saw {
    color: gray;
  }
</style>
```
* 위의 코드는 작동하지 않는다. 단순히 "saw"라고 쓰면 그 태그를 선택하는 선택자를 나타내기 때문에 `class가 "saw"인 태그를 선택`하는 기호인 (.)을 사용해야 한다.
```
<style>
  a {
    color: black;
    text-decoration: none;
  }
  .saw {
    color: gray;
  }
</style>
```
  3. 현재 머물고 있는 페이지의 링크를 빨간색으로 표시하기 위해 active 클래스를 추가한다.
```
    <style>
    ... 생략 ...
        .saw {
        color: gray;
      }
      .active {
        color: red;
      }
    ... 생략 ...
    </style>
  </head>
  <body>
    <h1><a href="lndex.html">WEB</a></h1>
    <ol>
      <li><a href="1.html" class="saw">HTML</a></li>
      <li><a href="2.html" class="saw active">CSS</a></li>
      <li><a href="3.html">JavaScript</a></li>
    </ol>
    ... 생략 ...
```
* `class라는 속성은 여러 개가 올 수 있고, 띄어쓰기로 구분`한다.
* 여러 개의 선택자를 `공동으로 제어`할 수 있다.
```
<li><a href="2.html" class="saw active">CSS</a></li>
```
* 위의 `<a>` 태그는 두 개의 클래스에 영향을 받고 있는 문제가 생긴다.
* 태그는 `가장 최근에 명령한 사람의 우선순위가 더 높다.`

### 선택자 우선순위

* 클래스 태그보다 우선순위가 높은 것은 `ID 선택자`이다.
```
... 생략 ...
    <ol>
      <li><a href="1.html" class="saw">HTML</a></li>
      <li><a href="2.html" class="saw" id= "active">CSS</a></li>
      <li><a href="3.html">JavaScript</a></li>
    </ol>
... 생략 ...
```
* id가 "active"인 값을 선택하는 방법
```
<style>
  ... 생략 ...
  #active {
    color: red;
  }
  .saw {
    color: gray;
  }
  ... 생략 ...
</style>
```
* 선택자 우선순위는 `태그 선택자 < 클래스 선택자 < ID 선택자`이다.
* 모두 같은 형태라면 `맨 마지막 선택자의 우선순위가 가장 높다.`

### 우선순위 원리

* `권장사항 :` id 선택자 값인 active 태그는 단 한 번만 등장해야한다.
  - id 값으로 active를 썼으면 문서의 다른 곳에서 등장하면 안된다.
  - 사람들은 `더 구체적인 것의 우선순위를 포괄적인 것보다 높게` 책정했다.
* `css selector`로 검색하면 여러가지 형태의 선택자가 나온다.

### 박스 모델

* `HTML 태그 하나하나를 박스로 취급해서 부피감을 결정하는 것이다.`
<br><br>
* `<h1>`태그는 `화면 전체`를 쓰고 있고 `<a>` 태그는 `콘텐츠 크기`만큼 사용하고 있다.
```
... 생략 ...
<title></title>
<style>
  h1 {
    border-width: 5px;
    border-color: red;
    border-style: solid;
  }
  a {
    border-width: 5px;
    border-color: red;
    border-style: solid;
  }
</style>
... 생략 ...
```
* 위의 코드를 통해 `박스의 테두리`를 그린다.
   - h1처럼 화면 전체를 쓰는 태그를 `블록 레벨 엘리먼트(block lever element)`라고 한다.
   - a처럼 자기 자신의 콘텐츠 크기만큼 쓰는 태그를 `인라인 엘리먼터(inline element)`라고 한다.
* 두 속성의 기본값을 바꾸는 것은 `display` 속성이다.
```
display: inline;
```
```
display: bolck;
```
* 두 속성은 기본값일 뿐 `CSS를 통해 언제든` 바꿀 수 있다.
<br><br>

* `,`라는 선택자를 통해 `코드의 중복`을 줄일 수 있다.
* 5px, solid, red의 순서는 중요하지 않다.
```
... 생략 ...
<title></title>
<style>
  h1, a {
    border: 5px solid red;
  }
</style>
... 생략 ...
```
* 콘텐츠와 테두리 사이에 여백 추가
```
padding: 20px;
```
```
... 생략 ...
<style>
  h1 {
    border: 5px solid red;
    padding: 20px;
  }
</style>
... 생략 ...
```
* 테두리와 테두리 사이 간격 조절하기
```
margin: 0;
```
```
... 생략 ...
<style>
  h1 {
    border: 5px solid red;
    padding: 20px;
    margin: 0;
  }
</style>
... 생략 ...
```
* 박스 모델의 크기 변경하기
```
width: 100px;
```
```
... 생략 ...
<style>
  h1 {
    border: 5px solid red;
    padding: 20px;
    margin: 0;
    width: 100px;
  }
</style>
... 생략 ...
```
* 웹 페이지에서 'CSS' 텍스트를 대상으로 마우스 오른쪽 버튼 `검사`를 누른다.
  - CSS 코드가 복잡해졌을 때 `어떤 태그가 어떠한 영향`을 받는지 파악하기 위한 도구
