<template>
  <div class="test">
    <div class="webgl"></div>
  </div>
</template>

<script>
// import * as THREE from 'three'
// import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls'
// import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader'


export default {
  name: 'Test',
  data () {
    return {
      container: null,
      scene: null,
      camera: null,
      controls: null,
      renderer: null,
      stats: null
    }
  },
  mounted () {
   
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>

.test {
    display: flex;
}
.webgl {    
    width: 40rem;    
    height:30rem;
    outline: none !important;
    margin: auto;  
    background-color:lightblue;
}
</style>