# mission-03 해설
### 작업 방식
- Netflix 시안을 보고 각 부품을 `컨포넌트화` 시켜서 작업
- 모바일 분기점은 768px로 설정
<hr><br><br>

### 파일 구조
![](https://velog.velcdn.com/images/thdgusrbek/post/c9652ad9-701e-4aee-89ed-09ccdf0f00f3/image.png)<hr><br><br>

### 메인 페이지(mission-03.html) 코드 요약
``` html
<body>
  <div role="none" class="template_container">
    
    <header class="header"></header>
    
    <main class="main"></main>
    
    <div role="none" class="divider"></div>
    
    <footer class="footer">...</footer>
    
  </div>
<body>
```
<hr><br><br>

### button Component
![](https://velog.velcdn.com/images/thdgusrbek/post/4065bee7-4a2d-4b39-8d9d-e39992ceda64/image.png)
``` html
<button class="btn" type="button">버튼</button>
```
``` css
.btn {
   width: 70px;
   height: 40px;
   background: #E50914;
   color: #FFF;
   border: none;
   border-radius: 4px;
   text-align: center;
   font-family: 'Spoqa Han Sans Neo', 'sans-serif';
   font-size: 1rem;
   font-weight: 500;
   line-height: 1.5rem;
   letter-spacing: -0.008px;
}

.btn:hover {
   background: #B70710;
}

.btn:focus {
   outline: 0;
   border: 3px solid #58E590;
}
```
<hr><br><br>

### button_arrow Component
![](https://velog.velcdn.com/images/thdgusrbek/post/31c2105c-c8c5-4c05-b04d-485ec72efd94/image.png)
``` html
<button class="btn_arrow btn_arrow_normal_right" type="button">버튼
   <svg ...></svg>
</button>
```
``` css
.btn_arrow {
   width: 113px;
   height: 56px;
   background: #E50914;
   color: #FFF;
   border: none;
   text-align: center;
   font-family: 'Spoqa Han Sans Neo', 'sans-serif';
   font-size: 22px;
   font-weight: 400;
   line-height: 26px;
}

.btn_arrow:hover {
   background: #B70710;
}

.btn_arrow:focus {
   border: 3px solid #58E590;
   background: #B70710;
   outline: 0;
}
```
<hr><br><br>

### select Component
![](https://velog.velcdn.com/images/thdgusrbek/post/0fd54945-14a6-4956-b4b0-37b3cf246b76/image.png)
- `<select>`는 스타일이 수정이 어려워 `<button>`를 사용해서 새롭게 작성
- `글로벌 아이콘`, `한국어`, `아래모양 아이콘`을 `flex`로 배치
- 언어 선택 창을 `absoulte`를 사용해서 배치
- 동작은 js를 사용해서 조작
``` html
<button class="select_btn" data-val="onOff">

   <ul>
      <li aria-hidden class="global_icon" data-val="onOff"></li>
      <li class="state_lang" data-val="onOff">한국어</li>
      <li aria-hidden class="select_down_icon" data-val="onOff"></li>
   </ul>

   <div class="select_lang hide_none">
      <div class="check_icon_wrapper">
         <!-- span태그로 충분한가? -->
         <span class="check_icon ko"></span>
         <span class="check_icon en hide_hidden"></span>
      </div>

      <div role="list" class="lang">
         <span role="listitem" class="lang_ko">한국어</span>
         <span role="listitem" class="lang_en" lang="en-US">English</span>
      </div>
   </div>

</button>
```
``` css
/* 셀렉트 버튼 기본 스타일 */
.select_btn {
   cursor: pointer;
   pointer-events: auto;
   width: 113px;
   height: 40px;
   border-radius: 2px;
   border: 1px solid#757575;
   background-color: #000;
   color: #757575;
   position: relative;
}

.select_btn ul {
   display: flex;
   flex-flow: row nowrap;
   justify-content: space-around;
   list-style: none;
   margin-top: 0;
   margin-bottom: 0;
}

.global_icon {
   background-image: url('./../../images/global.svg');
   width: 16px;
   height: 16px;
}

.select_down_icon {
   background-image: url('./../../images/select_down.svg');
   width: 16px;
   height: 16px;
}

.check_icon {
   display: inline-block;
   width: 12px;
   height: 12px;
   margin-left: 10px;
   background-image: url('./../../images/check.svg');
   background-repeat: no-repeat;
}

.select_lang {
   width: 113px;
   height: 86px;
   color: #000;
   background-color: #E3E3E3;
   border-radius: 12px;
   opacity: 0.9;
   font-size: 16px;
   font-weight: 700;
   line-height: 24px;
   letter-spacing: -0.008px;
   display: flex;
   flex-flow: row nowrap;
   align-items: center;
   row-gap: 6px;
   position: absolute;
   top: 0;
   left: 0;
}

.lang {
   text-align: start;
}

.select_btn:focus,
.select_btn:hover {
   border: 3px solid #2EDE75;
   outline: 0;
}

.lang :first-child:hover,
.lang :last-child:hover {
   color: #2EDE75;
}

/* 공간은 차지하고 숨기기 */
.hide_hidden {
   visibility: hidden;
}

/* 공간 차지하지 않고 숨기기 */
.hide_none {
   display: none;
}
```
<hr><br><br>

### header Component
![](https://velog.velcdn.com/images/thdgusrbek/post/13ccc6dc-ae56-4b26-bed8-68620ba7d0cc/image.png)
- `언어선택 버튼(select)`, `로그인 버튼(button)`을 `<div>`로 감싸고 `flex`를 사용해서 배치
``` html
<!-- html -->
<header class="header">
   <div role="none" class="header_inner">
      <a href="/" class="logo"></a>
      <div role="none" class="header_button_wrapper">
         <button class="select_btn" data-val="onOff">...</button> <!-- select 컨포넌트 사용 -->
         <button class="btn" type="button">로그인</button> <!-- button 컨포넌트 사용 -->
      </div>
   </div>
</header>
```
``` css
/* css */
body {
   margin: 0;
   padding: 0;
}

.header {
   background-color: #000;
   width: 100%;
   height: auto;
}

.header_inner {
   display: flex;
   flex-flow: row nowrap;
   padding: 20px 65px;
   justify-content: space-between;
   align-items: center;
}

.logo {
   display: inline-block;
   background-image: url('./../../images/Logo.svg');
   background-repeat: no-repeat;
   background-size: contain;
   width: 140px;
   height: 38px;
}

.header_button_wrapper {
   display: flex;
   column-gap: 24px;
}


@media (max-width: 768px) {
   .header_inner {
      padding: 10px 25px;
   }

   .logo {
      width: 80px;
      height: 22px;
   }

   .header_button_wrapper {
      column-gap: 16px;
   }

   .header .select_btn {
      height: 30px;
   }

   .header .btn {
      width: 60px;
      height: 30px;
      font-size: 12px;
   }
}
```
<hr><br><br>

### input_email Component
![](https://velog.velcdn.com/images/thdgusrbek/post/5db44252-b13b-4ba4-863d-639f9a0d92ca/image.png)
- `label`과 `input`을 을 연결하고 `label`에 `이메일 주소`라는 문구를 작성
- 전체를 감싸는 태그(`input_email_container`)에 `relative` 속성을 주고 `label`을 `absolute`로 배치
- `invalid` 상태일 때, 보여 줄 문구를 `span`안에 작성하고 `absolute`로 배치 후 `display: none`으로 숨겨준다. (js로 `invalid` 상태일 때만 보이게 조작)
- 동작은 js를 사용해서 조작
``` html
<div role="none" class="input_email_container">
   <label for="user_email" class="user_email_label">이메일 주소</label>
   <span role="alert" class="user_email_invalid">정확한 이메일 주소를 입력하세요.</span>
   <div role="none" class="input_email_wrapper">
      <input type="email" class="user_email" id="user_email" data-val="focus">
     
     <!-- button_arrow 컨포넌트 사용 -->
      <button class="btn_arrow btn_arrow_normal_right" type="button">30일 무료 이용
         <svg ..></svg>
      </button>
   </div>
</div>
```
``` css
.input_email_container {
   position: relative;
}

.user_email_label {
   position: absolute;
   top: 20px;
   left: 18px;
   color: #757575;
   font-family: 'Spoqa Han Sans Neo', 'sans-serif';
   transition: all 0.3s ease-in-out;
}

.user_email_focus {
   top: 10px;
   left: 19px;
   color: #E50914;
   font-size: 12px;
   line-height: 18px;
   font-weight: bold;
   letter-spacing: -0.006px;
}

.input_email_wrapper {
   display: flex;
   flex-flow: row nowrap;
}

.user_email {
   box-sizing: border-box;
   width: 540px;
   height: 60px;
   padding: 26px 20px 10px;
   border: none;
   outline: none;
}

.user_email_invalid {
   /* display: block; */
   display: none;
   border-top: 3px solid #E50914;
   position: absolute;
   color: #E50914;
   font-size: 14px;
   font-weight: bold;
   line-height: 21px;
   letter-spacing: -0.007px;
   width: 520px;
   top: 57px;
   padding-top: 5px;
   padding-left: 20px;
}

.input_email_container .btn_arrow {
   width: 210px;
   height: 60px;
   border-radius: none;
}

.input_email_container .btn_arrow {
   display: flex;
   justify-content: center;
   align-items: center;
   column-gap: 10px;
}

.show {
   display: block;
}


@media (max-width: 768px) {
   .input_email_container {
      display: inline-block;
   }

   .user_email_label {
      position: absolute;
      color: #757575;
      font-family: 'Spoqa Han Sans Neo', 'sans-serif';
      transition: all 0.3s ease-in-out;


      top: 10px;
      left: 20px;
      font-size: 14px;
      font-weight: 400;
      line-height: 21px;
      letter-spacing: -0.007px;
   }

   .user_email_focus {
      color: #E50914;
      font-size: 12px;
      line-height: 18px;
      font-weight: bold;
      letter-spacing: -0.006px;


      top: -23px;
      left: 16px;
   }

   .input_email_wrapper {
      flex-flow: column;
      align-items: center;
      row-gap: 12px;
   }

   .user_email {
      box-sizing: border-box;

      padding: 10px 20px 10px;
      width: 245px;
      height: 40px;
      border-radius: 30px;
      /* border: 1px solid #000; */
   }

   .user_email_invalid {
      /* display: block; */
      display: none;
      border-top: none;
      position: absolute;
      width: auto;
      top: 46px;
      padding-top: 2px;
      padding-left: 15px;
   }


   .input_email_container .btn_arrow {

      width: 160px;
      height: 40px;
      border-radius: 30px;
      font-size: 14px;
      font-weight: 400;
      line-height: 21px;
      letter-spacing: -0.007px;
   }

   .show {
      display: block;
   }


   /* focus되면 input에 적용 */
   .user_email_focus_mobile {
      height: 46px;
      border: 3px solid #E50914;
   }

   /* focus되면 버튼에 적용 */
   .btn_arrow_focus {
      transform: translateY(20px);
   }
}
```
<hr><br><br>

### promotion Component
![](https://velog.velcdn.com/images/thdgusrbek/post/0d7fecca-7f98-4dcd-a45a-1d35ae1c528b/image.png)
- 전체를 `ul`로 감싸고 안에 `li`로 작성
- `flex`로 배치
``` html
<ul class="promotion_container">
   <li>영화, TV 프로그램을 무제한으로.</li>
   <li>다양한 디바이스에서 시청하세요. 언제든 해지하실 수 있습니다.</li>
   <li>시청할 준비가 되셨나요? 멤버십을 등록하거나 재시작하려면 이메일 주소를 입력하세요.</li>
   <div role="none" class="input_email_container"></div> <!-- input_email 컨포넌트 사용 -->
   <li>신규 회원만 이 프로모션을 이용하실 수 있습니다.</li>
</ul>
```
``` css
.promotion_container {
   color: #fff;
   display: flex;
   flex-flow: column nowrap;
   justify-content: center;
   align-items: center;
   row-gap: 28px
}

ul {
   padding: 0;
}

.promotion_container li {
   margin: 0;
   word-break: keep-all;
   text-align: center;
   font-family: 'Spoqa Han Sans Neo', 'sans-serif';
   list-style: none;
}

.promotion_container li:nth-of-type(1) {
   width: 518px;
   font-size: 60px;
   font-weight: 700;
   line-height: 72px;
   letter-spacing: -0.03px;
}

.promotion_container li:nth-of-type(2) {
   width: 520px;
   text-shadow: 0px 2px 6px rgba(0, 0, 0, 0.55);
   font-size: 20px;
   font-weight: 500;
   line-height: 30px;
   letter-spacing: -0.01px;
}

.promotion_container li:nth-of-type(3) {
   width: 306px;
   text-shadow: 0px 2px 6px rgba(0, 0, 0, 0.55);
   font-size: 16px;
   font-weight: 300;
   line-height: 24px;
   letter-spacing: -0.008px;
}

.promotion_container li:nth-of-type(5) {
   width: 322px;
   text-shadow: 0px 2px 6px rgba(0, 0, 0, 0.55);
   font-size: 16px;
   font-weight: 300;
   line-height: 24px;
   letter-spacing: -0.008px;
}


@media (max-width: 768px) {
   .promotion_container li:nth-of-type(1) {
      width: 339px;
      font-size: 34px;
      line-height: 40px;
   }

   .promotion_container li:nth-of-type(2) {
      width: 259px;
      font-size: 18px;
      line-height: 27px;
      letter-spacing: -0.009px;
   }

   .promotion_container li:nth-of-type(3) {
      width: 264px;
      font-size: 14px;
      line-height: 21px;
      letter-spacing: -0.007px;
   }

   .promotion_container li:nth-of-type(5) {
      width: 339px;
      font-size: 12px;
      line-height: 18px;
      letter-spacing: -0.006px;
   }
}
```
<hr><br><br>

### footer Component
![](https://velog.velcdn.com/images/thdgusrbek/post/d61ff146-5863-4978-be03-14ef7686643d/image.png)<br><br>
- 클릭 시 이동해야 함으로 `<a>` 사용
- `grid`를 사용해 배치
![](https://velog.velcdn.com/images/thdgusrbek/post/104d61ae-41cc-4936-b8cb-eb45a3a7402c/image.png)<br><br>
- 주소를 나타냄으로 `<address>` 사용
- 모바일, 데스크톱 배치가 다르지 않기에 `<div>`를 사용해서 `margin`으로 간격만 설정
![](https://velog.velcdn.com/images/thdgusrbek/post/56d7fbf4-b124-483d-8582-0ce317bc721c/image.png)
``` html
<footer class="footer">

   <div role="none" class="footer_ask_wrapper">
      <!-- div가 아닌 다른 태그가 있을까? -->
      <div class="footer_ask">질문이 있으신가요&#63;</div>
      <div class="footer_ask">문의 전화&#58; <a href="tel: +82-0-308-321-0058">00-308-321-0058</a></div>
   </div>

   <div role="link" class="footer_nav">
      <a href="/">자주 묻는 질문</a>
      <a href="/">고객센터</a>
      <a href="/">계정</a>
      <a href="/">미디어 센터</a>
      <a href="/">투자 정보 &#40;<span lang="en-US">IR</span>&#41;</a>
      <a href="/">입사 정보</a>
      <a href="/"><span lang="en-US">Netflix</span> 지원 디바이스</a>
      <a href="/">이용 약관</a>
      <a href="/">개인정보</a>
      <a href="/">쿠키 설정</a>
      <a href="/">회사 정보</a>
      <a href="/">문의하기</a>
      <a href="/">속도 테스트</a>
      <a href="/">법적 고지</a>
      <a href="/"><span lang="en-US">Netflix</span> 오리지널</a>
   </div>

   <button class="select_btn" data-val="onOff"></button> <!-- select 컨포넌트 사용 -->

   <address class="footer_address">
      <!-- address 안에 태그들을 div로 작성해도 되는가? -->
      <div>Netflix 대한민국</div>
      <div>넷플릭스서비시스코리아 유한회사</div>
      <div>통신판매업신고번호: 제2018-서울종로-0426호</div>
      <div>전화번호: <a href="tel: +82-0-308-321-0058">00-308-321-0058</a></div>
      <div>대표: 레지널드 숀 톰프슨</div>
      <div>이메일 주소: <a href="mailto:korea@netflix.com">korea@netflix.com</a></div>
      <div>주소: 대한민국 서울특별시 종로구 우정국로 26, 센트로폴리스 A동 20층 우편번호 03161</div>
      <div>사업자 등록번호: 165-87-00119</div>
      <div>클라우드 호스팅: Amazon Web Services Inc.</div>
      <div>공정거래위원회 웹사이트</div>
   </address>

</footer>
```
``` css
.footer {
   color: #fff;
   background-color: #000;
   /* border: 1px solid #fff; */
}

.footer_ask_wrapper {
   display: flex;
   flex-flow: row nowrap;
   column-gap: 5px;
}

.footer_ask {
   color: #C8C8C8;
   font-size: 20px;
   font-style: normal;
   font-weight: 700;
   line-height: 30px;
   font-family: 'Spoqa Han Sans Neo', 'sans-serif';
   letter-spacing: -0.01px;
}

.footer_ask a {
   text-decoration: none;
   color: #C8C8C8;
}

.footer_nav {
   display: grid;
   grid-template-columns: repeat(4, 205px);
   grid-template-rows: auto;
   margin-top: 50px;
   row-gap: 16px;
   column-gap: 60px;
}

.footer_nav a {
   text-decoration: none;
   color: #ACACAC;
   font-family: 'Spoqa Han Sans Neo', 'sans-serif';
   font-size: 16px;
   font-weight: 400;
   line-height: 19px;
}

.footer .select_btn {
   margin-top: 46px;
}

.footer_address {
   margin-top: 46px;
   color: #919191;
   font-family: 'Spoqa Han Sans Neo', 'sans-serif';
   font-size: 16px;
   font-weight: 400;
   line-height: 24px;
   letter-spacing: -0.008px;
   font-style: normal;
}

.footer_address a {
   text-decoration: none;
   color: #919191;
}

.footer_address div:nth-of-type(1) {
   color: #ACACAC;
   font-size: 22px;
   font-weight: 500;
   line-height: 26px;
   margin-bottom: 16px;
}


@media (max-width: 768px) {
   .footer_ask_wrapper {
      flex-flow: column;
   }

   .footer_nav {
      grid-template-columns: repeat(2, 163px);
      row-gap: 10px;
      column-gap: 0px;
      margin-top: 26px;
   }

   .footer_nav a {
      font-size: 14px;
      line-height: 21px;
   }

   .footer .select_btn {
      margin-top: 51px;
   }

   .footer_address {
      margin-top: 30px;
      font-size: 14px;
      line-height: 21px;
   }

   .footer_address div:nth-of-type(1) {
      font-size: 20px;
      line-height: 30px;
      margin-bottom: 10px;
   }
}
```
<hr><br><br>

### template Component
![](https://velog.velcdn.com/images/thdgusrbek/post/05f8eddc-cdcf-4ad4-9203-1565f9cebe45/image.png)
- 기본 템플릿 컴포넌트로 `header`, `main`, `divider`, `footer`로 이루어져 있음
- 시안이 `height: 1630px`로 제작되어 전체 컨테이너를 `1630px`로 설정하고 각각의 영역을 %로 계산에서 작성
- `background-image`에 이미지를 넣고 `linear-gradient`로 그림자 느낌을 적용
- 배경이미지와 `footer`가 자연스럽게 이어지도록 `divider`에 `linear-gradient`를 적용
``` html
<div class="template_container">
  <header class="header"></header> <!-- header 컨포넌트 사용 -->
   
  <main class="main">메인 컨텐츠</main>
   
  <div role="none" class="divider"></div>
   
  <footer class="footer"></footer> <!-- footer 컨포넌트 사용 -->
</div>
```
``` css
.template_container {
   background-image: url('./../../images/background.png');
   background-image: url('./../../images/background.png'), linear-gradient(180deg, #000000 0%, #000000 80%);
   background-repeat: no-repeat;
   background-size: cover;
   width: 100%;
   height: 1630px;
}

.template_container .header {
   background-color: transparent;
   height: 8%;
}

.template_container .header_inner {
   padding-top: 40px;
   padding-bottom: 40px;
   padding-left: calc((100% - 90%)/2);
   padding-right: calc((100% - 90%)/2);
}

.template_container .main {
   height: 42%;
}

.divider {
   height: 10%;
   background: linear-gradient(180deg, rgba(0, 0, 0, 0.1) 0%, rgba(0, 0, 0, 0.2) 10%, rgba(0, 0, 0, 0.3) 20%, rgba(0, 0, 0, 0.4) 30%, rgba(0, 0, 0, 0.5) 40%, rgba(0, 0, 0, 0.6) 50%, rgba(0, 0, 0, 0.7) 60%, rgba(0, 0, 0, 0.8) 70%, rgba(0, 0, 0, 0.9) 80%, rgba(0, 0, 0, 0.95) 90%, #000000 100%);
}

.template_container .footer {
   height: 40%;
   padding-top: 46px;
   /* padding-bottom: 50px; */
   padding-left: calc((100% - 90%)/2);
   padding-right: calc((100% - 90%)/2);
   border-top: 4px solid #2F2F2F;
}


@media (max-width: 768px) {
   .template_container .header {
      background-color: transparent;
      height: 5%;
   }

   .template_container .header_inner {
      padding-top: 20px;
      padding-bottom: 20px;
   }

   .template_container .main {
      height: 45%;
   }

   .divider {
      height: 5%;
      background: linear-gradient(180deg, rgba(0, 0, 0, 0.1) 0%, rgba(0, 0, 0, 0.2) 20%, rgba(0, 0, 0, 0.4) 40%, rgba(0, 0, 0, 0.6) 60%, rgba(0, 0, 0, 0.8) 80%, #000000 100%);
   }

   .template_container .footer {
      height: 45%;
      border-top: 4px solid #2F2F2F;
   }
}
```
<hr><br><br>

### 필요한 Component를 조립해서 만든 메인 페이지(mission-03.html)
``` html
<body>
  <div role="none" class="template_container">
    <header class="header"></header> <!-- header 컨포넌트 사용-->

    <main class="main">
       <ul class="promotion_container"></ul> <!-- promotion 컨포넌트 사용 -->
    </main>

      <div role="none" class="divider"></div>

      <footer class="footer"></footer> <!-- footer 컨포넌트 사용 -->
  </div>
</body>
```
<br><br>
- 데스크톱 ver<br><br>
![](https://velog.velcdn.com/images/thdgusrbek/post/e00d7397-1e2a-463b-8d13-2a7aab767d2b/image.png)<br><br>
- 모바일 ver<br><br>
![](https://velog.velcdn.com/images/thdgusrbek/post/59b2d1cd-50b7-42f4-8f7e-8e4360a8103f/image.png)
<hr><br><br>

### [💻 Demo](https://song0331.github.io/home-work/)
