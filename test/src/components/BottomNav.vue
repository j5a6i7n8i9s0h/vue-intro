<template>
    <div>
        <div >
            <v-btn
            fab
            fixed
            bottom
            right
            style="margin-bottom:30px;margin-right:25px"
            @click="$emit('triggerModal')"
            >
                <v-icon>create</v-icon>
            </v-btn>
        </div>
        <!-- </div>
        <v-bottom-nav
            :value="true"
            fixed=""
            color="white"
        >
              <v-btn
        color="red"
        flat
        value="recent"
      >
        <span>Recent</span>
        <v-icon>history</v-icon>
      </v-btn>

      <v-btn
        color="red"
        flat
        value="favorites"
      >
        <span>Favorites</span>
        <v-icon>favorite</v-icon>
      </v-btn>

      <v-btn
        color="red"
        flat
        value="nearby"
      >
        <span>Nearby</span>
        <v-icon>place</v-icon>
      </v-btn>
        </v-bottom-nav> -->
    </div>
</template>

<script>
export default {
  name: "BottomNav"
};
</script>

<style lang="">
</style>