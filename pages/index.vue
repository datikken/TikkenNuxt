<template>
  <v-container
    class="cardsContainer"
    fluid
    grid-list-lg
    fill-height
  >
    <v-fade-transition mode="out-in">
      <v-layout v-if="show" key="0" wrap>
        <v-flex>
          <v-card>
            <v-card-title class="title">
              Frontend developer
            </v-card-title>   
            <div class="cardWrap">
              <div class="wrapItem2">
                <picture>
                  <source media="(min-width: 650px)" srcset="/avatar250px.png">
                  <source media="(min-width: 465px)" srcset="/avatar125.png">
                  <img src="avatar125.png" alt="Tikken" style="width:auto;">
                </picture>
              </div>
              <div class="wrapItem1">
                <ul>
                  <li>
                    <p>Шадыбеков Никита</p>
                  </li>
                  <li>
                    <p>23.03.1992</p>
                  </li>
                  <li>
                    <p>г. Санкт-Петербург</p>
                  </li>
                </ul>
              </div>
            </div>
          </v-card>
        </v-flex>

        <v-flex>
          <v-card>
            <v-card-title class="title">
              Навыки
            </v-card-title>
            <ul>
              <li>
                HTML / CSS 3
              </li>
              <li>
                Pug / Mustache
              </li>
              <li>
                SASS (SCSS) / Less / Stylus 
              </li>
              <li>
                <p>React (16.8) / Redux / Next</p>
              </li>
              <li>
                <p>Vue (3) / Vuex / Nuxt</p>
              </li>
              <li>
                <p>GSAP / Pixi JS / Three JS</p>
              </li>
            </ul>
          </v-card>
        </v-flex>
      </v-layout>

      <v-layout v-else key="1" justify-center />
    </v-fade-transition>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    show: true
  })
}
</script>

<style>
ul {
  list-style-type: none;
  line-height: 7px;
  padding-bottom: 20px;
  margin-right: 10px;
}
li {
  margin: 20px 0 20px 0;
}
.cardsContainer {
  padding-top: 5px;
}
@media screen and (max-width: 321) {
  ul {
    font-size: 20px;
  }
}

.cardWrap {
  display: flex;
  justify-content: center;
  padding-bottom: 25px;
  flex-wrap: wrap;
}
</style>
