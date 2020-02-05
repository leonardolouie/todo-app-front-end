<template>
 <div class="mb-4">
            <h1 class="text-grey-darkest text-xl font-bold">Todo List</h1>
            <div class="flex mt-4">
                <input v-model="title" class="shadow appearance-none border rounded w-full py-2 px-3 mr-4 text-grey-darker" placeholder="Add Todo">
                <button class="flex-no-shrink p-2 border-2 rounded text-teal border-teal hover:text-white hover:bg-teal" @click="addTodo">Add</button>
            </div>
        </div>
</template>


<script>
import uuid from 'uuid'
export default {
    name:'AddTodo',
    data() {
        return {
            title:''
        }
    },
    methods: {
        addTodo(){
            const newTodo = { 
                id:uuid.v4(),
                title:this.title,
                completed:false
            }

            this.title=''
            this.$emit('add-todo', newTodo)
        }
        
    }
}
</script>

<style scoped>
  

</style>