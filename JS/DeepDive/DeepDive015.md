# JS - DeepDive
## 2022-11-25 Fri

## 객체 리터럴

### 객체란?

* 정의
  * 0개 이상의 `프로퍼티`로 구성된 집합이다.
  * 프로퍼티는 key와 value로 구성된다.

* 자바스크립트
  * 객체(object) 기반의 프로그래밍 언어다.
  * 자바스크립트를 구성하는 거의 `모든 것`이 객체이다.
  * 원시 값을 제외한 나머지 값(함수, 배열, 정규 표현식 등)이 모두 객체이다.
    * 자바스크립트의 모든 값은 프로퍼티 값이 될 수 있다.
    * 함수는 `일급 객체`이므로 값으로 취급 가능하며, 프로퍼티 값이 될 수 있다.
    * 프로퍼티 값이 함수라면 일반 함수와 구분하기 위해 `메서드(method)`라 부른다.
  * 이렇게 객체의 집합으로 프로그램을 표현하려는 프로그래밍 패러다임을 `객체지향 프로그래밍`이라 한다.

* 객체 타입(object/reference type)
  * 다양한 타입의 값을 하나의 단위로 구성한 복합적인 자료구조(data structure)다.
  * 원시 타입의 값은 `변경 불가능한 값(immutable value)`이나 객체는 변경 가능한 값(mutable value)이다.

* 역할
  * 프로퍼티 
    * 객체의 `상태`를 나타내는 값(data)
  * 메서드 
    * 프로퍼티(상태 데이터)를 참조 
    * 프로퍼티를 조작할 수 있는 동작(behavior)

* 이점
  * 객체는 프로퍼티와 메서드를 모두 포함할 수 있다.
  * 상태와 동작을 `하나의 단위로 구조화`할 수 있어 유용하다.

* 객체와 함수
  * 객체는 함수와 밀접한 관계를 가진다.
    1. 함수로 객체를 생성
    2. 함수 자체가 객체
  * 함수와 객체는 서로 분리해 생각할 수 없다.

### 객체 리터럴에 의한 객체 생성

* 인스턴스(instance)
  * 클래스에 의해 생성되어 메모리에 저장된 실체
  * 객체는 클래스와 인스턴스를 포함한 개념이다.
    * 클래스는 인스턴스를 생성하기 위한 템플릿
    * 인스턴스는 객체가 메모리에 저장되어 실제로 존재하는 `본체`

* 객체 생성 방법
  1. 객체 리터럴
  2. Object 생성자 함수
  3. 생성자 함수
  4. Object.create 메서드
  5. 클래스(ES6)

* 객체 리터럴
  * 가장 보편적인 방법이다.
  * `중괄호 ({...})` 내에 0개 이상의 프로퍼티를 정의한다.
  ```
  var minda = {
    name: 'Hong',
    sayHallo: function() {
      console.log('Hello!');
    }
  };
  ```
  * `객체 리터럴의 중괄호는 코드 블록이 아니다.`
  * 객체 리터럴은 `값으로 평가되는 표현식`이기 때문에 세미콜론을 붙인다.
  
### 프로퍼티

* 프로퍼티
  * 객체는 `프로퍼티의 집합`이며, 프로퍼티는 `키와 값`으로 구성된다.
  ```
  var minda = {
    // 프로퍼티 키는 name, 프로퍼티 값은 'Hong'
    name: 'Hong',
    age : 23
  };
  ```
  * 마지막 프로퍼티 뒤에는 쉼표를 사용하지 않아도 되고 사용해도 된다.
  * 사용할 수 있는 값
    * `프로퍼티 키` : 빈 문자열로 포함하는 모둔 문자열 또는 심벌 값
    * `프로퍼티 값` : 자바스크립트에서 사용할 수 있는 모든 값
  * 프로퍼티 키는 프로퍼티 값에 접근할 수 있는 식별자 역할이다.
  * 식별자 네이밍 규칙을 준수하는 프로퍼티 키와 않은 프로퍼티 키는 차이가 있다.
    * `식별자 네이밍 규칙을 따르지 않는 이름에는 따옴표를 사용해야 한다.`
    * 번거롭기 때문에 식별자 네이밍 규칙을 준수하는 키를 사용할 것을 권장한다.
    ```
    var minda = {
      firstName: 'Minda',
      `last-naem': 'Hong'
    };

    console.log(minda);
    ```
    ```
    var minda = {
      last-name: 'Hong' // SyntaxError: Unexpected token - 
    };
    ```
* 동적 생성
  * 프로퍼티 키를 동적으로 생성할 수 있다.
  * 프로퍼티 키를 사용할 표현식을 `대괄호([...])`로 묶어야 한다.
  ```
  var name = {};
  var key = 'clock';

  name[clock] = 'apple';

  console.log(name); // {clock: 'apple'}
  ```
  * 프로퍼티 키에 `문자열이나 심벌 값 외의 값`을 사용하면 암묵적 타입 변환으로 `문자열`이 된다.
    * 숫자 리터럴 역시 `내부적으로 문자열로 변환`된다.
  * 예약어를 프로퍼티 키로 사용해도 에러가 발생하지 않는다.
    * 에러 발생의 여지가 있으므로 권장하지 않는다.
  * 이미 존재하는 프로퍼티 키를 중복 선언하면 먼저 선언한 프로퍼티를 `덮어쓴다.`
  ```
  var minda = {
    name: 'Lee',
    name: 'Hong'
  };
  
  console.log(minda); // {name: 'Hong'};
  ```
### 메서드

* 메서드
  * 자바스크립트에서 `사용할 수 있는 모든 값`은 프로퍼티 값으로 사용할 수 있다.
  * 자바스크립트 함수 역시 일급 객체이니, `값으로 취급`할 수 있다.
  * 프로퍼티 값이 함수일 경우 일반 함수와 구분하기 위해 `메서드(method)`라고 부른다.
  ```
  var circle = {
    radius: 3,

    getDiameter: function() {
      return 2 * this.radius;
    }
  };
  ```
  * 이 때 `this 키워드는 객체 자신을 가리키는 참조 변수`이다.


### 프로퍼티 접근

* 프로퍼티에 접근하는 방법
  * 프로퍼티 키가 네이밍 규칙을 준수하면 `아래의 방식 모두 사용할 수 있다.` 
    1. 마침표 프로퍼티 접근 연산자(.)를 사용하는 `마침표 표기법(dot notation)`
   ```
  console.log(minda.name);
   ```
    2. 대괄호 프로퍼티 접근 연산자([...])를 사용하는 `대괄호 표기법(bracket notation)`
   ```
  console.log(minda['name']);
   ```
   * 이 때 대괄호 표기법 내부에 지정하는 프로퍼티 키는 `반드시 따옴표로 감싼 문자열`이어야 한다.
   * 따옴표로 감싸지 않으면 `자바스크립트 엔진이 식별자로 해석`한다.
  ```
  var minda = {
    name: 'Hong'
  };

  console.log(minda[name]); // ReferenceError: name is not defined
  ```
  * 객체에 존재하지 않는 프로퍼티에 접근하면 undefined를 반환한다.
    * ReferenceError가 발생하지 않는 것에 주의
    ```
    var minda = {
      name: 'Hong'
    };

    console.log(minda.age); // undefined
     ```
* 대괄호 접근 연산자를 사용해야 할 때
  * 프로퍼티 키가 `식별자 네이밍 규칙`을 준수하지 않으면 무조건 `대괄호 표기법`을 사용해야 한다.
  * 단, 키가 `숫자로 이뤄진 문자열이라면 따옴표를 생략할 수 있다.`
  ```
  var minda = {
    1: 23
  };

  minda.1; // SyntaxError : Unexpected number
  minda[1];
  ```

* 예제
```
var minda = {
  `last-name`: 'Hong',
 };

minda.`last-name`; // SyntaxError: Unexpected string
minda.last-name; // NaN
minda[last-name]; // ReferenceError: last is no defined
```
```
minda.last-name; // NaN
```
  1. minda.last-name을 실행하면 엔진은 `먼저 minda.last를 평가`한다.
  2. minda 객체에는 last 프로퍼티가 없기 때문에 `undefined 평가`된다.
  3. 따라서 `undefined-name`과 같다.
  4. 엔진은 name 식별자를 찾는다.
  5. Node.js에서는 name 식별자가 없으므로 `ReferenceError가 발생`한다.
  6. 브라우저에서는 name이라는 `전역 변수(window의 프로퍼티)가 암묵적으로 존재`한다.
      * 해당 프로퍼티는 `기본값`이 빈 문자열이다.
  7. 따라서 undefined-' '취급이 되므로 `NaN`이 된다.



### 프로퍼티 값 갱신

* 갱신
  * 이미 존재하는 프로퍼티에 값을 할당하면 `값이 갱신된다.`
  ```
  var minda = {
    name : 'Hong'
  };

  minda.name = 'Lee';

  console.log(minda); // {name:'Lee'}
  ```

### 프로퍼티 동적 생성

* 동적 생성
  * `존재하지 않는 프로퍼티`에 값을 할당
    1. 프로퍼티가 동적으로 생성되어 추가
    2. 프로퍼티 값이 할당
     ```
    var minda = {
      name : 'Hong'
    };

    minda.age = 23;

    console.log(minda); // {name:'Hong', age: 23}
     ```

### 프로퍼티 삭제

* 삭제
  * delete 연산자는 객체의 프로퍼티를 삭제한다.
  ```
  var minda = {
    name : 'Hong'
  };

  minda.age = 23;

  delete minda.age;

  console.log(minda); // {name: 'Hong'}
   ```
  * delete의 피연산자는 프로퍼티 값에 접근할 수 있어야 한다.
    * 존재하지 않는 프로퍼티를 삭제하면 `아무런 에러 없이 무시`된다.
    ```
    delete minda.address;
    ```

