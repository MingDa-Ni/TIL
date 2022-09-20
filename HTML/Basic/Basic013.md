# HTML - Basic
## 2022-09-20 Thu

### 변수와 대입 연산자

* 변수는 `바뀔 수 있는 값`이다.
```
x=1000;
y=1;
x+y;
```
* 여기서 x, y는 `변수(variable)`이며 =는 `대입 연산자`다.
* 단, 아래의 경우는 `바뀌지 않는 상수(constant)`이기 때문에 에러 처리 된다.
```
1=2;
```
* `변수를 쓰는 이유`
  1. 하나로 축약하긴 어렵지만 공식을 사용하기 위해서이다.
  2. 특정 단어를 모두 다른 단어로 바꾸는 예시
  ``` 
  민정이는 오늘부터 미라클 모닝을 실천하기 위해 8시 30분에 일어났다.
  다른 사람은 6시부터 일어나지만, 민정이에게 8시 30분은 충분한 미라클이었다.
  그 후 민정이는 또 다시 잠을 청할까하다 다시 일어섰고, 체중계에 올라섰다.
  기분 좋은 민정이는 또 다시
  ... 생략 ...
  ```
  - `바꿀 부분을 변수로`만든다.
  ``` 
  name = '밍동망동';
  name + "이는 오늘부터 미라클 모닝을 실천하기 위해 8시 30분에 일어났다.
  다른 사람은 6시부터 일어나지만,"+name+"이에게 8시 30분은 충분한 미라클이었다.
  그 후 "+"name"+"이는 또 다시 잠을 청할까하다 다시 일어섰고, 체중계에 올라섰다.
  기분 좋은 "+name+"이는 또 다시
  ... 생략 ...
  ```
* 변수를 사용할 때는 다음과 같이 `var 키워드`를 작성하자.
```
var name = '밍동망동';
```

### 웹 브라우저 제어

* 모드 버튼을 눌러 홈페이지의 `배경색과 글씨색`을 바꾸고 싶다.
* `<body>` 태그가 페이지 전체를 감싸기 때문에 해당 태그의 스타일 속성을 `모드 변경에 의해` 바꾸고 싶다.
  - 하지만 HTML은 `한번 화면에 표시된 자신`을 바꿀 수 없는 정적 언어이다.
  - 디자인의 CSS와 동적 제어인 자바스크립트를 통해 `모드 변경`을 해야 한다.

### CSS 기초

* 특정 부분을 CSS로 꾸미고 싶은데 감쌀 태그가 없다면 `<div>`를 사용한다.
```
<p><div>JavaScript</div>
... 생략 ...
```
* 다만 `<div>` 태그는 화면 전체를 쓰기 때문에 줄바꿈 되는데, `줄바꿈되지 않는 무색무취의 태그`가 바로 `<span>` 태그이다.
```
<p><span>JavaScript</span>
... 생략 ...
```
* 클래스 선택자는 `.`을 이용하며 id 선택자는 `#`을 이용한다.
```
.js {
    font-weight: bold;
    color: red;
}
```
```
#first {
  color: green;
}
```
* 클래스(class)와 아이디(id)
  - `클래스(class)는 무언가를 그루핑`하며 `아이디(id)는 어느 한 가지 대상을 식별`한다는 의미이다.
  - id는 학번과도 같은데, 학번은 `절대 중복되지 않아야`하기 때문에 first 아이디는 그 페이지에서 더 이상 id로 사용할 수 없다.


### 제어할 태그 선택

* night / day 버튼으로 모드를 바꾸어 `글자색과 배경색`을 바꾸기
    1. `<body>` 태그에 `style 속성을 동적으로 상호작용`에 의해 넣기
    - 브라우저가 `<body> 태그를 선택`해야한다.
    - javascript select tag by css seletor 키워드를 검색한다.
    - `document.querySelector(selectors);
    ```
    var el = document.querySelector(".myclass");
    ```
    ```
    document.querySelector('body')
    ```
    2. `<body>` 태그에 `스타일 속성을 자바스크립트`로 넣는 방법
    - javascript element style
    ```
    document.getElementByid(id).style.property=new style
    ```
    ```
    document.querySelector('body').style.
    ```
    ```
    document.querySelector('body').style.backgroundColor = 'black';
    ```
    ```
    document.querySelector('body').style.color = 'white';
    ```