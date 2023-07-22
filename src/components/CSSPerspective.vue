<script setup>
import {ref, reactive, computed} from 'vue'

  let initialProperties = reactive({
    perspective: 100,
    rotateX: 0,
    rotateY: 0,
    rotateZ:0
  })

  const reset = function(){
    initialProperties.perspective = 100,
    initialProperties.rotateX = 0,
    initialProperties.rotateY = 0,
    initialProperties.rotateZ = 0
  }

  const boxStyle = computed(function(){
    return { transform:`
        perspective(${initialProperties.perspective}px)
        rotateX(${initialProperties.rotateX}deg)
        rotateY(${initialProperties.rotateY}deg)
        rotateZ(${initialProperties.rotateZ}deg)
      `}
  })
</script>

<template>
  <h1 style="color: white; align-items: center;">CSS Perspective Playground</h1>
  <main>
    <section class="settings">
      <div class="settings-container">
        <label>perspective: {{ initialProperties.perspective }}px;</label>
        <input type="range" min="0" max="999" v-model="initialProperties.perspective" />

        <label>rotateX: {{ initialProperties.rotateX }}deg; </label>
        <input type="range" min="-180" max="180" v-model="initialProperties.rotateX" />

        <label>rotateY: {{ initialProperties.rotateY }}deg; </label>
        <input type="range" min="-180" max="180" v-model="initialProperties.rotateY" />

        <label>rotateZ: {{ initialProperties.rotateZ }}deg; </label>
        <input type="range" min="-180" max="180" v-model="initialProperties.rotateZ" />

        <button type="button" @click.prevent="reset">Reset</button>       
      
      </div>
    </section>
    <section class="output">
      <div class="box-container">
        <div class="box" :style="boxStyle"></div>
      </div>
    </section>
  </main>
</template>

<style scoped>
  
</style>
