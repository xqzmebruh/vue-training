<template>
  <div class="userform-wrapper">
    <div class="userform">
      <div class="textbox">
        <strong>Имя</strong>

        <input v-model="user.userName" class="inp" type="text" />
      </div>
      <div class="textbox">
        <strong>Фамилия</strong>

        <input v-model="user.userSurname" class="inp" type="text" />
      </div>
      <div class="textbox">
        <strong>Отчество</strong>

        <input v-model="user.userLastname" class="inp" type="text" />
      </div>
      <div class="textbox">
        <strong>Дата рождения</strong>

        <input v-model="user.dateOfBirth" class="inp" type="text" />
      </div>

      <button class="btn" @click="createUser">Создать</button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

interface User {
  id?: number
  userName: string
  userSurname: string
  userLastname: string
  dateOfBirth: string
}

const user = ref<User>({
  userName: '',
  userSurname: '',
  userLastname: '',
  dateOfBirth: '',
})

const emit = defineEmits<{ createUser: [User] }>()

const createUser = () => {
  user.value.id = Date.now()
  emit('create', user.value)
  user.value = {
    userName: '',
    userSurname: '',
    userLastname: '',
    dateOfBirth: '',
  }
}
</script>

<style scoped>
.textbox {
  margin-top: 3px;
  margin-bottom: 3px;
  display: flex;
  flex-direction: column;
}
.userform-wrapper {
  display: flex;
  justify-content: center;
}
.userform {
  display: flex;
  flex-direction: column;
  padding: 10px;
  border: 1px solid teal;
}
.btn {
  margin-top: 10px;
  padding: 5px;
  align-self: end;
  border: 1px solid teal;
  background: none;
  color: teal;
}
.inp {
  border: 1px solid teal;
  padding-bottom: 3px;
  padding-top: 3px;
}
</style>
