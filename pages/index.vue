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
              <div class="wrapItem1">
                <picture>
                  <source media="(min-width: 650px)" srcset="/avatar250px.png">
                  <source media="(min-width: 465px)" srcset="/avatar125.png">
                  <img src="avatar125.png" alt="Tikken" style="width:auto;">
                </picture>
              </div>
              <div class="wrapItem2">
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
                  <li>
                    <a href="https://vk.com/datikken" target="blank">
                      <img src="/vk.svg" alt="Vk" class="socialIcon">
                    </a>
                    <a href="https://www.facebook.com/" target="blank">
                      <img src="/facebook.svg" class="socialIcon" alt="Facebook">
                    </a>
                    <a href="https://www.instagram.com/tikkentikken/" target="blank">
                      <svg class="socialIcon" x="0px" y="0px" viewBox="0 0 202.5 202.5" style="enable-background:new 0 0 202.5 202.5;">
                        <circle id="littleCircle" class="st0" cx="101" cy="101.5" r="18.9" />
                        <circle id="lens" class="st0" cx="125.5" cy="78.6" r="2.9" />
                        <path
                          id="camera"
                          class="st0"
                          d="M79,60.5h44c10.5,0,19,8.5,19,19v44c0,10.5-8.5,19-19,19H79c-10.5,0-19-8.5-19-19v-44
                C60,69,68.5,60.5,79,60.5z" 
                        />
                        <circle id="bigCircle" class="st0" cx="101.2" cy="101.2" r="98.2" />
                      </svg>
                    </a>
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

.cardWrap {
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  justify-content: center;
  padding-bottom: 25px;
  flex-wrap: wrap;
}

.socialIcon {
  width: 50px;
  filter: grayscale(100%);
}

.socialIcon:hover {
  width: 50px;
  filter: grayscale(0%);
}

.st0 {
  fill: none;
  stroke: #ef4649;
  stroke-width: 7;
  stroke-linecap: round;
  stroke-miterlimit: 10;
}

#bigCircle {
  stroke-dasharray: 700;
  animation: bigCircle 4s linear infinite;
}

#littleCircle {
  stroke-dasharray: 150;
  animation: littleCircle 4s linear infinite;
}

#camera {
  stroke-dasharray: 300;
  animation: camera 4s linear infinite;
}

#lens {
  fill: #ef4649;
  animation: lens 4s linear infinite;
}

@keyframes bigCircle {
  0% {
    stroke-dashoffset: 700;
  }
  25% {
    stroke-dashoffset: 0;
  }
}
@keyframes camera {
  0%,
  25% {
    stroke-dashoffset: 300;
  }
  50% {
    stroke-dashoffset: 0;
  }
}
@keyframes littleCircle {
  0%,
  50% {
    stroke-dashoffset: 150;
  }
  75% {
    stroke-dashoffset: 0;
  }
}

@keyframes lens {
  0%,
  75% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>
