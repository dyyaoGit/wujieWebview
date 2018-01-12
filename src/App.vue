<template>
  <div id="app">
      <div style="height: 1.28rem;background: #000;"></div>
      <mainContent></mainContent>
  </div>
</template>

<script>
  import mainContent from '@/components/main-content'
  export default {
    name: 'app',
    components: {mainContent},
    data() {
      return {}
    }
  }
</script>

<style>
  @import 'assets/main.css';
  #app {
    min-height: 13.34rem;
  }
</style>
