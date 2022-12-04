<template>
  <div class="home">
    <img id='logo' alt="PokemonLogo" src="../assets/LogoPokemon.png">
    <Home />

  </div>
</template>

<script>
import Home from '@/components/Home.vue'


export default {
  name: 'HomeView',
  components: {
    Home
  }
}
</script>
<style scoped>
#logo {
  width: 450px;
  height: 220px;
  margin: 0 auto;
}
</style>
