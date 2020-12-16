<template>
    <div class="list1">
        <div class="list2" v-bind:key="step.name" v-for="step in steps">
            <StepItem v-bind:step="step" v-on:toggle-description="$emit('toggle-description', step.name)" />
        </div>
    </div>
</template>

<script>
import StepItem from './StepItem.vue'
export default {
    name: "Steps",
    components: {
        StepItem
    },
    props: ['steps']
}
</script>

<style scoped>
.list1{
    width: auto;
}
.list2{
    width: auto;
}
</style>