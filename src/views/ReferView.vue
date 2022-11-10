<template>
  <div>
    <HeaderCont />
    <TitleCont name1="reference" name2="api" />

    <section className="cont__refer">
      <div className="container">
        <div className="refer__inner">
          <h2>CSS</h2>
          <ul className="refer_list">
            <li v-for="refer in refers" :key="refer.title">
              <a href="#">
                <span className="num">{{ refer.num }}</span>
                <span className="name">{{ refer.title }}</span>
                <span className="desc">{{ refer.desc }}</span>
                <span className="star">{{ refer.descStar }}</span>
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

export default {
  components: {
    HeaderCont,
    FooterCont,
    TitleCont,
    ContactCont,
  },

  setup() {
    const refers = ref([]);

    const reference = () => {
      fetch(
        "https://kim-chanmi.github.io/react_api/src/utils/cssReference_me.json"
      )
        .then((response) => response.json())
        // .then((result) => console.log(result.cssRefer))
        .then((result) => (refers.value = result.cssRefer))
        .catch((error) => console.log("error", error));
    };
    reference();

    return {
      refers,
      reference,
    };
  },
};
</script>

<style lang="scss" scoped>
.refer__inner {
  padding-bottom: 200px;

  h2 {
    font-size: 30px;
    color: var(--black);
    margin-bottom: 10px;
  }
  .refer_list {
    border: 1px solid var(--bg-dark-border);
    margin-bottom: 20px;
    li {
      border-bottom: 1px solid var(--bg-dark-border);
      a {
        display: flex;
        align-items: center;
        width: 100%;
        color: var(--black);

        span {
          display: inline-block;
          padding: 15px 20px;
        }

        .num {
          flex: 1 1 5%;
          text-align: center;
          border-right: 1px solid var(--bg-dark-border);
        }
        .name {
          flex: 1 1 20%;
        }
        .desc {
          flex: 1 1 65%;
          border-right: 1px solid var(--bg-dark-border);
          font-family: var(--font-kor1);
          // font-family: "NanumSquare-ExtraBold";
        }
        .star {
          flex: 1 1 10%;
          text-align: center;
        }
      }
    }
  }
}
</style>
