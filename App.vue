<template>
  <view class="container">
    <Statusbar />
    <Header title="Task List" />

    <view class="inputContainer" >
      <text-input class="input" v-model="newTodoText" placeholder="Adicionar" />           
      <touchable-opacity class="add-btn" :on-press="newTodo" >                   
        <Text class="btn-text"> ADD </Text>
      </touchable-opacity> 
    </view>

    <view class="todo" v-for="todo in todos" :key="todo.id">
      <touchable-opacity :on-press="() => toggleDone(todo.id)" >
        <text class="todo-text done" v-if="todo.done">{{todo.title}}</text>
        <text class="todo-text" v-else>{{todo.title}}</text>
      </touchable-opacity>

      <touchable-opacity class="remove-btn" :on-press="() => removeTodo(todo.id)">
        <text  class="remove-btn-text" >REMOVE</text>
      </touchable-opacity>
    </view>
  </view>  
</template>

<script>
import Statusbar from './components/Statusbar';
import Header from './components/Header';

import lixeira from './assets/lixeira.png'

console.disableYellowBox = true;

export default {

  data () {
    return {
      newTodoText: '',
    
      todos: [
        {
        id: 0,
        title: 'Remove sample text',
        done: false,
        
      }
    ]
    }
  },
  components: {
    Statusbar,
    Header,

  },
  methods: {
    newTodo () {
      this.todos.push({
        id: this.todos.length + 1,
        title: this.newTodoText,
        done: false
      });

      this.newTodoText = '';
    },
    toggleDone (id) {
     this.todos = this.todos.map(todo => {
       if(todo.id === id) 
        todo.done = !todo.done;
          return todo;
     })
    },
    removeTodo (id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    }
  }
}

</script>

<style>
.container {
  background-color: rgb(243, 243, 243);
  flex: 1;
}

.inputContainer {

  flex-direction: row;
  justify-content: center;
  align-items: stretch;
}

.input {
  flex: 1;
  height: 50px;
  background-color: #b6b6b6;
  font-size: 18px;
  color: rgb(49, 170, 218);
 
  

}

.add-btn {
  width: 100px;
  height: 50px;
  background-color: rgb(14, 69, 95);
  justify-content: center;
  align-items: center;
}

.btn-text {
  font-size: 20px;
  font-weight: 700;
  color: rgb(255, 255, 255);

}

.todo {
  flex-direction: row;
  justify-content: space-between;
  padding: 15px;
  background-color: rgb(224, 233, 233)
}

.todo-text {
  font-size: 18px;

}

.done {
  color: rgb(255, 255, 255);
  
}

.remove-btn-text {
  font-size: 18px;
  color: #44C9E1;

}

</style>
