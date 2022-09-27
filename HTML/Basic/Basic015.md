# HTML - Basic
## 2022-09-27 Tue

### 배열

* 살림이 늘어나면 서랍이나 수납상자에 넣는 것과 같다.
* 데이터가 많아짐에 따라 `데이터 중 서로 연관있는 것들을 잘 정돈해 담아두는 수납상자`가 `배열(array)`이다.
* 문자열은 `따옴표에서 따옴표로` 끝나듯 배열은 `대괄호로 시작해 대괄호로` 끝난다.
```
var coworkers = ["egoing", "leezche"];
```

### 배열 사용법

* 배열에 들어있는 항목 가져오는 방법
```
document.write(coworkers[0]);
```

* 배열에 들어있는 값의 개수를 체크
  - 검색 엔진에서 `javascript array count`를 검색
```
document.write(coworkers.length);
```

* 데이터 추가
  - 검색 엔진에서 `javascript array add data`를 검색
  - push()는 `배열의 끝에 데이터를 추가`하는 역할이다.
```
coworkers.push('duru');
coworkers.push('taeho');
```

### 반복문

* 프로그램은 기본적으로 `위에서부터 아래로 순서대로 코드가 실행`된다.
* 반복문 키워드 : `while`
  - while 괄호 안에는 `불리언 데이터 타입`이 들어온다.
  - while 괄호 안의 내용이 `true인 동안에는 코드가 반복 실행된다.`
  - while 괄호 안의 내용이 `false가 될 때까지` 실행된다.
* 반복문은 `프로그램의 흐름을 제어`하는 `제어문`이다.

### 배열과 반복문

* 배열에 담긴 데이터를 순차적으로 꺼내서 `<li>`라는 태그를 만드는 기능
```
var minda = ['sleep', 'dance', 'watch', 'eat', 'teach'];

... 생략 ...

var i = 0;
while(i<minda.length) {
  document.write('<li>' + minda[i] + '</li>');
  i = i + 1;
}
```
* `배열`은 순서대로 `연관된 데이터를 정리 정돈`하는 것이다.
* `반복문`은 순서대로 `배열에 담긴 데이터를 하나씩 꺼내 자동화 처리`를 하는 것이다.
  - 두 기능은 서로 잘 연관되어 사용된다.


### 배열과 반복문의 활용

* 야간 모드일 때 링크가 밝게 표시되고 주간 모드일 때 어두운 계열로 링크가 표시되도록
* 웹 페이지의 모든 `<a>` 태그를 가져오기
  - 검색어 : `javascript get element by css selector multiple`
  - querySelectorAll을 사용
  ```
  document.querySelectorAll('a');
  ```
  ```
  NodeList(4) [a, a, a, a];
  ```
  * 위의 코드에서 `대괄호`는 노드 리스트다.
<br><br>
* 반복문에서 링크의 글자색 변경

```
var alist = document.querySelectorAll('a');
var i = 0;
while(i<alist.length) {
    alist[i].style.color = 'powderblue';
    console.log(alist[i]);
    i = i + 1;
}
```
   ```
    <input type="button" value="night" onclick="
      var target = document.querySelector('body');
      if(this.value ==='night') {
      target.style.backgroundColor = 'black';
      target.style.color = 'white';
      this.value = 'day';

      var alist = document.querySelectorAll('a');
      var i = 0;
      while(i<alist.length) {
      alist[i].style.color = 'powderblue';
      console.log(alist[i]);
      i = i + 1;
      }
    } else {
      target.style.backgroundColor = 'white';
      target.style.color = 'black';
      this.value='night';

      var alist = document.querySelectorAll('a');
      var i = 0;
      while(i<alist.length) {
      alist[i].style.color = 'blue';
      console.log(alist[i]);
      i = i + 1;
      }
    }
    ">
    ```