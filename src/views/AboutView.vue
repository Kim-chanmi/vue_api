<template>
  <div>
    <HeaderCont />
    <TitleCont name1="about" name2="reperence" />
    <section className="cont__about">
      <div className="container">
        <div className="about__inner">
          <div className="part1">
            <img
              src="https://github.com/Kim-chanmi/vue_api/blob/main/src/assets/img/About_Vue01.jpg?raw=true"
              alt="하늘"
            />
            <h3 className="about__title">
              미래를 위해 오늘을 차분히 걷는 사람
            </h3>
            <p>
              언제나 미래를 위해 오늘의 걸음을 차분히 내딛고자 하는 마음으로,
              단시간에 과업을 수행하려는 욕심 없이 조용히 노력을 끌어모아 가는
              저의 성격은, 오랜 세월에 걸쳐 축적된 노하우를 태산과도 같은
              존재감으로 실천해 나가는 귀사의 행보에 맞물리는 점이 있다고
              생각했습니다. 낙숫물이 돌을 뚫는 성실한 노력의 중요성을 알고
              있으면서도, 자만하지 않고, 당장 준비가 떠들썩한 성과로 이어지지
              않더라도, 훗날을 대비하는 축적의 흐름이, 저의 미래까지 같이
              담보해줄 듯한 신뢰를 주어, 지원하게 되었습니다. <br />
              <br />
              어린 시절부터 할 일을 뒤로 미루지 않고, 욕심내지 않으며 찬찬히
              발짝을 내디뎌 성과를 이뤄낼 줄 알았던 온유한 성격으로 업무를
              꾸준히 수행하며, 단시간에 성과를 올리는 화려하고 개성적인 스타일은
              아니나, 그러므로 더욱 온건하게 진국을 우려내는 담백한 맛의
              소유자로, 귀사와 서서히 농도를 맞춰갈 수 있도록 노력하겠습니다.
              향후 귀사를 빛나게 할 위대한 족적의 한 걸음을 매일 조금씩 아로새겨
              나가는 직원의 마음가짐으로, 귀사와 뜻을 함께할 저의 성실한 업무
              수행의 자세를 부디 기대해 주시길 바랍니다. 감사합니다.
            </p>
          </div>
          <div className="part2">
            <img
              src="https://github.com/Kim-chanmi/vue_api/blob/main/src/assets/img/About_Vue02.jpg?raw=true"
              alt="러닝"
            />
            <div>
              <h3 className="about__title">도전과 노력으로 일하는 사람</h3>
              <p>
                사회생활에서 가장 중요한 것은 도전과 노력이라고 생각합니다. 저는
                언제나 현재에 충실하며 미래를 보는 안목으로 발전하기 위해 노력해
                왔고 지금은 귀사에 입사하기 위한 도전을 하고 있습니다. 분명
                귀사는 제게 많은 도움을 줄 것입니다. 하지만 이는 제가 중요하게
                여기는 노력이 뒷받침되어야 가능한 일일 것입니다. 제가 만약
                귀사에 입사하게 된다면 우선 끈기 있는 자세로 맡은 바 임무에
                충실히 해낼 수 있도록 하겠습니다. 그리고 저는 다양한 방면에서
                많은 경험을 쌓았다고 생각합니다. 이 경험을 바탕으로 여러 사람과
                함께 발전하고 웃으면서 근무하고 싶습니다. 한결 같은 마음으로
                성실하게 일하며 배우며, 책임감 있게 생활하겠습니다.
              </p>
            </div>
          </div>
          <div className="part3">
            <img
              src="https://github.com/Kim-chanmi/react_api/blob/main/src/assets/img/About_React03.jpg?raw=true"
              alt="들판"
            />
            <div>
              <h3 className="about__title">없어서는 안 될 사람</h3>
              <p>
                밝은 웃음을 가진 아이, 그 뒤에 책임감이 강한 아이, 아버지로부터
                성실함을 물려받은 아이라고 저를 소개하였습니다. 저는 이런 제
                자신에게 자신감이 있어서 이렇게 귀사에 지원하게 되었습니다. 아직
                배워야 할 것이 많고, 직접적인 사무직 경험이 없어 모르는 것도
                많을 것이라고 생각합니다. 하지만 매일 진일보하는 자세로 배워나갈
                것을 약속드립니다. 그래서 1년 후에는 이 회사에 없어서는 안 될
                귀중한 사원으로 성장하겠습니다. 또한 원만한 인간관계도 약속드릴
                수 있습니다. 예상치 못한 갈등에 부딪치거나 힘든 상황이 생겼을
                때도 좌절하거나 낙심하지 않고 대화로 풀어가며 함께 협동하는
                사원이 되겠습니다. <br />
                <br />
                아직 어리지만 그만큼 발전가능성이 충분하며 앞으로가 더욱
                기대되는 사람이 될 수 있습니다. 믿고 맡겨 주신다면 저 사람은
                언제 봐도 기분 좋은 사람이야, 저 사람과 일을 하면 저절로 힘이
                솟아, 저 친구가 한 일은 항상 믿을 만해, 라는 말을 듣는 사원으로
                성장하겠습니다. 잘 부탁드립니다.
              </p>
            </div>
          </div>
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

export default {
  components: {
    HeaderCont,
    FooterCont,
    TitleCont,
    ContactCont,
  },
};
</script>
<style lang="scss">
.about__inner {
  > div {
    margin-bottom: 500px;
    font-family: var(--font-kor2);
    line-height: 1.6;
    color: var(--black);

    .about__title {
      font-size: 24px;
      margin-bottom: 30px;
      color: var(--black);
    }
    p {
      text-align: 1.5;
    }
  }
  .part1 {
    margin-top: 200px;

    img {
      margin-bottom: 50px;
      object-fit: cover;
    }
    p {
      width: 65%;
      font-size: 16px;
    }
  }
  .part2 {
    display: flex;
    justify-content: space-between;

    img {
      width: 65%;
      object-fit: cover;
    }
    div {
      width: 30%;
      font-size: 16px;
    }
  }
  .part3 {
    display: flex;
    justify-content: space-between;
    flex-direction: row-reverse;

    img {
      width: 65%;
      object-fit: cover;
    }
    div {
      width: 30%;
      font-size: 16px;
    }
  }
}
</style>
