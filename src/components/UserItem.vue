<template>
    <div class="user">
        <div><strong>Имя: </strong> {{ user.userName }}</div>
        <div><strong>Фамилия: </strong> {{ user.userSurname }}</div>
        <div><strong>Отчество: </strong> {{ user.userLastname }}</div>
        <div><strong>Дата рождения: </strong> {{ user.dateOfBirth }}</div>
    </div>
</template>

<script script>

         defineProps({
            user:{
                type: Object,
                required: true,
            }
        })
    
</script>

<style scoped>

</style>