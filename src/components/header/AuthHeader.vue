<template>
  <header class="d-flex justify-content-end align-items-center">
    <div>here will be the status</div>
    <b-form-input type="text" placeholder="Введите логин"
    ></b-form-input>
    <b-form-input type="password" placeholder="Введите пароль"></b-form-input>
    <b-btn pill variant="primary">Войти</b-btn>
    <b-btn pill variant="secondary">Зарегистрироваться</b-btn>
  </header>
</template>

<script>
export default {
  name: "AuthHeader"
};
</script>

<style scoped></style>
