<template>
<div>
  <div class="container d-flex justify-content-center">
    <div class="row" style="margin-top: 7%;">
      <div class="col">
          <center><h3>Silahkan Registrasi</h3></center><br><br>
        <label for="">Username :</label><br>
        <input v-model="username" style="border-radius: 10px; width: 8cm;" type="username" placeholder="Username"><br><br>
        <label for="">Password :</label><br>
        <input v-model="password" style="border-radius: 10px; width: 8cm;" type="password" placeholder="Password"><br><br>
        <center><input style="border-radius: 10px; width: 5cm; background-color: white;" type="submit" value="Registrasi" @click="login"></center>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import axios from "axios"

export default {
    name: "Register",
    data() {
        return {
            username: "",
            password: "",
            useres: {},
        }
    },
    methods: {
        async login() {
            const payload = {
            username: this.username,
            password: this.password,
            role: "siswa"
            }
            const register = await axios.post('http://localhost:3000/useres',payload)
            var convertToString = JSON.stringify(register.data)
            sessionStorage.setItem("USER_DATA",convertToString)
            this.$router.push("/")
        },
    },
    mounted() {
        this.getUsers()
    }
}
</script>