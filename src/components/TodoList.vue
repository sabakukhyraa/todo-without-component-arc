<template>

    <!-- <div class="todo-s">
        <ul>
            <li class="todo" v-for="todoItem in todoList" :key="todoItem.id" :class=" {'bg-green' : todoItem.checked, 'bg-red' : !todoItem.checked} ">
                <div class="center">
                <input class="check" type="checkbox" :id="todoItem.id" v-model="todoItem.checked">
                <label class="todo-text" :for="todoItem.id">{{ todoItem.text }}</label>
                </div>
                <button @click="deleteItem(todoItem.id)" class="btn">Sil</button>
            </li>
        </ul>
    </div>         -->
    <div class="todo-s">
        <ul>
            <li class="todo" v-for="todoItem in itemList" :key="todoItem.id" :class=" {'bg-green' : todoItem.checked, 'bg-red' : !todoItem.checked} ">
                <div class="center">
                    <input class="check" type="checkbox" :id="todoItem.id" @change="$emit('instant-check', todoItem.id)">
                    <label class="todo-text" :for="todoItem.id">{{ todoItem.text }}</label>
                </div>
                <button @click="deleteItem(todoItem.id)" class="btn">Sil</button>
            </li>
        </ul>
    </div>        
    
</template>

<script>
    export default {
        data() {
            return {
                instantChecked: false,
            }
        },
        props: ["itemList"],
        inject : ["todoList", "deleteItem"],
    }

    
</script>