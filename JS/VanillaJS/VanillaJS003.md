# JS - VanillaJS
## 2022-10-21 Fri

### argument(인수)

* function을 실행하는 동안 `어떤 정보를 function에 보낼 수 있는가?`
  - 인수가 들어오면 `nameOfPerson이라는 변수`로 쓰인다.

  ```javascript
  function sayHello(nameOfPerson){ 
    console.log("Hello! my name is C"+nameOfPerson);
  }
  ```
  - 함수 호출은 아래와 같이 한다.
  ```javascript
  sayHello('nico');
  sayHello('dal');
  sayHello('lynn');
  ```
  - argument는 여러 개 설정할 수 있다.
  ```javascript
  function sayHello(nameOfPerson, age){
  console.log("Hello! my name is "+ nameOfPerson + "ane I'm " + age);
  }
  ```
  - 함수 호출은 순서대로 한다.
  ```javascript
  sayHello('nico', 10);
  sayHello('dal', 23);
  ```
* 인자의 존재
  - 함수 안에서만 인자 변수가 존재한다.
  - 함수 밖에서 인자를 호출하면 에러 메시지가 뜬다.
  ```javascript
  function sayHello(nameOfPerson){

  }
  console.log(nameOfPerson);
  ```

* 오브젝트 안에서는 다르게 선언한다.
  ```javascript
  const player = {
    name:"Minda",
    sayHello: function(otherPersonName){
     console.log('hello! + otherPersonName');
    },
  };
  ```
  - 오브젝트 안에 함수를 넣을 수 있다.
  ```javascript
  console.log(player.name)
  player.sayHello('lynn');
  ```

* NoN은 `Not a Number`을 가리킨다.