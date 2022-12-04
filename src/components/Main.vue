<template>
  <div class="main">
    <img id="logo" src="../assets/LogoPokemon.png" alt="logo" />
    <h1>List of Pokemons</h1>
    <p>Choose your pokemon!</p>

    <!-- search -->
    <p id="searchP">
      Search <input id="search" type="text" v-model="searchTerm" />
    </p>

    <!-- list of pokemons -->
    <div class="list">
      <article
        v-for="pokemon in filteredPokemons"
        :key="pokemon.id"
        @click="setPokemonUrl(pokemon.url)"
      >
        <router-link :to="{ name: 'detail', params: { id: pokemon.name } }">
          <img
            :src="imageUrl + pokemon.id + '.png'"
            width="96"
            height="96"
            alt="pokemon.id"
          />

          <h2>{{ pokemon.name }}</h2>
        </router-link>
      </article>
    </div>
  </div>
</template>

<script>
import Detail from "../components/Detail.vue";

export default {
  components: { Detail },
  props: ["imageUrl", "apiUrl"],
  data: () => {
    return {
      pokemonID: "",
      searchTerm: "",
      pokemons: [],
      kanto: 151, // first 151 pokemons
    };
  },
  computed: {
    // pokemon search
    filteredPokemons() {
      return this.pokemons.filter((pokemon) => {
        return pokemon.name.match(this.searchTerm);
      });
    },
  },
  methods: {
    // get data
    fetchData() {
      let req = new Request(this.apiUrl + this.kanto);
      fetch(req)
        .then((resp) => {
          if (resp.status === 200) return resp.json();
        })
        .then((data) => {
          data.results.forEach((pokemon) => {
            pokemon.id = pokemon.url
              .split("/")
              .filter(function (part) {
                return !!part;
              })
              .pop();
            this.pokemons.push(pokemon);
          });
        })
        .catch((error) => {
          console.log(error);
        });
    },
    setPokemonUrl(url) {
      this.$emit("setPokemonUrl", url);
    },
  },
  created() {
    this.fetchData();
  },
};
</script>

<style scoped>
/*  Pokemon font */
@font-face {
  font-family: "PokemonSolid";
  src: url("../assets/fonts/PokemonSolid.ttf") format("truetype");
}
@font-face {
  font-family: "PokemonHollow";
  src: url("../assets/fonts/PokemonHollow.ttf") format("truetype");
}

#logo {
  width: 450px;
  height: 220px;
  margin: 0 auto;
}

.list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  grid-gap: 10px;
  width: 100%;
  max-width: 510px;
  /* border: 1px solid blue; */
  float: left;
}
article {
  height: 150px;
  background-color: #efefef;
  text-align: center;
  text-transform: capitalize;
  border-radius: 5px;
  cursor: pointer;
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2), 0 10px 10px rgba(0, 0, 0, 0.2);
}
h1 {
  font-family: "PokemonSolid";
  text-shadow: 2px 1px 2px black;
  letter-spacing: 4px;
  color: white;
}
h2 {
  margin: 0;
  font-size: 18px;
  color: white;
  font-family: "PokemonSolid";
  text-shadow: 2px 1px 2px black;
  text-decoration: none;
  border-radius: 5px;
  background: #83bf97;
  letter-spacing: 3px;
}
.main p {
  font-family: "PokemonSolid";
  font-size: 18px;
  text-shadow: 2px 1px 2px black;
  color: #fff;
  background: #83bf97;
  border-radius: 5px;
  letter-spacing: 4px;
  display: block;
}

.list img {
  background: #5adbbd;
  border-radius: 50%;
}
#search {
  margin: 0 auto;
  margin-bottom: 20px;
  display: block;
  padding: 10px 6px;
}
#searchP {
  padding-bottom: 10px;
}
</style>