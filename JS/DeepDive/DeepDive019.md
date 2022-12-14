# JS - DeepDive
## 2022-12-01 Thu

#### 얕은 복사

* 얕은 복사(shallow copy)
  1. 한 단계까지만 복사하는 것 
       * 객체에 중첩되어 있는 객체의 경우 참조 값을 복사
       * 원본과는 다른 객체
  ```javascript
  const obj = { x: {y:1}};

  const a1 = {...obj};
  ```
  ```javascript
  console.log(a1===obj); // false
  console.log(a1.x===ojb.x); // true
  ```
  2. 객체를 할당한 변수를 다른 변수에 할당하는 것
  ```javascript
  const obj = {x:1};

  const a2 = obj;
  ```
#### 깊은 복사

* 깊은 복사(deep copy)
  1. 객체에 중첩되어 있는 객체까지 모두 복사하는 것
       * 객체에 중첩되어 있는 객체까지 모두 복사해 `원시값처럼 완전한 복사본`
       * 원본과는 다른 객체
  ```javascript
  const obj = { x: {y:1}};

  const a2 = _.cloneDeep(obj);
  ```
  ```javascript
  console.log(a2===obj); // false
  console.log(a2.x===ojb.x); // false
  ```
  2. 원시 값을 할당한 변수를 다른 변수에 할당
  ```javascript
  const v = 3;

  const a1 = v;
  ```
#### 참조에 의한 전달

* 여러 개의 식별자가 하나의 객체를 공유한다는 것
```javascript
var character = {
  name: 'Cream'
};

var copy = character; // 얕은 복사
```
* 참조에 의한 전달
  * 객체를 가리키는 변수(character)가 다른 변수(copy)에 할당되면 `원본의 참조 값이 복사되어 전달`된다.
    1. 원본 character를 사본 copy에 할당
    2. 원본 character의 참조 값을 복사해서 copy에 저장
  * 이 경우 원본과 사본은 `모두 동일한 객체`를 가리킨다.
    * `두 개의 식별자가 하나의 객체를 공유`하게 된다.
    * 원본 또는 사본 중, `어느 한쪽이 객체를 변경`하면 서로 영향을 주고 받는다.

* `값에 의한 전달`과 `참조에 의한 전달`
  * 식별자가 기억하는 `메모리 공간에 저장되어 있는 값을 복사해서 전달`하는 것은 동일하다.
  * 다만 식별자가 기억하는 메모리 공간의 값에 차이가 있다.
    1. 변수에 저장되어 있는 값이 원시 값
    2. 변수에 저장되어 있는 값이 참조 값
         * 엄연히 말하면 `값에 의한 전달`만 존재한다.
         * 자바스크립트에서 `정확한 용어가 존재하지 않는` 이유이다.
         * 이러한 연유로 `공유에 의한 전달`이라고 표현하는 경우도 있으나, 공식적인 용어는 아니다.
  * `포인터`가 존재하는 다른 언어의 `참조에 의한 전달`과 의미가 일치하지 않는다.

* 마무리 퀴즈
```javascript
var cha1 = {
  name: 'Lema'
};
var cha2 = {
  name: 'Lema'
};
```
```javascript
console.log(cha1 === cha2);
console.log(cha1.name === cha2.name);
```

* `===` 연산자는 변수에 저장되어 있는 값을 `타입 변환하지 않고 비교`한다.
  * 객체를 할당한 변수는 참조 값을 가진다.
  * 변수를 할당한 변수는 원시 값을 가진다.
* 객체 리터럴은 평가될 떄마다 객체를 생성한다.
  * cha1과 cha2가 가리키는 변수는 `내용은 같지만 다른 메모리에 저장된 별개의 객체`이다.
  * 하지만 프로퍼티 값을 참조하는 cha1.name은 값으로 평가되는 표현식이다.
  * 두 프로퍼티 값 모두 원시값 `Lema`로 평가된다.