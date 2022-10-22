# JS - VanillaJS
## 2022-10-23 Sun

## event에 반응하라

### title 클릭시 색상 변경

* 1단계
  - 한 번 클릭했을 때 파란색으로 변경
    1. h1의 색상을 얻는다.
    ```
    console.log(h1.style.color);
    ```
    2. h1의 색상을 설정한다.
    ```
    h1.style.color = "blue";
    ```
    3. h1의 color를 가져온다.
    ```
    console.log(h1.style.color);
    ```
  - 완성 코드
  ```
  function handleTitleClick(){
    console.log(h1.style.color);
    h1.style.color = "blue";
    console.log(h1.style.color);
  }
  ```
* 2단계
  - 가져온 color가 blue라면 tomato로 바꿔주세요.
  ```
  if(h1.style.color === 'blue'){
    h1.style.color = 'tomato';
  } else {
    h1.style.color = 'blue';
  ```
* 3단계
    1.  코드 개선 및 중복 제거
    ```
    const currentColor = h1.style.color;
    ```
    2. 변경될 변수 지정
    ```
    let newColor;
    ```
    3. 이 자체로 newColor는 h1에 영향을 안주므로 수정
    ```
    h1.style.color = newColor;
    ```
  - 완성 코드 
  ```
  const h1 = document.querySelector("div.hello:first-child h1");

  function handleTitleClick(){
   const currentColor = h1.style.color;
   let newColor;
   if(currentColor === 'blue'){
     newColor = 'tomato';
   } else {
     newColor = 'blue';
   }
   h1.style.color = newColor;
  }
  ```