<template>
  <v-card :style="bg_color"
    class="
      mt-3
      
      d-flex
      justify-center

      overflow-hidden

      recommended
    "
  >
    <v-card-title>
      <v-icon class="material-icons"
        style="
          font-size: 74px;

          opacity: .68;
        "
      >
        {{ icon }}
      </v-icon>
    </v-card-title>

    <div
      class="
        flex
        d-fex
        justify-space-between

        panel_bg
      "
    >
      <v-icon class="material-icons">
        {{ bg_icon }}
      </v-icon>
      <v-icon class="material-icons">
        {{ bg_icon }}
      </v-icon>
    </div>
  </v-card>
</template>

<script>
export default {
  props: {
    icon: {
      typeof: String
    },
    bg_color: {
      typeof: String
    },
    bg_icon: {
      typeof: String
    },
  }
}
</script>

<style lang="scss">
  .recommended {
    height: 117px !important;

    border-radius: 1rem !important;

    * { color: var( --theme-background ) !important; }
  }

  .panel_bg {
    $icon-size: 16vh;
    
    position: absolute;

    width : 100%;
    height: 100%;

    opacity: .1;

    display: flex;

    .v-icon {
      font-size: $icon-size;

      &:first-child { right: calc( #{ $icon-size } /1.8 ); }
      &:last-child  { left : calc( #{ $icon-size } /18 ); }
    }
  }
</style>