<template>
  <div class="test">
    <div class="container"></div>
  </div>
</template>

<script>
// Import three js, the controls, and loaders
import * as THREE from 'three'
// import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls'
// import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader'


export default {
  name: 'Test',
  data () {
    return {
      // Create all the datas needed for the scene : datas that will update and re-render
      scene: null,
      camera: null,
      renderer: null,
      container: null,
      geometry: null,
      material: null,
      cube: null
    }
  },
methods: {
  // Create an init method to set up the environnment
  init () {
  // set container
    this.container = document.querySelector('.container')

  // create scene
    this.scene = new THREE.Scene()
    this.scene.background = new THREE.Color('skyblue')
  
  // create and assign camera
    this.camera = new THREE.PerspectiveCamera(30, window.innerWidth / window.innerHeight, 1, 1000)
    this.camera.position.z = 5

  // Create the renderer
    this.renderer = new THREE.WebGLRenderer()
    this.renderer.setSize(this.container.clientWidth, this.container.clientHeight)
    this.container.appendChild(this.renderer.domElement)

  // Create elements in the scene (geometry)
    this.geometry = new THREE.BoxGeometry( 1, 1, 1 );
    this.material = new THREE.MeshBasicMaterial( {color: 0x00a1cb} );
    this.cube = new THREE.Mesh(this.geometry, this.material );
    this.scene.add(this.cube);

  // Render everytime we have an update
    this.renderer.setAnimationLoop(() => {
      this.render()
      this.cube.rotation.x += 0.01;
      this.cube.rotation.y += 0.01;
    })
  },
  render () {
    this.renderer.render(this.scene, this.camera)
  }
},
  mounted () {
    // Call init method everytime the component is rendered and mounted
   this.init()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>

.test {
    display: flex;
    margin: auto;
}
.container {    
    width: 40rem;    
    height:30rem;
    outline: none !important;
    margin: auto;  
}
</style>