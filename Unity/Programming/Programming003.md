# Unity - Programming
## 2022-10-09 Sun

### 제어문

* if문
  - 미연시 특정 분기처럼 if문은 조건을 참과 거짓으로 평가한다.
  ```
  public class MisoneoCode : MonoBehaviour {
    void Start() {
      int love = 100;

      if (love > 70)
      {
        Debug.Log("굿엔딩 : 초-미소녀 겟또!");
      }

      if (love <= 70)
      {
        Debug.Log("배드엔딩 : 영장 발부");
      }
    }
  }
  ```

* if .. else문
  - 조건이 거짓일 때 처리를 구성할 수 있다.

* else if문
  - else문에 조건을 덧붙일 수 있다.
  ```
  int love = 50;

  if (조건 1){
    
  }
  else if (조건 2){

  }
  else{

  }  
  ```

* 논리 연산자
  - `둘 이상의 조건`을 함께 사용해야할 때 사용하는 연산자
    - A && B → `A 그리고 B`
    - A :: B → `A 또는 B`
    - !A → `A가 아니다`
  
* `for문`
  - 순번을 반복할 때
  ```
  for (초기화; 조건; 갱신){

  }
  ```

* `while문`
  - 조건을 `만족하는 동안` 반복할 때
    - 살아있는 동안 데미지가 깎이는 상태
    ```
    while (조건)
    {

    }
    ```

### 배열

* 배열은 나열된 여러 값을 하나의 변수로 다룰 수 있는 타입이다.
  - 호실이 표기된 호텔방으로 가정
  - 방마다 값이 들어가있고 호실 번호를 알면 찾아갈 수 있다.
  - 호실번호는 `인덱스(Index)`이며 각 방을 `배열의 요소` 또는 `배열의 원소`라고 부른다.
  ```
  int[] students = new int[5];
  ```
    - new 키워드는 `어떠한 타입의 오브젝트를 생성`한다는 의미다.
    - new를 이용해 5개의 방을 가진 int 배열을 생성하여 students 변수에 할당했다.

* 배열은 반복문과 연관이 깊다.
```
for (int i=0; i<students.Length; i++)
{
  Debug.Log((i+1)+"번 캐릭터 체력: "+students[i]);
}
```