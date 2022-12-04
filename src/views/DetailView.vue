<template>
  <div v-if="pokemon">
    <GoBack />
    <h2>Detail Pokemon:</h2>
    <div class="details">
      <div class="upper-details">
        <img
          :src="imageUrl + pokemon.id + '.png'"
          width="96"
          height="96"
          alt="pokemon.id"
        />
        <h1>{{ pokemon.name }}</h1>
        <hr />
        <h4>Weight: {{ pokemon.weight / 10 }}kg</h4>
        <h4>Height: {{ pokemon.height / 10 }}m</h4>
        <hr />
      </div>
      <div class="bottom-details">
        <h3>Type</h3>
        <div
          class="type"
          v-for="(value, index) in pokemon.types"
          :key="'value' + index"
        >
          <div v-if="value.type.name == 'grass'">
            <div class="pokemon-type">
              <img src="../assets/img/grass.svg" class="icon-grass" />
              <p>{{ value.type.name }}</p>
            </div>
          </div>

          <div v-if="value.type.name == 'poison'">
            <div class="pokemon-type">
              <img src="../assets/img/poison.svg" class="icon-poison" />
              <p>{{ value.type.name }}</p>
            </div>
          </div>

          <div v-if="value.type.name == 'dragon'">
            <div class="pokemon-type">
              <img src="../assets/img/dragon.svg" class="icon-dragon" />
              <p>{{ value.type.name }}</p>
            </div>
          </div>

          <div v-if="value.type.name == 'dark'">
            <div class="pokemon-type">
              <img src="../assets/img/dark.svg" class="icon-dark" />
              <p>{{ value.type.name }}</p>
            </div>
          </div>

          <div v-if="value.type.name == 'electric'">
            <div class="pokemon-type">
              <img src="../assets/img/electric.svg" class="icon-electric" />
              <p>{{ value.type.name }}</p>
            </div>
          </div>

          <div v-if="value.type.name == 'fairy'">
            <div class="pokemon-type">
              <img src="../assets/img/fairy.svg" class="icon-fairy" />
              <p>{{ value.type.name }}</p>
            </div>
          </div>

          <div v-if="value.type.name == 'fighting'">
            <div class="pokemon-type">
              <img src="../assets/img/fighting.svg" class="icon-fighting" />
              <p>{{ value.type.name }}</p>
            </div>
          </div>

          <div v-if="value.type.name == 'fire'">
            <div class="pokemon-type">
              <img src="../assets/img/fire.svg" class="icon-fire" />
              <p>{{ value.type.name }}</p>
            </div>
          </div>

          <div v-if="value.type.name == 'flying'">
            <div class="pokemon-type">
              <img src="../assets/img/flying.svg" class="icon-flying" />
              <p>{{ value.type.name }}</p>
            </div>
          </div>

          <div v-if="value.type.name == 'ghost'">
            <div class="pokemon-type">
              <img src="../assets/img/ghost.svg" class="icon-ghost" />
              <p>{{ value.type.name }}</p>
            </div>
          </div>

          <div v-if="value.type.name == 'ground'">
            <div class="pokemon-type">
              <img src="../assets/img/ground.svg" class="icon-ground" />
              <p>{{ value.type.name }}</p>
            </div>
          </div>

          <div v-if="value.type.name == 'ice'">
            <div class="pokemon-type">
              <img src="../assets/img/ice.svg" class="icon-ice" />
              <p>{{ value.type.name }}</p>
            </div>
          </div>

          <div v-if="value.type.name == 'normal'">
            <div class="pokemon-type">
              <img src="../assets/img/normal.svg" class="icon-normal" />
              <p>{{ value.type.name }}</p>
            </div>
          </div>

          <div v-if="value.type.name == 'psychic'">
            <div class="pokemon-type">
              <img src="../assets/img/psychic.svg" class="icon-psychic" />
              <p>{{ value.type.name }}</p>
            </div>
          </div>

          <div v-if="value.type.name == 'rock'">
            <div class="pokemon-type">
              <img src="../assets/img/rock.svg" class="icon-rock" />
              <p>{{ value.type.name }}</p>
            </div>
          </div>

          <div v-if="value.type.name == 'steel'">
            <div class="pokemon-type">
              <img src="../assets/img/steel.svg" class="icon-steel" />
              <p>{{ value.type.name }}</p>
            </div>
          </div>

          <div v-if="value.type.name == 'water'">
            <div class="pokemon-type">
              <img src="../assets/img/water.svg" class="icon-water" />
              <p>{{ value.type.name }}</p>
            </div>
          </div>
        </div>
      </div>
      <div class="bottom-moves">
        <h3 @click="showMoves = !showMoves" id="clickMoves">Moves</h3>
        <ul class="moves">
          <div
            v-show="showMoves === true"
            class="ability"
            v-for="(value, indeks) in pokemon.moves"
            :key="'value' + indeks"
          >
            <li>{{ value.move.name }}</li>
          </div>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import Detail from "../components/Detail.vue";
import GoBack from "../components/GoBack.vue";

export default {
  props: ["id"],
  name: "Detail",
  components: { Detail, GoBack },
  data() {
    return {
      showMoves: false,
      pokemon: null,
      iconUrl: "",
      imageUrl:
        "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/",
    };
  },

  mounted() {
    fetch("https://pokeapi.co/api/v2/pokemon/" + this.id)
      .then((res) => res.json())
      .then((data) => (this.pokemon = data))
      .catch((err) => console.log(err.message));
  },
};
</script>

<style>
.details {
  background: rgba(222, 253, 224, 0.4);
  width: 250px;
  min-height: 200px;
  margin: 0 auto;
  border-radius: 25px;
  padding: 15px;
  padding-bottom: 30px;
}
.details p,
h4,
h1 {
  color: white;
  text-shadow: 2px 1px 2px black;
}
.pokemon-type {
  display: flex;
  /* border: 1px solid green; */
}
h1 {
  letter-spacing: 6px;
}
#clickMoves:hover {
  text-decoration: underline;
}
.pokemon-type p,
h4 {
  margin-top: -5px;
  padding-left: 10px;
}
hr {
  margin-top: -10px;
  color: rgba(222, 253, 224, 0.4);
}
.upper-details,
.bottom-details,
.bottom-moves {
  font-family: "PokemonSolid";
  letter-spacing: 4px;
  font-size: 18px;
  color: white;
}
.upper-details img {
  background: rgba(90, 219, 189, 0.5);
  border-radius: 50%;
}
.upper-details p,
h1 {
  text-transform: capitalize;
  font-size: 26px;
}
.bottom-details h3,
.bottom-moves h3,
.bottom-moves li {
  text-shadow: 2px 1px 2px black;
}
.bottom-details p {
  font-size: 12px;
}
ul.moves,
li {
  font-family: "PokemonSolid";
  list-style-type: none;
  font-size: 12px;
  color: white;
  margin-left: -20px;
  margin-bottom: 0px;
}
/* icons type */
.icon-bug,
.icon-dark,
.icon-dragon,
.icon-electric,
.icon-fairy,
.icon-fighting,
.icon-fire,
.icon-flying,
.icon-ghost,
.icon-grass,
.icon-ground,
.icon-ice,
.icon-normal,
.icon-poison,
.icon-psychic,
.icon-rock,
.icon-steel,
.icon-water {
  margin-left: 10px;
  width: 20px;
  height: 20px;
  background: greenyellow;
  border-radius: 30%;
  padding: 5px;
}
.icon-bug {
  background: #1c4b29;
}
.icon-dark {
  background: #040706;
}
.icon-dragon {
  background: #448b95;
}
.icon-electric {
  background: #e3e32b;
}
.icon-fairy {
  background: #971944;
}
.icon-fighting {
  background: #994025;
}
.icon-fire {
  background: #ac1e23;
}
.icon-flying {
  background: #ac1e23;
}
.icon-ghost {
  background: #33336b;
}
.icon-grass {
  background: #157a3f;
}
.icon-ground {
  background: #a9702a;
}
.icon-ice {
  background: #87d1f5;
}
.icon-normal {
  background: #73525b;
}
.icon-poison {
  background: #5e2d88;
}
.icon-psychic {
  background: #a42a6c;
}
.icon-rock {
  background: #48180b;
}
.icon-steel {
  background: #5f756d;
}
.icon-water {
  background: #1552e2;
}

/*  Pokemon font */
@font-face {
  font-family: "PokemonSolid";
  src: url("../assets/fonts/PokemonSolid.ttf") format("truetype");
}
@font-face {
  font-family: "PokemonHollow";
  src: url("../assets/fonts/PokemonHollow.ttf") format("truetype");
}
@font-face {
  font-family: "PokemonClassic";
  src: url("../assets/fonts/PokemonClassic.ttf") format("truetype");
}
</style>