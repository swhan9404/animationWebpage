# 만들면서 특이사항

## 네오사인 글씨 만들기

```css
.box h2{
    color: #fff;
    font-size : 5em;
    font-weight: 600;
    letter-spacing: 0.1em;
    /*그림자를 흐림정도를 여러개를 줘서 번지는 것 처럼 표현하기*/
    text-shadow: 0 0 10px #00b3ff,
                0 0 20px #00b3ff,
                0 0 40px #00b3ff,
                0 0 80px #00b3ff,
                0 0 120px #00b3ff
}
```



## 글씨를 통과하는 형광색 막대기 만들기

```css
.lightbar{
    position: absolute;
    top: 0;
    left: 0;
    width: 10px;
    height: 100%;
    border-radius: 10px;/*둥굴게 깍기*/
    background:#fff;
    z-index: 2;/*글씨 위에 올라가도록*/
    box-shadow: 0 0 10px #00b3ff,
                0 0 20px #00b3ff,
                0 0 40px #00b3ff,
                0 0 80px #00b3ff,
                0 0 120px #00b3ff;
    animation: animatelightbar 5s linear infinite;/*애니메이션 적용*/
}
@keyframes animatelightbar{
    0%, 5%{
        transform: scaleY(0) translateX(0);
    }
    10%{/*막대기 커지게*/
        transform: scaleY(1) translateX(0);
    }
    90%{/*커진 막대기가 글씨 처음부터 끝까지 움직이게*/
        transform: scaleY(1) translateX(calc(600px - 10px));
    }
    95%, 100%{/*마지막 장소에서 작아지면서 사라지기*/
        transform: scaleY(0) translateX(calc(600px - 10px));
    }
}
```



## 글씨 가리는 박스 만들기

```css
.topLayer{
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: #000;
    animation: animateTopLayer 10s linear infinite;
}
@keyframes animateTopLayer{
    0%, 2.5%{
        transform: translateX(0);
    }
    5%{ 
        transform: translateX(0);
    }
    45%{/* 막대기를 따라 오른쪽으로 이동하면서 가린거 풀기*/
        transform: translateX(100%);
    }
    47.5%, 50%{
        transform: translateX(100%);
    }

    50.001%, 52.5%{ /* 왼쪽에 박스 옮기기*/
        transform: translateX(-100%);
    }
    55%{
        transform: translateX(-100%);
    }
    95%{ /* 왼쪽에서 오른쪽으로 박스 옮기면서 가리기*/
        transform: translateX(0%);
    }
    97.5%, 100%{
        transform: translateX(0%);
    }
}
```

