# HTML - Basic
## 2022-09-17 Sat

### 박스 모델 응용
* 개발자 도구 : F12 혹은 마우스 우클릭 `검사`이다.
* 박스 모델을 가지고 있는 태그에 커서를 갖다대면 박스 모델 상황이 나타난다. 
<br><br>
* 밑줄을 긋는 방법
```
border-bottom: 1px solid gray;
```
* 목차에 옆줄을 긋는 법
```
ol {
  border-right: 1px solid gray;
}
```
 1. 테두리가 끝쪽으로 가있는 이유
 2. `<ol> 태그는 블록 레벨 엘리먼트`이기 때문이다.
 3. `width 값을 지정`하면 된다.
```
ol {
  border-right: 1px solid gray;
  width: 100px;
}
```

### 그리드 소개

* 본문과 목차를 나란히 작성하는 방법: `그리드(Grid)`
<br><br>
* 각 단어에 테두리를 주고 나란히 배치하기
  1. 나란히 배치하기 위해 태그로 묶어야한다.
  2. 어떠한 의미도 없는 태그 `<div>`
  3. `<div>`: division의 약자
  4. `div 태그는 블록 레벨 엘리먼트이다.`
  5. 똑같은 목적으로 고안된 `인라인 엘리먼트는 <span>`이다.
  6. 그리드의 부피감을 알아보는 코드
```
<style>
    div {
      border: 5px solid gray;
    }
</style>
```
* 두 개의 태그를 나란히 놓기 위한 그리드는 `두 개의 태그를 감싸는 부모가 필요`하다.
```
<div id="grid">
```
```
<div>
  <div>MINDA</div>
  <div>HARU</div>
</div>
```
* `display`를 통해 `태그의 표시되는 방법을 변경`한다.
```
grid-template-columns: 150px 1fr;
```
```
#grid {
  border: 5px solid pink;
  display: grid;
  grid-template-columns: 150px 1fr;
}
```
* 150px `1fr` : `남은 공간을 다 쓴다는 의미`
* 2fr 1fr : 영억을 2:1로 나눠 사용한다는 의미
<br><br>
* 그리드는 최신 기능이기 때문에 `현재 환경에서 사용할 수 있는지` 판단해야 한다.
* Can I Use : `https://caniuse.com`

### 그리드 써먹기

* 나란히 놓고 싶은 대상은 `<ol>` 태그와 `<h2>,<p>` 태그이다.
* `<h2>,<p>` 태그를 묶기 위해 `의미도 기능도 없는 <div> 태그를 사용`한다.
  1. `<div>` 태그와 `<ol>` 태그를 한 번 더 묶기 위한 `부모 태그`가 필요하다.
  2. 바깥쪽 `<div>` 태그를 그리드로 지정하기 위해 id 값을 `grid`로 지정한다.
```
<div>
  <h2>
  ... 생략 ...
  <p>
<div>
```
```
<div id="grid">
  <ol>
    <li><a href="1.html" class="saw">HTML</a></li>
    <li><a href="2.html" class="saw" id= "active">CSS</a></li>
    <li><a href="3.html">JavaScript</a></li>
  </ol>
  <div>
  <h2>MINDA란 무엇인가?</h2>
  <p> </p>
</div>
```
```
<style>
  #grid {
    border: 5px solid pink;
    display: grid;
    grid-template-columns: 150px 1fr;
  }
</style>
```
* 개발자 도구의 박스 모델을 `더블클릭하여 값을 조정할 수 있다.`
* padding으로 인해 글이 밀리면 해당 영역을 조정하기 위해 `<div>`에 id 값을 지정하고 다음과 같이 작성한다.
```
# article {
  padding-left: 25px;
}
```

### 코드 수정

* 나중에 다른 리스트가 본문에 추가되면 가독성이 떨어지므로 `<ol> 태그를 grid <ol>로 지정`한다.
```
#grid ol {
  border-right: 1px solid gray;
  width: 100px;
  margin: 0;
}
```