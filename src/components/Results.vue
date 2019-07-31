<template>
  <div class="Results">
    <h2>Results for "{{results[0].meta.id}}"</h2>
    <Result v-bind:key="result.meta.uuid" v-bind:result="result" v-on:click="emitClick" v-for="result in results" />
  </div>
</template>

<script>
import Result from './Result';

export default {
  name: 'Results',
  components: {
    Result
  },
  props: ['results'],
  methods: {
    emitClick(value) {
      this.$emit('click', value);
    }
  }
}
</script>

<style scoped>
  h2 {
    text-align: center;
    text-transform: uppercase;
    color: #F1FAEE;
    text-shadow: 0px 2px 2px #1D3557;
  }

  .Results {
    
  }
</style>