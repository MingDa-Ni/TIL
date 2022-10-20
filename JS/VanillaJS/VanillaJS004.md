# JS - VanillaJS
## 2022-10-21 Fri

### return

* 데이터를 얻어 응용할 수 있다.
  ```
  const calculator = {
   plus : function(a, b){
     return a+b;
   },
  }
  ```
  - return하면 함수는 그대로 끝난다.
  ```
   plus : function(a, b){
     return a+b;
     console.log('minda');
   },
   ```  
   - `console.log('minda');`는 실행되지 않는다.
  
### conditionals

* parseInt()
  - 첫 번째 인자를 문자열로 반환해 `NaN`이나 `정수`를 반환한다.
  ```
  const age = parseInt(prompt("How old are you?"));
  ```
  - prompt에 입력 받을 숫자가 parseInt() 처리된다.

* isNaN()
  - NaN을 판별하는 함수이다.
  - NaN은 (==, ===)로 `판단할 수 없다.`
    1. NaN == NaN
    2. NaN === NaN
    - 둘 모두 false 처리
  ```
  if(isNaN(age)){
    console.log("Please write a number");
  } else {
    console.log("Thank you for writing your age.")
  }
  ```
* `복잡`한 conditionals
  ```
  if ((a&&b) || (c&&d)) { 
  }
  ```
  - `(c&&d)부터 실행되고,` (a&&b), 그리고 || or 연산자가 실행된다.
  - else는 선택사항이다.
