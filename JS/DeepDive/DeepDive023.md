# JS - DeepDive
## 2022-12-08 Thu

### 참조에 의한 전달과 외부 상태의 변경

* 매개변수 전달
  * 함수 몸체 내부에서 변수와 동일하게 취급된다.
    * 값에 의한 전달
    * 참조에 의한 전달
```
function chageVal(primitive, obj){
  primitive += 100;
  obj.name='Kim';
}

var num = 100;
var cha = {name: 'Lee'};

changeVal(num, person);
```
