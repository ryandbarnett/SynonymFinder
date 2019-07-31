<template>
  <div>
    <ul v-bind:key="index" v-for="(synonym, index) in synonyms">
      <Synonym v-bind:synonym="synonym" v-on:click="emitClick"/>
    </ul>
  </div>
</template>

<script>
import Synonym from './Synonym';

export default {
  name: 'Synonyms',
  components: {
    Synonym
  },
  props: ['synonyms'],
  methods: {
    emitClick(value) {
      this.$emit('click', value);
    }
  }
}
</script>