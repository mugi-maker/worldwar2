<script lang="ts">
  import { Canvas, T } from '@threlte/core'
  import Scene from './Scene.svelte'
  import Settings from './Settings.svelte'
  import { OrbitControls, PerfMonitor } from '@threlte/extras'

  let billboarding = true
  let fps = 1
</script>

<div>
  <Canvas>
    <!-- <PerfMonitor /> -->

    <T.PerspectiveCamera
      makeDefault
      position.z={-80}
      position.y={10}
      position.x={10}
    >
      <OrbitControls />
    </T.PerspectiveCamera>

    <Scene
      {billboarding}
      {fps}
    />
  </Canvas>

  <Settings
    bind:billboarding
    bind:fps
  />
</div>

<style>
  div {
    height: 100%;
  }
</style>
s