# 1. swiper 설치

- https://swiperjs.com/demos
- cdn 이용

```html
<link rel="stylesheet" href="https://unpkg.com/swiper/swiper-bundle.css" />

<script src="https://unpkg.com/swiper/swiper-bundle.min.js"></script>  
```



- 사용한 속성
  - Effect coverflow
  - infinity loop
  - Autoplay



# 2. 바닥 반사

- `-webkit-box-reflect`  속성 이용
  - below : 방향
  - 1px : 반사의 크기
  - linear-gradient : 직선으로 진행하는 색상무늬

```css
.swiper-slide {
  background-position: center;
  background-size: cover;
  width: 500px;
  height: 600px;
  background: #fff;
  /* 반사 */
  -webkit-box-reflect : below 1px linear-gradient(transparent, transparent, #0006);
}
```

