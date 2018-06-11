<template>
  <div id="app">
    <VueOtpInput seperator="-" :numInputs="4" shouldAutoFocus/>
  </div>
</template>

<script>
  import VueOtpInput from './components/VueOtpInput.vue';

  export default {
    name: 'app',
    data() {
      return {};
    },
    components: {
      VueOtpInput
    },
    methods: {}
  };
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
