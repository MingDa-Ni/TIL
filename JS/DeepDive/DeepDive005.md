# JS - DeepDive
## 2022-11-14 Mon

### 언매니지드와 매니지드

* unmanaged language
  * 개발자가 명시적으로 `메모리 할당과 해제`를 하기 위해 `저수준 메모리 제어 기능`을 제공한다.
  * 메모리 제어를 `개발자가 주도`할 수 있다.
  * `개발자의 역량에 따라 최적의 성능`을 확보할 수 있다.
* managed language
  * 개발자가 `명시적으로 메모리를 할당하고 해제할 수 없다.`
  * 메모리 해제는 가비지 콜렉터가 수행하며 개발자가 관여할 수 없다.
  * 개발자가 `일정한 생산성`을 확보할 수 있으나 손실은 감수해야 한다.

### 식별자 네이밍 규칙

* 식별자
  * `어떤 값을 구별해 식별해낼 수 있는 고유한 이름`이다.
    1. 특수문자를 제외한 `문자, 숫자, 언더스코어(_), 달러 기호($)`를 포함할 수 있다.
    2. 식별자는 숫자로 시작하는 것을 `허용하지 않는다.`
    3. 예약어는 식별자로 사용할 수 없다.
  * 변수 이름도 `네이밍 규칙`을 따라야 한다.
  * 자바스크립트는 대소문자를 구별한다.
    ```
    var firstname;
    var firstName;
    ```
* 주석
  * 변수 선언에 `별도의 주석`이 필요하다면 `변수의 존재 목적을 명확히 드러내지 못하는 것`이다.
* 네이밍 컨벤션(naming convention)
  * 변수나 함수 
    * 카멜 케이스(camelCase)
    ```
    var firstName;
    ```
  * 생성자 함수와 클래스 이름
    * 파스칼 케이스(PascalCase)
    ```
    var FirstName;
    ```
 