<script setup>
    import {ref} from 'vue'

    const name =  ref('')

    function clear() {
        name.value = '';
    }
    function toUppercase() {
        console.log("uppercase fn")
        name.value = name.value.toUpperCase();
    }

</script>
<template>
    <main>
        <h1>Hello Vue My name is: {{ name }}</h1>
        <input :value="name" v-model="name"/>
        <div>
            <button @click="clear">Clear</button>
            <button @click="toUppercase">UppperCase</button>
        </div>
    </main>
</template>

<style scoped>
    main{
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column
    }
    main > h1{
        color: red
    }
    main  button{
        margin:10px;

    }
</style>