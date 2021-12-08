<template>
  <div class="content">
    <div class="m">
      <div v-for="(pokemon, index) in pokemons" :key="index" class="mr">
        <v-card
          class="mx-auto m-2"
          max-width="344"
          width="200px"
        >
          <v-img
            :src="pokemon.url"
            height="200px"
          />

          <v-card-title>
            {{ pokemon.name }}
          </v-card-title>
          <v-card-actions>
            <v-btn
              color="primary"
              dark
              @click="infoPokemon(pokemon)"
            >
              Explore
            </v-btn>
            <v-spacer />
          </v-card-actions>
        </v-card>
      </div>
    </div>
    <div class="fix">
      <Pokemon :pokemon="pokeData" :modal-info="modalInfo" @close-modal="closeModal" />
    </div>
  </div>
</template>
<script>
import axios from 'axios'
import Pokemon from '../components/Pokemon'
export default {
  components: {
    Pokemon
  },
  data () {
    return {
      show: false,
      isActive: true,
      pokemons: [],
      modalInfo: false,
      pokeData: []
    }
  },
  async fetch () {
    const instance = this
    for (let i = 0; i <= 150; i++) {
      const reponse = await axios.get(`https://pokeapi.co/api/v2/pokemon/${i + 1}`)
      const pokemon = {
        name: reponse.data.name,
        abilities: reponse.data.abilities,
        url: reponse.data.sprites.front_default
      }
      instance.pokemons.push(pokemon)
    }
  },
  methods: {
    infoPokemon (pokeInfo) {
      this.pokeData = pokeInfo
      this.modalInfo = true
    },
    closeModal () {
      if (this.modalInfo) {
        this.modalInfo = false
      } else {
        this.modalInfo = true
      }
    }
  }
}
</script>
<style scoped>
.m{
  display: flex;
  flex-wrap: wrap;
  width: 50%;
  margin-right: 30%;
}
.content{
  display: flex;
  justify-content: space-around;
}
.mr{
  margin-right: 60px;
  margin-bottom: 10px;
}
.fix{
  position: fixed;
  margin-left: 55%;
  width: 350px;
}
</style>
