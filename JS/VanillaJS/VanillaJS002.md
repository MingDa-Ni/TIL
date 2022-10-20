# JS - VanillaJS
## 2022-10-05 Wed

### array

* 데이터 정리
  - 데이터를 가장 `최선의 방법`으로 정리한다.
  - `자료 검색, 삽입`에 용이한 데이터 저장 방법이다.
  ```
  const daysOfWeek = ['mon', 'tue', 'wed', 'thu', 'fri', 'sat'];
  ```
* 데이터 삽입
  ```
  daysOfWeek.push('sun');
  ```
* 같은 단어 `다중 선택`
  - ctrl+d를 눌러 한번에 수정 가능


### object

* 게임
  - player.name
  - player.points
  - player.handsome

* 정돈
  ```
  const player = {
    name : 'minda',
    points : 10,
    mana : 25,
  }
  ```
  - `object는 property를 가진 데이터를 저장할 수 있다.`
  - 배열과 다르게 의미를 붙여줄 수 있다.
* object를 부르는 `두 가지` 방법
  ```
  console.log(player.name);
  ```
  ```
  console.log(player['name']);
  ```
* constant 자체는 수정 불가하나 내부를 바꾸는 것은 가능하다.
  - A반, B반, C반은 동일하나 구성원은 바뀔 수 있는 것과 같다.
  - 위의 코드에서 const는 `player object를 가리킨다`


