<script lang="ts">
	import { T } from '@threlte/core'
    import { OrbitControls, Float, Text } from '@threlte/extras';
    import Hearts from './Hearts.svelte';
	export let autoRotate: boolean
	export let enableDamping: boolean
	export let rotateSpeed: number
	export let zoomToCursor: boolean
	export let zoomSpeed: number
	export let minPolarAngle: number
	export let maxPolarAngle: number
	export let enableZoom: boolean

    const urlParams = new URLSearchParams(window.location.search);
    const nameTo = urlParams.get('nameTo')
    const nameFrom = urlParams.get('nameFrom')
</script>

<Text
  text={`Для: ${nameTo ? nameTo : 'Вас'}`}
  fontSize={0.4}
  textAlign={'start'}
  color='red'
  position={[-1.8, 4, 0]}
/>

<Text
  text={`От: ${nameFrom ? nameFrom : 'honddk'}`}
  fontSize={0.5}
  color='red'
  textAlign={'start'}
  position={[0, -3, 0]}
/>

<T.PerspectiveCamera
  makeDefault
  position={[0, 3, 10]}
>
  <OrbitControls
    {enableDamping}
    {autoRotate}
    {rotateSpeed}
    {zoomToCursor}
    {zoomSpeed}
    {minPolarAngle}
    {maxPolarAngle}
    {enableZoom}
  />
</T.PerspectiveCamera>

<Float
  floatIntensity={1}
  rotationIntensity={1}
  rotationSpeed={[8, 3, 4]}
>
  <Hearts/>
</Float>

