# JS - DeepDive
## 2022-12-23 Fri

### 재귀 함수

* 재귀 호출(recursive call)
  * 함수가 자기 자신을 호출하는 것
* 재귀 함수(recursive function)
  * 자기 자신을 호출하는 행위
  * 재귀 호출을 수행하는 함수
  * `반복되는 처리`를 위해 사용
  ```javascript
  function countdown(n) {
    if (n<0) return;
    console.log(n);
    conuntdown(n-1); // 재귀 호출
  }

  countdown(10);
  ```
  * 재귀함수를 이용하면 반복 처리를 `반복문 없이` 구현 가능
    * countdown 함수 내부에서 호출한 `식별자 countdown은 함수 이름`
    * 함수 몸체 내부에서만 유효
    * 함수 내부에서 자기 자신 호출 가능
  * 함수 내부에서 재귀 호출하는 법
    1. 함수 이름
    2. 함수를 가리키는 식별자
    ```javascript
    // 함수를 가리키는 식별자로 재귀 호출
    return n * factorial(n-1);
    ```
* 특징
  * 자신을 무한 재귀 호출
  * `꼭 탈출 조건을 만들어야함`
  ```javascript
  if (n <= 1) return 1;
  ```
    * 탈출 조건이 없으면 `스택 오버플로(stack overflow)`가 발생
* 장점
  * 반복문 없이 구현할 수 있음
* 주의사항
  1. 무한 반복에 빠질 위험
  2. 그로 인한 스택 오버 플로
* 권장
  * `재귀 함수`를 사용하는 편이 직관적으로 이해하기 쉬울 때만 사용
### 중첩 함수

* 중첩 함수(nested function)
  * 함수 내부에 정의된 함수
  * `내부 함수(inner function)`이라고도 함
  * `중첩 함수는 외부 함수 내부에서만 호출 가능`
* 필요성
  * `외부 함수`를 돕는 `헬퍼 함수(helper function)` 역할
  ```javascript
  function outer() {
    var x = 3;

    // 중첩 함수
    function inner() {
      var y = 5;
      // 외부 함수 변수 참조 가능
      console.log( x * y );
    }
    inner(); // 외부 함수 내에서만 출력 가능
  }
  outer();
  ```
* 주의
  * 호이스팅으로 혼란이 생길 수 있음
    * if문이나 for문 등의 코드 블록 함수 선언문을 통해 정의하는 것은 바람직하지 않음

### 콜백 함수

* repeat 함수
  * 어떤 일을 반복 수행
  ```javascript
  function repeat1(n) {
    for (var i = 0; i < n; i++) console.log(i);
  }

  repeat1(5);
  ```
  * `console.log`에 강하게 의존하고 있어 다른 일 수행 불가
  * 다른 일을 하고 싶다면, 새롭게 정의해야 함
    1. 공통 로직은 미리 정의
    2. 변경되는 로직만 추상화

```javascript
// 외부의 전달받은 fun을 num만큼 반복 호출
// 고차함수
function repeat(num, fun) {
  for (var i = 0; i < num; i++) {
    fun(i); // i를 전달하며 fun을 호출
  }
}

// 콜백 함수
var logAll = function(i){
  console.log(i);
};

var lodOdds = function(i){
  if(i%2) console.log(i);
};

repeat(5, logOdds); // 1 3
```
* 예제
  * 경우에 따른 함수 fun을 추상화
  * 외부에서 전달받음
    * 함수는 `일급 객체`므로 매개변수를 통해 전달 가능
    * 로직의 일부분을 함수로 전달받아 수행
* 콜백함수(callback function)
  * `매개변수를 통해 다른 함수 내부로 전달되는 함수`
* 고차함수(Higher-Order Function, HOF)
  * `변수를 통해 함수 외부에서 콜백 함수를 전달받은 함수`
    1. 매개변수를 통해 함수를 전달
    2. 반환값으로 함수를 반환하는 함수
  * `고차 함수는 콜백 함수를 자신의 일부분으로 합성`
* `중첩 함수`와 `헬퍼 함수`
  * 유사
    * 중첩 함수는 외부 함수를 돕는 헬퍼 함수다.
    * 콜백 함수는 고차 함수에 전달되어 헬퍼 함수의 역할을 한다.
  * 차이
    * 중첩 함수는 고정되어 교체가 어려움
    * `콜백 함수는 주입식이기에 자유로운 교체 가능`
* 콜백함수의 전달
  * `고차 함수는 전달받은 콜백 함수의 호출 시점을 결정해 호출`
    1. 콜백 함수는 고차 함수에 의해 호출
    2. 고차 함수는 필요에 따라 콜백 함수에 인수 전달
  * 콜백 함수가 `함수 내부에만 호출`되면? 
    * 익명 함수 리터럴로 정의하며 `곧바로` 전달
    ```javascript
    // repeat 함수를 호출할 때마다 평가되어 함수 객체 생성
    repeat(5, function(i){
      if(i % 2) console.log(i);
    });
    ```
      * 이때 `함수 리터럴`은 고차함수가 호출될 때마다 평가되어 함수 객체 생성
* `함수 외부에서 콜백 함수 정의 후` 고차 함수에 전달하는 것이 효율적일 때
  1. 콜백 함수를 다른 곳에서도 호출할 필요가 있을 때
  2. 함수를 전달받는 함수가 자주 호출될 때
   
### 순수 함수와 비순수 함수

* 순수 함수(pure function)
  * 어떤 외부 상태에 의존하지도 않고 변경하지도 않는 함수
  * 부수 효과가 `없는` 함수
```javascript
var count = 0;

function increase(n){
  return ++n;
}
```
* 비순수 함수(impure function)
  * 외부 상태에 의존하거나 외부 상태를 변경하는 함수
  ```javascript
  var count = 0;

  function increase(){
    return ++count;
  }
 
  * 부수 효과가 `있는` 함수

* 순수 함수와 인수
  * 동일한 인수가 전달되면 `언제나 동일한 값`을 반환
    * 외부 상태에 의존하지 않음
    * 오로지 `매개변수를 통해` 내부로 전달된 인수에게만 의존해 값을 생성
  * 함수 내부 상태에만 의존해도 호출될 때마다 변화하면 순수함수가 아님
    * 현재 시각
  * 일반적으로 `최소 하나 이상의 인수`를 전달 받음
    * 그렇지 않으면 언제나 같은 값을 반환해 상수와 마찬가지
    * 순수 함수는 `인수를 변경하지 않음으로써 불변성을 유지`하는 것이 기본
* 비순수 함수와 인수
  * 함수의 외부 상태에 의존
  * 외부 상태에 따라 반환값이 달라짐
    1. 전역 변수
    2. 서버 데이터
    3. 파일
    4. Console.
    5. DOM
* 비순수 함수 억제
  * 함수가 외부 상태를 변경하면 `추적이 어려움`
  * 비순수 함수를 최대한 줄여 부수 효과를 최대한 억제
  * 함수형 프로그래밍
    * 순수 함수와 보조 함수의 조합을 통해 부수 효과를 최소화해 불변성(immutability)을 지향하는 프로그래밍 패러다임
      1. 로직 내의 조건문과 반복문을 제거해 복잡성을 해결 → 가독성↓
      2. 변수 사용 억제 → 언제든 변경
      3. 생명주기 최소화
      4. 상태 변경을 피해 오류를 최소화