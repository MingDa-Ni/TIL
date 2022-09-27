# HTML - Basic
## 2022-09-26 Mon

### 프로그래밍 언어

* `HTML`과 `자바스크립트`는 둘 다 컴퓨터 언어다.
  - 자바스크립트는 프로그래밍 언어지만 HTML은 아니다.
  - `프로그램` : 음악회가 시간의 흐름에 따라 연주되는 것처럼 그러한 `순서`를 가르키는 말
  - 프로그래밍 언어 : `시간 순서에 따라 실행돼야 할 기능`을 프로그래밍 언어의 문법에 맞게 적어두는 것

### 비교 연산자와 불리언

* 비교 연산자
  - `===` 연산자는 왼쪽과 오른쪽이 같은 값인지를 판단한다.
  - 같다고 판단되면 참(true)이고 다르면 거짓(false)이다.
```
===
```
```
document.write(1===1);
``` 

* 불리언
  - ===는 `비교 연산자`인 동시에 `이항 연산자`이다. 
  - 좌항과 우항의 관계에 따라 `true` 혹은 `false` 중에 하나의 값을 만들어낸다.
  - `true와 false`라는 두가지 값을 묶어 `불리언(boolean)`이라고 한다.

* HTML에서는 `<`를 출력할 때 `&lt`(less than)이라고 써야한다.
```
<h3>1&lt;2</h3>
```

### 조건문

```
document.write("1<br>");
if(true) {
  document.write("2<br>");
} else {
  document.write("3<br>");
}
document.write("4<br>");
```
```
1
2
4
```

```
document.write("1<br>");
if(false) {
  document.write("2<br>");
} else {
  document.write("3<br>");
}
document.write("4<br>");
```
```
1
3
4
```
* if문 뒤에 따라오는 `괄호 안에는 불리언 데이터 타입`이 오는데, 불리언 값에 따라 실행되는 코드가 달라진다.

### 조건문 활용

* `하나의 버튼으로 주간/야간을 바꿀 수 있도록 구현` : 토글(toggle) 기능
  1. 버튼을 하나로 만들기
  ```
  <input type="button" value="night" onclick=" ">
  ```
  2. 현재 모드에 따라 코드가 실행되도록 하기
  ```
  <input type="button" value="night" onclick=" 
    if(night) {
      document.querySelector('body').style.backgroundColor = 'black';
      document.querySelector('body').style.color = 'white';
    } else {
      document.querySelector('body').style.backgroundColor = 'white';
      document.querySelector('body').style.color = 'black';      
    }
  ">
  ```
  3. 현재 값이 true인지 false인지 확인하기
  - 개발자 도구 - 맨 왼쪽의 아이콘 - 버튼에 해당하는 코드 클릭 - [Edit as HTML] - id 속성 추가 : night_day
  - `id 값이 'night_day'인 엘리먼트의 value` 값을 알아내는 방법 : `javascript element get value` 검색
  ```
  document.querySelector('#night_day').value
  ```
   - value가 `night`이라면 야간 모드를 실행하고, 그렇지 않다면 주간 모드를 실행한다. 
   - 이때, 모드를 바꾸었을 때 `value 값을 바꿔준다.`
  ```
  <input id="night_day" type="button" value="night" onclick=" 
    if(document.querySelector('#night_day'.value==='night') {
      document.querySelector('body').style.backgroundColor = 'black';
      document.querySelector('body').style.color = 'white';
      document.querySelector('#night_day').value = 'day';
    } else {
      document.querySelector('body').style.backgroundColor = 'white';
      document.querySelector('body').style.color = 'black';     
      document.querySelector('#night_day').value = 'night'; 
    }
  ">
  ```


### 중복 제거와 리팩터링

* `리팩터링(refactoring) : 공장으로 다시 보내 개선한다.`
    - 코딩을 하면 코드에 비효율적인 면이 생긴다.
    - 그 코드를 자체적으로 효율을 높인다.
    - `가독성을 높이고, 유지보수를 편리하게 하며, 중복된 코드를 줄이는 방향으로 코드를 개선한다.`

* 모드 변경 버튼을 하나 더 만든다.
  ```
  if(document.querySelector('#night_day2'.value==='night')
  ```
    - id 값을 `night_day`에서 `night_day2`로 바꾸면 정상적으로 동작한다.
    - 하지만 1억 개의 버튼을 만들게 되면, 그 모든 것을 바꿔야할 불편함이 생긴다.
  ```
  <input id="night_day2" type="button" value="night" onclick=" 
    if(document.querySelector('#night_day2'.value==='night') {
      document.querySelector('body').style.backgroundColor = 'black';
      document.querySelector('body').style.color = 'white';
      document.querySelector('#night_day2').value = 'day';
    } else {
      document.querySelector('body').style.backgroundColor = 'white';
      document.querySelector('body').style.color = 'black';     
      document.querySelector('#night_day2').value = 'night'; 
    }
  ">
  ```

* `this 키워드`
   - onclick과 같은 `이벤트 안에서 실행되는 코드에서 현재 코드가 속해 있는 태그를 가리키도록 약속된 키워드`
   - 코드의 document.querySelector('#night_day2')는 자기 자신을 가리키고 있다.
   - 상단의 코드를 모두 this로 바꿔주면 된다. 
    ```
    if(this.value==='night')
    ```
    ```
  <input id="night_day2" type="button" value="night" onclick=" 
    if(this.value==='night') {
      document.querySelector('body').style.backgroundColor = 'black';
      document.querySelector('body').style.color = 'white';
      this.value = 'day';
    } else {
      document.querySelector('body').style.backgroundColor = 'white';
      document.querySelector('body').style.color = 'black';     
      this.value = 'night'; 
    }
  ">
  ```

* document.querySelector('body')가 중복해서 등장하고 있다.
  - 코딩을 잘 하기 위해서는 `중복을 끝까지 쫓아가 없애`버려야 한다.
  - `<body>` 태그를 `target 변수`에 할당한다.
```
<input type="button" value="night" onclick="
  var target = document.querySelector('body');
  if(this.value ==='night') {
  target.style.backgroundColor = 'black';
  target.style.color = 'white';
  this.value = 'day';
} else {
  target.style.backgroundColor = 'white';
  target.style.color = 'black';
  this.value='night';
  }
">
```