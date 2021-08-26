<template>
  <v-app
    class="theme-dark"
    :class="responsivity"
  >
    <main-bar @open_menu="menu"></main-bar>

    <v-navigation-drawer
      class="main-rounded-xl-r glass-r"
      :width="328"
      v-model="is_menu"
      absolute
      temporary
      overlay-color="black"
      overlay-opacity="0.5"
    >
      <main-menu ref="mainMenu" @menu_close="is_menu = false"></main-menu>
    </v-navigation-drawer>

    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>
import '@/styles/main.scss'

import mainMenu from '@/components/app/menu.vue'
import mainBar  from '@/components/app/bar.vue'

export default {
  name: 'App',

  data: () => ({
    is_menu: false,
  }),

  components: {
    mainMenu,
    mainBar,
  },
  
  methods: {
    menu( ) {
      this.is_menu = true;
    }
  },

  computed: {
    // eslint-disable-next-line vue/return-in-computed-property
    responsivity ( ) {
      switch ( this.$vuetify.breakpoint.name ) {
        case 'xs': return 'bp_xs'
        case 'sm': return 'bp_sm'
        case 'md': return 'bp_md'
        case 'lg': return 'bp_lg'
        case 'xl': return 'bp_xl'
      }
    },
  }
};
</script>
