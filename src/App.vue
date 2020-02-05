/* eslint-disable no-console */

<template>
 <div class="h-100 w-full flex items-center justify-center bg-teal-lightest font-sans">
   <div class="bg-white rounded shadow p-6 m-4 w-full lg:w-3/4 lg:max-w-lg">
     <loading :active.sync="isLoading"></loading>
     <AddTodos v-on:add-todo="addTodosdos"/>
      <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
    </div>
  </div>
</template>

<script>

import Todos from './components/Todos'
import AddTodos from './components/AddTodo'
import axios from 'axios'
import Loading from 'vue-loading-overlay';
import 'vue-loading-overlay/dist/vue-loading.css';

export default {
  name: 'app',
  components: {
    Todos,
    AddTodos,
    Loading
  },

  data() { 
  return { 
      todos:[ 
        
      ],
      isLoading: true,
      fullPage: true
    }
  },
  methods:{
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    },
    addTodosdos(item) {
       this.todos = [...this.todos, item]
    }
  },
  created(){

      axios.get('https://jsonplaceholder.typicode.com/todos?limit=5').then((result) => {
          this.todos = result.data
          this.isLoading = false
    }).catch(err => err)

  }
  
}
</script>



<style>

</style>
