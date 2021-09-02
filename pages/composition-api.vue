<template>
    <div>
      <h1>{{ state.text }}</h1>
      <p>{{ state.count }}</p>
      <v-btn @click="changeText" >button</v-btn>
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent, reactive, toRef } from '@nuxtjs/composition-api'
  
  interface State {
    text: string
    count: number
  }
  
  export default defineComponent({
    setup() {
      const state = reactive<State>({
        text: 'Hello, World!',
        count: 0,
      })
  
      const count = toRef(state, 'count')
      // or
      //const { count } = toRefs(state)
  
      function changeText(): void {
        state.text='Hello, Nuxt!'
        count.value++
      }
  
      return {
        state,
        changeText,
      }
    },
  })
  </script>
