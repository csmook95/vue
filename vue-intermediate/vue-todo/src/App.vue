<template>
  <div id="app">
    <todo-header></todo-header>
    <todo-input v-on:addTodoItem="addOneItem"></todo-input>
    <todo-list v-bind:propsData="todoItems" 
    v-on:removeTodoItem="removeOneItem" 
    v-on:toggleComplete="toggleOneComplete"></todo-list>
    <todo-footer
    v-on:clearAll="clearAllItems"></todo-footer>
  </div>
</template>

<script>
import TodoFooter from './components/TodoFooter.vue'
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'

export default {
  data(){
    return {
      todoItems:[]
    }
  },

  methods:{
    addOneItem(todoItem){
      if(todoItem !==''){
        var obj = {completed: false, item: todoItem}
        localStorage.setItem(todoItem, JSON.stringify(obj)); 
        this.todoItems.push(obj)
      }
    },
    removeOneItem(todoItem, index){
      localStorage.removeItem(todoItem.item)
      this.todoItems.splice(index, 1)
    },
    toggleOneComplete(todoItem, index){
      this.todoItems[index].completed=!this.todoItems[index].completed
      localStorage.removeItem(todoItem.item);
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
    },
    clearAllItems(){
      localStorage.clear();
      this.todoItems=[];
    }
  },

  components: { TodoHeader, TodoList, TodoFooter, TodoInput },
  
  created(){
    if(localStorage.length >0){
      for(var i=0; i< localStorage.length ; i++){
        if(localStorage.key(i) !=="loglevel:webpack-dev-server"){
          this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))))
        }
      }
    }
  }
}
</script>

<style>
body{
  font-family: 'Ubuntu', sans-serif;
  text-align: center;
  background-color: #f6f6f6;
}

input{
  border-style: groove;
  width: 200px;
}

button{
  border-style: groove;
}

.shadow{
  box-shadow: 5px 10px 10px rgda(0,0,0,0.03);
}
</style>
