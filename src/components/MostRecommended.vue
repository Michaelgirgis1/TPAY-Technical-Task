<template>
  <div class="most-recommended container">
    <div class="row">
      <div class="col-lg-8 col-md-10 col-sm-10">
        <div class="section-title">
          <h2>Most Recommendation</h2>
          <div class="section-title__more">
            <span class="section-title__more__word">see all</span>
            <span class="icon-arrow-down"></span>
          </div>
        </div>
        <swiper
          :options="swiperRecommendationOption"
          ref="mySwiper"
          v-if="mostRecommendationList.length > 0"
        >
          <swiper-slide v-for="item of mostRecommendationList" :key="item.key">
            <router-link
              :to="{
                name: 'Details',
                params: { title: item.title, body: item.body },
              }"
              ><GameCard :title="item.title" :description="item.body"></GameCard
            ></router-link>
          </swiper-slide>
        </swiper>
        <listingLoader v-if="isRecommandedLoaderShow"></listingLoader>
      </div>
    </div>
  </div>
</template>

<script>
import { Swiper, SwiperSlide } from "vue-awesome-swiper";
import axios from "axios";

import "swiper/swiper-bundle.css";
// Import Swiper styles
import "swiper/swiper.scss";
import listingLoader from "../components/listingLoader";
import GameCard from "./GameCard";

export default {
  data() {
    return {
      mostRecommendationList: [],
      isRecommandedLoaderShow: false,
      swiperRecommendationOption: {
        spaceBetween: 10,
        slidesPerView: 5,
        loop: true,
        autoplay: {
          delay: 1500,
          stopOnLastSlide: false,
          disableOnInteraction: true,
        },
        speed: 400,
        breakpoints: {
          320: {
            slidesPerView: 2.5,
            spaceBetween: 10,
          },
          768: {
            slidesPerView: 3,
            spaceBetween: 30,
          },
          1024: {
            slidesPerView: 5,
            spaceBetween: 30,
          },
        },
      },
    };
  },
  components: {
    Swiper,
    SwiperSlide,
    listingLoader,
    GameCard,
  },
  methods: {
    getMostRecommandationList() {
      this.isRecommandedLoaderShow = true;
      axios.get("http://jsonplaceholder.typicode.com/posts").then((resp) => {
        console.log(resp.data);
        this.mostRecommendationList = resp.data;
        this.isRecommandedLoaderShow = false;
      });
    },
  },
  mounted() {
    this.getMostRecommandationList();
  },
};
</script>

<style lang="scss" scoped>
.most-recommended {
  > .row {
    //   margin: 0;
    > div {
      margin: 0 auto;
      background: #fff;
      margin-bottom: 35px;
    }
  }
}
@media (max-width: 768px) {
  .most-recommended {
    > .row {
      margin: 0;
    }
  }
}
</style>