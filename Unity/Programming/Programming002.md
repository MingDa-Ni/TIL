# Unity - Programming
## 2022-10-09 Sun


### 첫 스크립트 작성

* 콘솔 창
  - `Windows > General > Console` 
  - `Collapse 탭`이 활성화된 경우 해제하는걸 추천
    - 같은 내용의 로그가 하나로 묶인다.
    - 로그 출력 순서를 확인하기 불편하다.

* `using`
    - 사용할 라이브러리 경로를 지정하여 코드를 사용할 수 있다.
    ```
    using System.Collections;
    ```
    - using 뒤의 경로를 네임스페이스(namespace)라고 한다.
    - 개발에 필요한 라이브러리를 네임스페이스로 제공
* `Start()`
    - 코드 실행이 시작되는 지점이다.
      - 상황에 맞춰 실행되는 `유니티 이벤트 메서드`다.
      - 게임 시작과 함께 실행될 코드를 넣는다.
    - 게임이 `시작될 때 자동으로 한 번` 실행된다.
* 스크립트 동작
  - 스크립트를 동작시키기 위해 `게임 월드에 존재하는 오브젝트`로 만들어야 한다.
  
### 코딩 기본 규칙

* 콘솔 출력
```
Debug.Log("출력하고 싶은 값");
```

* `using`
```
uisng System.Collections;
using System.Collections.Generic;
using UnityEngine;
```
  - using에 네임스페이스를 지정하면 코드를 현재 스크립트로 불러온다.
    - 유니티가 제공하는 여러 기능을 활용할 수 있다.
  - Debug.Log는 UnityEngine에 포함된 메서드다.

### 변수 연습

* string
  - 문자열을 저장한다.
  ```
  string characterName = "Minda";
  ```
* char
  - 문자 하나를 저장한다.
  ```
  char bloodType = 'B';
  ```
* int
  - 정수를 저장한다.
  ```
  int age = 23;
  ```
* float
  - 소수점을 가진 실수를 저장한다.
  - 타입 뒤에 `f`를 붙여야 한다.
  - `소수점 아래 7자리까지만 정확히 표현 가능`하다.
  ```
  float height = 163.5f;
  ```
* bool
  - 참과 거짓 중 하나를 저장한다.
  ```
  bool isFemaile = true;
  ```

### 메서드 연습

* GetDistance() 
  - 두 점 사이의 거리를 계산하는 메서드
  ```
  float GetDistance(float x1, float y1, float x2, float y2) {
    float width = x2 - x1;
    float height = y2 - y1;

    float distance = width * width + height * height;
    distance = Mathf.Sqrt(distance);

    return distance;
  }
  ```
  - 메서드를 선언한다.
  - `Mathf.Squrt(distance);`를 이용해 제곱근을 구한다.

* 스코프
  - `같은 이름의 변수`를 두 개 이상 선언하면 에러가 발생한다.
  - `{}`
    - 메서드의 `중괄호 밖`에서는 메서드 `내부의 구현이 보이지 않는다.`
    - 메서드 `내부에서 선언한 변수`는 메서드 `내부에서 유효`하다.
    - `스코프`는 선언된 변수나 메서드 등이 관측되는 유효 범위이다.
  - 예제 코드는 서로의 스코프가 겹치지 않기 때문에 사용 가능하다. 

