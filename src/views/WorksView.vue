<script lang="ts">
import wkImg1 from "@/assets/works/wk1_portfolio.svg";
import wkImg2 from "@/assets/works/wk_sample.svg";
import wkImg3 from "@/assets/works/wk_sample.svg";
import wkImg4 from "@/assets/works/wk_sample.svg";
import wkImg5 from "@/assets/works/wk_sample.svg";
import { ref } from 'vue';
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from 'swiper/vue';

// Import Swiper styles
import 'swiper/css';
import 'swiper/css/free-mode';
import 'swiper/css/navigation';
import 'swiper/css/thumbs';
import 'swiper/css/effect-fade';

// import required modules
import { FreeMode, Navigation, Thumbs, EffectFade } from 'swiper/modules';

export default {
  components: {
    Swiper,
    SwiperSlide,
  },
  setup() {
    // Swiperの実装
    const thumbsSwiper = ref(null);
    const setThumbsSwiper = (swiper: any) => {
      thumbsSwiper.value = swiper;
    };

    // 現在スライドに合わせて説明を表示する。
    const activeSlide = ref(0);
    const works = [
      {
        no: 1,
        lang: ["HTML", "CSS/Sass", "Javascript"],
        dscrpton: "自身のポートフォリオサイト。デザイン~フロント部分を実装した後にGitHubPagesを利用して公開。フレームワークは 「Vue3」 を使用しています。",
        img: wkImg1
      },
      {
        no: 2,
        lang: ["N/A"],
        dscrpton: "slide 2",
        img: wkImg2
      },
      {
        no: 3,
        lang: ["N/A"],
        dscrpton: "slide 3",
        img: wkImg3
      },
      {
        no: 4,
        lang: ["N/A"],
        dscrpton: "slide 4",
        img: wkImg4
      },
      {
        no: 5,
        lang: ["N/A"],
        dscrpton: "slide 5",
        img: wkImg5
      }
    ]

    return {
      thumbsSwiper,
      setThumbsSwiper,
      modules: [FreeMode, Navigation, Thumbs, EffectFade],
      activeSlide,
      works
    };
  },
};
</script>

<template>
    <section class="works">
        <div class="container works__container">
            <h2 class="ttl works__ttl">Works</h2>
            <div class="works__content">
                <div class="works__mv">
                    <div class="works__mv-frame">
                      <swiper
                          :effect="'fade'"
                          :spaceBetween="10"
                          :thumbs="{ swiper: thumbsSwiper }"
                          :modules="modules"
                          class="mySwiper2"
                      >
                          <swiper-slide
                              v-for="(work, index) in works"
                              :key="index"
                              @click="activeSlide = index"
                          ><img :src="work.img"
                          /></swiper-slide>
                      </swiper>
                    </div>
                    <div class="works__mv-image"></div>
                </div>
                <div class="summary works__summary">
                    <h3 class="summary__heading">Language</h3>
                    <ul class="summary__list">
                        <li
                            v-for="(item, index) in works[activeSlide].lang"
                            :key="index"
                        >{{ item }}</li>
                    </ul>
                    <h3 class="summary__heading">Description</h3>
                    <p class="summary__dscrpton">{{ works[activeSlide].dscrpton }}</p>
                </div>
            </div>
            <swiper
                @swiper="setThumbsSwiper"
                :spaceBetween="10"
                :slidesPerView="4"
                :freeMode="true"
                :watchSlidesProgress="true"
                :modules="modules"
                class="mySwiper"
            >
                <swiper-slide
                    v-for="(work, index) in works"
                    :key="index"
                    @click="activeSlide = index"
                ><img :src="work.img"
                /></swiper-slide>
            </swiper>
        </div>
    </section>
</template>

<style scoped>
.swiper {
  width: 100%;
  height: 100%;
}

.swiper-slide {
  text-align: center;
  font-size: 18px;
  background: #fff;

  /* Center slide text vertically */
  display: flex;
  justify-content: center;
  align-items: center;
}

.swiper-slide img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.swiper {
  width: 100%;
  height: 300px;
  margin-left: auto;
  margin-right: auto;
}

.swiper-slide {
  background-size: cover;
  background-position: center;
}

.mySwiper2 {
  height: 100%;
  width: 100%;
}

.mySwiper {
  height: 20%;
  box-sizing: border-box;
  padding: 10px 0;
}

.mySwiper .swiper-slide {
  width: 25%;
  height: 100%;
  opacity: 0.4;
}

.mySwiper .swiper-slide-thumb-active {
  opacity: 1;
}

.swiper-slide img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>