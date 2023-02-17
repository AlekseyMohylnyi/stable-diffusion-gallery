<template>
  <div class="home">    
    <h2>home sweet home!!!</h2>
    <HelloWorld />
  </div>
</template>

<script>
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld
  }
}
</script>

<style>
.home {
  height: 100%;
}
</style>
