<template>
  <div>
    <v-row
      class="px-7 mt-8"
      v-show="$vuetify.breakpoint.lg ||
              $vuetify.breakpoint.xl ? false : true"
      no-gutters
    >
      <v-col
        class="d-flex"
        cols="12"
        sm="12"
        ful
      >
        <v-btn
          @click="menu_close"
          icon
        >
          <v-icon class="material-icons theme-error theme-body-2">
            close
          </v-icon>
        </v-btn>

        <v-spacer></v-spacer>
        
        <v-btn
          plain
        >
          ホドキ
        </v-btn>
        
        <v-spacer></v-spacer>
        
        <v-btn
          plain
          icon
        >
          <v-icon class="material-icons theme-body-1">
            settings
          </v-icon>
        </v-btn>
      </v-col>
    </v-row>

    <v-row no-gutters>
      <v-list
        v-for="section in sections"
        :key="section.title"
        class="mx-7"
        width="100%"
        dense
      >
        <v-list-item-title class="main-menu-title" >
          {{ section.title }}
        </v-list-item-title>

        <v-list-item-content
          class="pa-0"
          :class="{ 'mt-9': section.title }"
        >
          <v-list-item-content class="">
            <v-col
              v-for="item in section.items"
              :key="item.title"
              class="pa-0 mb-5"
              cols="4"
              sm="4"
            >
              <v-btn
                class="pa-0"
                height="auto"
                block
                text
              >
                <div class="d-flex flex-column body-2">
                  <v-icon class="material-icons mb-5 main-menu-icon" :style="item.icon.color">
                    {{ item.icon.name }}
                  </v-icon>

                  {{ item.title }}
                </div>
              </v-btn>
            </v-col>
          </v-list-item-content>
        </v-list-item-content>
      </v-list>
    </v-row>
  </div>
</template>

<script>
import '@/styles/components/app/menu.scss'

export default {
  data: () => ({
    is_menu: true,
    sections: [
      {
        title: '',
        items: [
          { title: 'Home'   , icon: { name: "home",                  color: "background-image: linear-gradient( to top right, #FFAFBD, #FFC3A0 ) !important;" } },
          { title: 'App'    , icon: { name: "devices",               color: "background-image: linear-gradient( to top right, #58D952, #52D99A ) !important;" } },
          { title: 'Premium', icon: { name: "local_fire_department", color: "background-image: linear-gradient( to top right, #F8D90F, #D3DD18 ) !important;" } },
        ]
      },
      {
        title: 'Popular',
        items: [
          { title: 'Anime' , icon: { name: "spa",            color: "background-image: linear-gradient( to top right, #FFAFBD, #FFC3A0 ) !important;" } },
          { title: 'Meme'  , icon: { name: "emoji_emotions", color: "background-image: linear-gradient( to top right, #58D952, #52D99A ) !important;" } },
          { title: 'Design', icon: { name: "margin",         color: "background-image: linear-gradient( to top right, #049DBF, #023E73 ) !important;" } },
          { title: 'Japan' , icon: { name: "landscape",      color: "background-image: linear-gradient( to top right, #FFAFBD, #FFC3A0 ) !important;" } },
          { title: 'Game'  , icon: { name: "gamepad",        color: "background-image: linear-gradient( to top right, #58D952, #52D99A ) !important;" } },
        ],
      },
      {
        title: 'Ather',
        items: [
          { title: 'Animal', icon: { name: "pets",              color: "background-image: linear-gradient( to top right, #FFAFBD, #FFC3A0 ) !important;" } },
          { title: 'Movie' , icon: { name: "theater_comedy",    color: "background-image: linear-gradient( to top right, #58D952, #52D99A ) !important;" } },
          { title: 'Sport' , icon: { name: "sports_volleyball", color: "background-image: linear-gradient( to top right, #F8D90F, #D3DD18 ) !important;" } },
        ],
      },
    ]
  }),

  methods: {
    menu_close ( ) {
      this.$emit('menu_close', false)
    }
  }
}
</script>
