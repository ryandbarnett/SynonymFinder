<template>
  <li class="Synonym" v-on:click="click(synonym)">{{synonym}}</li>
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

<style scoped>
  .Synonym {
    padding: 10px 15px;
    margin: 10px;
    border-radius: 10px;
    background: #457B9D;
    box-shadow: 2px 3px 1px #1D3557;
    text-transform: uppercase;
    cursor: pointer;
    color: #F1FAEE;
    font-weight: bold;
    border: 2px solid transparent;
    transition: .25s;
  }

  .Synonym:hover {
    color: #457B9D;
    background: #F1FAEE;
    border: 2px solid #457B9D;
    box-shadow: 1px 2px 1px #1D3557;
  }
</style>