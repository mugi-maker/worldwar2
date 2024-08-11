<!--
	-	uses aseprite json loader
	- one sprite is WASD controlled
	- uses an untyped useInstancedSprie() hook in UpdaterWalking component
 -->

<script lang="ts">
  import { InstancedSprite, buildSpritesheet } from '@threlte/extras'
  import WalkingBehaviour from './WalkingBehaviour.svelte'

  export let billboarding = true
  export let fps: number

  const player = buildSpritesheet.fromAseprite(
    '/textures/player.json',
    '/textures/player.png'
  )
</script>

{#await player then spritesheet}
  <InstancedSprite
    {spritesheet}
    count={100}
    playmode={'FORWARD'}
    {fps}
    {billboarding}
    castShadow
  >
    <WalkingBehaviour />
  </InstancedSprite>
{/await}
