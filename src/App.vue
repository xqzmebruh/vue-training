<template>
<div>
    <user-form 
    @create="createUser"
    />
    <user-list 
    :users="users"
    />
</div>
</template>

<script>
import UserForm from './components/UserForm.vue';
import UserList from './components/UserList.vue';
export default{
    components: {
        UserForm,UserList
    },
 data() {
     return{
         users :[
             {id: 1, userName: 'test', userSurname: 'testov', userLastname: 'testovich', dateOfBirth: '00.00.1989'}
         ],
     }
 },
  methods: {
        createUser(user){
            this.users.push(user);
        },
       
     }
}
</script>

<style>

</style>