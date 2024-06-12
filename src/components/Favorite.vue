<template>
  <h3>Added to favorites:</h3>
  <div @click="getFromFavs(index)" v-for="(el, index) in favs" :key="index">
    <span>{{ el.from }} </span>
    <span>{{ el.to }}</span>
  </div>
</template>
<script>
  export default {
    props: {
      favs: {
        type: Array,
        required: true
      },
      getFromFavs: {
        type: Function,
        required: true
      }
    }
  }
</script>
<style scoped>
  h3 {
    color: white;
    font-family: 'Montserrat', cursive;
  }
  div {
    display: flex;
    justify-content: center;
    width: 500px;
    margin: 10px auto;
    transition: all 500ms ease;
  }
  span {
    background-color: #4a0e42;
    padding: 10px 15px;
    color: #fff;
  }
  div:hover {
    opacity: 0.7;
    transform: scale(1.1);
    cursor: pointer;
  }
</style>
