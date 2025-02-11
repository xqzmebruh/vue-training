<template>
  <div class="user">
    <div><strong>Имя: </strong> {{ user.userName }}</div>
    <div><strong>Фамилия: </strong> {{ user.userSurname }}</div>
    <div><strong>Отчество: </strong> {{ user.userLastname }}</div>
    <div><strong>Дата рождения: </strong> {{ user.dateOfBirth }}</div>
  </div>
</template>

<script setup lang="ts">
interface User {
  id: number
  userName: string
  userSurname: string
  userLastname: string
  dateOfBirth: string
}

const props = defineProps<{
  user: User
}>()
</script>

<style scoped></style>
