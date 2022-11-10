<template>
  <div>
    <HeaderCont />
    <TitleCont name1="movie" name2="reference api" />
    <section class="cont_movie">
      <div class="container">
        <div class="cont__popular__movie">
          <div class="movie__pop">
            <div class="movie__popular_inner">인기 TOP20</div>
            <ul>
              <li>
                <swiper
                  :effect="'coverflow'"
                  :grabCursor="true"
                  :centeredSlides="true"
                  :slidesPerView="'auto'"
                  :initialSlide="1"
                  :autoplay="{
                    delay: 2500,
                    disableOnInteraction: false,
                  }"
                  :coverflowEffect="{
                    rotate: 50,
                    stretch: 0,
                    depth: 100,
                    modifier: 1,
                    slideShadows: true,
                  }"
                  :pagination="true"
                  :modules="modules"
                  class="mySwiper"
                >
                  <swiper-slide v-for="slider in sliders" :key="slider.id">
                    <a :href="`https://www.themoviedb.org/movie/${slider.id}`">
                      <img
                        :src="`https://image.tmdb.org/t/p/w500/${slider.poster_path}`"
                        :alt="slider.title"
                      />
                    </a>
                  </swiper-slide>
                </swiper>
              </li>
            </ul>
          </div>
        </div>
        <div class="movie__search">
          <h2>검색하기</h2>
          <form @submit.prevent="SearchMovies()">
            <input
              type="search"
              id="search"
              placeholder="검색하세요"
              v-model="search"
            />
            <button type="submit">검색</button>
          </form>
        </div>
        <div class="movie__inner">
          <ul>
            <li v-for="movie in movies" :key="movie.id">
              <a :href="`https://www.themoviedb.org/movie/${movie.id}`">
                <img
                  :src="`https://image.tmdb.org/t/p/w500/${movie.poster_path}`"
                  :alt="movie.title"
                />
                <em>
                  <span class="title">{{ movie.title }}</span>
                  <span class="star">{{ movie.vote_average }}</span>
                </em>
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
import "swiper/css/effect-coverflow";
import "swiper/css/pagination";
import { EffectCoverflow, Pagination, Autoplay } from "swiper";

export default {
  components: {
    HeaderCont,
    TitleCont,
    ContactCont,
    FooterCont,
    Swiper,
    SwiperSlide,
  },
  setup() {
    const movies = ref([]);
    const sliders = ref([]);
    const search = ref("marvel");

    const SearchMovies = async () => {
      fetch(
        `https://api.themoviedb.org/3/search/movie?api_key=130fd98d6e6907020a62f2869eed23e1&query=${search.value}`
      )
        .then((response) => response.json())
        .then((result) => {
          movies.value = result.results;
          search.value = "";
        })
        .catch((error) => console.log(error));
    };
    SearchMovies();

    const TopMoviies = async () => {
      fetch(
        `https://api.themoviedb.org/3/movie/popular?api_key=130fd98d6e6907020a62f2869eed23e1&language=en-US`
      )
        .then((response) => response.json())
        .then((result) => (sliders.value = result.results))
        .catch((error) => console.log(error));
    };
    TopMoviies();
    return {
      movies,
      sliders,
      search,
      SearchMovies,
      modules: [EffectCoverflow, Pagination, Autoplay],
      TopMoviies,
    };
  },
};
</script>
<style lang="scss">
.movie__inner {
  ul {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;

    li {
      width: 23%;
      position: relative;
      transition: all 0.4s;

      &:hover {
        scale: 1.03;
      }

      em {
        display: block;
        height: 80px;
        margin-bottom: 30px;
        font-family: var(--font-kor1);
      }

      .title {
        padding: 5px 0;
        display: inline-block;
        color: #000;
        font-size: 18px;
      }
      .star {
        background: #fff;
        color: #000;
        position: absolute;
        left: 10px;
        top: 10px;
        width: 30px;
        height: 30px;
        border-radius: 50%;
        text-align: center;
        line-height: 30px;
        font-weight: 800;
      }
    }
  }
  a {
    color: var(--white);
  }
}

.movie__search {
  margin-bottom: 100px;
  position: relative;

  .container {
    position: relative;
  }

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
.movie__pop {
  margin-top: 150px;
  width: 100%;

  .movie__popular_inner {
    font-size: 25px;
    margin-bottom: 70px;
    text-align: left;
    font-family: var(--font-kor1);
  }

  ul {
    display: flex;
    justify-content: space-between;
    width: 80%;
    margin: 0 auto;

    .swiper-wrapper {
      width: 30%;

      .swiper-slide-active img {
        margin-bottom: 80px;
      }
    }

    li {
      margin-bottom: 60px;
    }
  }
  a {
    color: var(--black);
  }
}
</style>
