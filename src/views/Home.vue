<template>
  <v-content class="width: 50px!important;">
    <v-card
      class="flex d-lg-flex flex-row transparent justify-space-around"
      style="max-width: 1359px; margin: 0 auto;"
      outlined tile
    >
      <v-navigation-drawer
        class="main-menu"
        style="
          position: absolute;
          left: 0;
        "
        :width="328"
        v-show="$vuetify.breakpoint.lg ||
                $vuetify.breakpoint.xl ? true : false"
        permanent
        overlay-color="black"
        overlay-opacity="0.5"
      >
        <main-menu ref="mainMenu"></main-menu>
      </v-navigation-drawer>

      <div>
        <post
          v-for='(target, index) in posts.slice(0, post_count)'
          :key='index'

          :user_id  =target.user_id
          :user_name=target.user_name

          :post_id  =target.post_id
          :post_name=target.post_name
        ></post>

        <div class="text-center mt-4 mb-4 opacity" v-if="is_loading">
          <v-progress-circular
            indeterminate
            style="opacity: .5;"
          ></v-progress-circular>
        </div>
      </div>

      <div
        id="app-ad-panel"

        v-show="$vuetify.breakpoint.lg ||
                $vuetify.breakpoint.xl ? true : false"
      >
        <v-card
          class="
            width-100

            blue
            rounded-lg

            pl-4

            d-flex
            align-center
          "
          style="height: 64px;"
        >
          <v-img
            :lazy-src="require( '@/assets/icon/logo 50 trans.png' )"
            :src="require( '@/assets/icon/logo 500 trans.png' )"

            :max-width="54"
          ></v-img>
          <span
            class="
              d-flex
              flex-column
              justify-space-between

              ml-2
            "
          >
            <h1
              class="
                mb-1
                body-2

                white--text
              "
            >Totsu App</h1>

            <h3
              class="
                caption

                white--text
              "
            >Everything in your hands</h3>
            
            <div id="panel-stars">
              <v-icon class="material-icons">star</v-icon>
              <v-icon class="material-icons">star</v-icon>
              <v-icon class="material-icons">star</v-icon>
              <v-icon class="material-icons">star</v-icon>
              <v-icon class="material-icons">star</v-icon>
            </div>
          </span>

          <v-card
            class="
              light-green

              white--text
            "
            id="panel-free"
          >
            FREE
          </v-card>
        </v-card>

        <h1 class="mt-5 text-lg-h6 font-weight-light">
          Three for you:
        </h1>

        <recommended
          v-for="rec in recommendations"
          :key="rec"

          :icon=rec.icon
          :bg_icon=rec.icon_bg
          :bg_color=rec.color
        ></recommended>
      </div>
    </v-card>
  </v-content>
</template>

<script>
  import Post        from '@/components/post.vue'
  import mainMenu    from '@/components/app/menu.vue'
  import recommended from '@/components/home/recommended.vue'
  
  export default {
    name: 'Home',

    data: ( ) => {
      return {
        post_count: 2,
        is_loading: false,
        posts: [
          {
            user_id  : 0,
            user_name: 'Bobby Grand',

            post_id  : 0,
            post_name: 'Est lectus',
          },
          {
            user_id  : 1,
            user_name: 'Bobby Grand',

            post_id  : 1,
            post_name: 'Est lectus',
          },
          {
            user_id  : 0,
            user_name: 'Bobby Grand',

            post_id  : 0,
            post_name: 'Est lectus',
          },
          {
            user_id  : 1,
            user_name: 'Bobby Grand',

            post_id  : 1,
            post_name: 'Est lectus',
          },
          {
            user_id  : 0,
            user_name: 'Bobby Grand',

            post_id  : 0,
            post_name: 'Est lectus',
          },
          {
            user_id  : 1,
            user_name: 'Bobby Grand',

            post_id  : 1,
            post_name: 'Est lectus',
          },
          {
            user_id  : 0,
            user_name: 'Bobby Grand',

            post_id  : 0,
            post_name: 'Est lectus',
          },
          {
            user_id  : 1,
            user_name: 'Bobby Grand',

            post_id  : 1,
            post_name: 'Est lectus',
          }
        ],
        recommendations: [
          {
            icon   : 'movie',
            icon_bg: 'theaters',
            color  : 'background-image: linear-gradient(45deg, #58D952, #52D99A)'
          },
          {
            icon   : 'spa',
            icon_bg: 'live_tv',
            color  : 'background-image: linear-gradient(45deg, #FEC194, #FF0061)'
          },
          {
            icon   : 'sports_esports',
            icon_bg: 'gamepad',
            color  : 'background-image: linear-gradient(45deg, #58D952, #52D99A)'
          },
        ]
      }
    },

    components: {
      mainMenu,
      Post,
      recommended,
    },

    methods: {
      scroll ( ) {
        let is_post_end = parseInt( this.post_count ) >= parseInt( this.posts.length );

        window.onscroll = ( ) => {
          let bottomOfWindow = Math.max( window.pageYOffset,
                                  document.documentElement.scrollTop,
                                  document.body.scrollTop) +
                                  
                                  window.innerHeight ===
                                  document.documentElement.offsetHeight

          if ( bottomOfWindow & !this.is_loading & !is_post_end ) {
              this.is_loading = true;

              setTimeout ( ( ) => {
                this.post_count++;
                
                this.is_loading = false;
              }, 1000, !is_post_end )
          }

          if ( is_post_end )
            this.is_loading = true
        }
      }
    },

    mounted ( ) {
      this.scroll( );
      this.$refs.mainMenu.open_menu();
    },
  }
</script>

<style lang="scss">
  #app-ad-panel {
    position: absolute;

    width: 260px;
    right: 0;


    .v-card { border-radius: 1rem !important; }


    span h3 {
      line-height: .4rem;

      opacity: .9;
    }
  

    #panel-free {
      position: absolute;

      right: 7%;
      top  : -25%;

      padding: .42rem .8rem;

      border-radius: 6px !important;
      

      font-size  : .7rem;
      font-weight: bold;

      letter-spacing: 2px;
    }


    #panel-stars {
      line-height: 1.3rem;

      * {
        font-size: 14px;

        color: var( --theme-background ) !important;

        opacity: .75;
      }
    }
  }
</style>