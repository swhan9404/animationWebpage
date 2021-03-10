# 만들면서 특이사항

## header 부분

- display : flex 를 통해서 가로 정렬함
  - justify-content : flex-end
  - align-items: center



## 스크롤 내리면 크기 바뀜

- javascript로 스크롤 내리면 header에 sticky라는 클래스를 줌
- css에서 sticky 관련 설정을 해줌
  - header.sticky
    - 높이 80으로 변경
  - header.sticky .logo
    - 왼쪽 맨위에 붙도록 위치조정
  - header.sticky .banner
    - 불투명도 : 50%
  - header.sticky nav ul
    - 1초 딜레이 주고 생성
    - 왼쪽정렬(display: flex; justify-content: flex-end; 에 의하여 translateX(0)으로)

```javascript
<script>
    window.addEventListener("scroll", function(){
      const header = document.querySelector('header');
      /* scroll을 하게되면 header 에 sticky 라는 클래스를 붙여줌*/
      header.classList.toggle('sticky', window.scrollY >0);
    });
</script>
```



## 화면크기가 작아지면 깨지는 것 방지

- 991px 까지에 대한 것 따로 설정

```css
/* 여기에서부터 responsive */
@media (max-width: 991px){
    section,
    header{
        padding: 40px;
    }
    section h2{
        font-size: 2em;
    }
    header.sticky .logo{
        left: 40px;
    }
    header.sticky .banner{
        opacity: 0;
    }
}
```



### 메뉴 토글 처리

밑에 내용들은 `@media (max-width: 991px)` 이거 안에 있는 내용들임

- 원래 메뉴 리스트 안보이게 처리
- 토글 만들어서 나타나게 처리
- 자바스크립트로 토글 누르면 작동할 수 있게  active 클래스 붙여주기
  - `.toggle active` 처럼 될 수 있도록
  - `nav active` 처럼 될 수 있도록
- `ㄴnav.active ul` 에 대해 css 설정
  - 메뉴가 나타날 수 있게
  - 세로 정렬로
- `header.sticky nav ul`  로 메뉴가 보이게 설정

```css
    nav ul{ /* 글자가 많아서 깨지니 안보이게 처리 밑에 토글로 대신함*/
        display: none;
        opacity: 0;
        visibility: hidden;
    }
    nav.active ul {
        position: fixed;
        top: 80px;
        left: 0;
        width: 100%;
        height: calc(100% - 80px);
        background: #000;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }
    nav ul li a{
        font-size: 2em;
    }
    header.sticky nav ul{
        opacity:1;
        visibility: visible;
    }

    header.sticky .toggle{
        position: fixed;
        top: 15px;
        right: 40px;
        width: 50px;
        height: 50px;
        cursur: pointer;
        background: #fff url(menu.png);
        background-size: 30px;
        background-repeat: no-repeat;
        background-position: center;
    }
    header.sticky .toggle.active{
        background: #fff url(close.png);
        background-size: 25px;
        background-repeat: no-repeat;
        background-position: center;
    }
```



# 완성작품

![동적인 페이지](readme.assets/동적인 페이지.gif)