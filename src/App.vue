<script setup>
import {
  computed,
  reactive,
} from 'vue';

const properties = reactive({
  perspective: 100,
  rotateX: 0,
  rotateY: 0,
  rotateZ: 0,
});

const reset = () => {
  properties.perspective = 100
  properties.rotateX = 0
  properties.rotateY = 0
  properties.rotateZ = 0
}

const box = computed(() => {
  return {
    transform: `
      perspective(${properties.perspective}px)
      rotateX(${properties.rotateX}deg)
      rotateY(${properties.rotateY}deg)
      rotateZ(${properties.rotateZ}deg)
    `
  }
});

</script>

<template>
  <section class="container bg-sky-300 p-20 mx-auto">
    <h1 class="text-2xl font-bold mb-20 text-center">Css Perspective</h1>
    <div class="grid grid-cols-2 gap-4">
      <div class="w-4/5">
        <label class="text-xl mb-1 font-bold block">
          Perspective: {{ properties.perspective }}px
        </label>
        <input
          class="mt-3 w-full"
          type="range"
          min="0"
          max="999"
          v-model="properties.perspective"
        />

        <label class="text-xl mt-8 mb-1 font-bold block">
          Rotate X: {{ properties.rotateX }}deg
        </label>
        <input
          class="mt-3 w-full"
          type="range"
          min="-360"
          max="360"
          v-model="properties.rotateX"
        />

        <label class="text-xl mt-8 mb-1 font-bold block">
          Rotate Y: {{ properties.rotateY }}deg
        </label>
        <input
          class="mt-3 w-full"
          type="range"
          min="-360"
          max="360"
          v-model="properties.rotateY"
        />

        <label class="text-xl mt-8 mb-1 font-bold block">
          Rotate Z: {{ properties.rotateZ }}deg
        </label>
        <input
          class="mt-3 w-full"
          type="range"
          min="-360"
          max="360"
          v-model="properties.rotateZ"
        />
      </div>


      <div class="w-4/5 text-center border-solid border-black border-2">
        <div v-bind:style="box" class="mx-auto mt-20 w-40 h-40 box bg-red-400"></div>
      </div>
    </div>


    <input
      @click.prevent="reset()"
      class="mt-10 bg-red-400 px-10 py-3 rounded-md cursor-pointer text-white font-semibold"
      type="submit"
      value="Reset"
    />
  </section>
</template>

<style scoped></style>
