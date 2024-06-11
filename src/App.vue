<template>
  <header>
    <p v-if="error !== ''" className="error-text">{{ error }}</p>
    <h1>CRYPTO MASTER</h1>
    </header>

  <main>
    <Input :changeAmount="changeAmount" :convert="convert"/>
    <p v-if="result !== 0" className="result-text">{{ result }}</p>
    <div class="selectors">
      <Selector :setCurrency="setFirstCurrency"/>

      <Selector :setCurrency="setSecondCurrency"/>
    </div>
  </main>
</template>

<script>
  import Input from './components/Input.vue'
  import Selector from './components/Selector.vue'
  import CryptoConvert from 'crypto-convert';

  const convert = new CryptoConvert();

  export default {
    components: { Input, Selector},
    data() {
      return {
        amount: 0,
        firstCurrency: '',
        secondCurrency: '',
        error: '',
        result: 0
      }
    },
    methods: {
      changeAmount(val) {
        this.amount = val
      },
      setFirstCurrency(val) {
        this.firstCurrency = val
      },
      setSecondCurrency(val) {
        this.secondCurrency = val
      },
      async convert() {
        if(this.amount <= 0){
          this.error = "The amount can't be zero or less than zero"
          return
        } else if(this.firstCurrency == '' || this.secondCurrency == '') {
          this.error = "Choose the currencies "
          return
        } else if(this.firstCurrency == this.secondCurrency) {
          this.error = "Currencies can't be the same"
          return
        }

        this.error = ''

        await convert.ready();
        if(this.firstCurrency == 'BTC' && this.secondCurrency == 'ETH'){
          this.result = convert.BTC.ETH(this.amount);
        }else if (this.firstCurrency == 'BTC' && this.secondCurrency == 'USDT') {
          this.result = convert.BTC.USDT(this.amount);
        }else if (this.firstCurrency == 'BTC' && this.secondCurrency == 'DOGE') {
          this.result = convert.BTC.DOGE(this.amount);
        }else if (this.firstCurrency == 'ETH' && this.secondCurrency == 'BTC') {
          this.result = convert.ETH.BTC(this.amount);
        }else if (this.firstCurrency == 'ETH' && this.secondCurrency == 'USDT') {
          this.result = convert.BTC.USDT(this.amount);
        }else if (this.firstCurrency == 'ETH' && this.secondCurrency == 'DOGE') {
          this.result = convert.ETH.DOGE(this.amount);
        }else if (this.firstCurrency == 'USDT' && this.secondCurrency == 'BTC') {
          this.result = convert.USDT.BTC(this.amount);
        }else if (this.firstCurrency == 'USDT' && this.secondCurrency == 'ETH') {
          this.result = convert.USDT.ETH(this.amount);
        }else if (this.firstCurrency == 'USDT' && this.secondCurrency == 'DOGE') {
          this.result = convert.USDT.DOGE(this.amount);
        }
      }
    }
  }
</script>


<style scoped>
  .selectors {
    display: flex;
    justify-content: space-around;
    width: 700px;
    margin: 0 auto;
  }
  .error-text {
    background-color: red;
    color: white;
    border-radius: 3px;
    padding: 5px 5px;
    position: relative;
    top: 10px;
    font-family: 'Montserrat', sans-serif;
  }

</style>
