<template>
  <form v-on:submit.prevent="submit()">
    <input v-bind:value="value" v-on:input="updateValue($event.target.value)"/>
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