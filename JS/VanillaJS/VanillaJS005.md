# JS - VanillaJS
## 2022-10-22 Sat

### element 가져오기

* getElementById
  - ID를 통해 element를 가져오고 변경할 수 있다.
  - 더 많은 element를 가져와야할 때는 `getElementByClassName`를 사용한다.
  ```
    <h1 class="hello">Mindani!</h1>
    <h1 class="hello">Mindani!</h1>
    <h1 class="hello">Mindani!</h1>
    <h1 class="hello">Mindani!</h1>
    <h1 class="hello">Mindani!</h1>

  const hellos = document.getElementsByClassName("hello");
  ```
* tagName
```
  <div class="hello">
    <h1>Grab me!</h1>
  </div>

const title = document.getElementsByTagName("h1");
```

* `querySelector`
  - element를 `CSS 방식`으로 검색할 수 있다. 
  ```
    <div class="hello">
      <h1>Grab me!</h1>
    </div>

  const title = document.querySelector(".hello h1");
  ```

* getElementByClassName와 querySelector
   - `getElementByClassName`은 calssName이란 것을 알기 때문에 이름만 작성하면 된다.
  ```
  const hellos = document.getElementsByClassName("hello");
  ```
  - `querySelect`는 className이란 것을 명시해주어야 한다.
  ```
  const title = document.querySelector("#hello");
  ```
  ```
  const title = document.querySelector("div h1");
  ```
  - `h1만 가져오거나 id 하위의 form을 가져오는 것`들은 getElementById로 할 수 없다.
  ```
  const title = document.querySelector("#hello form");
  ```
 
* querySelectAll
  -  `querySelect`는 element를 return하기 때문에 가장 최우선의 하나만 가져온다.
  -  모두 가져오고 싶다면 `querySelectorAll`을 사용한다.