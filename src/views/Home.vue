<template>
  <div class="home-page">
    <Header></Header>

    <div class="home-page__category">
        <swiper :options="swiperCategoryListOption">
          <swiper-slide v-for="(item, index) of categoryList" :key="item.key">
            <span
              class="home-page__category__item"
              :data-index="index"
              :class="{ active: active_el == index }"
              @click="highlightMenu($event, index)"
              >{{ item }}</span
            >
          </swiper-slide>
        </swiper>
    </div>
    <div class="featured-game">
      <div class="container">
      <div class="row">
        <div class="col-lg-8 col-md-10">
          <div class="row">
            <div class="col-lg-9 col-md-12">
              <div class="featured-game__image">
                <img
                  src="../assets/images/feature-game.jpeg"
                  alt="feature-game"
                />
              </div>
            </div>
            <dov class="col-lg-3">
              <div class="featured-game__content">
                <h3 class="featured-game__content__title">Subway Surface</h3>
                <span class="featured-game__content__subtitle">SYBO Games</span>
                <p class="featured-game__content__description">
                  SURF the urban wave! DODGE the oncoming trains! GRIND trains
                  with your cool… crew of friends! Run as far as you can on the
                  endless train tracks with your friends Jake, Tricky & Fresh
                  whilst attempting to escape from the Inspector and his fast
                  paced dog… Read more
                </p>
                <span class="featured-game__content__download"
                  >300k Downloads</span
                >
                <button class="generic__btn">more info</button>
              </div>
            </dov>
          </div>
        </div>
      </div>

      </div>
    </div>
  

    <MostRecommendation></MostRecommendation>
    <div class="home-page_popular container">
      <div class="row">
        <div class="col-lg-8 col-md-10 col-sm-10">
          <div class="section-title">
            <h2>Most Popular</h2>
            <div class="section-title__more">
              <span class="section-title__more__word">see all</span>
              <span class="icon-arrow-down"></span>
            </div>
          </div>
          <swiper
            :options="swiperPopularOption"
            v-if="mostPopularList.length > 0"
          >
            <swiper-slide v-for="item of mostPopularList" :key="item.key">
              <router-link
                :to="{
                  name: 'Details',
                  params: { title: item.title, body: item.body },
                }"
                ><GameCard
                  :title="item.title"
                  :description="item.body"
                ></GameCard
              ></router-link>
            </swiper-slide>
          </swiper>
          <listingLoader v-if="isPopularLoaderShow"></listingLoader>
        </div>
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
import GameCard from "../components/GameCard";
import listingLoader from "../components/listingLoader";
import Header from "../components/Header";
import MostRecommendation from "../components/MostRecommended";

export default {
  name: "Home",
  components: {
    Swiper,
    SwiperSlide,
    GameCard,
    listingLoader,
    Header,
    MostRecommendation,
  },
  data() {
    return {
      mostPopularList: [],
      isPopularLoaderShow: false,
      active_el: 5,

      swiperCategoryListOption: {
        spaceBetween: 10,
        loop: false,
        slidesPerView: 13,
        autoplay: {
          delay: 5000,
        },
        speed: 400,
        breakpoints: {
          320: {
            slidesPerView: 3,
            spaceBetween: 10,
          },
          414: {
            slidesPerView: 4,
            spaceBetween: 10,
          },
          768: {
            slidesPerView: 7,
            spaceBetween: 30,
          },
          1024: {
            slidesPerView: 13,
            spaceBetween: 30,
          },
        },
      },
      categoryList: [
        "action",
        "advanture",
        "sport",
        "arcada",
        "puzzle",
        "strategy",
        "simulation",
        "action",
        "advanture",
        "sport",
        "arcada",
        "puzzle",
        "strategy",
        "simulation",
        "action",
        "advanture",
        "sport",
        "arcada",
        "puzzle",
        "strategy",
        "simulation",
      ],
      swiperPopularOption: {
        spaceBetween: 10,
        loop: false,
        slidesPerView: 5,
        autoplay: {
          delay: 5000,
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
  methods: {
    getMostPopularList() {
      this.isPopularLoaderShow = true;
      axios.get("http://jsonplaceholder.typicode.com/posts").then((resp) => {
        console.log(resp.data);
        this.mostPopularList = resp.data;
        this.isPopularLoaderShow = false;
      });
    },

    highlightMenu(e, index) {
      // document.querySelector('active').classList.remove('active');
      // e.target.classList.toggle('active')
      this.active_el = index;
      console.log(e.srcElement, index);
    },
    sendData(title) {
      this.$emit("sendData", title);
    },
  },
  mounted() {
    this.getMostPopularList();
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/home-page.scss";
</style>
