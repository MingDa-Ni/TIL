# JS - DeepDive
## 2022-11-22 Tue

### 반복문

* 반복문(loop statement)
  * 조건식의 `평가 결과가 참`인 경우 코드 블록을 실행한다.
  * 조건식을 다시 평가하여 여전히 참이라면 실행, 거짓일 때까지 반복한다.
* 대체 기능
  * `배열 순회`할 때 forEach
  * `객체 프로퍼티 열거`할 때 for...in문
  * `이터러블을 순회`할 수 있는 for...of문
  
#### for

* 조건식
  * `거짓으로 평가될 때까지` 코드 블록 반복 실행
  * for문의 i 변수는 반복을 의미하는 iteration의 i이다.
  ```
  for(변수 선언문; 조건식; 증감식;)
  ```
  * for문의 변수 선언문, 조건식, 증감식은 옵션이다.
  * 어떠한 것도 선언하지 않으면 무한 루프가 된다.
  * for문은 중첩하여 사용할 수 있다.

#### while

* 조건식
  * `평가 결과가 참이면` 코드 블록을 반복 실행한다.
  * 조건식 평가 결과가 `불리언 값이 아니라면` 불리언 값으로 강제 변환
  ```
  var count = 0;

  while (count < 2) {
    console.log(count); // 0 1
    count++;
  }
  ```
  * 조건식의 평가 결과가 언제나 참이면 무한루프
  ```
  while (true) { ... }
  ```
* 구분
  * for문은 `반복 횟수가 명확`할 때, while문은 `반복 횟수가 불명확할 때` 주로 사용
  * while문은 조건문 평가 결과가 거짓이면 `코드 블록을 실행하지 않고 종료`
  

#### do...while

* 조건식
  * 코드 블록을 초기에 `먼저 실행`하고 조건식을 평가
  * 무조건 1회는 실행된다.
  ```
  var count = 0;

  do {
    console.log(count); // 0 1
    count++;
  } while (count < 2);
  ```

* break문
  * break는 `레이블 문, 반복문, switch문에서` 코드 블록을 탈출한다.
    * 그 외에 사용하면 `SyntaxError(문법 에러)`가 발생한다.
  * 레이블 문(label statement)
    * 식별자가 붙은 문이다.
    ```
    kind : console.log('kind');
    ```
    * 실행 순서를 제어하는데 사용한다.
    * case문과 default문도 레이블 문이다.
    * 중첩된 for문에서 `외부 for문을 탈출`하려면 레이블 문을 사용한다.
    ```
    outer : for(var i=0; i<5; i++) {
      for (var j = 0; j < 5; j++) {
        if (i+j === 5) break outer;
        console.log(`inner [${i}, ${j}]);
      }
    }
    ```
    * `레이블 문은 중첩된 for 문 외부로 탈출할 때 유용하다.`
    * 그 외에는 `프로그램 흐름 복잡성과 가독성 저하`로 권장하지 않는다.
  * break문은 반복문을 더 이상 진행하지 않아도 될 때 `불필요한 반복`을 회피할 수 있어 유용하다.
* countinue문  
  * 반복문의 코드 블록 실행을 `현 지점에서 중단`하고 증감식으로 실행 흐름을 이동
    * 반복문을 탈출하는 개념이 아니다.
  ```
  var string = 'Mindani Haru';
  var serch = 'i';
  var count = 0;

  for (var i = 0; i<string.length; i++) {
    if(string[i]!==serch)continue;
    count++;
  }

  ```
  * 실행문이 길면 사용한다.
    * if문으로 실행하게 되면 들여쓰기가 한 단계 더 깊어지기 때문이다.
    * 가독성 측면에서 좋다.
