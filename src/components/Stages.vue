<template>
    <div class="stages">
        <div class="stage stage-background-color" v-bind:key="stage.name" v-on:click="$emit('change-index', stage.index, $event.target)" v-for="stage in stages">
            <div class="stage-text">{{stage.name}}</div>
        </div>
    </div>
</template>

<script>
//import StageItem from './StepItem.vue'
export default {
    name: "Stages",
    components: {
        //StageItem
    },
    props: ['stages']
}
</script>

<style scoped>
.stages{
    display: flex;
    height: 60px;
    max-width: 100%;
    /* background-color: lightsalmon; */
    justify-content:space-between;
}
.stage{
    display: flex;
    /* padding: 5px 0px; */
    border-radius: 5px;
    width: 20%;
    font-size: 30px;
    font-weight: bolder;
    flex-grow: 1;
    align-items: center;
}
.stage:not(:last-child){
    margin-right: 3px;
}
.stage-background-color{
    background-color: #828cb9;
}
.stage-text{
    width: 100%;
    user-select: none;
    pointer-events: none;
}

</style>