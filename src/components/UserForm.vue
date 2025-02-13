<template>
  <div class="userform-wrapper">
    <div class="userform">
      <div class="textbox">
        <strong>Имя</strong>
        <input v-model="user.userName"
        class="inp"
        type="text"
        />
        <span v-if="errors.userName" class="error">{{ errors.userName }}</span>
      </div>
      <div class="textbox">
        <strong>Фамилия</strong>
        <input
          v-model="user.userSurname"
          class="inp"
          type="text"
        />
        <span v-if="errors.userSurname" class="error">{{ errors.userSurname }}</span>
      </div>

      <div class="textbox">
        <strong>Отчество</strong>
        <input
          v-model="user.userLastname"
          class="inp"
          type="text"
        />
        <span v-if="errors.userLastname" class="error">{{ errors.userLastname }}</span>
      </div>

      <div class="textbox">
        <strong>Дата рождения</strong>
        <input
          v-model="user.dateOfBirth"
          class="inp"
          type="date"
        />
        <span v-if="errors.dateOfBirth" class="error">{{ errors.dateOfBirth }}</span>
      </div>

      <button class="btn" @click="createUser">Создать</button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed } from '@vue/reactivity'
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

const errors = ref<Record<string, string>>({
  userName: '',
  userSurname: '',
  userLastname: '',
  dateOfBirth: '',
})

const validateFunc = (field: keyof User): string => {
  const value = user.value[field] as string

  if (!value.trim()) {
    return 'Поле обязательно для заполнения'
  }

  if (field !== 'dateOfBirth' && /\d/.test(value)) {
    return 'Поле недолжно содержать цифр'
  }

  return ''

}

const isFormValid = (): boolean => {
  let isValid = true

  Object.keys(user.value).forEach((field) => {
    const error = validateFunc(field as keyof User)
    errors.value[field] = error

    if (error && field !== 'dateOfBirth') {
      isValid = false
    }
})
  return isValid
}

const emit = defineEmits<{ create: [User] }>()

const createUser = () => {
  if (!isFormValid()) return

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

.btn:hover {
  cursor: pointer;
  border: 1px solid forestgreen;
  color: black;
}

.inp {
  border: 1px solid teal;
  padding-bottom: 3px;
  padding-top: 3px;
}
.error {
  color: red;
  font-size: 1em;
}
</style>
