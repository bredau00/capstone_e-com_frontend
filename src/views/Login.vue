<template>
      
<div class="container border mt-5 pt-4">
  <h2>Login</h2>
  <form @submit.prevent="login">
    <!-- Email input -->
    <MDBInput
      type="email"
      label="Email address"
      id="form2Email"
      v-model="email"
      wrapperClass="mb-4"
    />
    <!-- Password input -->
    <MDBInput
      type="password"
      label="Password"
      id="form2Password"
      v-model="password"
      wrapperClass="mb-4"
    />
    <!-- Submit button -->
    <MDBBtn type="submit" color="primary" block> Sign in </MDBBtn>

    <!-- Register buttons -->
    <div class="text-center">
      <p>Not a member? <a href="#!">Register</a></p>
    </div>
  </form>
</div>
</template>

<script>
 import {
    MDBRow,
    MDBCol,
    MDBInput,
    MDBCheckbox,
    MDBBtn,
    MDBIcon
  } from "mdb-vue-ui-kit";
  import { ref } from "vue";
  import axios from 'axios'
  import { loginUser } from '../utils/auth'
  export default {
    name: 'login',
        data() {
            return {
                email: '',
                password: ''
            }
        },
    components: {
      MDBRow,
      MDBCol,
      MDBInput,
      MDBCheckbox,
      MDBBtn,
      MDBIcon
    },
    setup() {
      const form2Email = ref("");
      const form2Password = ref("");
      const form2LoginCheck = ref(true);

      return {
        form2Email,
        form2Password,
        form2LoginCheck,
      };
    },
    methods: {
    login() {
      fetch("https://eccomerce-backend.herokuapp.com/users", {
        method: "PATCH",
        body: JSON.stringify({
          email: this.email,
          password: this.password,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      })
        .then((response) => response.json())
        .then((json) => {
          localStorage.setItem("jwt", json.jwt);
          alert("User logged in");
          this.$router.push({ name: "Home" });
        })
        .catch((err) => {
          alert(err);
        });
    },
  },

  };
</script>

<style>

</style>