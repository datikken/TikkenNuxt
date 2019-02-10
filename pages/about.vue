<template>
  <v-container fluid grid-list-md>
    <v-layout row wrap d-flex justify-space-around>
      <v-btn
        class="floatingButton"
        color="red"
        absolute
        dark
        fab
        bottom
        right
        @click="ok = !ok"
      >
        <img src="/calculator.png">
      </v-btn>
      <Api />
      <Calculator v-if="ok" />
    </v-layout>
  </v-container>
</template>

<script>
import { TimelineMax } from 'gsap'
import Splitter from 'split-html-to-chars'
import Calculator from '~/components/calculator.vue'
import Api from '~/components/api.vue'
// import Todolist from '~/components/todolist.vue'
export default {
  components: {
    Calculator,
    Api
    // Todolist
  },
  data: () => {
    return {
      ok: false,
      lorem: `Тут я публикую разные поделки.`
    }
  },
  mounted() {
    const els = this.$el.querySelectorAll('.js-split')
    ;[].forEach.call(els, function(el) {
      el.outerHTML = Splitter(el.outerHTML, '<span class="letter">$</span>')
    })
  },
  transition: {
    name: 'slide',
    mode: 'out-in',
    css: false,
    enter: function(el, done) {
      const tl = new TimelineMax({ onComplete: done })
      const els = el.querySelectorAll('.letter')
      tl.set(els, { y: -20, opacity: 0 })
      tl.staggerTo(els, 0.5, { y: 0, opacity: 1 }, 0.05)
    },
    leave: function(el, done) {
      const tl = new TimelineMax({ onComplete: done })
      tl.fromTo(el, 0.3, { y: 0, opacity: 1 }, { y: 100, opacity: 0 })
      done()
    }
  }
}
</script>

          <style>
.letter {
  display: inline-block;
}

.aboutWrap {
  display: flex;
}
</style>
