<template>
  <div>
    <h3>{{result.shortdef[0]}}</h3>
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