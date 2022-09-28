# HTML - Basic
## 2022-09-28 Wed

### 함수

* 코드가 많아지면 그 코드를 정리 정돈하기 위한 도구
  - 간단한 도구 `함수`
  - 그보다 조금 더 큰 `객체`
```
function two() {
  document.write('<li>Nun</li>');
  document.write('<li>Na</li>');
}
```
```
two();
```
* `two();`를 보면 웹 브라우저가 two 함수를 실행하고 싶다는 것을 알게 되며 `그 위치에서 코드가 실행`된다.

### 매개변수와 인자

* `원하는 제품을 선택하면 그 제품에 해당하는 제품이 제공되는 자판기`처럼 제품 선택은 `입력` 제품 제공은 `출력`이 된다.
  - `입력`에 해당하는 것은 `매개변수(parameter)` 또는 `인자(argument)`이다.
  - `출력`에 해당하는 것은 `return`과 관련 있다.
* 함수를 실행할 때 입력값을 주면 그 함수가 입력값에 따라 다른 결과를 출력하는 경우
```
function sum(left, right) {
  document.write(left + right + '<br>');
}
```
* 위의 코드에서 left와 right처럼 `변수를 매개하는 변수`는 `매개변수(parameter)`이다.
```
sum(2, 3);
```
* 이때 함수로 전달하는 2, 3이라는 값은 `인자(argument)`라고 하며 값을 받아 `함수 안으로 매개하는 변수`가 매개변수이다.

### return문

* `표현식(expression)` : sum()을 실행했을 때 2+3의 계산 결과인 `5`를 받도록 표현식을 만들고 싶다.
  - 1+1은 숫자 2에 대한 표현식이다.
  - 3-1 역시 숫자 2에 대한 표현식이다.
  - 1===1은 true에 대한 표현식이다.
  - 이때 사용하는 것이 `return`이다.

* 함수로 나타난 것을 다양한 방법으로 사용해야 한다면, `return`을 사용한다.
* 예를 들어 `sum()을 실행한 결과의 색깔을 바꾸어`야 할 때
  - 두 값이 더하는 작업을 다양한 곳에서 사용할 때 `return`을 이용한다.
  - 결과를 출력한 뒤 `줄바꿈`을 한다.
  - 결과의 글자색을 `빨간색`으로 표현한다.
  - `폰트 크기`를 다르게 한다.
  - 위의 것들은, `숫자 5에 대한 표현식`을 만들어 사용하면 된다.

```
function sum(left, right) {
  return left + right;
}
document.write(sum(2,5) + '<br>');
document.write('<div style="color: red">' + sum(2,5) + '</div><br>');
document.write('<div style="font-size: 3rem">' + sum(2,5) + '</div><br>');
```
* left, right (매개변수)를 통해 값을 return으로 출력함으로써 `다양한 용도로 함수를 활용`할 수 있게 했다.

### 함수의 활용

* 중복된 위와 아래의 코드를 함수로 빼기
```
<script>
  function nightDayHandler(self) {
    var target = document.querySelector('body');
    if(self.value ==='night') {
    target.style.backgroundColor = 'black';
    target.style.color = 'white';
    self.value = 'day';

    var alist = document.querySelectorAll('a');
    var i = 0;
    while(i<alist.length) {
    alist[i].style.color = 'powderblue';
    console.log(alist[i]); 
    i = i + 1;
    }
  } else {
    target.style.backgroundColor = 'white';
    target.style.color = 'black';
    self.value='night';

    var alist = document.querySelectorAll('a');
    var i = 0;
    while(i<alist.length) {
      alist[i].style.color = 'blue';
      console.log(alist[i]);
      i = i + 1;
    }
  }
}
</script>
```
```
<input type="button" value="night" onclick="
   nightDayHandler();
">
```

* 이때 `onclick` 이벤트 안에서 `this`는 `이벤트가 소속된 태그를 가르키도록 약속`되어 있다.
  - nightDayHandler() 안에서 this는 input이 아니라 전역 객체를 갖게 된다.
  - 함수 안에서 this 값이 input 버튼을 가리키도록 this 값이 유지된다.
  - 따라서 `function nightDayHandler(self)`로 코드를 바꿔 `this라는 인자를 self라는 매개변수`로 받는다.
```
function nightDayHandler(self)
```