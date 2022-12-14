# JS - DeepDive
## 2022-12-18 Sun

## 스코프

### 정의

* 스코프
  * 식별자는 `선언된 위치`에 의해 `다른 코드가 자신을 참조`할 수 있는 유효 범위가 결정
  * 즉, 스코프는 식별자가 유효한 범위이다.
  * 식별자
    * 변수 이름
    * 함수 이름
    * 클래스 이름 등
* 두 개의 변수가 이름이 같은 경우
  * 어떤 변수를 참조할 지 결정
  * `식별자 결정(identifier resolution)`
  * 스코프를 통해 어떤 변수를 참조할 지 결정
  * 스코프 : `식별자를 검색할 때 사용하는 규칙`

#### 렉시컬 환경
* `렉시컬 환경(lexical environment)` 
  * 코드가 어디서 실행되고 어떤 코드가 있는지
  * 코드의 문맥(context)는 렉시컬 환경으로 이뤄진다.
  * 이를 구현한 것이 실행 컨텍스트
* `실행 컨텍스트(execution context)`
  * 모든 코드는 실행 컨텍스트에서 평가되고 실행
  * 스코프와 깊은 관련

#### 식별자

* 식별자
  * 어떤 값을 구별해야하므로 `유일(unique)`
  * 하나의 값은 유일한 식별자에 연결(name bindeing)
* 폴더 별로 파일을 묶는 것처럼 `스코프`를 통해 식별자인 `변수 이름의 충돌을 방지`하는 것이다.
* 동일한 스코프 내에서 `식별자는 유일`해야 한다.
* 다른 스코프에는 `같은 식별자`를 사용할 수 있다.
* 따라서, 스코프는 `네임 스페이스`다.

#### 스코프

1. 식별자가 유효한 범위
2. 식별자를 검색할 때 사용하는 규칙
3. 네임 스페이스

### 종류

1. 전역 
     * 전역에서 선언
     * 전역 스코프
     * 전역 변수
2. 지역
     * 지역에서 선언
     * 지역 스코프
     * 지역 변수

#### 전역 스코프

* 전역
  * 코드의 가장 바깥 영역
  * 전역 스코프(global scope)를 만듦
  * 전역 변수(global variable)가 됨
* `전역 변수는 어디서든지 참조할 수 있다.`
* 함수 내부에서도 참조할 수 있다.

#### 지역 스코프
* 지역
  * 함수 몸체 내부
  * 지역 스코프(local scope)를 만듦
  * 지역 변수(local variable)가 됨
* `자신의 지역 스코프와 하위 지역 스코프에서 유효`
* 지역변수를 전역에서 참조하면 에러가 발생한다.

### 스코프 체인

* 함수의 중첩
  * 함수 몸체 내부에 함수가 정의
    * 내부에 정의한 함수는 `중첩 함수(nested function)`
    * 중첩 함수를 포함하는 함수는 `외부 함수(outer function)`
  * `지역 스코프도 중첩될 수 있다.`
  * 스코프가 `함수의 중첩`에 의해 `계층적 구조`를 갖는다.

* `스코프 체인(scope chain)`
  * 실행 컨텍스트의 렉시컬 환경을 단방향으로 연결(chaining)
  * 스코프가 계층적 연결
  * `변수를 참조하는 코드의 스코프`에서 시작해 `상위 방향`으로 이동하며 선언된 `변수를 검색(identifier resolution)`
  * 물리적인 실체로 존재
    1. 자바스크립트 엔진이 자료구조인 `렉시컬 환경(Lexical Environment)`를 생성
    2. 변수 식별자가 자료구조에 키로 등록
    3. 변수 할당이 일어나면 변수 식별자에 해당하는 값을 변경

* 렉시컬 환경(Lexical Environment)
  * 함수의 렉시컬 환경은 함수가 호출되면 곧바로 생성

#### 변수 검색

* 스코프 체인에 의해 변수 검색
   * 참조하는 코드의 스코프에서 시작해 `상위 스코프 방향`으로 이동하며 변수 검색
   * 절대 하위 스코프로 검색하지 않는다.
     * `상위 스코프에서 유효한 변수는 하위 스코프에서 자유롭게 참조`
     * 하위 스코프에서 유효한 변수를 상위 스코프에서 참조할 수 없다.
   * 상속(자식의 자산을 부모가 사용할 수 없음)과 동일 

#### 함수 검색

* 함수 선언문 정의
  1. 런타임 이전에 함수 객체가 생성된다.
  2. 함수 이름과 동일한 이름의 `식별자를 암묵적 생성`
  3. 생성된 함수 객체를 할당

```
funciton ex() {
  console.log('minda');
}

funtion test() {
  funtion ex(){
    console.log('inji');
  }

  ex();
}
```

### 함수 레벨 스코프

* 정의
  * var 키워드는 `함수의 코드 블록만을 지역 스코프로 인정`
  * 지역은 `함수 몸체 내부`를 의미한다.
  * 지역은 지역 스코프를 만든다.
    * `코드 블록이 아닌 함수에 의해서만 지역 스코프가 생성`
    * 코드 블록 안에서 의도치 않은 재할당이 생성될 수 있음
    ```javascript
    var i = 10;

    for (var i = 0; i<5; i++>){
      console.log(i);
    }

    console.log(i);
    ```

* 블록 레벨 스코프(block level scope)
  * C나 자바
  * `모든 코드 블록(if, for, while, try/catch 등)`이 지역 스코프를 만듦
  * ES6에 도입된 LET, CONST는 블록 레벨 스코프를 지원


### 렉시컬 스코프

* 상위 스코프 결정하는 법에 대한 고찰
  1. `함수를 어디서 호출`했는지
  2. `함수를 어디서 정의`했는지

* `호출` 기준
  * test 함수의 상위 스코프 
    * ex의 지역 스코프
    * 전역 스코프
  * `동적 스코프(dynamic scope)`
    * 호출 시점에 상위 스코프를 결정하기 때문
* `정의` 기준
  * test 함수의 상위 스코프
    * 전역 스코프
  * `렉시컬 스코프(lexical scope)` 또는 `정적 스코프(static scope)`
    * 함수 정의가 평가되는 시점에 상위 스코프가 결정되기 때문
    * 자바스크립트를 포함한 대부분의 언어는 렉시컬 스코프

#### 자바스크립트는 . . .
* 렉시컬 스코프
  * 함수를 어디서 정의했는지
    * 호출된 위치는 어떠한 영향도 주지 않는다.
  * `언제나 자신이 정의된 스코프`가 함수의 상위 스코프다.
  * 함수 정의로 실행되어 상성된 함수 객체는 `상위 스코프`를 기억한다.
    * 함수의 상위 스코프를 참조해야 할 필요가 있기 때문

```javascript
var a = 1;

function ex(){
  var a = 10;
  test();
}

function test() {
  console.log(a);
}
```
```javascript
ex();
test();
```
* 예제
  * test 함수는 전역에서 정의된 함수다.
    1. 전역 코드가 실행되기 전에 함수 객체를 생성
    2. 자신이 정의된 스코프(전역 스코프)를 기억
    3. 언제나 자신이 기억하고 있는 전역 스코프를 상위 스코프로 사용
  * 따라서 호출하면 전역 변수 a의 값인 1을 두 번 출력한다.