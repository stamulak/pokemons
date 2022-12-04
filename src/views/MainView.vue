<template>
  <div class="wrapper">
    <Main
      :imageUrl="imageUrl"
      :apiUrl="apiUrl"
      @setPokemonUrl="setPokemonUrl"
    />
  </div>
</template>

<script>
import Main from "../components/Main.vue";

export default {
  name: "MainView",
  components: { Main },
  data: () => {
    return {
      imageUrl:
        "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/",
      apiUrl: "https://pokeapi.co/api/v2/pokemon?limit=",
      pokemonUrl: "",
    };
  },
  methods: {
    setPokemonUrl(url) {
      this.pokemonUrl = url;
    },
  },
};
</script>

<style>
.wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  padding: 10px;
  width: calc(100% - 20px);
  min-height: calc(100vh - 20px);
  font-weight: normal;
}

h1 {
  color: #efefef;
}
</style>