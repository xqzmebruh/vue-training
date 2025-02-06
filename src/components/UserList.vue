<template>
    <div>
        <h3>Список пользователей</h3>
        <user-item 
        v-for="user in users" 
        :key="user.id"
        :user="user"
        />
    </div>
    
</template>

<script>
import UserItem from './UserItem.vue';
    export default {
        components: {UserItem},
        props:{
            users:{
                type: Array,
                required: true
            }
        }
    }
</script>

<style scoped>
.user{
    padding: 10px;
    margin-top: 10px;
    border: 1px solid teal;
}
</style>