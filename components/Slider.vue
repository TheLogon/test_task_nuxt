<template>
  <section class="animals">
    <div class="animals__container">
      <div class="animals__inner">
        <div class="animals__slider">
          <slick
            ref="slick"
            :options="slickOptions"
            class="animals__slider_wrapper"
            v-if="!posts.length == 0"
          >
            <div class="animals__slide" v-for="post in posts" :key="post.id">
              <div class="animals__slide_img">
                <img :src="post.image" alt="" />
              </div>
              <div class="animals__slide_bot">
                <div class="animals__slide_wrap">
                  <p class="animals__slide_title">{{ post.title }}</p>
                  <p class="animals__slide_text">{{ post.category }}</p>
                </div>
                <div class="animals__slide_icon">
                  <img :src="post.image" alt="" />
                </div>
              </div>
            </div>
          </slick>
        </div>

        <a href="#" class="animals__btn btn">choose your favorite</a>
      </div>
    </div>
  </section>
</template>

<script>
import Slick from "vue-slick";
import "slick-carousel/slick/slick.css";

export default {
  components: { Slick },
  data() {
    return {
      posts: [],
      slickOptions: {
        rows: 2,
        infinite: true,
        speed: 300,
        centerMode: false,
        mobileFirst: true,
        prevArrow:
          '<div class="animals-button-prev"><svg width="18" height="10" viewBox="0 0 18 10" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M5.00179 9.10745L5.10646 9.2094L5.21112 9.10745L5.35128 8.97092L5.46159 8.86347L5.35128 8.75602L1.74841 5.24656L17 5.24656H17.15V5.09656V4.90344V4.75344H17L1.74878 4.75344L5.35129 1.24398L5.46158 1.13653L5.35128 1.02909L5.21112 0.892552L5.10646 0.790595L5.00179 0.892553L0.895334 4.89275L0.785027 5.0002L0.895338 5.10764L5.00179 9.10745Z" fill="white" stroke="white"  stroke-width="0.3" /></svg></div>',
        nextArrow:
          '<div class="animals-button-next"><svg width="18" height="10" viewBox="0 0 18 10" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M12.9982 0.892548L12.8935 0.7906L12.7889 0.892552L12.6487 1.02908L12.5384 1.13653L12.6487 1.24398L16.2516 4.75344H1H0.85V4.90344V5.09656V5.24656H1H16.2512L12.6487 8.75602L12.5384 8.86347L12.6487 8.97091L12.7889 9.10745L12.8935 9.2094L12.9982 9.10745L17.1047 5.10725L17.215 4.9998L17.1047 4.89236L12.9982 0.892548Z" fill="white" stroke="white" stroke-width="0.3"/></svg></div>',
        responsive: [
          {
            breakpoint: 1600,
            settings: {
              slidesToScroll: 3,
              slidesToShow: 3,
            },
          },
          {
            breakpoint: 955,
            settings: {
              slidesToScroll: 2,
              slidesToShow: 2,
            },
          },
          {
            breakpoint: 320,
            settings: {
              slidesToScroll: 1,
              slidesToShow: 1,
            },
          },
        ],
      },
    };
  },
  created() {
    fetch("https://fakestoreapi.com/products")
      .then((res) => res.json())
      .then((data) => (this.posts = data));
  },
  methods: {
    next() {
      this.$refs.slick.next();
    },
    prev() {
      this.$refs.slick.prev();
    },
    reInit() {
      // Helpful if you have to deal with v-for to update dynamic lists
      this.$refs.slick.reSlick();
    },
  },
};
</script>
