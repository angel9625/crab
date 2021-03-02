<template>
  <div id="App">
    <!-- <home /> -->
    <!-- <mine></mine> -->
    <history></history>
    <!-- <controler-tab></controler-tab> -->
  </div>
  <!-- <router-view /> -->
</template>
<script>
// import ControlerTab from './components/common/ControlerTab.vue'
import History from './views/history/History.vue'
// import Home from './views/home/Home.vue'
// import Mine from './views/mine/Mine.vue'
export default {
  components: {
    History
    // ControlerTab
    // Home
    // Mine
  }
}
</script>
<style lang="scss">
</style>
