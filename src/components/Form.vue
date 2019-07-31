<template>
  <form v-on:submit.prevent="submit()">
    <input v-bind:value="value" v-on:input="updateValue($event.target.value)"/><br/>
    <input type="submit" />
  </form>
</template>

<script>
export default {
  name: 'Form',
  props: ['value'],
  methods: {
    updateValue(value) {
      this.$emit('input', value);
    },
    submit() {
      this.$emit('submit');
    }
  }
}
</script>

<style scoped>
  form {
    margin-top: 20px;
  }

  input {
    width: 100%;
    color: #1D3557;
    text-transform: uppercase;
    margin: 10px 0;
    padding: 10px;
    border:0 none;
    font-size: 20px;
    border-radius: 5px;
    background: #A8DADC;
    transition: .25s;
    box-shadow: 2px 3px 1px #1D3557;
  }

  input:focus {
    outline-color: #A8DADC !important;
  }

  input[type=submit] {
    cursor: pointer;
    color: #F1FAEE;
    font-weight: bold;
    text-transform: uppercase;
    background: #E63946;
  }

  input[type=submit]:hover {
    color: #E63946;
    background: #F1FAEE;
    box-shadow: 1px 2px 1px #1D3557;
  }
</style>