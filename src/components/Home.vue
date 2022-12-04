<template>
  <div class="hello">
    <h1>Welcome to Pokedex app</h1>
    <p>
      Here you can see all pokemons from <b>Kanto</b> region. <br />
      You can search for your favourite Pokemon, from <b>Pokedex</b> menu.
    </p>
    <p id="small">
      If you click on it, it will show it's name, type, weight, height and
      moves.
    </p>
  </div>
</template>

<script>
export default {
  name: "Home",
};
</script>

<style scoped>
h1 {
  font-family: "PokemonSolid";
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
p {
  margin-top: 50px;
  color: white;
  background: #42b983;
  padding: 20px;
  font-size: 18px;
}
#small {
  margin-top: 0;
  font-size: 14px;
}
</style>
