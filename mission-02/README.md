> ## mission-2 해설
전체를 `<section>`으로 감싸고
그 안에 
`<h2>`,
`<p>`,
`<p>`,
`<form>`이 들어있다.
![](https://velog.velcdn.com/images/thdgusrbek/post/7c13204b-cd6f-4500-bf9c-49b76529d988/image.png)<br>
#### Figma에서 가져온 css를 적용
``` css
.signIn_container {
   width: 1440px;
   height: 850px;
   margin: auto;
   background-image: url(./images/커피\ 이미지.png);
}
```
``` css
.signIn_title {
   width: 98px;
   height: 36px;
   color: #FEFEFE;
   text-align: center;
   font-family: 'Spoqa Han Sans Neo', 'sans-serif';
   font-size: 36px;
   font-style: normal;
   font-weight: 100;
   line-height: normal;
   letter-spacing: -0.72px;
   text-transform: uppercase;
   margin: 0;
   margin-left: auto;
   margin-right: auto;
   padding-top: 100px;
}
```
``` css
/* 영어 멘트 첫 단어만 대문자 */
[lang="en"] {
   text-transform: capitalize;
}
```
``` css
/* 영어 멘트 */
.sub_ment_en {
   width: 187px;
   height: 18px;
   color: #FEFEFE;
   text-align: center;
   font-family: 'Spoqa Han Sans Neo', 'sans-serif';
   font-size: 18px;
   font-weight: 300;
   font-style: normal;
   line-height: normal;
   letter-spacing: -0.36px;
   margin: 0;
   margin-top: 24px;
   margin-left: auto;
   margin-right: auto;
}
```
``` css
/* 한글 멘트 */
.sub_ment_ko {
   width: 175px;
   height: 12px;
   color: #FEFEFE;
   text-align: center;
   font-family: 'Spoqa Han Sans Neo', 'sans-serif';
   font-size: 12px;
   font-weight: 100;
   font-style: normal;
   line-height: normal;
   letter-spacing: -0.24px;
   margin: 0;
   margin-left: auto;
   margin-right: auto;
   padding-top: 9px;
}
```
<br><br><br><br>
> ### form 태그
``` html
<form action="/" method="post">
  <fieldset>
    <legend>로그인</legend>
    <div class="input_container">...</div>
    <div class="btn_container">...</div>
  </fieldset>
</form>
```
<br><br>
`<form>`에 `position: relative`를 주어 안에 요소들은 `position: absoluste`로 위치를 잡았다.
``` css
/* 폼에 테두리 제거 */
fieldset {
   border: none;
}
```
``` css
/* 숨김 콘텐츠 */
legend {
   position: absolute;
   width: 1px;
   height: 1px;
   padding: 0;
   margin: -1px;
   overflow: hidden;
   clip: rect(0, 0, 0, 0);
   clip-path: polygon(0 0, 0 0, 0 0);
   white-space: nowrap;
   border-width: 0;
}
```
``` css
form {
   position: relative;
}
```
<br><br><br><br>
> ### form 안에 첫 번째 div
첫 번째 div는  `<div class="input_container">`
``` html
<div class="input_container">
  <div class="user_email">
    <label for="user_email" class="user_email_label"></label>
    <input type="email" id="user_email" placeholder="이메일" required>
    <p class="email_invalid_ment">이메일 입력 방법이 잘못되었습니다. (예: user@domain.com)</p>
    <svg class="email_valid">길어서 생략</svg>
    <svg class="email_invalid">길어서 생략</svg>
  </div>
```
``` html
  <div class="user_pw">
    <label for="user_pw" class="user_email_pw"></label>
    <input type="password" id="user_pw" placeholder="패스워드" required>
    <p class="pw_invalid_ment">패스워드는 숫자, 영어 조합 6자 이상 입력해야 합니다.</p>
    <svg class="pw_valid">길어서 생략</svg>
    <svg class="pw_invalid">길어서 생략</svg>
    <button class="pw_hidden" type="button">
      <svg>길어서 생략</svg>
    </button>
    <button class="pw_visible" type="button">
      <svg>길어서 생략</svg>
    </button>
  </div>
```
``` html
  <div class="email_save">
    <input type="checkbox" id="check">
    <label for="check">이메일 저장</label>
  </div>
</div>
```
<br><br>
`이메일 인풋`, `패스워드 인풋`, `이메일 체크 박스` 각각을 `<div>`로 만들어서 `position: absolute`으로 위치를 잡았다.<br>(모든 `<input>`은 `<label>`로 연결했다)
``` css
.input_container {
   margin-top: 100px;
}
```
``` css
.user_email,
.user_pw {
   position: absolute;
   width: 540px;
   height: 40px;
   top: 100px;
   left: 0;
   right: 0;
   margin: auto;
}
```
``` css
.user_email input,
.user_pw input {
   width: 100%;
   background-color: initial;
   color: #FEFEFE;
   border: none;
   border-bottom: 1px solid #fefefe80;
   padding-bottom: 8px;
   font-family: 'Spoqa Han Sans Neo', 'sans-serif';
   font-size: 18px;
   font-style: normal;
   font-weight: 400;
   letter-spacing: -0.36px;
}
```
``` css
.email_invalid_ment,
.pw_invalid_ment {
   display: none;
   color: #fefefe80;
   font-family: 'Spoqa Han Sans Neo', 'sans-serif';
   font-size: 12px;
   font-style: normal;
   font-weight: 400;
   line-height: normal;
   letter-spacing: -0.24px;
   margin-top: 5px;
}
```
``` css
.email_valid,
.pw_valid,
.email_invalid,
.pw_invalid {
   display: none;
   position: absolute;
   top: 50%;
   right: 0;
   transform: translateY(-50%);
}
```
``` css
.user_pw {
   top: 193px;
}
```
``` css
.pw_invalid_ment {
   margin-top: 3px;
}
```
``` css
.pw_valid,
.pw_invalid {
   right: 30px;
}
```
``` css
.pw_hidden {
   cursor: pointer;
   display: none;
   position: absolute;
   top: 50%;
   right: 0;
   transform: translateY(-50%);
   background-color: initial;
   border: none;
}
```
``` css
.pw_visible {
   cursor: pointer;
   display: none;
   position: absolute;
   top: 50%;
   right: 0;
   transform: translateY(-50%);
   background-color: initial;
   border: none;
}
```
``` css
.show {
   display: block;
}
```
``` css
.email_save {
   position: absolute;
   width: 540px;
   height: 12px;
   font-size: 12px;
   top: 247px;
   left: 0;
   right: 0;
   margin: auto;
   color: #fefefe80;
}
```
<br><br><br><br>
> ### form 안에 두 번째 div
두 번째(마지막) div는 `<div class="btn_container">`
``` html
<div class="btn_container">
  <button class="signIn_btn" type="submit">로그인
    <svg>길어서 생략</svg>
  </button>
  <button class="signUp_btn" type="button">회원가입
    <svg>길어서 생략</svg>
  </button>
</div>
```
<br><br>
`로그인`, `회원가입`은 모두 `<button>`으로 만들고 `btn_container`(클래스)에 `flex`, `absolute`를 주어 위치를 잡았다.
``` css
.btn_container {
   position: absolute;
   top: 319px;
   left: 0;
   right: 0;
   display: flex;
   gap: 20px;
   width: 540px;
   height: 48px;
   margin: auto;
}
```
``` css
.signIn_btn {
   background-color: #FEFEFE;
   color: #24388D;
   border: none;
}
```
``` css
.signUp_btn {
   background-color: initial;
   border: 1px solid #FEFEFE;
   color: #FEFEFE;
}
```
``` css
.signIn_btn,
.signUp_btn {
   cursor: pointer;
   position: relative;
   width: 260px;
   height: 48px;
   border-radius: 8px;
   font-family: 'Spoqa Han Sans Neo', 'sans-serif';
   font-style: normal;
   font-size: 20px;
   font-weight: 500;
   line-height: 28px;
   letter-spacing: -0.4px;
}
```
``` css
.signIn_btn svg,
.signUp_btn svg {
   position: absolute;
   top: 50%;
   right: 14px;
   transform: translateY(-50%);
}
```
> ### 데스크 톱
![](https://velog.velcdn.com/images/thdgusrbek/post/079aa36f-620f-4640-a3a6-362777b2db27/image.gif)
<br><br><br><br>
> ### 미디어 쿼리 추가
`@media (max-width : )`를 사용해서 반응형으로 만들었다.<br>Figma에 나온 css를 참고해서<br>데스크 톱과 같은 값은 제외하고 새롭거나 변경된 값만 작성
``` css
/* 모바일 화면 */
@media (max-width : 600px) {
   .signIn_container {
      width: 375px;
      height: 812px;
      background-size: cover;
      background-position: 50% 50%;
      background-repeat: no-repeat;
   }
```
``` css
   .signIn_title {
      padding-top: 70px;
   }
```
``` css
   .input_container {
      margin-top: 114px;
   }
```
``` css
   .user_email,
   .user_pw {
      width: 311px;
      height: 40px;
      top: 100px;
      left: 0;
      right: 0;
      margin: auto;
   }
```
``` css
   .email_invalid_ment,
   .pw_invalid_ment {
      display: none;
      color: #fefefe80;
      font-size: 12px;
      font-style: normal;
      font-weight: 400;
      line-height: normal;
      letter-spacing: -0.24px;
      margin-top: 5px;
   }
```
``` css
   .email_valid,
   .pw_valid,
   .email_invalid,
   .pw_invalid {
      display: none;
      position: absolute;
      top: 50%;
      right: 0;
      transform: translateY(-50%);
   }
```
``` css
   .user_pw {
      top: 193px;
   }
```
``` css
   .pw_invalid_ment {
      margin-top: 3px;
   }
```
``` css
   .pw_valid,
   .pw_invalid {
      right: 30px;
   }
```
``` css
   .pw_hidden {
      cursor: pointer;
      display: none;
      position: absolute;
      top: 50%;
      right: 0;
      transform: translateY(-50%);
      background-color: initial;
      border: none;
   }
```
``` css
   .pw_visible {
      cursor: pointer;
      display: none;
      position: absolute;
      top: 50%;
      right: 0;
      transform: translateY(-50%);
      background-color: initial;
      border: none;
   }
```
``` css
   .show {
      display: block;
   }
```
``` css
   .email_save {
      width: 311px;
   }
```
``` css
   .btn_container {
      flex-flow: column nowrap;
      gap: 15px;
      width: 311px;
      height: auto;
      margin: auto;
   }
```
``` css
   .signIn_btn,
   .signUp_btn {
      width: 100%;
   }
}
```
> ### 모바일
![](https://velog.velcdn.com/images/thdgusrbek/post/12eac327-b4ad-4aee-ad9b-b07150526ed9/image.gif)
