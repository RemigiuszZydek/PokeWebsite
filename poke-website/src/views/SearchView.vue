<template>
  <div class="wrapper">
    <div class="search">
      <label for="search">Search
      <input id="search"
      name="search"
      v-model="searchValue"
      @input="handleInput"/>
    </label>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

const API = 'https://pokeapi.co/api/v2/pokemon/';
export default {
  name: 'SearchView',
  data() {
    return {
      searchValue: '',
    };
  },
  methods: {
    handleInput() {
      axios.get(`${API}${this.searchValue}`)
        .then((response) => {
          console.log(response.data.sprites.other.home.front_default);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .wrapper{
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 0;
    padding: 30px;
    width: 100%;
  }

</style>
