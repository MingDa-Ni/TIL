# JS - VanillaJS
## 2022-10-03 Mon

### 명명 규칙

- 카멜케이스
  - 단어에 공백이 필요하면 `다음 단어의 첫 문자를 대문자`로 쓴다.
  ```javascript
  myName
  veryLongName
  ```
  - 파이썬은 스네이크 케이스다.
  ```javascript
  very_long_name
  ```

### 변수 타입

* `const, let`
  - constant는 `상수`므로 변하지 않는다.
  - 변수 업데이트가 필요한 경우 `let`을 쓴다.
  - `기본적으로 const를 사용하고 업데이트시 let을 쓴다.`

* var
  - 과거에는 var만 있었지만 최근엔 사용을 지양한다.
  - `언어를 통해 보호 받지 못하고, 실수 찾기가 불편`해서이다.
  - `always const sometimes let never var`

* undefined
  - 변수가 존재해 공간이 마련되었지만 `값이 부재`해 정의되지 않은 변수

* null
  - 변수 안에 어떤 것이 없다는 것을 확실히 할 때 쓴다.
  - `비어있음`이 들어가있다.

* 자바스크립트는 프랑켄슈타인 같기 때문에 var과 같은 `과거의 것을 없앨 수 없고 쌓아가는 방식`을 이용한다.