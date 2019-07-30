<template>
  <div>
    <h2>Results for "{{results[0].meta.id}}"</h2>
    <div v-for="result in results">
      <Result v-bind:key="result.meta.uuid" v-bind:result="result" />
    </div>
  </div>
</template>

<script>
import Result from './Result';

export default {
  name: 'Results',
  components: {
    Result
  },
  props: ['results']
}
</script>