<template>
  <main>
    <PhaserExample class="inline" />
    <HelloWorld class="inline" />
  </main>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import PhaserExample from './components/PhaserExample'

export default {
  name: 'App',
  components: {
    HelloWorld,
    PhaserExample
  }
}
</script>
<style scoped>
.inline {
  display: inline-block;
}
</style>
