<template>
  <div id="app">
    <table class="table-1">
      <tr>
        <th class="id">id</th>
        <th class="users">users</th>
      </tr>
      <table1 
      v-for="(user, index) in usersTable1" :key="user.id"
      v-bind:users_data="user"
      @addUserT2="addUserToTable2"
      @deleteUserT1="deleteUserToTable1(index)"
      />
    </table>
    <table class="table-2">
      <tr>
        <th class="id">id</th>
        <th class="users">users</th>
      </tr>
      <table2 
      v-for="(user, index) in usersTable2" :key="user.id"
      v-bind:users_data="user"
      @addUserT1="addUserToTable1"
      @deleteUserT2="deleteUserToTable2(index)"
      />
    </table>
  </div>
</template>

<script>
import table1 from './components/table1.vue'
import table2 from './components/table2.vue'
import axios from 'axios'

export default {
  data(){
    return{
            usersTable1:[],
            usersTable2:[
              {
                id: '1',
                name: 'Andrey'
            },
            {
                id: 2,
                name: 'Vladimir'
            },
            {
                id: 3,
                name: 'Sergey'
            },
            {
                id: 4,
                name: 'Alexandr'
            },
            {
                id: 5,
                name: 'Konstantin'
            }]
        }
  },
  components:{
    table1,
    table2
  },
  async mounted(){
        const res = axios.get('http://localhost:3000/users')
        this.usersTable1 = (await res).data
  },
  methods:{
    addUserToTable2(data){
      this.usersTable2.push(data)
      
    },
    deleteUserToTable1(index){
      this.usersTable1.splice(index, 1)
    },
    addUserToTable1(data){
      this.usersTable1.push(data)
      
    },
    deleteUserToTable2(index){
      this.usersTable2.splice(index, 1)
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 100px;
  display: flex;
}

.id{
  background: #AFCDE7;
  color: white;
  padding: 10px 10px;
  width: 50px;
}

.users{
  background: #AFCDE7;
  color: white;
  padding: 10px 10px;
  width: 100px;
}

.table-1{
  margin-left: 20%;
}
.table-2{
  margin-left: 20%;
}

</style>
