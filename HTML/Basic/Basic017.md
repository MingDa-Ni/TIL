# HTML - Basic
## 2022-09-29 Thu

### 객체 예고

* 객체는 여러가지 다면적 얼굴을 가지고 있다.
* Basic017에서는 `정리 정돈의 객체`를 학습한다.
  - 코드가 많아지면 정리 저돈을 위해 함수를 사용한다.
  - 하지만 함수 역시 연관된 변수가 엄청나게 많아지면 한계가 생긴다.
  - 이런 상황에서 `서로 연관된 함수와 변수`를 같은 이름으로 그루핑해서 정리 정돈하는 것이 객체이다.

```
target.style.color = 'white';
```
* 한 줄짜리 코드도 시간이 지날수록 의미가 불명확해 뜻을 파악하기 어렵다면 `로직에 이름을 부여`한다.

### 객체 쓰기와 읽기

* 배열은 `[]`로 작성하지만 객체는 `{}`로 작성한다.
  - 배열은 `정보가 순서대로 저장`된다.
  - 객체는 `순서 없이 저장`한다.
  - 객체는 `이름이 있는 정리 정돈 상자`이다.

* 객체 꺼내기
  - `점(.)`은 `객체 접근 연산자(object access operator)`이다.
  - coworkers라는 객체에 접근하는 연산자이다.
```
document.write("programmer : " + coworkers.programmer + "<br>")
```
* 객체 추가하기
```
coworkers.bookkeeper = "unseo";
```

* 객체의 이름에 `공백`이 들어갈 때

```
coworkers["data scientist"] = "taeho";
```
  - `이름에 공백`이 들어갈 때 점(.)으로는 할 수 없고 `대괄호` 안에 문자열 형태로 넣으면 된다.

### 객체와 반복문

* 객체에 있는 데이터를 모조리 가져올 때
  - 검색 엔진에서 `javascript object iterate`를 검색
  - `for .. in`을 사용한다.

* 사용된 `for`은 `객체에 있는(in) key 값을 가져오는 반복문`이다.
  - `key` 값은 "programmer", "designer", "bookkeeper", "data scientist"를 가리킨다.
  - coworkers에 있는 key를 하나하나 꺼내 코드를 실행하는 명령어가 for이다.
  - 객체 안에 들어있는 데이터 수만큼 `{}`의 코드가 실행딘다.
  - 실행될 때마다 key값이 하나하나 `변숫값`으로 설정된다.
  ```
  for(var key in coworkers) {
    document.write(key + '<br>');
  }
  ```
* key 값이 아닌 `데이터`를 가져올 때
```
for(var key in coworkers) {
  document.write(coworkers[key] + '<br>');
}
```

### 객체 프로퍼티와 메서드

* 객체는 문자열, 배열, 숫자, 함수 역시 담을 수 있다.
```
coworkers.showAll = function(){
 for(var key in coworkers) {
  document.write(key + ' : ' + coworkers[key] + '<br>');
  }
}
```
* 위의 코드는 showAll이라는 메서드를 추가하는 코드다.
  - `function showAll(){ }`과 동일하다.
  - 하지만 showAll( ) 함수 안에 coworkers의 이름이 있어 유지보수가 어렵다는 단점이 있다.
  - 이 때 showAll( ) 함수 안에서 `이 함수가 소속된 객체를 가리키는 기호`인 `this`를 사용하면 된다.
  ```
  coworkers.showAll = function(){
  for(var key in this) {
    document.write(key + ' : ' + this[key] + '<br>');
    }
  }
  ```
* showAll( )도 `coworkers에 소속`되었기 때문에 화면에 표시된다. 
  - if문으로 showAll( )을 제외하는 코드를 작성하면 된다.
* `객체에 소속된 함수는 메서드`라하며, `객체에 소속된 변수를 프로퍼티`라 한다.

### 객체의 활용

* 객체 예고에서 봤던 중복되지 않은 함수명으로 작성한 코드를 `Body`라는 변수에 객체를 담아보자.
```
var Body = {
  setColor: function(color) {
  document.querySelector('body').style.color = color;
  },
  setBackgroundColor: function(color) {
  document.querySelector('body').style.backgroundColor = color;
  }
}
```
* 객체에 프로퍼티로 setColor를 지정한 다음 function을 지정한다.
  - `프로퍼티와 프로퍼티를 구분하기 위해 콤마`를 사용한다.

```
var Links = {
setColor: function(color) {
  var alist = document.querySelectorAll('a');
  var i = 0;
  while(i<alist.length) {
    alist[i].style.color = color;
    console.log(alist[i]);
    i = i + 1;
    }
  }
}
```
* LinksSetColor( )로 객체를 만든다.
```
document.querySelector('body').style.backgroundColor = color;
```
* document가 객체고, querySelector( )는 함수이며, 객체에 소속된 메서드이다.