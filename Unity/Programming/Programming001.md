# Unity - Programming
## 2022-10-06 Thu

### 변수 개념

* 변수는 `값을 저장하는 장소`이다.
  - 저장한 값을 언제든지 접근하고 수정할 수 있다.
  - 값을 `기억`하고 `재사용`하기 위해 사용

* 변수 선언
  - 사용할 `데이터의 종류`를 표시하는 것을 `변수 선언`이라 한다.
  ```
  int gold;
  ```
  - int는 `integer(정수)`의 약자다.
  - 변수 선언과 동시에 `초깃값을 할당`할 수 있다.
  ```
  int gold = 20000;
  ```

* 변수의 여러 형태
  - float
    - `floating point(부동소수점)`의 약자다.
    - 소수점이 숫자 사이를 떠다닌다.
    - 실수(소수점을 가질 수 있는 수)를 저장하는 차입이다.
  - bool
    - `boolean(불리언)`의 약자다.
    - bool은 값으로 true와 false만 사용할 수 있다.
  - string
    - `문자열`을 저장하는 타입이다.
    - 반드시 `큰따옴표("")`로 묶어야한다.

### 함수(메서드) 개념

* 함수는 `정해진 동작을 수행하는 코드` 묶음이다.
  - 함수를 사용하면 `중복 코드`를 줄일 수 있다.
  ```
  void Move(int hp, int distance) {
    체력 hp만큼 감소
    오브젝트를 distance미터 옮기기
    효과음 재생
  }
  ``` 
  ```
  void Move(int hp, int distance)
  ```
  - 외부로부터 int 타입의 값을 두 개 받겠다는 의미이다.
  - 입력을 통해 `외부에서 받은 값`을 hp와 distance라는 `변수에 대입해 내부에서 사용`한다.

* 함수의 `처리 결과`를 다른 곳에 `전달`해야할 때
  - return 키워드를 사용해 값을 `외부에 전달`할 수 있다.

  ```
  void GetRandomNumber() {
    int number = 0;
    number = 3

    return number;
  }
  ```
  - return
    - GetRandomNumber() 함수를 종료한다.
    - GetRandomNumber() 함수를 실행한 곳으로 돌아가 number의 값을 전달한다.
    - retrun으로 전달할 타입을 추측할 수 없어 반환값의 타입을 `표시`해주어야 한다.
    ```
    int GetRandomNumber() {

    }
    ```
    - 이 경우 GetRandomNumber()의 결과로 정수 int를 반환한다.
    ```
    int randomNumber = GetRandomNumber();
    ```
    - 다음과 같이 함수를 `실행`하여 반환값을 다른 변수에 저장하면 된다.
    - 함수가 끝났을 때 사용 시점으로 되돌아가 값을 전달하기 때문에 return 키워드를 사용한다.
* 모든 함수는 `return 키워드`를 가져야하지만 `void 반환은 암묵적으로 return을 반환`하기 때문에 생략 가능하다. 
* C#에서는 함수를 method(메서드)라고 부르며 `함수와 혼용 가능`하다.



