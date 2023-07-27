<template>
  <Swiper :modules="[SwiperAutoplay, SwiperEffectCreative]" :slides-per-view="1" :loop="true" :effect="'creative'"
    :autoplay="{
      delay: 1000,
    }" :creative-effect="{
  prev: {
    shadow: false,
    translate: ['-50%', 0, -1],
  },
  next: {
    translate: ['100%', 0, 0],
  },
}">
    <SwiperSlide>
      <img
        src="https://images.unsplash.com/photo-1682685797661-9e0c87f59c60?ixlib=rb-4.0.3&ixid=M3wxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1440&q=40"
        alt="">
    </SwiperSlide>
    <SwiperSlide>
      <img
        src="https://images.unsplash.com/photo-1690311075738-30513e417e12?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1440&q=40"
        alt="">
    </SwiperSlide>
  </Swiper>
</template>