<template>
  <li v-on:click="click(synonym)">{{synonym}}</li>
</template>

<script>

export default {
  name: 'Synonym',
  props: ['synonym'],
  methods: {
    click(value) {
      this.$emit('click', value);
    }
  }
}
</script>