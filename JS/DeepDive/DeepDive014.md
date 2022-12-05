# JS - DeepDive
## 2022-11-24 Thu

###  명시적 타입 변환

* 개발자의 의도에 따라 명시적 타입 변경
  1. 생성자 함수(String, Number, Boolean)
  2. 빌트인 메서드
  3. 암묵적 타입 변환 이용

* 표준 빌트인 생성자 함수와 빌트인 메서드
  * 표준 빌트인(built-in)
    * 객체를 생성하기 위한 함수
    * new 연산자와 함께 호출
  * 표준 빌트인 메서드
    * 자바스크립트에서 기본 제공하는 빌트인 객체의 메서드

#### 문자열 타입으로 변환

* 변환 방법
  1. String 생성자 함수를 new 연산자 없이 호출
  ```javascript
  Stirng(NaN); // "NaN"
  ```
  2. Object.prototype.toString 메서드를 사용
  ```javascript
  (Infinity).toString(); // "Infinity"
  ```
  3. 문자열 연결 연산자 이용
  ```javascript
  1 + ''; // "1"
  ```

#### 숫자 타입으로 변환
* 변환 방법
  1. Number 생성자 함수를 new 연산자 없이 호출
  ```javascript
  Number('163.7'); // 163.7
  ```
  2. parseInt.parseFloat 함수를 사용 (문자열만 변환 가능)
  ```javascript
  parseInt('163.7'); // 163.7
  ```
  3. `+ 단항 산술 연산자`를 이용
  ```javascript
  + '0'; // 0
  + true // 1
  ```
  4. `* 산술 연산자`를 이용
  ```javascript
  '0' * 1; // 0
  '-1' * 1; // -1
  ```
  ```javascript
  true * 1; // 1
  false * 1; // 0
  ```


#### 불리언 타입으로 변환

* 변환 방법
  1. Boolean 생성자 함수를 new 연산자 없이 호출
  ```javascript
  문자열 타입 → 불리언 타입
  Boolean(''); // false
  Boolean('false'); // true
  ```
  ```javascript
  null과 undefined → 불리언 타입
  Boolean(null); // false
  Boolean(undefined); // false
  ```
  ```javascript
  객체 타입 → 불리언 타입
  Boolean({}); // true
  Boolean([]); // true
  ```
  2. ! 부정 논리 연산자를 두 번 사용
  ```javascript
  문자열 타입 → 불리언 타입
  !!''; // false
  !!'false'; // true
  ```
  ```javascript
  null과 undefined → 불리언 타입
  !!null; // false
  !!undefined; // false
  ```
  ```javascript
  객체 타입 → 불리언 타입
  !!{}; // true
  !![]; // true
  ```


### 단축 평가

* 단축 평가
  * `논리합 또는 논리곱 연산자 표현식의 평가 결과는 불리언 값이 아닐 수 있다.`
  * 논리합 또는 논리곱 연산자 표현식은 언제나 2개의 연산자 중 `어느 한쪽으로 평가`된다.

#### 논리 연산자를 사용한 단축 평가

* 논리곱(단축평가)
  ```javascript
  'Cat' && 'Dog' // "Dog"
  ```
  * 논리곱 연산자는 `좌항에서 우항`으로 평가된다.
  * 첫 번째 피연산자가 Truthy므로 true가 된다.
  * 논리곱 연산자는 두 번째 피연산자까지 확인해야한다.
  * 이럴 때, 논리곱 연산자는 `논리 연산의 결과를 결정하는 두 번째 피연산자, 'Dog'를 그대로 반환`한다.

* 논리합(단축평가)
  ```javascript
  'Cat' || 'Dog' // "Cat"
  ```
  * 논리합 연산자는 하나만 true여도 true 반환한다.
  * 첫 번째 피연산자가 Truthy이다.
  * `두 번째 피연산자까지 평가해보지 않아도 평가할 수 있다.`
  * 논리합 연산자는 첫 번째 피연산자인 `'Cat'`을 그대로 반환한다.

* 단축평가
  * 논리곱 연산자와 논리합 연산자는 `논리 연산의 결과를 결정`하는 피연산자를 `타입 변환하지 않고 그대로 반환`한다.
  * 이를 단축 평가(short-circuit evaluation)이라 한다.
  * 표현식을 `평가하는 도중 평가 결과가 확정`됐다면 나머지 평가 결과를 생략한다.
    ```javascript
     단축 평가 표현식       평가 결과
    true || anything         true
    false || anything      anything
    ture && anything       anything
    false && anything       false
    ```

* 사용
  * 단축 평가를 통해 `if문을 대체`할 수 있다.
    1. Truthy값일 때 무언가를 해야하면 논리곱 연산자 표현식으로 if문을 대체할 수 있다.
    ```javascript
    if (done) message = '완료';
    ```
    ```javascript
    message = done && '완료';
    console.log(message); // 완료
    ```

    2. Flasy값일 때 무언가를 해야하면 논리합 연산자로 if문을 대체할 수 있다.
    ```javascript
    if (!done) message = '미완료';
    ```
    ```javascript
    message = done || '미완료';
    console.log(message); // 미완료
    ```
  * 삼항 조건 연산자는 `if ... else문을 대체`할 수 있다.
    ```javascript
    if (done) message = '완료';
    else      message = '미완료';
    console.log(message); // 완료
    ```
    ```javascript
    message = done ? '완료' : '미완료';
    console.log(message); // 완료
    ```
* 유용한 상황
  * 객체를 가리키기를 기대하는 변수가 `null 또는 undefined가 아닌지 확인`하고 프로퍼티를 참조
  ```javascript
  var name = null;
  var value = name && name.value; // null
  ```
  * 함수 매개변수에 기본값을 설정
    * undefined로 인해 발생할 수 있는 에러를 방지한다.
  ```javascript
  function getStringLength(str) {
    str = str || '';
    return str.length;
  }
  ```

#### 옵셔널 체이닝 연산자

* 옵셔널 체이닝(optional chaining)
  * `?.` 좌항의 피연산자가 `null 또는 undefined라면 undefined를 반환한다.`
  * 그렇지 않다면 `우항의 프로퍼티 참조를 이어간다.`
  * 객체를 가리키기를 기대하는 변수가 `null 또는 undefined가 아닌지 확인하고 프로퍼티를 참조`할 때 유용하다.
  ```javascript
  var name = null;
  var value = name?.vale;
  console.log(value);
  ```
* 논리 연산자와 차이
  ```javascript
  var name = '';
  var length = name && name.length;
  console.log(length);
  ```
  * 논리 연산자
    * 좌항 피연산자가 `Falsy값`이면 `좌항 피연산자를 그대로 반환`한다.
  ```javascript
  var name = '';
  var length = name?.length;
  console.log(length); // 0
  ```
  * 옵셔널 체이닝 연산자
    * 좌항 피연산자가 Falsy값이라도 null 또는 undefined가 아니면 `우항의 프로퍼티 참조를 이어간다.`

#### null 병합 연산자

* null 병합 연산자(nullish coalescing)
  * 좌항의 피연산자가 null 또는 undefined라면 `우항의 피연산자 반환`
  * 그렇지 않으면 `좌항의 피연산자를 반환`한다.
  * null 병합 연산자인 `??는 변수에 기본값을 설정`할 때 유용하다.
  ```javascript
  var name = null ?? 'default'
  console.log(name); // "default"
  ```
* 논리 연산자와 차이
  ```javascript
  var name = '' || 'default';
  console.log(name); // "default"
  ```
  * 논리 연산자
    * Flasy인 `0이나 ''도 기본값으로 유효`하다면 예기치 않은 동작이 발생한다.
  ```javascript
  var name = '' ?? 'default';
  console.log(name); // ""
  ```
  * null 병합 연산자
    * false로 평가되는 Falsy값이라도 `null 또는 undefined`가 아니면 `좌항의 피연산자를 그대로 반환한다.`
  