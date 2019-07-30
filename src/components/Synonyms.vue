<template>
  <div>
    <ul v-for="(synonym, index) in synonyms">
      <Synonym v-bind:key="index" v-bind:synonym="synonym" />
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
  props: ['synonyms']
}
</script>