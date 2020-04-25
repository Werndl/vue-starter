<template>
  <div>
    <h1>Twój email to: {{ email }}</h1>
    <input type="text" v-model="email">
    <button @click="alertMyEmail()">Wyświetl mój e-mail w alercie</button>

    <div v-if="email.length < 10">Ale masz krótki adres!</div>
    <div v-else-if="email.length < 15">Twój adres e-mail jest w sam raz.</div>
    <div v-else>Twój adres e-mail jest stanowczo za długi.</div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        email: ''
      };
    },
    methods: {
      alertMyEmail() {
        alert(this.email);
      }
    }
  }
</script>

<style>
</style>
