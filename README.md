## mission-1 해설

> ### 1. 첫 번째 ui (꿀생강차)
- 로고와 문장을 하나의 `<div>`로 감싸서 `display: flex;`를 주고 `flex-direction: column;`으로 방향을 바꿔준다.
- 로고와 문장을 감싼 `<div>`와 상품사진을 감싸는 `<div>`를 만들고 `display: flex;`를 준다.
- Figma에서 추출한 css 속성을 넣어준다.
- 버튼은 2개를 생성
  - active 전, 후 버튼 - `position: absolute;`를 준다.(각 ui의 상위 div에 `position: relative;`)
``` html
<div class="ui_1">
   <div class="wrapper">
      <img src="./images/honeytea_logo.png" alt="오뚜기" class="honeyTea_logo">
      <p class="descrpition_honeyTea">따뜻한 차 향기</p>
   </div>
   <img src="./images/honeytea.png" alt="꿀생강차" class="honeyTea_img">
   <button class="btn" type="button"><span class="btn_icon">></span></button>
   <button class="btn_buy" type="button">
      <span class="descrpition_buy">구매하기</span>
      <span class="btn_icon">></span>
   </button>
</div>
```
``` css
/* 따뜻한 차 향기 ui_1 */
.ui_1 {
   width: 502px;
   height: 310px;
   background-color: #fff;
   margin: auto;
   display: flex;
   justify-content: space-between;
   gap: 24px;
   position: relative;
   border: 1px solid #ccc;
}
.wrapper {
   display: flex;
   flex-direction: column;
   gap: 13px;
}
.honeyTea_logo {
   width: 112px;
   height: 67px;
   margin-left: 73px;
   margin-top: 75px;
}
.descrpition_honeyTea {
   width: 200px;
   height: 37px;
   font-weight: 700;
   font-size: 24px;
   line-height: 36px;
   text-align: center;
   color: rgba(78, 78, 78, 1);
   margin: 0;
   margin-left: 28px;
}
.honeyTea_img {
   width: 222px;
   height: 270px;
   margin-top: 20px;
   margin-right: 28px;
}
```
#### 결과물
![](https://velog.velcdn.com/images/thdgusrbek/post/c6384546-bf9b-4bb4-a51c-4d876abb44ec/image.png)<br><br><br><br>

> ### 2. 두 번째 ui (핸드크림)
- 로고, 문장, 상품 사진을 모두 `<div>`로 감싸서 block으로 만든다.
- Figma에서 추출한 css 속성을 넣어준다.
- 버튼은 모든 ui(꿀생강차, 핸드크림, 보리차)가 같은 방식을 사용
``` html
<div class="ui_2">
   <div>
      <img src="./images/handcream_logo.png" alt="Kamill" class="handcream_logo">
   </div>
   <p class="descrpition_handcream">핸드크림 모음</p>
   <div>
      <img src="./images/handcream.png" alt="핸드크림" class="handcream_img">
   </div>
   <button class="btn" type="button"><span class="btn_icon">></span></button>
   <button class="btn_buy" type="button">
      <span class="descrpition_buy">구매하기</span>
      <span class="btn_icon">></span>
   </button>
</div>
```
``` css
/* 핸드크림 모음 */
.ui_2,{
   width: 243px;
   height: 310px;
   border: 1px solid #ccc;
   background-color: #fff;
   position: relative;
}
.ui_2 {
   text-align: center;
}
.handcream_logo {
   width: 114px;
   height: 42px;
   margin-top: 14px;
}
.descrpition_handcream {
   width: 200px;
   height: 27px;
   margin: auto;
   margin-top: 10px;
   color: rgba(85, 85, 85, 1);
   text-align: center;
   font-size: 18px;
   font-style: normal;
   font-weight: 700;
   line-height: 27px;
}
.handcream_img {
   width: 195px;
   height: 196px;
   margin-top: 7px;
}
```
#### 결과물
![](https://velog.velcdn.com/images/thdgusrbek/post/6a4aade5-0349-48e5-85b7-0024b3634f0a/image.png)<br><br><br><br>

> #### 3. 세 번째 ui (보리차)
- `ui_3` 클래스에 `position: relative;`를 준다.
- 로고, 문장, 상품 사진에 `position: absolute;`를 주어 `ui_3` 클래스를 기준으로 position을 잡아준다. (Figma에서 추출한 길이를 넣어준다)
- Figma에서 추출한 css 속성을 넣어준다.
- 버튼은 모든 ui(꿀생강차, 핸드크림, 보리차)가 같은 방식을 사용
``` html
<div class="ui_3">
   <img src="./images/tea_logo.png" alt="gomgom" class="tea_logo">
   <p class="descrpition_tea">고소한 보리차</p>
   <img src="./images/tea.png" alt="보리차" class="tea_img">
   <button class="btn" type="button"><span class="btn_icon">></span></button>
   <button class="btn_buy" type="button">
      <span class="descrpition_buy">구매하기</span>
      <span class="btn_icon">></span>
   </button>
</div>
```
``` css
/* 고소한 보리차 */
.ui_3 {
   width: 243px;
   height: 310px;
   border: 1px solid #ccc;
   background-color: #fff;
   position: relative;
}
.tea_logo {
   width: 114px;
   height: 42px;
   position: absolute;
   top: 14px;
   left: 64px;
}
.descrpition_tea {
   width: 200px;
   height: 27px;
   color: rgba(85, 85, 85, 1);
   text-align: center;
   font-size: 18px;
   font-style: normal;
   font-weight: 700;
   line-height: 27px;
   margin: 0;
   position: absolute;
   top: 66px;
   left: 21px;
}
.tea_img {
   width: 195px;
   height: 196px;
   position: absolute;
   top: 100px;
   left: 23px;
}
```
#### 결과물
![](https://velog.velcdn.com/images/thdgusrbek/post/95263682-cdd6-43c4-b312-4f4b740e236a/image.png)<br><br><br><br>

> ### active 사용 모습
![](https://velog.velcdn.com/images/thdgusrbek/post/5ee1174d-2cf2-4eb7-a6f0-017c4a73495d/image.gif)
