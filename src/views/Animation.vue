<template>
  <div class="animation">
    <h1 class="title">Animation</h1>
    <main class="contents">
      <div class="box">
        <img class="image" src="../assets/image01.jpeg" alt="dolphin">
        <h2 class="sub-title">What is Lorem Ipsum?</h2>
        <p>
          Lorem Ipsum is simply dummy text of the printing and typesetting industry.
          Lorem Ipsum has been the industry's standard dummy text ever since the 1500s,
          when an unknown printer took a galley of type and scrambled it to make a type specimen book.
          It has survived not only five centuries, but also the leap into electronic typesetting,
          remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages,
          and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.
        </p>
      </div>
      <div class="box">
        <img class="image" src="../assets/image02.jpeg" alt="stingray">
        <h2 class="sub-title">Why do we use it?</h2>
        <p>
          It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout.
          The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters,
          as opposed to using 'Content here, content here', making it look like readable English.
          Many desktop publishing packages and web page editors now use Lorem Ipsum as their default model text,
          and a search for 'lorem ipsum' will uncover many web sites still in their infancy.
          Various versions have evolved over the years, sometimes by accident, sometimes on purpose (injected humour and the like).
        </p>
      </div>
      <div class="box">
        <img class="image" src="../assets/image03.jpeg" alt="penguin">
        <h2 class="sub-title">Where can I get some?</h2>
        <p>
          There are many variations of passages of Lorem Ipsum available,
          but the majority have suffered alteration in some form, by injected humour,
          or randomised words which don't look even slightly believable.
          If you are going to use a passage of Lorem Ipsum,
          you need to be sure there isn't anything embarrassing hidden in the middle of text.
          All the Lorem Ipsum generators on the Internet tend to repeat predefined chunks as necessary,
          making this the first true generator on the Internet. It uses a dictionary of over 200 Latin words,
          combined with a handful of model sentence structures, to generate Lorem Ipsum which looks reasonable.
          The generated Lorem Ipsum is therefore always free from repetition, injected humour, or non-characteristic words etc.
        </p>
      </div>
    </main>
  </div>
</template>

<script>
// @ is an alias to /src
// import {TweenMax} from "gsap";

export default {
  name: 'animation',
  components: {
    //
  },
  mounted() {
    // rootからbottom:-150pxの位置で発火
    const options = {
      root: null,
      rootMargin: "0px 0px -150px",
      threshold: 0
    }

    const images = document.querySelectorAll('.image')
    images.forEach((target) => this.onIntersect(target, options))

    const subTitles = document.querySelectorAll('.sub-title')
    subTitles.forEach((target) => this.onIntersect(target, options))
  },
  methods: {
    onIntersect(target, options = {}) {
      const observer = new IntersectionObserver(this.addShowClass, options)
      // 監視したい要素をobserveする。
      observer.observe(target)
    },
    addShowClass(entries) {
      for(const e of entries) {
        if (e.isIntersecting) {
          e.target.classList.add("show")
        }
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.animation {
  margin: 5%;

  .box {
    margin: 30px 0 60px 0;

    .image {
      opacity: 0;
      transform: translateY(40px);
      transition: opacity 1.4s, transform 0.8s;

      &.show {
        opacity: 1;
        transform: translateY(0);
      }
    }

    .sub-title {
      opacity: 0;
      transform: translateX(-40px);
      transition: opacity 1.4s, transform 0.8s;

      &.show {
        opacity: 1;
        transform: translateX(0);
      }
    }

    > p {
      background-color: #f9f9f9;
      padding: 16px;
      text-align: left;
    }
  }

  img {
    width: 100%;
    height: 90vh;
    margin-bottom: 30px;
  }

  h2 {
    margin-bottom: 10px;
  }
}
</style>
