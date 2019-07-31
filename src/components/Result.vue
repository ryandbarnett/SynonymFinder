<template>
  <div class="Result">
    <div class="Result-header">
      <h3>Definition: {{result.shortdef[0]}}</h3>
      <p><i>{{result.fl}}</i></p>
      <h3>Synonyms:</h3>
      <hr>
    </div>
    <Synonyms v-bind:synonyms="result.meta.syns[0]" v-on:click="emitClick" />
  </div>
</template>

<script>
import Synonyms from './Synonyms';

export default {
  name: 'Result',
  components: {
    Synonyms
  },
  props: ['result'],
  methods: {
    emitClick(value) {
      this.$emit('click', value);
    }
  }
}
</script>

<style scoped>
  .Result {
    color: #E63946;
    background: #F7FFF7;
    border: 2px solid #1D3557;
    border-radius: 10px;
    margin: 30px 0;
    padding: 30px;
    box-shadow: 0px 2px 3px #1D3557;
  }

  .Result-header {
    margin: 0 10px;
  }

  h4, hr {
    margin-bottom: 20px;
  }

</style>