<template>
  <header>
      <h1>{{ propsdata }}</h1>
      <button v-on:click="sendEvents">send</button>
  </header>
</template>

<script>
export default {
    props: ['propsdata'],
    methods: {
        sendEvents: function(){
            this.$emit('renew');
        }
    }
}
</script>

<style>

</style>