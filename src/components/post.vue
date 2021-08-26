<template>
  <v-sheet
    class="mx-auto transparent post"
  >
    <a href="#">
      <v-img
        class="rounded-t-circle rounded-br-circle main-rounded-bl"
        max-width="24"
        max-height="24"
        :src="require( '@/assets/profile/' + user_id +'/picture.jpg' )"
      ></v-img>

      <h2>{{ user_name }}</h2>

      <v-icon class="material-icons">
        local_fire_department
      </v-icon>
    </a>

    <a href="#">{{ post_name }}</a>
    
    <a href="#">
      <v-img
        class="rounded-xl"
        height="100vw"
        :src="require( '@/assets/profile/' + post_id + '/works/0.jpg' )"
        :lazy-src="require( '@/assets/profile/' + post_id + '/works/0-lazy.jpg' )"
      >
        <template v-slot:placeholder>
          <v-row
            class="fill-height ma-0"
            align="center"
            justify="center"
          >
            <v-progress-circular
              indeterminate
              color="grey lighten-5"
            ></v-progress-circular>
          </v-row>
        </template>
      </v-img>
    </a>
  </v-sheet>
</template>

<script>
  import '@/styles/components/post.scss'

  export default {
    props: {
      user_id: {
        type   : Number,
        default: 99
      },

      user_name: {
        type   : String,
        default: 'Totsu Test'
      },

      post_id: {
        type   : Number,
        default: 99
      },

      post_name: {
        type   : String,
        default: 'Hello UwU'
      },
    },

    methods: {
      src: ( ) => {
        return 
      }
    },
  }
</script>
