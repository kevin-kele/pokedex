<template>
  <div>
    <div class="top">
      <v-img
        class="center"
        width="50px"
        src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/International_Pok%C3%A9mon_logo.svg/2560px-International_Pok%C3%A9mon_logo.svg.png"
      />
      <div>
        <equipe-poke @on-end="onEnd" :pokemons="pokeEquipeDonnee" @remove-poke="deletePoke" />
      </div>
    </div>

    <v-text-field
      v-model="filters"
      outlined
      label="Pokédex National"
    />
    <div class="content">
      <div class="m">
        <div v-for="(pokemon, index) in filtersPoke" :key="index" class="mr">
          <v-card
            class="mx-auto m-2"
            width="300px"
          >
            <v-img
              :src="pokemon.url"
              height="350px"
              contain
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
              <v-btn
                color="red"
                dark
                @click="addEquipe(pokemon)"
              >
                Add equipe
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
  </div>
</template>
<script>
import axios from 'axios'
import Pokemon from '../components/Pokemon'
import EquipePoke from '~/components/EquipePoke.vue'
export default {
  components: {
    Pokemon,
    EquipePoke
  },
  data () {
    return {
      show: false,
      isActive: true,
      pokemons: [],
      modalInfo: false,
      pokeData: [],
      filters: '',
      pokeEquipe: [],
      pokeEquipeDonnee: []
    }
  },
  async fetch () {
    const instance = this
    for (let i = 0; i <= 200; i++) {
      const reponse = await axios.get(`https://pokeapi.co/api/v2/pokemon/${i + 1}`)
      const pokemon = {
        name: reponse.data.name,
        order: reponse.data.order,
        abilities: reponse.data.abilities,
        powers: reponse.data.stats,
        type: reponse.data.types,
        url: reponse.data.sprites.other.dream_world.front_default
      }
      instance.pokemons.push(pokemon)
    }
  },
  computed: {
    filtersPoke () {
      return this.pokemons.filter(poke => poke.name.includes(this.filters))
    }
  },
  watch: {
    pokeEquipeDonnee: {
      handler () {
        localStorage.setItem('equipes', JSON.stringify(this.pokeEquipeDonnee))
      },
      deep: true
    }
  },
  mounted () {
    if (localStorage.getItem('equipes')) {
      this.pokeEquipeDonnee = JSON.parse(localStorage.getItem('equipes'))
    }
    if (localStorage.getItem('order')) {
      // this.pokeEquipeDonnee = JSON.parse(localStorage.getItem('order'))
    }
  },
  methods: {
    onEnd (e) {
      console.log(e)
      // order.push(ev.relatedContext.list)
      localStorage.setItem('order', JSON.stringify(e))
    },
    infoPokemon (pokeInfo) {
      this.pokeData = pokeInfo
      this.modalInfo = true
    },
    addEquipe (pokeInfo) {
      this.pokeEquipeDonnee.push(pokeInfo)
      localStorage.setItem('equipes', JSON.stringify(this.pokeEquipeDonnee))
    },
    closeModal () {
      if (this.modalInfo) {
        this.modalInfo = false
      } else {
        this.modalInfo = true
      }
    },
    deletePoke (x) {
      this.pokeEquipeDonnee.splice(x, 1)
    }
  }
}
</script>
<style scoped>
.top{
  display: flex;
  width: 1000px;
  margin: auto;
}
.m{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.content{
  display: flex;
  justify-content: space-around;
}
.mr{
  margin-right: 10px;
  margin-bottom: 10px;
}
.fix{
  width: 400px;
  margin-right:auto;
  margin-left: auto;
  margin-top: -10%;
  position: fixed;
}
.center{
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 2%;
}
</style>
