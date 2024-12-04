<script setup>
    import {ref} from 'vue'

    const activeColor = ref('')
    const colors = [
        'red',
        'blue',
        'yellow',
        'black'
    ]
</script>
<template>
    <h1 :style="{'color':activeColor}">Hello Deepak Sir.</h1>
    <p>Selected color is <span v-bind:style="{'color':activeColor}">{{ activeColor.toUpperCase() }}</span></p>
    <select v-model="activeColor">
        <option value="" disabled>Select your color</option>
        <option v-for="color in colors">{{ color }}</option>
    </select>
</template>

<style scoped>
    h1{
        text-align: center;
    }
</style>