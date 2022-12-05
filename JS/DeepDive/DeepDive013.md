# JS - DeepDive
## 2022-11-23 Wed

## 타입 변환과 단축 평가

### 타입 변환이란?

* 정의
  * 의도적으로 값의 타입을 변환하는 것
    * `명시적 타입 변환(explicit coercion)`
    * `타입 캐스팅(type casting)`
  * 개발자의 의도와 관계 없이 평가 도중 `엔진에 의해 암묵적`으로 자동 변환되는 것
    * `암묵적 타입 변환(implicit coercion)`
    * `타입 강제 변환(type coercion)`
* 값의 변경
  * `기존 원시 값`이 직접 변경되는 것은 아니다.
  * 원시 값은 변경 불가능한 값(immutable value)이다.
    * 타입 변환은 `기존 원시 값을 사용해 다른 타입의 새로운 원시 값을 생성`하는 것이다.
    * 암묵적 타입 변환 역시 `기존 변수를 재할당하지 않는다.`
  * 평가를 위해 피연산자의 값을 암묵적 타입 변환해 `새로운 타입의 값을 만들어` 단 한 번 사용하고 버린다.
* 주의
  * 명시적 타입 변환과 달리 암묵적 타입 변화는 표현식 평가를 `예측 가능`해야 한다.
  * 암묵적 타입 변환이 가독성 측면에서 좋을 수 있으므로, `예측`은 중요해진다.
  * 
### 암묵적 타입 변환

* 표현식
  * 표현식 평가시 `코드 문맥`에 부합하지 않는다면 다양한 상황이 발생한다.
  * 가급적 에러가 발생하지 않도록 표현식을 평가하자.

#### 문자열 타입으로 변환

* 예제
  ```javascript
  1 + '3' // 13
  ```
  * `+ 연산자`는 `피연산자 중 하나 이상이 문자열`이므로 문자열 연결 연산자로 동작한다.
  * 이 경우 문자열 타입이 아닌 피연산자를 문자열 타입으로 암묵적 타입 변환한다.
* 주의
  * 피연산자만 암묵적 타입 변환의 대상인 것은 아니다.
  * 템플릿 리터럴의 경우, `표현식 평가 결과`를 문자열 타입으로 암묵적 변환한다.
  ```javascript
  '1 + 1 = ${1 + 1}` // "1 + 1 = 2"
  ```
* 동작 예시
  ```javascript
  (Symbol()) + '' // TypeError
  ```
  ```javascript
  ({}) + `` // "[object Object]"
  ```
  ```javascript
  Math + `` // "[object Math]"
  ```
  ```javascript
  [] + `` // ""
  ```
  ```javascript
  [10, 20] + `` // "10, 20"
  ```
  ```javascript
  (function(){}) + `` // "function(){}"
  ```
  ```javascript
  Array + `` // "function Array() { [native code] }"
  ```


#### 숫자 타입으로 변환

* 예제
  ```javascript
  1 - '1' // 0
  1 * '10' // 10
  1 / 'one' // NaN
  ```
  * 산술 연산자의 모든 피연산자는 `코드 문맥상 모두 숫자 타입`이어야 한다.
  * 피연산자를 숫자 타입으로 변환할 수 없으면 연산 수행이 불가해 `NaN`이 된다.
  * 비교연산자 역시 마찬가지다.
    ```javascript
    '1' > 0 // true
    ```
    * 문맥상 숫자 타입이어야하므로 `암묵적 타입 변환`한다.
    * `+ 단항 연산자` 역시 암묵적 타입 변환을 수행한다.
    ```javascript
    +'' // 0
    +'1' // 1
    ```
    ```javascript
    +'string' // NaN
    ```
    ```javascript
    +null // 0
    +undefined //NaN
    ```
    ```javascript
    +Symbol() // TypeError
    ```
    ```javascript
    +{} // NaN
    +[] // 0
    +[10, 20] // NaN
    +(function(){}) // NaN
    ```

#### 불리언 타입으로 변환

* 정의
  * `제어문` 또는 `삼항 조건 연산자`는 논리적 참/거짓으로 평가되어야하므로 암묵적 타입 변환된다.
  * 이때 자바스크립트 엔진은 `불리언 타입이 아닌 값을 Truthy 값 또는 Falsy 값으로 구분한다.`
    * Truthy는 true로, Falsy는 false로 암묵적 타입 변환한다.
    ```javascript
    if ('sty') console.log('1');

    // 1
    ```
* 예제
  * 아래는 모두 false 평가된다.
  ```javascript
  if (!false)
  if (!undefined)
  if (!null)
  if (!0)
  if (!NaN)
  if (!'')              
  ```
* isFalsy
  * 다음은 Falsy를 판별하는 함수이다.
  ```javascript
  function isFalsy(v) {
    return !v;
  }
  ```
* isTruthy
  * 다음은 Truthy를 판별하는 함수다.
  ```javascript
  function isTruthy(v) {
    return !!v;
  }
  ```
  ```javascript
  isTruthy({});
  isTruthy([]);

  // 모두 true를 반환한다.
  ```
