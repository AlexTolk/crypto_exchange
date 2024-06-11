<template>
  <header>
    <h1>CRYPTO MASTER</h1>
    <Input />
    <div class="selectors">
      <Selector />
      <Selector />
    </div>
  </header>

  <main>

  </main>
</template>

<script>
  import Input from './components/Input.vue'
  import Selector from './components/Selector.vue'
  export default {
    components: { Input, Selector}
  }
</script>


<style scoped>
  .selectors {
    display: flex;
    justify-content: space-around;
    width: 700px;
    margin: 0 auto;
  }


</style>
