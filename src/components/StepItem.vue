<template>
    <div class="step-item">
        <div class="title" v-on:click="$emit('toggle-description', step.name)">
            {{step.name}}
        </div>
        <div class="description" v-bind:class="{'hide':step.hiddenDescription}">
            <span v-html="step.description"></span>
            <!-- {{step.description}} -->
        </div>
    </div>
</template>

<script>
export default {
    name: "StepItem",
    props: ["step"]
}
</script>

<style scoped>
.step-item{
    max-width: 600px;
    margin-top: 5px;
    margin-left: 0px;
    margin-right: 0px;
}

.title{
    background: #9ea7d8;
    border-radius: 5px;
    padding: 10px;
    position: relative;
    font-size: 30px;
    user-select: none;
    z-index: 1;
}
.description{
    background: #d0d8ff;
    border-radius: 5px;
    padding: 15px 10px 5px 10px;
    margin-top: -10px;
    position: relative;
    z-index: 0;
    font-size: 20px;
}

.hide{
    display: none;
}
</style>