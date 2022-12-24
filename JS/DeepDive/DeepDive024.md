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


### 순수 함수와 비순수 함수