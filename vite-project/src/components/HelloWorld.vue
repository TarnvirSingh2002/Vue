<template>
  <div id="divv">
    <h1>Hello world</h1>
    <h3>your Todos</h3>
    <div>
      <!--here we pass the props -->
      <NewTodo  @addtodo="addTodo"/>
      <Todo v-for="(todo, index) in todos"
        :key="index" 
        :todoString="todo.toString"
        :complete="todo.complete"
        @del="removeTodo(todo)"
        @edit="editTodo(index, $event)",
      />
    </div>
  </div>
</template>

<script>
import NewTodo from './NewTodo.vue';
import Todo from './Todo.vue';
  export default{
  components: {
    Todo,
    NewTodo
  },
    data(){
      return {
        todos:[
          {toString:"make angular", complete:false},
          {toString:"make tang", complete:true},
          {toString:"make food", complete:false},
          {toString:"make king", complete:true},
        ]
      }
    },
    methods:{
      editTodo(index,newToString){
        this.todos[index].toString=newToString;
      },

      removeTodo(deletetodo){
        this.todos = this.todos.filter(ele=> ele.toString!=deletetodo.toString);
      },

      addTodo(newToString){
        this.todos.push({
          toString:newToString,
          complete:false
        })
      }
    },
  }
</script>

<style scoped>
#divv{
  background-color: grey;
}
h1{
  color:blue;
}
</style>