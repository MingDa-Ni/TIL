# JS - VanillaJS
## 2022-10-23 Sun

## className 수정

* className을 바꾸게 되면 본래 className은 잃는다.
  - `classList`를 이용하면 과거와 현재를 모두 얻을 수 있다.

### classList
* classList
  - class 목록을 가져간다.
  - `contains function`을 이용 
    - 명시한 것이 class에 포함되었는지 알려준다.
  ```javascript
  if(h1.classList.contains(clickedClass)){
  }
  ```

### toggle function

* toggle
  - class name이 존재하는지 확인한다.
    - `존재`하면 toggle을 `제거`한다.
    - 존재하지 `않으면 toggle을 추가`한다.
  ```javascript
  function handleTitleClick(){
    h1.classList.toggle('clicked');
  }
  ```