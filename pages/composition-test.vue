<template>
    <div>
        <h1>{{ state.text }}</h1>
        <p>{{ state.count }}</p>
        <v-btn color="success" @click="changeText">button</v-btn>
    </div>
</template>

<script lang="ts">
import { defineComponent , reactive, toRef} from '@vue/composition-api'

interface State {
    text : string
    count : number
}

export default defineComponent({
    setup() {
        const state = reactive<State>({
            text : 'hello, Nuxt!',
            count : 0
        })

        const count = toRef(state,'count')
        // or
        //const { count } = toRefs(state)

        function changeText(): void {
            state.text = 'hello, composition api!'
            count.value++;
        }

        return{
            state,
            changeText
        }
    },
})
</script>
