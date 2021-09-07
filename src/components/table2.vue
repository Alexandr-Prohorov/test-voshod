<template>
    <tr class="element"
    @click="addUser(); deleteUser()"
    >
        <td class="id">{{users_data.id}}</td>
        <td class="name">{{users_data.name}}</td>
    </tr>
</template>

<script>


export default {
   name: "table2",
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
           this.$emit('addUserT1', this.users_data)
           
           
       },
       addUser(){
           this.$emit('deleteUserT2', this.users_data)
           
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