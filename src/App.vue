<template>
  <div id="app">
    <div style="background-color: gray"></div>

    <Loanrequest />

  </div>
</template>

<script>
  
import Loanrequest from './components/Loanrequest.vue'

export default {
  name: 'app',
  components: {
    Loanrequest
  }
}
</script>

<style lang="css">
  @import '../node_modules/bulma/css/bulma.css';
</style>
