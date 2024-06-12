<template>
  <input min="0" type="number" @input="changeAmount($event.target.value)" placeholder="input the amount">
  <br>
  <button @click="convert()">Convert</button>
  <button @click="favorite()">Add to favorites</button>
</template>

<script>
  export default{
    props: {
      changeAmount: {
        type: Function,
        required: true
      },
      convert: {
        type: Function,
        required: true
      },
      favorite: {
        type: Function,
        required: true
      }
    }
  }
</script>

<style>
  input {
    outline: none;
    border-radius: 3px;
    border: none;
    padding: 15px;
    background-color: #fff;
    color:rgb(7, 4, 29);
    font-size: 1.2em;
    font-family: 'Montserrat', sans-serif;
  }
  button {
    margin: 10px;
    padding: 10px 15px;
    background-color: rgb(205, 174, 0);
    color: rgb(7, 4, 29);
    border-radius: 5px;
    outline: none;
    cursor: pointer;
    border: 0;
  }
</style>
