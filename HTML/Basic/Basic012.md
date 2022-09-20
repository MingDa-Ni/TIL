# HTML - Basic
## 2022-09-20 Tue

### 자바 스크립트

* HTML은 정적이기 때문에 `웹 페이지도 사용자와 상호작용할 수 있게` 만들어 진 것이 `자바 스크립트(JavaScript)`이다.
* 웹 페이지는 한 번 `출력된 화면을 바꾸는 능력`이 없기 때문에, 그것을 가능하게 해주는 것이 `자바 스크립트`다.
  - 웹 페이지 - 개발자 도구(F12) - Elements 탭은 `웹 페이지를 구성하는 HTML 태그`를 보여준다.
  - `Elements`는 태그를 나타낸다. 
* 버튼을 눌러 모드를 바꾸는 기능
  1. `<input>` 태그는 속성으로 `button`을 지정하면 버튼이 되며, value에 버튼의 이름을 적을 수 있다.
  ```
  <input type="button" value="Minda">
  ```
  2. onclick 속성에 자바스크립트 코드를 넣으면 `버튼을 클릭했을 때` 그 코드가 실행된다.
  ```
  <input type="button" value="night" onclick="
   document.querySelector('body').style.backgroundColor = 'black';
   document.querySelector('body').style.color = 'white';
  ">
  ```
  3. 위의 코드에서 `<body>` 태그를 선택하는 코드가 `document.querySelector('body')`이다.
  4. 그리고 그 `<body>` 태그에 style 속성 값으로 black을 지정한다.
  ```
  .style.background='black'
  ```
* `style 속성값으로는 반드시 CSS 코드가 온다.`
<br><br>
* 자바스크립트는 `사용자와 상호작용하는 언어`이다.
* 자바스크립트는 `HTML을 제어하는 언어`이다.

### `<script> 태그`

* 기본적으로 자바스크립트는 `HTML 위에서 동작하는 언어`이다.
* 웹 브라우저에게 자바스크립트 코드가 시작된다는 사실을 알리는 태그가 `<script>` 태그이다.
```
<body>
  <script>
    document.write('hello world');
  </script>
</body>
```
* HTML과 차이가 있는 것은, 자바스크립트는 동적이지만 HTML은 정적이라는 것이다.
```
<body>
  <script>
    document.write(1+1);
  </script>
  1+1
</body>
```

### 이벤트

* 이벤트는 자바스크립트가 `사용자와 상호작용하는 핵심적인 역할`을 한다.
* `웹 브라우저에서 일어나는 일`을 사건(event)라고 부른다.
<br><br>
* 경고창을 띄울 때 : javascript alert
    1. 이벤트가 일어났을 때 `어떠한 자바스크립트 코드를 실행하게` 하는 것
  ```
   onclick="alert('Hello! I am an alert box!!');
  ```
* 글자를 입력하려 할 때 

  1. 글자를 입력하고 `내용이 변했을 때를 체크하는` 이벤트
  ```
  <input type="text onchange="alert(`changed')">
  ```
  2. 사용자가 키를 입력했을 때 이벤트를 발생
  ```
  <input type="text" onkeydown="alert('key down!')">
  ```

* 이처럼 이벤트는 `on으로 시작하는 속성`이며, 이런 속성을 `이벤트`라고 정의한다.


### 콘솔

* 파일이 아니라 `간단하게 어떤 코드를 실행해야 하는 상황들`에 콘솔을 사용한다.
  - 웹 페이지 - 개발자도구(F12) - Console 탭을 눌러 사용한다.
  <br><br>
* 텍스트의 글자수를 헤아릴 때
```
JavaScript (JS) is a lightweight, interpreted, or just-in-time compiled programming language with first-class functions. While it is most well-known as the scripting language for Web pages, many non-browser environments also use it, such as Node.js, Apache CouchDB and Adobe Acrobat. JavaScript is a prototype-based, multi-paradigm, single-threaded, dynamic language, supporting object-oriented, imperative, and declarative (e.g. functional programming) styles. Read more about JavaScript.
```
  1. 문자를 `' '`로 묶으면 그 안의 것들은 문자가 된다.
  2. 문자의 개수를 알려주는 명령어는 `.lenth`이다.
  ```
  alert('JavaScript (JS) is a lightweight, interpreted, or just-in-time compiled programming language with first-class functions. While it is most well-known as the scripting language for Web pages, many non-browser environments also use it, such as Node.js, Apache CouchDB and Adobe Acrobat. JavaScript is a prototype-based, multi-paradigm, single-threaded, dynamic language, supporting object-oriented, imperative, and declarative (e.g. functional programming) styles. Read more about JavaScript.'.length);
 ```
  3. 이 모든 것을 alert()로 감싸면 된다.


### 문자열과 숫자

* 자바스크립트에는 `6개의 데이터 타입`이 있고 `객체`가 있다.
* 숫자(Number)
  1. 해당 타입에서 중요한 것은 `연산`이다.
  2. `+`는 왼쪽의 값과 오른쪽의 값을 더해 하나를 만들기 때문에 `이항 연산자`이다.
  3. 개중 산수를 하는 경우는 `산술 연산자`라고도 부른다.
  <br><br>
* 문자열
  1. `문자열`은 `따옴표(" ")`로 이루어져 있다.
  2. `작은 따옴표(' ')`도 무방하다.
  3. 산술 연산자처럼 문자열에도 유용한 기능이 있는데 `Javascript String`을 검색하면 된다.
  ```
  .length
  ```
  4. 이런 것들을 `프로퍼티(Properties)`라고 한다.
   <br><br>
  - 그 밖의 여러가지 메서드
  ```
  'Hello World'.toUpperCase()
  ```
  1. 결과를 `모두 대문자로 출력`해준다.
  ```
  'Hello World'.indexOf('o')
  ```
  2. `찾고자 하는 값`을 찾아준다. 이때, 숫자의 시작은 0이며 공백도 포함한다.