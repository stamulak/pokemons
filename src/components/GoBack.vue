<template>
  <span class="go-back">
    <button @click="goBack">go back</button>
  </span>
</template>

<script>
export default {
  methods: {
    goBack() {
      return this.$router.go(-1);
    },
  },
};
</script>

<style scoped>
button {
  border: none;
  background: rgba(222, 253, 224, 0.4);
  padding: 5px 25px 5px 25px;
  border-radius: 25px;
  color: white;
  font-weight: bolder;
  text-shadow: 2px 1px 2px black;
  font-size: 18px;
}
button:hover {
  /* text-shadow: 1px 1px 1px black; */
  text-decoration: underline;
  cursor: pointer;
}
</style>