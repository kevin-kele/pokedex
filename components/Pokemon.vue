<template>
  <v-card
    v-show="modalInfo"
    class="mx-auto"
    dark
    max-width="600"
    elevation="4"
    card-border-radius="10px"
  >
    <v-card-title>
      <v-icon
        large
        left
      />
      <span class="text-h3 text font-weight-bold">{{ pokemon.name }}</span>
    </v-card-title>
    <div class="border">
      <v-img
        :src="pokemon.url"
        height="200px"
      />
    </div>

    <v-card-text v-for="(power, index) in pokemon.abilities" :key="index" class="text-h6 font-weight-bold">
      attack : {{ power.ability.name }}
    </v-card-text>

    <v-card-actions>
      <v-list-item class="grow">
        <v-list-item-avatar color="grey darken-3">
          <v-img
            class="elevation-2"
            src="http://pngimg.com/uploads/pokeball/pokeball_PNG34.png"
          />
        </v-list-item-avatar>
        <v-row
          align="center"
          justify="end"
        >
          <v-icon class="mr-1">
            mdi-heart
          </v-icon>
          <span class="subheading mr-2">256</span>
          <span class="mr-1">·</span>
          <v-icon class="mr-1">
            mdi-share-variant
          </v-icon>
          <v-btn @click="close()">
            close
          </v-btn>
        </v-row>
      </v-list-item>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  props: ['modal-info', 'pokemon', 'pokeInfo'],
  data: () => ({
  }),
  methods: {
    close () {
      this.$emit('close-modal')
    }
  }
}
</script>

<style lang="scss" scoped>
.border{
  border: 1px solid white;
  background-color: rgb(214, 204, 204);
}
.text{
  margin: auto;
}
</style>>
