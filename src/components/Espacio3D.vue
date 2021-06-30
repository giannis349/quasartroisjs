<template>
  <Renderer ref="renderer" resize="window" :pointer="{ onMove: updateTilt }"
            :orbit-ctrl="{ enableDamping: true, dampingFactor: 0.005, autoRotate: true, maxPolarAngle: Math.PI / 2,
            screenSpacePanning: false, minDistance: 100, maxDistance: 2000 }"
            shadow>
    <Camera :position="{ x: 400, y: 200, z: 0 }"/>
    <Scene ref="scene" background="#666666" :fog="myFog">
      <AmbientLight />
      <PointLight ref="light" :position="{ y: 0, z: 20 }" />
      <SpotLight color="#ffffff" :intensity="0.5" :position="{ y: 150, z: 0 }" :cast-shadow="true" :shadow-map-size="{ width: 1024, height: 1024 }" />
      <SpotLight color="#4455ee" :intensity="0.5" :position="{ y: -150, z: 0 }" :cast-shadow="true" :shadow-map-size="{ width: 1024, height: 1024 }" />
      <GltfModel @load="printe('loadeee')" :position="{x: 0, y: 0}" ref="teatro" src="3dmodels/teatro_jrr.gltf" :cast-shadow="true" :receive-shadow="true" />
      <GltfModel :materialParams="{color: '#ffff00'}" :position="{x: 100, y: 0, z: 60}" src="3dmodels/teatro_jrr.gltf" :cast-shadow="true" :receive-shadow="true"></GltfModel>
      <GltfModel :materialParams="{color: '#ffff00'}" :position="{x: -100, y: 0, z: 50}" src="3dmodels/teatro_jrr.gltf" :cast-shadow="true" :receive-shadow="true"></GltfModel>
      <GltfModel :materialParams="{color: '#ffff00'}" :position="{x: -200, y: 0, z: 40}" src="3dmodels/teatro_jrr.gltf" :cast-shadow="true" :receive-shadow="true"></GltfModel>
      <GltfModel :materialParams="{color: '#ffff00'}" :position="{x: -80, y: 0, z: 100}" src="3dmodels/teatro_jrr.gltf" :cast-shadow="true" :receive-shadow="true"></GltfModel>
    </Scene>
    <EffectComposer>
      <RenderPass/>
      <UnrealBloomPass :strength="0.05"/>
      <FXAAPass />
      <TiltShiftPass :gradient-radius="tiltRadius" :start="{ x: 0, y: this.tiltY }" :end="{ x: 0, y: this.tiltY }" />
    </EffectComposer>
  </Renderer>
</template>

<script>
import { Object3D, MathUtils, Color, FogExp2 } from 'three'
import {
  Plane,
  CylinderGeometry,
  StandardMaterial,
  Camera,
  AmbientLight,
  DirectionalLight,
  PointLight,
  GltfModel,
  EffectComposer,
  Renderer,
  RenderPass,
  SpotLight,
  Scene,
  UnrealBloomPass,
  FXAAPass,
  TiltShiftPass
} from 'troisjs'

export default {
  name: 'Espacio3D',
  components: {
    Plane,
    CylinderGeometry,
    StandardMaterial,
    Camera,
    GltfModel,
    AmbientLight,
    DirectionalLight,
    PointLight,
    EffectComposer,
    Renderer,
    RenderPass,
    SpotLight,
    Scene,
    UnrealBloomPass,
    FXAAPass,
    TiltShiftPass
  },
  setup () {
    return {
      NUM_INSTANCES: 7
    }
  },
  data () {
    return {
      tiltRadius: 100,
      tiltY: 100,
      myFog: undefined
    }
  },
  methods: {
    printe (val) {
      console.log(val)
    },
    updateTilt ({ positionN }) {
      this.tiltRadius = this.size.height / 3
      this.tiltY = this.size.height / 2;
      this.tiltY = (positionN.y + 1) * 0.5 * this.size.height
    }
  },
  mounted () {
    // init instanced mesh matrix
    // const imesh = this.$refs.imesh.mesh
    this.renderer = this.$refs.renderer
    this.size = this.renderer.three.size
    this.teatro = this.$refs.teatro
    this.scene = this.$refs.scene
    this.niebla = new Color('ff0000')
    this.myFog = new FogExp2(0xff0000, 0.9)
    console.log(this.teatro)
    console.log(this.scene)
    this.scene.fog = this.myFog
    const dummy = new Object3D()
    const { randFloat: rnd, randFloatSpread: rndFS } = MathUtils
    for (let i = 0; i < this.NUM_INSTANCES; i++) {
      dummy.position.set(rndFS(200), rndFS(200), rndFS(200))
      const scale = rnd(0.2, 1)
      dummy.scale.set(scale, scale, scale)
      dummy.updateMatrix()
      // imesh.setMatrixAt(i, dummy.matrix)
    }
    // imesh.instanceMatrix.needsUpdate = true
  }
}
</script>
