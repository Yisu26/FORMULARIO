<template>
    <div class="container">
      <div class="row">
        <div class="col">
          <div class="card">
            <div class="card-body">
              <h2 class="card-title">Iniciar Sesión</h2>
              <hr class="hr">
              <label for="email">Correo electrónico</label>
              <input type="text" class="form-control" v-model="email">
              <span v-if="errorEmail" class="text-danger">Este campo es requerido</span>
              <label for="password">Contraseña</label>
              <input type="password" class="form-control" v-model="password">
              <span v-if="errorPassword" class="text-danger">Este campo es requerido</span>
              <hr class="hr">
              <button type="button" class="btn btn-primary" @click="login">Iniciar Sesión</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent } from 'vue';
  
  export default defineComponent({
    data() {
      return {
        email: '',
        password: '',
        errorEmail: false,
        errorPassword: false,
      };
    },
    methods: {
      login() {
        this.errorEmail = this.email === '';
        this.errorPassword = this.password === '';
  
        if (!this.errorEmail && !this.errorPassword) {
          console.log('Iniciando sesión con:', this.email, this.password);
          this.$router.push('/');
        }
      }
    }
  });
  </script>
  
  <style scoped>
  .container {
    display: flex;
    justify-content: center;
    max-width: 350px;
    margin: 0 auto;
    padding: 20px;
    font-family: 'DM Sans', sans-serif;
    background-color: gray;
    border-radius: 10px;
    box-shadow: 0px 0px 15px rgba(0, 0, 0, 0.1);
  }
  
  .card {
    background-color: #ffffff;
    border: none;
    border-radius: 10px;
    box-shadow: 0px 0px 15px rgba(0, 0, 0, 0.1);
    padding: 20px;
    width: 300px;
  }
  
  .card-title {
    font-size: 24px;
    font-weight: bold;
    color: #333333;
    margin-bottom: 15px;
    text-align: center;
  }
  
  .hr {
    border: 1px solid #ddd;
    margin: 15px 0;
  }
  
  label {
    font-weight: 600;
    color: #555555;
    margin-top: 10px;
    display: block;
  }
  
  input[type="text"], input[type="password"] {
    width: 200px;
    padding: 10px;
    margin: 5px 0 15px 0;
    border-radius: 20px;
    border: 3px solid #000000;
    box-shadow: inset 0px 0px 5px rgba(0, 0, 0, 0.05);
    transition: all 0.3s ease;
    background-color: white;
    color: black;
  }
  
  input[type="text"]:focus, input[type="password"]:focus {
    border-color: #007bff;
    box-shadow: 0px 0px 8px rgba(0, 123, 255, 0.2);
  }
  
  .text-danger {
    color: #dc3545;
    font-size: 14px;
    margin-top: -10px;
    display: block;
  }
  
  .btn-primary {
    background-color: #ff0000;
    border: none;
    padding: 10px 15px;
    border-radius: 20px;
    color: #ffffff;
    font-weight: bold;
    cursor: pointer;
    transition: background-color 0.5s ease;
  }
  
  .btn-primary:hover {
    background-color: #8f0000;
  }
  </style>
  