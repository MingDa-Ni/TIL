# JS - VanillaJS
## 2022-10-23 Sun

### listen event 찾기

* MDN
  - elment의 이름을 `MDN`에 검색한다.
  ```javascript
  h1 html element mdn
  ```
  - `Web APIs`
    1. javascript 관점의 HTML Heading Elment이다.
    2. 이 방식이 아니면 console.dir을 통해 모든 event를 찾는다.
    3. 이때, on이 property 앞에 붙어있다면 event이다.
    4. on은 떼고 사용하면 된다.

## event를 listen하라

* event 사용의 두 가지 방법
  1. addEventListener
  ```javascript
  title.addEventListener("click", handleTitleClick);
  ```
  2. onclieck
  ```javascript
  title.onclieck = handleTitleClick;
  ```
  - addEventListener은 `removeEventListener`로도 삭제 가능하다.
  ```javascript
  title.addEventListener("mouseleave", handleMouseLeave);
  title.removeEventListener;
  ```

* window
  - 기본적으로 제공된다.
  ```javascript
  window.addEventListener("resize",handleWindowResize);
  ```
  - resize event는 창 크기를 바꿀 때 발생하는 event다.
  - 다만, window는 부분적으로 가져올 수 없고 `body, head, title 등 중요한 것`만 가져올 수 있다.