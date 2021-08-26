<template>
  <v-app-bar
    app
    flat
    absolute
  >
    <v-app-bar-nav-icon @click="open_menu">
      <icon-base
        width="30"
        icon-name="menu"
        icon-color="var( --theme-text-2 )"
      >
        <icon-menu/>
      </icon-base>
    </v-app-bar-nav-icon>

    <v-spacer></v-spacer>
    
    <v-autocomplete
      v-model="search_value"
      :items="search_items"
      class="theme-search d-flex align-center mx-4"
      dense
      flat
      clearable
      hide-details
      hide-selected
      item-text="name"
      item-value="symbol"
      label="Search..."
      solo-inverted
    >
      
    </v-autocomplete>

    <v-spacer></v-spacer>
    
    <v-btn
      icon
    >
      <v-img
        class="rounded-t-circle rounded-br-circle main-rounded-bl"
        max-width="32"
        max-height="32"
        src="@/assets/profile/0/picture.jpg"
      ></v-img>
    </v-btn>
  </v-app-bar>
</template>

<script>
  import '@/styles/components/app/bar.scss'

  import IconBase from '@/components/IconBase.vue'
  import IconMenu from '@/assets/icons/IconMenu.vue'

  export default {
    data: ( ) => ({
      search_items: [ 'Home', 'App', 'Crown', 'Anime', 'Meme',
                      'Design', 'Japan', 'Game', 'Animal', 'Movie',
                      'Sport'],
      search_value: null,
    }),

    components: {
      IconBase,
      IconMenu,
    },

    methods: {
      open_menu( ) {
        this.$emit( 'open_menu' )
      },
    },
  }
</script>
