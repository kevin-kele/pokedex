<template>
  <v-card
    v-show="modalInfo"
    id="padCarte"
    class="mx-auto"
    dark
    elevation="4"
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
        height="300px"
      />
    </div>
    <v-card-text v-for="(power, index) in pokemon.powers" :key="index" class="text-h6 pad">
      <span v-if="power.stat.name === 'attack' || power.stat.name === 'defense' || power.stat.name === 'special-attack' "> {{ power.stat.name }} - {{ power.base_stat }}</span>
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
.pad{
  padding:0;
  margin-top: 10px;
}
#padCarte{
  border-radius: 10px;
  padding: 5%;
  border:10px solid yellow;
}
.border div {
position: relative;
}
.border div::before {
position: absolute;
top: 0;
left: -75%;
z-index: 2;
display: block;
content: '';
width: 50%;
height: 100%;
background: -webkit-linear-gradient(left, rgba(255,255,255,0) 0%, rgba(255,255,255,.3) 100%);
background: linear-gradient(to right, rgba(255,255,255,0) 0%, rgba(255,255,255,.3) 100%);
-webkit-transform: skewX(-25deg);
transform: skewX(-25deg);
}
.border div:hover::before {
-webkit-animation: shine .75s;
animation: shine .75s;
}
@-webkit-keyframes shine {
100% {
left: 125%;
}
}
@keyframes shine {
100% {
left: 125%;
}
}
</style>>
