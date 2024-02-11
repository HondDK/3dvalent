<script>
  import { Group } from 'three'
  import { T, forwardEventHandlers } from '@threlte/core'
  import {useGltf, FakeGlowMaterial } from '@threlte/extras'
  export const ref = new Group()

  const gltf = useGltf('/jar_of_hearts.glb', { useDraco: true })
  const component = forwardEventHandlers()
</script>

<T is={ref} dispose={false} {...$$restProps} bind:this={$component}>
  {#await gltf}
    <slot name="fallback" />
  {:then gltf}
    <T.Group  rotation={[-Math.PI / 2, 0, 0]} scale={1.1} position={[0 ,-1.7 ,0]} >
      <T.Mesh geometry={gltf.nodes.Object_2.geometry} material={gltf.materials.Heart_UVlambert2SG} >
        <FakeGlowMaterial glowInternalRadius={5.0} glowSharpness={7.0} falloff={0.1}  glowColor="red"/>
      </T.Mesh>
      <T.Mesh geometry={gltf.nodes.Object_3.geometry} material={gltf.materials.Heart_UVlambert2SG} >
        <FakeGlowMaterial glowInternalRadius={5.0} glowSharpness={7.0} falloff={0.1} glowColor="red"/>
      </T.Mesh>
      <T.Mesh geometry={gltf.nodes.Object_5.geometry} material={gltf.materials.lambert2SG}/>
      <T.Mesh geometry={gltf.nodes.Object_6.geometry} material={gltf.materials.lambert2SG} />
      <T.Mesh geometry={gltf.nodes.Object_8.geometry} material={gltf.materials.lambert4SG} />
    </T.Group>
  {:catch error}
    <slot name="error" {error} />
  {/await}
  <slot {ref} />
</T>


