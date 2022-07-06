<template>
  <h1>To Do List</h1>
  <input 
  @keydown.enter="addNewTodo"
  type="text" 
  class="input-text" 
  id="inputText"
  placeholder="Yapılacak işi yazınız..."
  >

  <div class="todo-s">
    <ul>
      <li class="todo" v-for="todoItem in todoList" :key="todoItem.id" :class=" {'bg-green' : todoItem.checked, 'bg-red' : !todoItem.checked} ">
        <div class="center">
          <input class="check" type="checkbox" id="check" v-model="todoItem.checked">
          <label class="todo-text" for="check">{{ todoItem.text }}</label>
        </div>
        <button @click="deleteItem(todoItem.id)" class="btn">Sil</button>
      </li>
    </ul>
  </div>
  <div class="counter">
    <div>
      <small class="green">Tamamlanan: {{ completedItemCount }}</small>
      <small class="red">Tamamlanmamış: {{ unCompletedItemCount }}</small>
    </div>
    <small>Şuanda {{ todoList.length }} TODO var.</small>
  </div>
</template>



<script>
export default {
  data() {
    return {
      todoList : [],
      count : 1,
      inputText : ""
    }
  },

  methods : {
    addNewTodo(event) {
      this.todoList.push({
        id : new Date().getTime(),
        text : event.target.value,
        checked : false
        }
      )
      event.target.value = ""
      console.log(this.todoList)
    },


    deleteItem(id) {
      this.todoList = this.todoList.filter(
        (i) => i.id !== id
      )
    }
  },


  computed : {
    completedItemCount () {
      return this.todoList.filter((i) => i.checked).length
    },
    unCompletedItemCount () {
      return this.todoList.filter((i) => !i.checked).length
    }
  },

}

</script>



<style>

@import url('https://fonts.googleapis.com/css2?family=Oswald:wght@200;300;400;500;600;700&display=swap');


body{
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgb(234, 250, 255);
  font-family: 'Oswald', Avenir, Helvetica, Arial, sans-serif;
}


#app {
  font-family: 'Oswald', Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 2rem;
  width: 50%;
  border: solid 2px black;
  border-radius: 6px;
}


h1 {
  font-size: 4rem;
  margin: 1rem;
}


.input-text {
  width: 80%;
  font-size: 2rem;
  padding: 12px 20px;
  margin: 4px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-sizing: border-box;
}


.todo-s {
  font-size: x-large;
  margin: .5rem 0;
}



.todo-text {
  margin-left: 6px;
  cursor: pointer;
}

.todo {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 0;
  list-style: none;
  border-bottom: .5px solid gray;
}


.todo-s ul {
  text-align: start;
}


.counter {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.counter div {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
  margin: 0 0 1rem 1rem;
}


.counter small {
  margin-right: 6px;
}


small {
  font-size: 1.2rem;
}

.btn {
  padding: .70rem 1.5rem;
  border: 0;
  background-color: rgb(255, 50, 60);
  color: white;
  font-weight: 700;
  border-radius: 1rem;
  cursor: pointer;
  margin: 0 .3rem;
  transition: all 400ms;
}


.btn:hover {
  background-color: rgb(200, 25, 25);
  box-shadow: 0px 5px 20px -10px rgba(0,0,0,0.75);
}


.check {
  width: 1.5rem;
  height: 1.5rem;
}


.check:checked {
  filter: sepia(100%) brightness(80%) hue-rotate(170deg) saturate(70%) contrast(300%);
}


.center {
  display: flex;
  justify-content: center;
  align-items: center;
}


.bg-red {
  background-color: rgb(255, 220, 220);
}


.bg-green {
  background-color: rgb(220, 255, 220);
}

.red {
  color: red;
}

.green {
  color: green;
}

</style>