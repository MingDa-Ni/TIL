# JS - VanillaJS
## 2022-10-22 Sat

### element 찾기

* 대전제
  - app.js가 import 되었기 때문에 가능
  ```
  <script src='app.js'></script>
  ```
    1. app.js 덕분에 javascript가 html을 가져올 수 있다.
    2. app.js를 import한다.
    3. document가 html이 app.js를 load하기 때문에 존재한다.
    4. 브라우저가 document에 접근할 수 있게 한다.

* event
  - object의 속성에 대한 내용 전부를 보고 싶다면 `console.dir`을 사용한다.
  ```
  console.dir(object);
  ```
  - on으로 시작하는 것은 모두 이벤트다.
    1. 마우스를 올린다.
    2. 입력을 끝낸다.
    3. 이름을 적는다.
    4. enter를 누른다.
 
* `event listen`
  1. element 가져오기
  ```
  const title = document.querySelector("div.hello:first-child h1");
  ```
  2. `click event`
  ```
  function handleTitleClick(){
    console.log("title waw clicked!");
  }

  title.addEventListener("click", handleTitleClick);
  ```
   - ()를 넣으면 실행버튼이 되니까 생략한다.
   - handleTitleClick()이 아니라 handleTitleClick
