<template>
  <div class="robot">
    <div class="webgl"></div>
  </div>
</template>

<script>
import * as THREE from 'three'
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls'
import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader'


export default {
  name: 'Robot',
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
  methods: {
    init () {
      // set container
      this.container = document.querySelector('.webgl')

      // add camera
      const fov = 60 // Field of view
      const aspect = this.container.clientWidth / this.container.clientHeight
      const near = 0.1 // the near clipping plane
      const far = 30 // the far clipping plane
      const camera = new THREE.PerspectiveCamera(fov, aspect, near, far)
      camera.position.set(0, 5, 10)
      this.camera = camera

      // create scene
      this.scene = new THREE.Scene()
      this.scene.background = new THREE.Color('skyblue')

      // add lights
      const ambientLight = new THREE.HemisphereLight(
        0xffffff, // bright sky color
        0x222222, // dim ground color
        1 // intensity
      )
      const mainLight = new THREE.DirectionalLight(0xffffff, 4.0)
      mainLight.position.set(10, 10, 10)
      this.scene.add(ambientLight, mainLight)

      // add controls
      this.controls = new OrbitControls(this.camera, this.container)

      // create renderer
      this.renderer = new THREE.WebGLRenderer({ antialias: true })
      this.renderer.setSize(this.container.clientWidth, this.container.clientHeight)
      this.renderer.setPixelRatio(window.devicePixelRatio)
      this.renderer.gammaFactor = 2.2
      this.renderer.outputEncoding = THREE.sRGBEncoding
      this.renderer.physicallyCorrectLights = true
      this.container.appendChild(this.renderer.domElement)

      // set aspect ratio to match the new browser window aspect ratio
      this.camera.aspect = this.container.clientWidth / this.container.clientHeight
      this.camera.updateProjectionMatrix()
      this.renderer.setSize(this.container.clientWidth, this.container.clientHeight)

      const loader = new GLTFLoader()

      loader.load(
        '/models/RobotExpressive.glb',
        gltf => {
          this.scene.add(gltf.scene)
        },
        undefined,
        undefined
      )

      this.renderer.setAnimationLoop(() => {
        this.render()
      })
    },
    render () {
      this.renderer.render(this.scene, this.camera)
    }
  },
  mounted () {
    this.init()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>




.robot {
    display: flex;
}
.webgl {    
    width: 40rem;    
    height:30rem;
    outline: none !important;
    margin: auto;  
}


</style>