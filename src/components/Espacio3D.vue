<template>
  <Renderer ref="renderer" resize="window" :pointer="{ onMove: updateTilt }"
            :orbit-ctrl="{ enableDamping: true, dampingFactor: 0.05, autoRotate: true, maxPolarAngle: Math.PI / 2,
            screenSpacePanning: false, minDistance: 100, maxDistance: 1000 }"
            shadow>
    <Camera :position="{ x: 400, y: 200, z: 0 }"/>
    <Scene background="#ffffff">
      <AmbientLight />
      <PointLight ref="light" :position="{ y: 0, z: 20 }" />
      <SpotLight color="#ffffff" :intensity="0.5" :position="{ y: 150, z: 0 }" :cast-shadow="true" :shadow-map-size="{ width: 1024, height: 1024 }" />
      <SpotLight color="#4455ee" :intensity="0.5" :position="{ y: -150, z: 0 }" :cast-shadow="true" :shadow-map-size="{ width: 1024, height: 1024 }" />
      <GltfModel :position="{x: 0, y: 0}" ref="teatro" src="3dmodels/teatro_jrr.gltf" :cast-shadow="true" :receive-shadow="true" />
      <GltfModel :position="{x: 100, y: 0, z: 100}" src="3dmodels/teatro_jrr.gltf" :cast-shadow="true" :receive-shadow="true">
      </GltfModel>
    </Scene>
    <EffectComposer>
      <RenderPass/>
      <UnrealBloomPass :strength="0.3"/>
      <FXAAPass />
      <TiltShiftPass :gradient-radius="tiltRadius" :start="{ x: 0, y: this.tiltY }" :end="{ x: 100, y: this.tiltY }" />
    </EffectComposer>
  </Renderer>
</template>

<script>
import { Object3D, MathUtils } from 'three'
import {
  Camera,
  AmbientLight,
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
    Camera,
    GltfModel,
    AmbientLight,
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
      tiltY: 100
    }
  },
  methods: {
    print (val) {
      console.log(val)
    },
    updateTilt({ positionN }) {
      this.tiltRadius = this.size.height / 3;
      this.tiltY = (positionN.y + 1) * 0.5 * this.size.height;
    },
  },
  mounted () {
    // init instanced mesh matrix
    // const imesh = this.$refs.imesh.mesh
    this.renderer = this.$refs.renderer
    this.size = this.renderer.three.size
    this.teatro = this.$refs.teatro
    console.log(this.teatro)
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
