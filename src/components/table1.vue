<template>
    <tr class="element"
    @click="deleteUser(); addUser()"
    >
        <td class="id">{{users_data.id}}</td>
        <td class="name">{{users_data.name}}</td>
    </tr> 
</template>

<script>



export default {
   name: "table1",
   props:{
       users_data: {
           type: Object,
           default(){
               return {}
           }
       }
   },
   data(){
       return{}
   },
   methods:{
       deleteUser(){
           this.$emit('addUserT2', this.users_data)
           
           
       },
       addUser(){
           this.$emit('deleteUserT1', this.users_data)
           
       }
   }
    
    
    
}
</script>

<style>
th, td:first-child {
background: #AFCDE7;
color: white;
padding: 10px 10px;
}

td {
background: #faef52;
}

.element{
    cursor: pointer;
}

</style>