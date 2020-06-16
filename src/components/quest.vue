<template>
  <div>

    <!-- Header section -->

    <header class="header">
      <div class="wrapper">
        <div class="header__wrapper">
          <div class="header__logo">
            <p>
              <img :src="apidata.baseApiFilesUrl + 'files/Логотип/Plum.svg'" alt="Дизайн студия Plumberry"
                class="header__logo-pic">
            </p>
          </div>

          <nav class="header__nav">
            <ul class="header__list">
              <li class="header__item" v-for="(item, index) in headerItems" :key="parseInt(index)"
                @click="setHeaderSliderBlock(index)">
                <a href="#project-pic" class="header__link">{{item}}</a>
              </li>
              <li class="header__item">
                <button class="header__button">связаться с нами</button>
              </li>
            </ul>
          </nav>
        </div>
      </div>
    </header>

    <!-- Header section end -->

    <!-- Main start section start-->

    <main class="main">
      <div class="main__screen">
        <div class="upper__slider-arrows">
          <a href="#main-pic" class="slider-arrows" @click="setNextSlidesInfo()">
            <div>
              <img src="../assets/img/left_arrow.svg" alt="">
            </div>
          </a>
          <a href="#main-pic" class="slider-arrows" @click="setNextSlidesInfo()">
            <div>
              <img src="../assets/img/right_arrow.svg" alt="">
            </div>
          </a>
        </div>

        <!--  Upper slider section start-->

        <div id="main-pic" class="main-pic">
          <input type="radio" name="point" class="main-pic-input" id="slide1" :checked="infoIndex == 0">
          <input type="radio" name="point" class="main-pic-input" id="slide2" :checked="infoIndex == 1">

          <div class="slider">
            <div class="slides slide1"></div>
            <div class="slides slide2"></div>
          </div>
        </div>

        <!-- Upper slider section end -->

        <div class="main__circle">
          <nav class="main__nav__circles">
            <a href="#main-pic" class="main__nav__circle-link" v-for="(item, index) in apidata.slidesInfo"
              :key="parseInt(index)" @click="setNextSlidesInfo()">
              <div class="main__nav__circle" :class="{'project__nav__circle-selected': infoIndex == index}">
              </div>
            </a>
          </nav>
          <div class="offer">
            <p>
              {{apidata.slidesInfo[infoIndex].text1}}
            </p>
            <p>
              {{apidata.slidesInfo[infoIndex].text2}}
            </p>
          </div>
          <div class="offer datails">
            <p>
              {{apidata.slidesInfo[infoIndex].text3}}
            </p>
          </div>

        </div>
      </div>
      <section class="intro">
        <div class="intro__title">
          <h1>
            {{apidata.infoBlock.titleLight}}
          </h1>
        </div>
        <div class="intro__title">
          <h1>
            {{apidata.infoBlock.titleBold}}
          </h1>
        </div>

        <h3 class="intro__subtitle">
          Деятельности «Plumberry» — проектирование и дизайн интерьера. Дизайнеры и архитекторы компании помогут
          создать уникальный интерьер, отвечающий Вашим стилистическим пристрастиям, а также всем требованиям
          современных тенденций и эргономики. Мы также занимаемся разработкой и производством индивидуальной мебели
          для кухонь, гостиных, спален и т.п.
        </h3>

        <div class="benefits__cards">
          <div v-for="(value, item, index) in apidata.infoBlock" :key="parseInt(index)" :id="index">
            <div class="benefits__card-pic">
              <img :src="apidata.baseApiFilesUrl + apidata.infoBlock.blocks[index].icon" alt=""
                class="benefits__card_icon">
            </div>
            <h3>
              {{apidata.infoBlock.blocks[index].text}}
            </h3>
          </div>
        </div>
      </section>

      <!-- Projects section start -->

      <section class="projects">
        <div class="project__pic">
          <div class="project__slider-arrows">
            <a href="#project-pic" class="slider-arrows">
              <div>
                <img src="../assets/img/left_arrow.svg" alt="" @click="setPreviousProjectBlock()">
              </div>
            </a>
            <a href="#project-pic" class=" slider-arrows">
              <div>
                <img src="../assets/img/right_arrow.svg" alt="" @click="setNextProjectBlock()">
              </div>
            </a>
          </div>
          <nav class="project__circles">
            <a href="#project-pic" class="project__circle" v-for="(item, index) in apidata.sliderBlock"
              :key="parseInt(index)" @click="setSliderBlock(index)"
              :class="{'project__circle-selected': projIndex == index}">
              <div>
                <img :src="apidata.baseApiFilesUrl + apidata.sliderBlock[index].icon" alt=""
                  class="project__circle-pic">
              </div>
            </a>
          </nav>

          <nav class="project__nav__circles">
            <a href="#project-pic" class="project__nav__circle-link" v-for="(item, index) in apidata.sliderBlock"
              :key="parseInt(index)" @click="setSliderBlock(index)">
              <div class="project__nav__circle" :class="{'project__nav__circle-selected': projIndex == index}">
              </div>
            </a>
          </nav>

          <div class="project__wrapper">
            <div class="intro__title">
              <p>
                {{apidata.sliderBlock[projIndex].titleLight}}
              </p>
            </div>
            <div class="intro__title">
              <p>
                {{apidata.sliderBlock[projIndex].titleBold}}
              </p>
            </div>
            <div class="project__love">
              <p>{{apidata.sliderBlock[projIndex].subTitle}}</p>
            </div>
          </div>
          <img id="project-pic" :src="apidata.baseApiFilesUrl + apidata.sliderBlock[projIndex].images[id]" alt=""
            class="project-pic">
        </div>

        <div class="project__menu">
          <nav class="project__menu__nav">
            <ul class="project__menu__list">
              <li class="project__menu__item" v-for="(item, index) in projectMenu[projIndex]" :key="parseInt(index)"
                @click="setProjectMenu(index)">
                <p class="project__menu__link">{{item}}</p>
                <p class="project__submenu__link" v-for="(item, id) in projectSubMenu[position]" :key="parseInt(id)"
                  @click="setProjectMenuImage(index, id)" v-show="index == position">
                  {{apidata.sliderBlock[projIndex].titleLight}} -
                  {{projectMenu[projIndex][position]}} - {{id+1}}
                </p>
              </li>
            </ul>
          </nav>
        </div>
      </section>
    </main>

    <!-- Projects section end -->

    <!-- Main section end -->

    <!-- Footer section start -->

    <footer class="footer">
      <div class="wrapper">
        <div class="footer__wrapper">
          <nav class="footer__menu__nav">
            <ul>
              <li v-for="(item, index) in headerItems" :key="parseInt(index)">
                <a href="#project-pic" class="footer__menu__link" @click="setHeaderSliderBlock(index)">{{item}}</a>
              </li>
            </ul>
          </nav>
          <nav class="footer__menu__nav">
            <ul>
              <li>
                <a href="#1" class="footer__menu__link">Партнерская программа</a>
              </li>
              <li>
                <a href="#1" class="footer__menu__link">Блог</a>
              </li>
              <a href="#0" class="footer__link bottom">
                Согласие на обработку персональных данных
              </a>
            </ul>
          </nav>
          <div>
            <div class="social">
              <p class="footer__sign">Мы в социальных медиа</p>
            </div>
            <div class="social__media">
              <div class="social-icon">
                <a href="#1" class="footer__logo-link">
                  <img src="../assets/img/fb_icon.png" alt="" class="social-icon">
                </a>
              </div>
              <div class="social-icon">
                <a href="#2" class="footer__logo-link">
                  <img src="../assets/img/insta_icon.png" alt="" class="social-icon">
                </a>
              </div>
              <div class="social-icon">
                <a href="#3" class="footer__logo-link">
                  <img src="../assets/img/vk_icon.png" alt="" class="social-icon">
                </a>
              </div>
            </div>
          </div>
          <div>
            <p class="footer__sign">Подписаться на новости</p>
            <div class="footer__subscribe">
              <div class="footer__email"><input type="text" placeholder="EMAIL">
              </div>
              <a href="#0">
                <div class="footer__email circle">

                  <img src="../assets/img/right_arrow.svg" alt="" class="footer__subscribe-pic">
                </div>
              </a>
            </div>
            <div>
              <p class="footer__sign bottom">© ALL RIGHTS RESERVED</p>
            </div>

          </div>
        </div>
      </div>
    </footer>

    <!-- Footer section end -->

  </div>
</template>

<script>
  import axios from 'axios';
  export default {
    name: "quest",
    data() {
      return {
        projectMenu: [],
        projectSubMenu: [],
        projIndex: 0,
        position: 0,
        id: 0,
        infoIndex: 0,
        headerItems: ["Кухни", "Спальни", "Гостинные", "Ванные комнаты"],
        url: "https://raw.githubusercontent.com/obvu/frontend-testcase/master/apidata.json",
        apidata: {},
      }
    },
    created() {
      axios
        .get(this.url)
        .then(response => {
          this.apidata = response.data;

          /* Массив для меня выбора стилей в Project section (не выводим пункты для несуществующих картинок) - */

          for (let projIndex = 0; projIndex < this.apidata.sliderBlock.length; projIndex++) {
            this.projectMenu[projIndex] = [];

            for (let position = 0; position < this.apidata.sliderBlock[projIndex].types.length; position++) {
              let key = '';
              for (let i = 0; i < 3; i++) {
                key = key + this.apidata.sliderBlock[projIndex].types[position][i].toLowerCase();
              }
              for (let i = 0; i < this.apidata.sliderBlock[projIndex].images.length; i++) {
                if (this.apidata.sliderBlock[projIndex].images[i].toLowerCase().indexOf(key) != -1) {
                  this.projectMenu[projIndex].push(this.apidata.sliderBlock[projIndex].types[position]);
                }
              }
            }
          }
          console.log('projectMenu: ', this.projectMenu);
        })
        .catch(error => {
          console.log("error", error);
        });
    },
    methods: {
      setSliderBlock: function (index) {
        this.position = '';
        this.projIndex = index;
      },

      setProjectMenu: function (index) {
        this.position = '';
        let key = '';
        this.position = index;
        let projectSub = [];

        for (let i = 0; i < 3; i++) {
          key = key + this.projectMenu[this.projIndex][this.position][i].toLowerCase();
        }

        for (let i = 0; i < this.projectMenu[this.projIndex].length; i++)
          this.projectSubMenu[this.position] = 0;

        for (let i = 0; i < this.apidata.sliderBlock[this.projIndex].images.length; i++) {
          if (this.apidata.sliderBlock[this.projIndex].images[i].toLowerCase().indexOf(key) != -1) {

            projectSub.push(i);
          }
        }
        this.projectSubMenu[this.position] = projectSub;

      },
      setProjectMenuImage(index, id) {
        this.id = this.projectSubMenu[index][id];
      },
      setHeaderSliderBlock: function (index) {
        switch (index) {
          case 0:
            this.projIndex = 1;
            break;
          case 1:
            this.projIndex = 2;
            break;
          case 2:
            this.projIndex = 0;
            break;
          case 3:
            this.projIndex = 3;
        }
      },
      setPreviousProjectBlock: function () {
        if (this.projIndex == 0) this.projIndex = 3;
        else this.projIndex--;
      },
      setNextProjectBlock: function () {
        if (this.projIndex == 3) this.projIndex = 0;
        else this.projIndex++;
      },

      setNextSlidesInfo: function () {
        if (this.infoIndex == 1) this.infoIndex = 0;
        else this.infoIndex++;
      }

    },
  };
</script>

<style>
  /*Reset section*/

  html {
    box-sizing: border-box;
  }

  *,
  *::before,
  *::after {
    box-sizing: inherit;
  }

  html,
  body,
  div,
  h1,
  h2,
  h3,
  h4,
  h5,
  h6,
  p,
  a,
  ul,
  img,
  li,
  form,
  label,
  footer,
  header,
  main,
  nav,
  section {
    margin: 0;
    padding: 0;
    border: 0;
    font-size: 100%;
    font: inherit;
    vertical-align: baseline;
    box-sizing: border-box;
  }

  img {
    vertical-align: middle;
  }

  li {
    list-style-type: none;
  }

  /*Start*/

  @font-face {
    font-family: "PF Bague Sans Pro";
    src: url("../assets/fonts/PFBagueSansPro.eot");
    src: local("../assets/fonts/PF Bague Sans Pro"), local("PFBagueSansPro"),
      url("../assets/fonts/PFBagueSansPro.eot?#iefix") format("embedded-opentype"),
      url("../assets/fonts/PFBagueSansPro.woff2") format("woff2"),
      url("../assets/fonts/PFBagueSansPro.woff") format("woff"),
      url("../assets/fonts/PFBagueSansPro.ttf") format("truetype");
    font-weight: normal;
    font-style: normal;
  }


  @font-face {
    font-family: "PF Bague Sans Pro";
    src: url("../assets/fonts/PFBagueSansPro-Bold.eot");
    src: local("../assets/fonts/PF Bague Sans Pro Bold"), local("PFBagueSansPro-Bold"),
      url("../assets/fonts/PFBagueSansPro-Bold.eot?#iefix") format("embedded-opentype"),
      url("../assets/fonts/PFBagueSansPro-Bold.woff2") format("woff2"),
      url("../assets/fonts/PFBagueSansPro-Bold.woff") format("woff"),
      url("../assets/fonts/PFBagueSansPro-Bold.ttf") format("truetype");
    font-weight: bold;
    font-style: normal;
  }

  html {
    font-family: "PF Bague Sans Pro";
    font-style: normal;
    font-weight: normal;
    line-height: 1.2;
    font-size: 10px;
  }

  /*Header section*/

  #app {
    position: relative;
    width: 1366px;
    margin: 0 auto;
  }

  .header {
    position: relative;
    left: 0;
    top: 0;
    height: 76px;
  }

  .wrapper {
    position: relative;
    width: 1366px;
    margin: 0 auto;
    height: 76px;

  }

  .header__wrapper {
    display: flex;
    flex-wrap: wrap;
    align-items: flex-end;
    justify-content: space-between;
    background-color: white;
    height: 76px;

  }

  .header__nav {
    position: relative;
    margin-bottom: 15px;
  }

  .header__list {
    display: flex;
    flex-wrap: wrap;
  }

  .header__item {
    margin-left: 58px;
  }

  .header__link {
    font-size: 1.3rem;
    line-height: 1.8rem;
    letter-spacing: 0.2rem;
    text-transform: uppercase;
    text-decoration: none;
    outline: none;
  }

  .header__button {
    font-size: 1.3rem;
    line-height: 1.8rem;
    letter-spacing: 0.2rem;
    text-decoration: none;
    outline: none;
    height: 30px;
    width: auto;
    border: none;
    border-radius: 0.4rem;
    margin-left: 260px;
    color: white;
    text-transform: lowercase;
    background-color: #b18999;
    transform: translate(0, -25%);
  }

  /*Main section*/

  .main,
  .main__screen {
    position: relative;
    width: 1366px;
    margin: 0 auto;
    overflow: hidden;
  }

  .upper__slider-arrows {
    position: absolute;
    display: flex;
    align-items: flex-end;
    justify-content: space-between;
    width: 1336px;
    margin-left: 15px;
    margin-top: 330px;
  }

  .slider-arrows {
    position: relative;
    z-index: 10;
  }

  .main-pic {
    position: relative;
    height: 660px;
    width: 902px;
  }

  .main__circle {
    position: absolute;
    width: 1000px;
    height: 1000px;
    border-radius: 500px;
    background-color: #b18999;
    transform: translate(0, -100%);
    margin-top: 150px;
    margin-left: 763px;
    max-width: 100%;
    z-index: 5;
  }

  /*Upper slider section*/

  .main-pic-input {
    display: none;
  }

  .slider {
    height: inherit;
    overflow: hidden;
    position: relative;
    width: inherit;
    box-shadow: 0 0 20px rgba(0, 0, 0, .5);
  }

  .slides {
    height: inherit;
    opacity: 0;
    position: absolute;
    width: inherit;
    z-index: 0;
    transform: scale(1.5);
    transition: transform ease-in-out .5s, opacity ease-in-out .5s;
  }

  .slide1 {
    background-image: url("https://raw.githubusercontent.com/obvu/frontend-testcase/master/files/Слайдер/Гостиная1.png");
  }

  .slide2 {
    background-image: url("https://raw.githubusercontent.com/obvu/frontend-testcase/master/files/Слайдер/гостинная лофт.jpg");
  }

  #slide1:checked~.slider>.slide1,
  #slide2:checked~.slider>.slide2 {
    opacity: 1;
    z-index: 1;
    transform: scale(1);
  }

  /* Upper slider section end*/

  /* Main section*/

  .main__nav__circles {
    position: absolute;
    margin-left: 480px;
    margin-top: 236px;
  }

  .main__nav__circle,
  .project__nav__circle {
    position: relative;
    display: inline-block;
    width: 12px;
    height: 12px;
    text-align: center;
    border-radius: 50%;
    margin-right: 5px;
    border: 1px solid white;
  }

  .project__nav__circle-selected,
  .main__nav__circle:focus,
  .main__nav__circle:hover,
  .main__nav__circle:active,
  .project__nav__circle:focus,
  .project__nav__circle:hover,
  .project__nav__circle:active {
    background-color: white;
  }

  .offer {
    position: relative;
    top: 400px;
    margin-left: 97px;
    font-size: 4rem;
    line-height: 5.4rem;
    color: #f2f2f2;
    display: flex;
    flex-wrap: wrap;
    width: 280px;
  }

  .datails {
    font-size: 1.8rem;
    line-height: 2.5rem;
  }

  .intro {
    position: relative;
    width: 1258px;
    margin: 0 auto;
    margin-top: 54px;
  }

  .intro__title {
    display: inline-block;
    position: relative;
    font-size: 4.4rem;
    line-height: 5.8rem;
    color: #1b1c1c;
  }

  .intro__title:nth-child(2) {
    margin-left: 15px;
    font-weight: bold;
  }

  .intro__subtitle {
    width: 1253px;
    font-size: 1.8rem;
    line-height: 2.5rem;
    margin-bottom: 22px;
  }

  .benefits__cards {
    position: relative;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-column-gap: 45px;
    margin-bottom: 89px;
    font-size: 1.8rem;
    line-height: 2.5rem;
    color: #000000;
  }

  .benefits__card-pic {
    margin-bottom: 20px;
  }

  .benefits__card_icon {
    display: block;
  }

  /* Project section */

  .project__pic {
    display: inline-block;
  }

  .project__slider-arrows {
    position: absolute;
    display: flex;
    align-items: flex-end;
    justify-content: space-between;
    width: 818px;
    margin-left: 15px;
    margin-top: 369px;
  }

  .project__circles {
    position: absolute;
    margin-left: 40px;
    margin-top: 46px;
  }

  .project__circle {
    position: relative;
    display: inline-block;
    background-color: rgba(42, 38, 38, 0.90);
    width: 115px;
    height: 115px;
    margin-right: 30px;
    border-radius: 50%;
    text-align: center;
  }

  .project__circle-selected,
  .project__circle:focus,
  .project__circle:hover,
  .project__circle:active {
    background-color: #b18999;
    cursor: pointer;
  }

  .project__circle-pic {
    padding-top: 38px;
  }

  .project__nav__circles {
    position: absolute;
    margin-left: 50px;
    margin-top: 596px;
  }

  .project__wrapper {
    position: absolute;
    margin-left: 50px;
    margin-top: 626px;
  }

  .project-pic {
    object-fit: cover;
    width: 848px;
    height: 757px;
  }

  .project__love {
    font-size: 1.8rem;
    line-height: 2.5rem;
  }

  .project__menu {
    position: absolute;
    display: inline-block;
    background-color: #404040;
    width: 521px;
    height: 757px;
  }

  .project__menu__nav {
    position: absolute;
    margin-left: 68px;
    top: 203px;
  }

  .project__menu__link {
    font-size: 3rem;
    line-height: 4rem;
    color: white;
    text-decoration: none;
  }

  .project__submenu__link {
    font-size: 2rem;
    line-height: 3rem;
    color: white;
    text-decoration: none;
    padding-left: 10px;
  }

  .project__menu__link:focus,
  .project__menu__link:hover,
  .project__menu__link:active,
  .project__submenu__link:focus,
  .project__submenu__link:hover,
  .project__submenu__link:active {
    color: #65c8ce;
    outline: none;
    cursor: pointer;

  }

  /*Footer section*/

  .footer {
    position: relative;
  }

  .footer__wrapper {
    padding-top: 46px;
    position: relative;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    background-color: #151414;
    height: 217px;
  }

  .footer__menu__nav:first-child {
    padding-left: 120px;
  }

  .footer__menu__link {
    font-size: 0.9rem;
    line-height: 1.3rem;
    letter-spacing: 0.1rem;
    text-transform: uppercase;
    color: white;
    text-decoration: none;
  }

  .social {
    margin-bottom: 6px;
  }

  .social__media {
    display: grid;
    grid-template-columns: auto auto auto;
    justify-content: start;
    grid-column-gap: 12px;
  }

  .social-icon {
    display: inline-block;
    width: 30px;
    height: 30px;
    border-radius: 50%;
  }

  .footer__link {
    font-size: 1rem;
    line-height: 1.2rem;
    color: #999999;
    text-decoration: none;
  }

  .bottom {
    position: absolute;
    bottom: 14px;
  }

  .footer__subscribe {
    display: inline-block;
    position: absolute;
    margin-top: 16px;
  }

  .footer__email {
    display: inline-block;
    color: white;
  }

  .footer__sign {
    font-size: 1rem;
    line-height: 1.2rem;
    color: #999999;
    text-decoration: none;
  }

  input {
    border: 0;
    border-bottom: 2px solid #999999;
    background-color: #151414;
    outline: none;
    color: #999999;
  }

  .circle {
    width: 36px;
    height: 36px;
    border-radius: 50%;
    background-color: #b18999;
    transform: translate(0, -50%);
    margin-left: 16px;
    text-align: center;
  }

  .footer__subscribe-pic {
    padding-top: 11px;
  }

  .header__link:focus,
  .header__link:hover,
  .header__link:active,
  .header__button:hover,
  .header__button:focus,
  .header__button:active,
  .footer__menu__link:focus,
  .footer__menu__link:hover,
  .footer__menu__link:active,
  .social-icon:focus,
  .social-icon:hover,
  .social-icon:active,
  .footer__link:focus,
  .footer__link:hover,
  .footer__link:active,
  .slider-arrows:focus,
  .slider-arrows:hover,
  .slider-arrows:active {
    opacity: 0.7;
    outline: none;
    cursor: pointer;
  }
</style>