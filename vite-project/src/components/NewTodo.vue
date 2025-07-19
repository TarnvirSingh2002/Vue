<template>
   <form @submit.prevent="addtodo">
        <input v-model="newTodoo" type="text" placeholder="Enter something in this"/>
   </form>
</template>

<script>
export default{
    data(){
        return {
            newTodoo:""
        }
    },
    methods:{
        addtodo(){
            if(this.newTodoo.length>2){
                this.$emit("addtodo",this.newTodoo)
            }
            this.newTodoo=""
        }
    }

}
</script>

<style>

</style>