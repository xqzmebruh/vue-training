<template>
  <div>
    <h3>Список пользователей</h3>
    <UserItem v-for="user in users" :key="user.id" :user="user" />
  </div>
</template>

<script setup lang="ts">
import UserItem from './UserItem.vue'

interface User {
  id: number
  userName: string
  userSurname: string
  userLastname: string
  dateOfBirth: string
}

const props = defineProps<{
  users: User[]
}>()
</script>

<style scoped>
.user {
  padding: 10px;
  margin-top: 10px;
  border: 1px solid teal;
}
</style>
