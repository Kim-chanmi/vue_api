<template>
  <div>
    <HeaderCont />
    <TitleCont name1="unsplash" name2="reference api" />
    <section class="unsplash__wrap">
      <div class="container">
        <div class="unsplash__inner">
          <h2>Unsplash Random</h2>
          <ul>
            <li>
              <swiper
                :effect="'cards'"
                :grabCursor="true"
                :modules="modules"
                class="mySwiper"
              >
                <swiper-slide v-for="slide in sliders" :key="slide.id">
                  <a :href="`https://unsplash.com/photos/${slide.id}`">
                    <img :src="slide.urls.regular" :alt="slide.id" />
                  </a>
                </swiper-slide>
              </swiper>
            </li>
          </ul>
        </div>
        <div class="btn__list">
          <button v-for="title in titles" v-bind:key="title.name">
            {{ title.name }}
          </button>
        </div>
        <div class="unsplash_search">
          <h2>검색하기</h2>
          <form @submit.prevent="SearchUnsplashes()">
            <input
              type="search"
              id="search"
              placeholder="검색하세요"
              v-model="search"
            />
            <button type="submit">검색</button>
          </form>
        </div>
        <div class="cont__unsplash">
          <ul>
            <li v-for="splash in splashes" :key="splash.id">
              <a :href="`https://unsplash.com/photos/${splash.id}`">
                <img :src="splash.urls.regular" :alt="splash.id" />
              </a>
            </li>
          </ul>
        </div>
      </div>
    </section>

    <ContactCont />
    <FooterCont />
  </div>
</template>

<script>
import HeaderCont from "@/components/HeaderCont.vue";
import FooterCont from "@/components/FooterCont.vue";
import TitleCont from "@/components/TitleCont.vue";
import ContactCont from "@/components/ContactCont.vue";
import { ref } from "vue";

import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/effect-cards";
import { EffectCards } from "swiper";

export default {
  components: {
    HeaderCont,
    FooterCont,
    TitleCont,
    ContactCont,
    Swiper,
    SwiperSlide,
  },

  data: function () {
    return {
      modules: [EffectCards],
      titles: [
        { name: "3D Renders" },
        { name: "Experimental" },
        { name: "Architecture" },
        { name: "Fashion" },
        { name: "Nature" },
        { name: "People" },
        { name: "Athletics" },
      ],
    };
  },

  setup() {
    const splashes = ref([]);
    const sliders = ref([]);
    const search = ref("landscape");

    // const SearchSplashes = () => {
    //   fetch(
    //     `https://api.unsplash.com/search/photos/?client_id=ArGvdKlJWl3YpwcaZmGDf5jEEVo81-0sbA8evCVSBo4&query=${search.value}`
    //   )
    //     .then((response) => response.json())
    //     .then((result) => console.log(result))
    //     .then((error) => console.log(error));
    // };
    // SearchSplashes()
    const RandomSplashes = () => {
      fetch(
        "https://api.unsplash.com/photos/random/?client_id=ArGvdKlJWl3YpwcaZmGDf5jEEVo81-0sbA8evCVSBo4&count=30"
      )
        .then((response) => response.json())
        .then((result) => (splashes.value = result))
        // .then((result) => console.log(result))
        .then((error) => console.log(error));
    };
    RandomSplashes();

    const TopSplashes = () => {
      fetch(
        "https://api.unsplash.com/photos/random/?client_id=ArGvdKlJWl3YpwcaZmGDf5jEEVo81-0sbA8evCVSBo4&count=10"
      )
        .then((response) => response.json())
        .then((result) => (sliders.value = result))
        .then((error) => console.log(error));
    };
    TopSplashes();

    const SearchUnsplashes = async () => {
      fetch(
        `https://api.unsplash.com/search/photos?client_id=ArGvdKlJWl3YpwcaZmGDf5jEEVo81-0sbA8evCVSBo4&query=${search.value}`
      )
        .then((response) => response.json())
        .then((result) => {
          splashes.value = result.results;
          search.value = "";
        })
        .catch((error) => console.log(error));
    };
    SearchUnsplashes();

    return {
      splashes,
      search,
      sliders,
      RandomSplashes,
      TopSplashes,
      SearchUnsplashes,
    };
  },
};
</script>
<style lang="scss">
body {
  overflow-x: hidden;
}
.cont__unsplash {
  ul {
    column-count: 4;
    column-gap: 20px;
    width: 100%;

    li {
      margin-bottom: 20px;

      img {
        border-radius: 5px;
      }
    }
  }
}

.unsplash__inner {
  margin-bottom: 70px;
  h2 {
    font-size: 40px;
    color: var(--black);
    margin-bottom: 70px;
  }
  .swiper-slide img {
    width: 250px;
    height: 300px;
  }

  .swiper-slide {
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 18px;
    font-size: 22px;
    font-weight: bold;
    color: #fff;
  }

  a {
    color: var(--white);
  }
}
.unsplash_search {
  margin-bottom: 100px;
  position: relative;

  h2 {
    color: var(--black);
    font-size: 40px;
    text-indent: -9999px;
    height: 0;
  }

  input {
    background: #d5d5d5;
    border: 1px solid #d5d5d5;
    border-radius: 50px;
    color: var(--black);
    width: 100%;
    padding: 14px 30px;
    font-family: var(--font-kor1);
  }
  button {
    position: absolute;
    right: 8px;
    top: 5px;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    border: 0;
    font-family: var(--font-kor1);
    cursor: pointer;
    z-index: 1000;
    color: #000;
  }
}
.btn__list {
  margin-top: -40px;
  margin-bottom: 60px;
  text-align: center;

  button {
    display: inline-block;
    padding: 10px;
    margin-right: 10px;
    border-radius: 20px;
    cursor: pointer;
    background: #000;
    color: #fff;
    border: 1px solid #fff;
  }
  button:hover {
    background: #fff;
    color: #000;
    transition: all 0.3s;
  }
}
</style>
