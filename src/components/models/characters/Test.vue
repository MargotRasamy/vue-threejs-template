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
      elements: {
      }
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

  // Create elements in the scene

    this.box(0, 0, 0)
    this.box(1, 1, 0)
    
    this.ball(-2, 0, 0)
    this.ball(0, 1, 0)
    this.ball(0, -1, 0)

    console.log(this.elements)
  // Render everytime we have an update
    this.renderer.setAnimationLoop(() => {
      this.render()
      let acc = 0.01
      this.elements.cubes[0].rotation.y += acc
      this.elements.cubes[1].rotation.y += acc
      this.elements.spheres[0].rotation.y += acc
      this.elements.spheres[1].rotation.y += acc
    })
  },
  render () {
    this.onWindowResize()
    this.renderer.render(this.scene, this.camera)
  },
  onWindowResize() {
    this.camera.aspect = this.container.clientWidth / this.container.clientHeight;
    this.camera.updateProjectionMatrix();
    this.renderer.setSize(this.container.clientWidth, this.container.clientHeight);
  },

  box (xPos, yPos, zPos) {
    let geometry = new THREE.BoxGeometry(1,1,1)
    // let material = new THREE.MeshNormalMaterial({color: 0x00a1cb})
    let material = new THREE.MeshNormalMaterial()
    this.elements.cubes ? null : this.elements.cubes = []
    this.elements.cubes.push(new THREE.Mesh(geometry, material)) 
    this.elements.cubes[this.elements.cubes.length - 1].position.x = xPos
    this.elements.cubes[this.elements.cubes.length - 1].position.y = yPos
    this.elements.cubes[this.elements.cubes.length - 1].position.z = zPos
    this.scene.add(this.elements.cubes[this.elements.cubes.length - 1]) 
  },

  ball (xPos, yPos, zPos) {
    this.elements.spheres ? null : this.elements.spheres = []
    let geometry = new THREE.SphereGeometry(0.5,8,8)
    // let material = new THREE.MeshNormalMaterial({color: 0x00a1cb})
    let material = new THREE.MeshNormalMaterial()
    this.elements.spheres.push(new THREE.Mesh(geometry, material)) 
    this.elements.spheres[this.elements.spheres.length - 1].position.x = xPos
    this.elements.spheres[this.elements.spheres.length - 1].position.y = yPos
    this.elements.spheres[this.elements.spheres.length - 1].position.z = zPos
    this.scene.add(this.elements.spheres[this.elements.spheres.length - 1]) 
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
    width: 70vw;
    height: 70vh;
}
.container {    
    width: 70vw;
    height: 70vh;
    outline: none !important;
    margin: auto;  
}
</style>