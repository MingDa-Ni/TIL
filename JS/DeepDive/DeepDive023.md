# JS - DeepDive
## 2022-12-08 Thu

### 참조에 의한 전달과 외부 상태의 변경

* 매개변수 전달
  * 함수 몸체 내부에서 변수와 동일하게 취급된다.
    * 값에 의한 전달(call by value)
    * 참조에 의한 전달(call by reference)
```javascript
function chageVal(primitive, obj){
  primitive += 100;
  obj.name='Kim';
}

var num = 100;
var cha = {name: 'Lee'};

changeVal(num, person);
```
```javascript
console.log(num); // 100
console.log(person); // {name: "Lee"}
```
* 예제
  * changeVal은 매개변수를 통해 전달 받은 `원시 타입 인수`와 `객체 타입 인수`를 몸체에서 변경
    * primitive는 원시 값이기에 `재할당을 통해 교체`
    * obj는 변경 가능한 값이므로 `재할당 없이 직접 할당`

* 함수의 부수 효과
  * 함수가 외부 상태(ex. person)를 변경
    * 상태 변화 추적이 어려움
    * 코드의 복잡성↑ , 가독성↓
  * 발생 원인
    1. 객체가 변경할 수 있는 값
    2. 참조에 의한 전달 
  * 객체 변경 추적
    1. `옵저버(Observer)` 패턴을 통해 객체 참조를 공유하는 모든 이에게 변경 사항 통지
    2. 이에 대한 추가 대응
* 해결 방법
  * 객체를 `불변 객체(immutable object)`로 만들어 사용
  * 단점
    * 객체를 새롭게 생성하는 비용은 듦
  * 장점
    * 객체를 마치 원시 값처럼 `변경 불가능`하게 동작
    * 객체의 상태 변경 원천 봉쇄
    * 상태 변경이 필요한 경우 → 방어적 복사(defensive copy)를 통해 `원본 객체 복사`
      1. 새로운 객체 생성
      2. 재할당을 통해 교체
* 순수 함수
  * 외부 상태를 변경하지 않고 의존하지도 않는 함수
  * 함수형 프로그래밍
    * 순수 함수를 통해 부수 효과를 최대한 억제
        1. 오류 피하기
        2. 안정성 높이기

### 다양한 함수의 형태

#### 즉시 실행 함수

* 즉시 실행 함수(IIFE, Immediately Invoked Function Expression)
  * 함수 정의와 동시에 즉시 호출
  * 단 한 번만 호출되며 `다시는 호출 불가`
  ```javascript
  // 익명 즉시 실행 함수
  (function (){
    var a = 4;
    var b = 2;
    return a + 2;
  }());
  ```
  * 이름 없는 `익명 함수를 사용`하는 것이 일반적
    * 기명 함수도 가능
    * `그룹 연산자( ... )` 내의 기명함수는 함수 리터럴로 평가
    * 함수 이름은 함수 몸체에서만 참조하므로, 다시 호출 불가
  ```javascript
  (function plus(){
    var a = 4;
    var b = 2;
    return a + 2;
  }());

  plus(); // ReferenceError
  ```
* `그룹 연산자( . . . )`로 감싸야 하는 이유
  * 그룹 연산자를 사용하지 않으면 
    * `함수 선언문 형식에 맞지 않음`
    * 함수 선언문은 `함수 이름을 생략할 수 없다.`
  ```javascript
  function() {

  }(); // SyntaxError
  ```
  * 기명 함수를 정의해 그룹 연산자 없이
    * 암묵적 세미콜론 자동 삽입 기능
    * 자동적으로 `함수를 닫는 중괄호` 뒤에 ";"이 암묵적으로 생성
  ```javascript
  function ex() {

  }(); // SyntaxError
  ```
  ```javascript
  function ex() {};();
  ```
  * 따라서 함수 선언문 뒤의 ( . . . )가 호출 연산자가 아닌 `그룹 연산자로 해석`
    * 그룹 연산자가 없으므로 에러 발생

* 사용법
  * 그룹 연산자의 `피연산자`는 값으로 평가
  * 기명 또는 무명 함수를 `그룹 연산자`로 감싸기
    * 함수 리터럴로 평가되어 함수 객체가 생성
  ```javascript
  console.log(typeof (function f(){}));
  console.log(typeof (function (){}));
  ```

* `그룹 연산자로 묶는 이유`
  * `함수 리터럴로 평가시켜 함수 객체를 생성하기 위해서`

* 반환과 인수
  1. `값을 반환` 할 수 있다.
  ```javascript
  // 즉시 실행 함수도 일반 함수처럼 값을 반환
  var multiply = (function() {
    var a = 2;
    var b = 5;
    return a * b;
  }());

  console.log(multiply);
  ```
  2. `인수 전달`도 가능하다.
  ```javascript
  // 즉시 실행 함수도 일반 함수처럼 인수 전달
  var multiply = (function(a, b) {
    return a * b;
  }(4,2));

  console.log(multiply);
  ```

* 필요성
  * 스코프 문제를 방지할 수 있다.
  * `변수나 함수 이름의 충돌 방지`