<template>
    <div class="userform-wrapper">
        <div class="userform">
            <div class="textbox"><strong>Имя</strong>
            
                <input
                @input="userName = $event.target.value" 
                v-bind:value="userName" 
                class="inp" 
                type="text"
                >
            
            </div>
            <div class="textbox"><strong>Фамилия</strong>
            
                <input 
                @input="userSurname = $event.target.value"
                v-bind:value="userSurname" 
                class="inp" 
                type="text"
                >
            
            </div>
            <div class="textbox"><strong>Отчество</strong>
            
                <input 
                @input="userLastname = $event.target.value"
                v-bind:value="userLastname" 
                class="inp" 
                type="text"
                >
            
            </div>
            <div class="textbox"><strong>Дата рождения</strong>
            
                <input 
                @input="dateOfBirth = $event.target.value"
                v-bind:value="dateOfBirth" 
                class="inp" 
                type="text"
                >
            
            </div>

            <button class="btn" @click="createUser">Создать</button>
        </div>
    </div>

    <div class="user" v-for="user in users" :key="user.id">
        <div><strong>Имя: </strong> {{ user.userName }}</div>
        <div><strong>Фамилия: </strong> {{ user.userSurname }}</div>
        <div><strong>Отчество: </strong> {{ user.userLastname }}</div>
        <div><strong>Дата рождения: </strong> {{ user.dateOfBirth }}</div>
    </div>



</template>

<script>
export default{
 data() {
     return{
         users :[
             {id: 1, userName: 'test', userSurname: 'testov', userLastname: 'testovich', dateOfBirth: '00.00.1989'}
         ],
         userName: '',
         userSurname: '',
         userLastname: '',
         dateOfBirth: '',
     }
 },
  methods: {
        createUser(){
            const newUser = {
                id: Date.now(),
                userName: this.userName,
                userSurname: this.userSurname,
                userLastname: this.userLastname,
                dateOfBirth: this.dateOfBirth
            }
            this.users.push(newUser)
            this.userName = '';
            this.userSurname = '';
            this.userLastname = '';
            this.dateOfBirth = '';
        },
       
     }
}
</script>

<style>
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
.inp{
    border: 1px solid teal;
    padding-bottom: 3px;
    padding-top: 3px;
}

.user{
    padding: 10px;
    margin-top: 10px;
    border: 1px solid teal;
}
</style>