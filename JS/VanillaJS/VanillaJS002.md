# JS - VanillaJS
## 2022-10-05 Wed

<!-- 데이터를 정리하는 법, 데이터 구조 정리
가능한 최선의 방법으로 정리
자료 검색 , 삽입 , 데이터 저장 방법 >> 배열
원하는대로 작동도 안하고, 할수있는것도 없고, 금요일만 넘겨달라해도 넘겨줄 수 없음
(일주일을 호출하고 싶을 때)
const mon = "mon";
const tue = "tue";
const wed = "wed";
const thu = "thu";
const fri = "fri";
const sat = "sat";
const sun = "sun";
array는 값을 리스트로 정리하는 법
값을 추가하는 법 daysOfWeek.push("sun");

vscode 다중선택은 블록 지정 후 ctrl+d >> 같은 단어 선택 가능

const daysOfWeek = ["mon" , "tue" , "wed" , "thu" , "fri", "sat"];

console.log(daysOfWeek);

daysOfWeek.push("sun");

console.log(daysOfWeek);

--

object를 만들어야할 때
게임을 만든다고 상상

player.name
player.points
player.handsome
한개의 개체에 대해 설명하는 것이 더 잘 정돈
const player = {
  name : "minda",
  points: 10,
  fat: true, 
}
console.log(player);
console.log(player.name);
console.log(player["name"]);
객체 안에서 규칙과 밖의 규칙은 다르다.
오브젝트 안에서는 :를 사용하고, 하나 프로퍼티를 만들면 콤마를 작성한다.
배열은 모두가 같은 값을 가지니까 용도의 차이가 있다.
console.log(player.name);
console.log(player["name"]);
부르는 두가지 방법

const player = {
  name : "minda",
  points: 10,
  fat: true, 
}
console.log(player);
player.fat=false;
console.log(player);

constant는 수정할 수 없지만, 그 안의 것을 바꿀때는 괜찮음.
player이라는 오브젝트 변경시엔 에러지만 player.fat의 내부 물품은 바꾸어도 됨.
여기서의 constant는 객체임

오브젝트는 프로퍼티를 가진 데이터를 저장할 수 있게 해줌.
array는 무슨 뜻인지 몰라 저장할 수 없었지만, 오브젝트는 옆에 의미를 붙여줄 수 있음. -->