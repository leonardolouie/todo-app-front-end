<template>
   <div class="flex mb-4 items-center">
      <p class="w-full text-grey-darkest" v-bind:class="{'line-through text-green' : todo.completed}">{{todo.title}}</p>
      <button @click="markComplete"  class="flex-no-shrink p-2 ml-4 mr-2 border-2 rounded hover:text-white text-green border-green hover:bg-green" v-if="!todo.completed">Done</button>
      <button @click="markComplete"  class="flex-no-shrink p-2 ml-4 mr-2 border-2 rounded hover:text-white text-grey border-grey hover:bg-grey" v-if="todo.completed">Not Done</button>
     
      <button  @click="$emit('del-todo',  todo.id)" class="flex-no-shrink p-2 ml-2 border-2 rounded text-red border-red hover:text-white hover:bg-red">Remove</button>
  </div>

</template>

<script>
export default {
 name:'TodoItem',
 props:["todo"],
 methods:{
   markComplete(){
     this.todo.completed = !this.todo.completed
   }
 }
 
}
</script>


<style scoped>


</style>