# JS - DeepDive
## 2022-12-20 Tue

## let, const 키워드와 블록 레벨 스코프

### var 키워드로 선언한 변수의 문제점

* ES5까지의 유일한 변수 선언 → var 키워드
* 다른 언어와 구별되는 특징

#### 변수 중복 허용

* 중복 선언
  * var 키워드 변수는 중복 선언이 가능하다.
  * 중복 선언시 `초기화문`(변수 선언과 동시에 초기값을 할당하는 문) 유무에 따라 다르게 동작한다.
    * 있으면 → var 키워드가 없는 것처럼 동작
    ```javascript
    var x = 1;

    var x = 100; // var 키워드가 없는 것처럼 동작
    ```
    * 없으면 → 무시(에러는 발생하지 않음)
    ```javascript
    var y = 1;

    var y; // 변수 선언문 무시
    ```
#### 함수 레벨 스코프

* 함수 코드 블록
  * var 키워드로 선언한 변수는 함수의 코드 블록만을 지역 스코프로 인정
  * 함수 외부라면 `코드 블록 내에서 선언해도 전역 변수`

#### 변수 호이스팅

* 변수 호이스팅
  * var 키워드로 선언한 변수는 `변수 선언문 이전에 참조`
  * 할당문 이전에 참조하면 `언제나 undefined`
  ```javascript
  console.log(test); // undefined

  test = 1004;

  console.log(test); // 1234

  var test;
  ```
  * `가독성을 떨어뜨리고` 오류를 발생시킬 여지를 남긴다.

### let 키워드

* 이를 보완하기 위해 ES6에서 `let과 const`를 도입했다.

#### 변수 중복 선언 금지

* let과 중복 선언
  * let 키워드로 중복 선언하면 `문법 에러(SyntaxError)`가 발생한다.
  ```javascript
  let foo = 1004;
  let foo = 123; // SyntaxError
  ```
#### 블록 레벨 스코프

* let과 코드블록
  * let으로 선언하면 `모든 코드 블록`을 지역 스코프로 인정한다.
      1. 함수
      2. if문
      3. for문
      4. while문
      5. try / catch문
  * 함수 내의 코드 블록은 `함수 레벨 스코프에 중첩`된다.
  ```javascript
  let test = 1;
  { 
    let test = 3;
    let bar = 5;
  }
  console.log(test); // 1
  console.log(bar); // ReferenceError
  ```
#### 변수 호이스팅

* var와 호이스팅
  * 암묵적으로 `선언`과 `초기화`가 함께 진행된다.
    1. 선언 단계에서 스코프에 변수 식별자 등록
    2. 즉시 undefined 변수 초기화
    3. 변수 할당문에 도달하면 값이 할당
* let과 호이스팅
  * let 키워드 변수는 `호이스팅이 발생하지 않는 것`처럼 동작
  ```javascript
  console.log(test); // ReferenceError
  let test; // undefined
  test = 1; // 1
  ```
  * `선언 단계`와 `초기화 단계`가 분리되어 진행되기 때문이다.
    1.  암묵적으로 선언 단계가 먼저 실행
    2.  초기화 단계는 변수 선언문에 도달했을 때
  * 초기화 단계가 실행되기 이전이면 `참조 에러(ReferenceError)`가 발생

* `일시적 사각지대(Temporal Dead Zone; TDZ)`
  * 스코프 시작 지점부터 초기화 단계 시작 지점까지 변수 참조 불가
  * 해당 구간을 `일시적 사각지대`라 부른다.

* let은 호이스팅이 발생하지 않나?
  * 호이스팅 되지 않는다면 전역 변수가 출력되어야 한다.
  ```javascript
  let test = 1; 
  {
    console.log(test); // ReferenceError
    let test = 2;
  } 
  ```
  * 호이스팅되었기 때문에 참조 에러가 발생한다.
#### 전역 객체와 let

* window 프로퍼티
  * var 키워드로 선언한 전역 변수와 전역 함수
  * 선언하지 않은 변수에 값을 할당한 암묵적 전역
  * `전역 객체의 프로퍼티를 참조`할 때 window를 생략할 수 있다.
* 전역 객체와 let
  * let 키워드로 선언한 전역 변수는 `전역 객체의 프로퍼티가 아니다.`
  * let 전역 변수는 `보이지 않는 개념적 블록` 내에 존재한다.
  ```javascript
  // 브라우저 환경에서 실행해야 한다.
  let x = 1;

  // let, const 키워드의 전역 변수는 전역 객체 window의 프로퍼티가 아니다.
  console.log(window.x); // undefined
  ```

### const 키워드
* 상수 선언시 사용
  * 반드시 상수만을 위하진 않는다.
#### 선언과 초기화

* 선언 
  * `반드시 선언과 동시에 초기화`
  ```
  const a = 1;
  ```
* 초기화
  * let과 동일하게 `블록 레벨 스코프`이며 `변수 호이스팅이 발생하지 않는 것처럼 동작`
  ```javascript
  console.log(test); // ReferenceError
  const a = 1;
  console.log(test);
  ```
#### 재할당 금지

* 재할당
  * var과 let은 재할당이 자유로움
  * `const 키워드로 선언한 변수는 재할당이 금지`
  ```javascript
  const a = 1;
  a = 2; // TypeError
  ```

#### 상수

* 상수
  * `재할당이 금지된 변수`
  * 상수도 값을 저장하기 위한 `메모리 공간이 필요`하므로 변수라고 할 수 있다.
    * 하지만 상수는 변수와 달리 재할당이 금지된다. → 변수의 상대 개념
* 필요성
    1. 상태 유지
    2. 가독성
    3. 유지보수 편의
* 예제
  * 코드 내의 0.1의 의미가 불분명해 가독성이 좋지 않다.
  * const 키워드는 `재할당이 금지`므로 `공통적인 값`은 상수로 사용한다.
  * 변경시 하나만 변경하면 되기에 `유지보수성`이 대폭 상승한다.
  ```javascript
  const READING_RATE = 0.1;

  let preReadingPrice = 100;

  let afterReadingPrice = preReadingPrice * READING_RATE

  console.log(afterReadingPrice);
  ```
  * 일반적으로 상수는 `대문자로 선언해` 상수임을 명확히 나타낸다.
  * 여러 단어라면 (_)를 사용하는 `스네이크 케이스`로 표현한다.
  ```
  const READING_RATE = 0.1;
  ```


#### const 키워드와 객체

* const 
  * 키워드로 선언된 변수에 객체를 할당한 경우 값을 변경할 수 있다.
      1. 원시 값은 변경 불가능해 재할당 없이 변경 불가
      2. 객체는 재할당 없이도 직접 변경 가능
  * `재할당은 금지하나, 불변을 의미하지 않는다.`
  * 허용 목록
      1. 프로퍼티 동적 생성
      2. 프로퍼티 삭제
      3. 프로퍼티 값을 통해 객체를 변경 → 할당된 참조 값은 변경되지 않음

### 결론

* `기본적으로 const를 사용하고 재할당이 필요하면 let`
    1. ES6라면 var 키워드를 사용하지 않는다.
    2. 재할당이 필요한 경우만 let을 사용하되, 변수 스코프를 최대한 좁게 만든다.
    3. 읽기 전용(재할당이 필요 없는 상수) 원시값과 객체에는 const를 사용한다.
* 변수 선언에는 일단 const를 사용
  * 재할당이 필요하면 그때 let으로 변경
  * 객체는 `의외로 재할당의 경우가 드물다.`