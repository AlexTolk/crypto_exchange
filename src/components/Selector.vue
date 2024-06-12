<template>
  <ul>
    <li @click="setCurrency('BTC')" :className="cryptoNow == 'BTC' ? 'active' : '' ">Bitcoin</li>
    <li @click="setCurrency('ETH')" :className="cryptoNow == 'ETH' ? 'active' : '' ">ETH</li>
    <li @click="setCurrency('USDT')" :className="cryptoNow == 'USDT' ? 'active' : ''">USDT</li>
    <li @click="setCurrency('DOGE')" :className="cryptoNow == 'DOGE'? 'active' : '' ">Dogecoin</li>
  </ul>
</template>

<script>
  export default{
    props: {
      setCurrency: {
        type: Function,
        required: true
      },
      cryptoNow: {
        type: String,
        required: true
      }
    }
  }
</script>

<style scoped>
  ul {
    list-style: none;
    width: 200px;
    padding: 0;
    border-radius: 3px;
    border: 3px solid #000;
  }
  li {
    display: block;
    background-color: #1a032d;
    color: #fff;
    padding: 20px 0;
    font-family: 'Montserrat', sans-serif;
  }
  li:hover, li.active {
    background: #24043e;
    cursor: pointer;
  }
</style>
