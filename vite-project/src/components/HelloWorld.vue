<template>
  <h1>Hello world</h1>
  <h3>your Todos</h3>
  <div>
    <p v-for="(todo, index) in todos":key="index">{{index, todo.toString}} </p>
  </div>
</template>

<script>
  export default{
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
    }
  }
</script>

<style>
h1{
  color:blue;
}
</style>