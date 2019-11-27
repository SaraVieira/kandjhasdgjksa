<template>
  <main>
    <h2>Kanye West Quotes</h2>
    <h3 v-if="loading">Getting them quote</h3>
    <h3 v-if="quote">{{quote}}</h3>

    <button v-on:click="getQuote">Get another quote</button>
  </main>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      loading: false,
      quote: ""
    };
  },
  methods: {
    getQuote: async function() {
      this.loading = true;
      const data = await fetch("https://api.kanye.rest").then(rsp =>
        rsp.json()
      );

      this.quote = data.quote;
      this.loading = false;
    }
  },
  async mounted() {
    this.getQuote();
  }
};
</script>

<style scoped>
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

main {
  width: 80%;
  margin: auto;
}

button {
  width: 100%;
  border: none;
  height: 44px;
  color: white;
  background: #32d1b1;
  margin-top: 40px;
}
</style>
