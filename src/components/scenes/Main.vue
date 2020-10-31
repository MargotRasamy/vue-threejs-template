<template>
  <div class="main">
    <h1>{{ msg }}</h1>
    <Test/>
  </div>
</template>

<script>
import Test from '../models/characters/Test'

export default {
  name: 'Main',
  props: {
    msg: String
  },
  components: {
      Test
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.main {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
</style>
