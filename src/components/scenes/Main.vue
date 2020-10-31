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
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
