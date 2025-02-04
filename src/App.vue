<template>
 <div class="userform-wrapper">
        <div class="userform">
    <div class="textbox"><strong>Имя</strong>
    <form action="">
        <input class="inp" type="text">
    </form></div>
    <div class="textbox"><strong>Фамилия</strong>
    <form action="">
        <input class="inp" type="text">
    </form></div>
    <div class="textbox"><strong>Отчество</strong>
    <form action="">
        <input class="inp" type="text">
    </form></div>
    <div class="textbox"><strong>Дата рождения</strong>
    <form action="">
        <input class="inp" type="text">
    </form></div>
    <button class="btn">Создать</button>
    
    <div></div>

</div>
</div>
</template>

<script>

</script>

<style>
.textbox {
    margin-top: 3px;
    margin-bottom: 3px;
    
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
</style>