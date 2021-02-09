<template>
  <div class="details-page">
    <Header></Header>
    <div class="details-page__content">
      <div class="container">
        <div class="row">
          <div class="col-lg-8 col-md-10">
            <div class="details-page__content__image">
              <img src="../assets/images/feature-game.jpeg" alt="" />
            </div>
            <h3 class="details-page__content__title">{{ itemTitle }}</h3>
            <p class="details-page__content__description">{{ itemDetails }}</p>
          </div>
        </div>
      </div>
    </div>
    <MostRecommendation></MostRecommendation>
  </div>
</template>
<script>
import Header from "../components/Header";
import MostRecommendation from "../components/MostRecommended";

export default {
  props: ["title"],
  data() {
    return {
      itemTitle: "",
      itemDetails: "",
    };
  },
  components: {
    Header,
    MostRecommendation,
  },
  methods: {},
  mounted() {
    this.itemTitle = this.$route.params.title;
    this.itemDetails = this.$route.params.body;
  },
};
</script>

<style lang="scss">
.details-page__content {
  margin: 25px 0;
  .row {
    > div {
      margin: 0 auto;
      padding: 0;
      background-color: #fff;
    }
  }
  .details-page__content__image {
    margin-bottom: 25px;
    img {
      width: 100%;
    }
  }
  .details-page__content__title,
  .details-page__content__description {
    padding: 0 20px;
  }
  .details-page__content__description {
    font-size: calc(18px + (22 - 18) * ((100vw - 1366px) / (1920 - 1366)));
  }
  .details-page__content__title {
    font-size: calc(23px + (27 - 23) * ((100vw - 1366px) / (1920 - 1366)));
  }
}
@media (max-width: 1366px) {
  .details-page__content {
    .details-page__content__title {
      font-size: calc(16px + (23 - 16) * ((100vw - 320px) / (1366 - 320)));
    }
    .details-page__content__description {
      font-size: calc(14px + (18 - 14) * ((100vw - 320px) / (1366 - 320)));
    }
  }
}
@media (max-width: 768px) {
  .details-page__content {
    margin: 15px 0;
    .row {
      margin: 0;
    }
  }
}
</style>
