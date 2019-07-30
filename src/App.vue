<template>
  <div id="app">
    <Header />
    <Form />
    <div v-if="results.length">
      <Results v-bind:results="results" />
    </div>
    <h2 v-if="error">{{ error }}</h2>
  </div>
</template>

<script>
import Header from './components/Header';
import Form from './components/Form';
import Results from './components/Results';
import fetchData from './utils/fetchData';

export default {
  name: 'app',
  data() {
    return {
      results: [],
      error: ''
    }
  },
  components: {
    Header,
    Form,
    Results
  },
  mounted() {
    this.getSynonyms();
  },
  methods: {
    getSynonyms() {
      const {VUE_APP_BASE_URL, VUE_APP_KEY} = process.env;
      const url = `${VUE_APP_BASE_URL}umpire?key=${VUE_APP_KEY}`;
      fetchData(url).then((results) => {
        if (!!results && !!results[0].meta) {
          this.results = results;
          this.error = '';
        } else {
          this.results = [];
          this.error = 'No synonyms found :(';
        }
      });
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
</style>
