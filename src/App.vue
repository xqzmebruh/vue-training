<template>
  <div>
    <user-form @create="createUser" />
    <user-list :users="users" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import UserForm from './components/UserForm.vue'
import UserList from './components/UserList.vue'
const users = ref([
  {
    id: 1,
    userName: 'test',
    userSurname: 'testov',
    userLastname: 'testovich',
    dateOfBirth: '00.00.1989',
  },
])

const createUser = (user) => {
  users.value.push(user)
}
</script>

<style></style>
