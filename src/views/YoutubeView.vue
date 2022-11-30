<template>
  <div>
    <HeaderCont />
    <TitleCont name1="youtube" name2="reference api" />
    <section class="youtube__wrap">
      <div class="container">
        <div class="youtube__popular">
          <div class="youtube__inner">
            <h2>Youtube Random</h2>
            <li>
              <swiper
                :grabCursor="true"
                :effect="'creative'"
                :creativeEffect="{
                  prev: {
                    shadow: false,
                    translate: [0, 0, -400],
                  },
                  next: {
                    translate: ['100%', 0, 0],
                  },
                }"
                :modules="modules"
                class="mySwiper"
              >
                <swiper-slide
                  v-for="slider in sliders"
                  :key="slider.id.videoId"
                >
                  <a
                    :href="`https://www.youtube.com/watch?v=${slider.id.videoId}`"
                  >
                    <img
                      :src="slider.snippet.thumbnails.medium.url"
                      :alt="slider.snippet.description"
                    />
                  </a>
                </swiper-slide>
              </swiper>
            </li>
          </div>
        </div>
        <div class="movie__search">
          <h2>검색하기</h2>
          <form @submit.prevent="SearchYoutubes()">
            <input
              type="search"
              id="search"
              placeholder="검색하세요"
              v-model="search"
            />
            <button type="submit">검색</button>
          </form>
        </div>
        <div class="youtube__inner">
          <ul>
            <li v-for="youtube in youtubes" :key="youtube.id.videoId">
              <a
                :href="`https://www.youtube.com/watch?v=${youtube.id.videoId}`"
              >
                <img
                  :src="youtube.snippet.thumbnails.medium.url"
                  :alt="youtube.snippet.description"
                />
                <span>{{ youtube.snippet.title }}</span>
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
import "swiper/css/effect-creative";
import { EffectCreative } from "swiper";

export default {
  components: {
    HeaderCont,
    FooterCont,
    TitleCont,
    ContactCont,
    Swiper,
    SwiperSlide,
  },

  setup() {
    const youtubes = ref([]);
    const sliders = ref([]);
    const search = ref("landscape");

    const RandomYoutube = () => {
      fetch(
        "https://raw.githubusercontent.com/Kim-chanmi/react_api/main/src/utils/youtube_video.json"
      )
        .then((response) => response.json())
        .then((result) => (youtubes.value = result.items))
        // .then((result) => console.log(result))
        .catch((error) => console.log("error", error));
    };
    RandomYoutube();

    const TopYoutube = () => {
      fetch(
        "https://raw.githubusercontent.com/Kim-chanmi/react_api/main/src/utils/youtube_video.json"
      )
        .then((response) => response.json())
        .then((result) => (sliders.value = result.items))
        // .then((result) => console.log(result))
        .catch((error) => console.log("error", error));
    };
    TopYoutube();

    const SearchYoutubes = () => {
      fetch(
        `https://youtube.googleapis.com/youtube/v3/search?key=AIzaSyBMw5RG0lHjQd8xTnmA63HCsEe5tXuQ764&part=snippet&maxResults=10&type=video&q=${search.value}`
      )
        .then((response) => response.json())
        .then((result) => {
          youtubes.value = result.items;
          search.value = "";
        })
        // .then((result) => console.log(result))
        .catch((error) => console.log("error", error));
    };
    SearchYoutubes();

    return {
      modules: [EffectCreative],
      youtubes,
      sliders,
      search,
      RandomYoutube,
      TopYoutube,
      SearchYoutubes,
    };
  },
};
</script>
<style lang="scss">
.youtube__inner {
  ul {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    gap: 10px;
    font-family: var(--font-kor1);
    li {
      width: 24%;
      margin-bottom: 20px;

      span {
        display: inline-block;
        padding: 5px 0;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
        width: 100%;
      }
      img {
        border-radius: 5px;
        overflow: hidden;
      }
    }
  }
}
.youtube__inner {
  h2 {
    font-size: 40px;
    color: var(--black);
  }
  li {
    list-style: none;
  }
  .swiper img {
    margin: 100px auto;
  }

  .swiper-slide {
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 22px;
    font-weight: bold;
  }
}
.youtube__popular {
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
</style>
