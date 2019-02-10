<template>
  <v-app light>
    <v-navigation-drawer
      v-model="drawer"
      disable-resize-watcher      
      fixed
      app
    >
      <v-list>
        <v-list-tile
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          active-class="red--text"
          router
          exact
          @click="drawer = !drawer"
        >
          <v-list-tile-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title" />
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar
      :clipped-left="clipped"
      fixed
      app
    >
      <v-toolbar-side-icon class="hidden-md-and-up" @click="drawer = !drawer" /> 
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-toolbar-items class="hidden-sm-and-down">
        <v-toolbar-items>
          <v-btn flat>
            <nuxt-link to="/">
              Главная
            </nuxt-link>
          </v-btn>
          <v-btn flat>
            <nuxt-link to="/About">
              Поделки
            </nuxt-link>
          </v-btn>
        </v-toolbar-items>
      </v-toolbar-items>
      </v-btn>
    </v-toolbar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
   
    <v-footer
      :fixed="fixed"
      app
    >
      <span class="footerHeading">
        Made in Russia
      </span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'apps',
          title: 'Главная',
          to: '/'
        },
        {
          icon: 'bubble_chart',
          title: 'Поделки',
          to: '/About'
        }
      ],
      right: true,
      title: 'Tikken'
    }
  },
  head: {
    script: [
      {
        src: '#'
      }
    ]
  }
}
</script>

<style>
body {
  box-sizing: border-box;
}
.footerHeading {
  margin: 0 25px 0 25px;
}
a {
  text-decoration: none;
}
</style>
