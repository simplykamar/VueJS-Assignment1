<script setup>
    import {reactive, ref} from 'vue'

    const listData = ref([])
    const formInput = ref(
        {
            id:null,
            item:'',
            isCompleted:false
        })
    let generateId = 0
    function add(){
        if (formInput.value.item.length > 0){
        formInput.value.id=generateId
        listData.value.push(formInput.value)
        generateId+=1
        formInput.value = {
            id:null,
            item:'',
            isCompleted:false
        }
    }
    }
    function removeItem(id){
        console.log(id)
        listData.value = listData.value.filter(item=>item.id!==id)
    }
    function markCompleted(id){
        console.log(listData.value)
        listData.value.forEach(item=>
            {
                if (item.id===id){
                    item.isCompleted = !item.isCompleted
                }
            }
        )
        console.log(listData.value)
    }
</script>

<template>
    <div class="container">
        <div class="container-wrapper">
        <header>
            <nav>
                <div class="navbar-brand">Todo App</div>
            </nav>
        </header>
        <main>  
            <div class="main-content">
                <ul class="task-items">
                    <li class="task-item" v-for="item in listData">
                        <div v-on:click="markCompleted(item.id)" v-bind:style="{fontSize:'14px', color:'blue',cursor:'pointer'}">Done</div> 
                        <div v-if="item.isCompleted"><s>{{item.item}}</s></div> 
                        <div v-else>{{item.item}}</div> 
                        <div v-on:click="removeItem(item.id)" v-bind:style="{fontSize:'14px', color:'red',cursor:'pointer'}">Delete</div></li>
                </ul>
                <input v-model="formInput.item"/><br>
                <button class="new-button" v-on:click="add">+ Add task</button>
            </div>
        </main>
    </div>
    </div>
</template>
<style scoped>
.container {
    background-color: #f4f4f9;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    font-family: 'Arial', sans-serif;
}

.container-wrapper {
    display: flex;
    flex-direction: column;
    background-color: white;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    border-radius: 10px;
    padding: 20px;
    max-width: 400px;
    width: 100%;
}

header > nav {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 50px;
    background-color: rgb(175, 126, 235);
    border-radius: 10px;
    color: white;
    font-size: 32px;
    margin-bottom: 20px;
    font-weight: bold;
}

.main-content {
    width: 100%;
}

.task-items {
    padding: 0;
    margin: 0;
}

.task-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 20px;
    list-style: none;
    margin-top: 15px;
    text-transform: capitalize;
    background-color: #e9e9f3;
    padding: 10px;
    border-radius: 5px;
    transition: background-color 0.3s ease;
}

.task-item:hover {
    background-color: #d1d1e0;
}

.new-button {
    background-color: rgb(175, 126, 235);
    color: white;
    font-size: 18px;
    border: 0;
    padding: 10px 20px;
    border-radius: 10px;
    margin-top: 20px;
    cursor: pointer;
    transition: background-color 0.3s ease;
}

.new-button:hover {
    background-color: rgb(145, 106, 205);
}

input {
    height: 30px;
    padding: 5px;
    font-size: 16px;
    width: calc(100% - 10px);
    border: 1px solid #ccc;
    border-radius: 5px;
    margin-top: 10px;
    margin-bottom: 10px;
    box-sizing: border-box;
}

.task-item > div {
    cursor: pointer;
}

.task-item > div:nth-child(1) {
    color: blue;
    font-size: 14px;
}

.task-item > div:nth-child(3) {
    color: red;
    font-size: 14px;
}

.task-item s {
    color: gray;
}

</style>
