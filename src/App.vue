<template>
    <div id="app">
      <Quote />
      </div>
</template>

<script>
import Quote from '@/components/Quote.vue';
export default {
  name: 'App',
  components: {
    Quote
  },
  methods: {
    async getQuote() {
      const res = await fetch('https://zenquotes.io/api/random ')
      const { results } = await res.json()
      console.log(results)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
