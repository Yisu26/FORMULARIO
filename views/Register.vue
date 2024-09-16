<script lang="ts">
import { defineComponent, ref } from 'vue'
import { useRouter } from 'vue-router'

export default defineComponent({
  setup() {
    const router = useRouter()

    const name = ref('')
    const errorName = ref(false)
    const lastName = ref('')
    const errorLastName = ref(false)
    const year = ref('')
    const errorYear = ref(false)
    const phone = ref('')
    const errorPhone = ref(false)
    const address = ref('')
    const errorAddress = ref(false)
    const email = ref('')
    const errorEmail = ref(false)
    const users = ref([])

    const validateData = () => {
      let isValid = true

      if (name.value === '') {
        isValid = false
        errorName.value = true
      }

      if (lastName.value === '') {
        isValid = false
        errorLastName.value = true
      }

      if (year.value === '') {
        isValid = false
        errorYear.value = true
      }

      if (phone.value === '') {
        isValid = false
        errorPhone.value = true
      }

      if (address.value === '') {
        isValid = false
        errorAddress.value = true
      }

      if (email.value === '') {
        isValid = false
        errorEmail.value = true
      }

      return isValid
    }

    const register = () => {
      const isValid = validateData()

      if (isValid) {
        console.log(name.value, lastName.value, year.value, phone.value, address.value, email.value)
        console.log('Registrado')
        users.value.push({
          name: name.value,
          lastName: lastName.value,
          year: year.value,
          phone: phone.value,
          address: address.value,
          email: email.value
        })
        clear()
        console.log(users.value)
        router.push('/')
      }
    }

    const clear = () => {
      name.value = ''
      errorName.value = false
      lastName.value = ''
      errorLastName.value = false
      year.value = ''
      errorYear.value = false
      phone.value = ''
      errorPhone.value = false
      address.value = ''
      errorAddress.value = false
      email.value = ''
      errorEmail.value = false
    }

    return {
      name,
      errorName,
      lastName,
      errorLastName,
      year,
      errorYear,
      phone,
      errorPhone,
      address,
      errorAddress,
      email,
      errorEmail,
      users,
      register
    }
  }
})
</script>


<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <div class="card">
          <div class="card-body">
            <h2 class="card-title">Registrate</h2>
            <hr class="hr">
            <label for="name">Nombre</label>
            <input type="text" class="form-control" v-model="name">
            <span v-if="errorName" class="text-danger">Este campo es requerido</span>
            <label for="lastName">Apellidos</label>
            <input type="text" class="form-control" v-model="lastName">
            <span v-if="errorLastName" class="text-danger">Este campo es requerido</span>
            <label for="year">Fecha de nacimiento</label>
            <input type="text" class="form-control" v-model="year">
            <span v-if="errorYear" class="text-danger">Este campo es requerido</span>
            <label for="phone">Teléfono</label>
            <input type="text" class="form-control" v-model="phone">
            <span v-if="errorPhone" class="text-danger">Este campo es requerido</span>
            <label for="address">Dirección</label>
            <input type="text" class="form-control" v-model="address">
            <span v-if="errorAddress" class="text-danger">Este campo es requerido</span>
            <label for="email">Correo electronico</label>
            <input type="text" class="form-control" v-model="email">
            <span v-if="errorEmail" class="text-danger">Este campo es requerido</span>
            <hr class="hr">
            <p>Ya tienes cuenta? <a href="/login">Inicia sesión</a></p>
            <button type="button" class="btn btn-primary" @click="register">Registrar</button>
          </div>
        </div>
      </div>
      <div v-if="users.length !== 0" class="coll">
        <h3>Lista de usuarios</h3>
        <table class="tablee">
          <thead>
            <tr>
              <th class="th-spacing">Nombre</th>
              <th class="th-spacing">Apellidos</th>
              <th class="th-spacing">Fecha de nacimiento</th>
              <th class="th-spacing">Teléfono</th>
              <th class="th-spacing">Dirección</th>
              <th class="th-spacing">Correo electronico</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="user in users" :key="user">
              <td>{{ user.name }}</td>
              <td>{{ user.lastName }}</td>
              <td>{{ user.year }}</td>
              <td>{{ user.phone }}</td>
              <td>{{ user.address }}</td>
              <td>{{ user.email }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  max-width: 500px;
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

input[type="text"] {
  width: 400px;
  padding: 10px;
  margin: 5px 0 15px 0;
  border-radius: 20px;
  border: 3px solid #000000;
  box-shadow: inset 0px 0px 5px rgba(0, 0, 0, 0.05);
  transition: all 0.3s ease;
  background-color: white;
  color: black;
}

input[type="text"]:focus {
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

.tablee {
  width: 100%;
  margin-top: 30px;
  border-collapse: collapse;
  color: black;
}

.th-spacing {
  text-align: left;
  padding: 10px;
  background-color: #000000;
  color: white;
}

.tablee th,
.tablee td {
  border: 1px solid #ddd;
  padding: 8px;
}

.tablee tr:nth-child(even) {
  background-color: #f2f2f2;
}

.tablee tr:hover {
  background-color: #ddd;
}

.coll h3 {
  margin-top: 30px;
  font-size: 20px;
  font-weight: bold;
  color: #333333;
}

</style>
