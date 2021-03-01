# 만들면서 특이사항

## 글자마다 클래스주기

```html
  <script>
    // 글자쪼개기
    const text = document.querySelector('.text');
    // 정규표현식: /정규식/g 로 표현
    // \S : 공백 문자가 아닌 하나의 문자에 대응
    // $& : 일치한 문자열
    text.innerHTML = text.textContent.replace(/\S/g, "<span>$&</span>");

  </script>
```



## 각 글자마다 애니메이션주기

- 회전 : -360~360 랜덤
- X : -500, 500 랜덤
- Y : -500, 500 랜덤
- duration: 3초
- 딜레이 : 0.02초
- style : relative(움직여도 제자리 기억) ,inline-block

```html
<script>
	const animation= anime.timeline({
      targets : '.text span',
      easing : 'easeInOutExpo',
      loop: true
    });

    animation
      .add({
        rotate: function(){
          return anime.random(-360, 360)
        },
        translateX: function(){
          return anime.random(-500,500)
        },
        translateY: function(){
          return anime.random(-500,500)
        },
        duration : 5000,
        delay: anime.stagger(20),
      })

      .add({
        rotate: 0,
        translateX:0,
        translateY: 0,
        duration : 5000,
        delay: anime.stagger(20),
      })
</script>
```

