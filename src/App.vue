<template>
  <div id="app">
    <header>
      <Title />
      <Form v-model="value" v-on:submit="getSynonyms(value)" />
    </header>
    <main class="Results-container" v-if="results.length">
      <Results v-bind:results="results" v-on:click="handleClick"/>
    </main>
    <h2 class="error" v-if="error">{{ error }}</h2>
  </div>
</template>

<script>
import Title from './components/Title';
import Form from './components/Form';
import Results from './components/Results';
import fetchData from './utils/fetchData';

export default {
  name: 'app',
  data() {
    return {
      value: '',
      results: [],
      error: ''
    }
  },
  components: {
    Title,
    Form,
    Results
  },
  methods: {
    getSynonyms(value) {
      const {VUE_APP_BASE_URL, VUE_APP_KEY} = process.env;
      const url = `${VUE_APP_BASE_URL}${value}?key=${VUE_APP_KEY}`;
      fetchData(url).then((results) => {
        if (!!results && !!results[0].meta) {
          this.results = results;
          this.error = '';
        } else {
          this.results = [];
          this.error = `No synonyms found for "${value}"`;
        }
      });
    },
    handleClick(value) {
      this.value = value;
      this.getSynonyms(value);
    }
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }

  #app {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-image: url(./assets/arches.png);
    background-color: #F1FAEE;
    height: 100vh;
  }

  .Results-container {
    width: 100%;
    border-top: 2px solid #1D3557;
    background: #457B9D;
    margin: 20px 0;
    padding: 20px 40px;
  }

  header {
    background: #457B9D;
    border: 2px solid #1D3557;
    border-radius: 10px;
    margin: 30px 0;
    padding: 30px;
    box-shadow: 0px 2px 3px #1D3557;
  }

  .error {
    color: #E63946;
  }
</style>
