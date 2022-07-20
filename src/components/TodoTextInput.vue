<template>
    <div class="center">

    <input
        v-model="inputText"
        @keydown.enter="addNewTodo"
        type="text"
        class="input-text"
        id="inputText"
        placeholder="Yapılacak işi yazınız..."
        >

    <button @click="addNewTodo" class="btn" style="padding: 24px 48px">Ekle</button>

  </div>
</template>

<script>
    export default {
        data() {
            return {
                inputText: null,
            }
        },

        methods: {
            addNewTodo() {
                this.$emit("add-todo", this.inputText)
                this.inputText = ""
            }
        }
    }
</script>