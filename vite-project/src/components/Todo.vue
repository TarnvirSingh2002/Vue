<template>
    <h3>{{ todoString}}</h3>
    <form @submit.prevent = "endEditing()" class="flex-grow-1">
        <input @blur="startEditing()" v-model = "newTodoString" type="text" class="form-control"/>
    </form>
    <button @click="$emit('del')"> Delete</button>
    <button v-if="!isEditing" @click="startEditing()">Edit</button>
</template>

<script>
export default{ //all the things we write here used in this component only
    props:{
        todoString:String,
        complete:Boolean
    },
    data(){
        return{
            isEditing:false,
            newTodoString:""
        }
    },
    methods:{
        startEditing(){
            if(!this.isEditing){
                this.newTodoString=this.todoString;
                this.isEditing=true;
            }
            else{
                
                this.endEditing;
            }
        },
        endEditing(){
            this.isEditing = false;
            this.$emit('edit',this.newTodoString)
        }
    }
};
</script>

<style scoped>
h3{
    color:azure
}
</style>