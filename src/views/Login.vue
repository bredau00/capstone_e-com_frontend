<template>
      <h2>Login</h2>
      <div class="container">
        <form>
    <!-- Email input -->
    <MDBInput
      type="email"
      label="Email address"
      id="form2Email"
      v-model="form2Email"
      wrapperClass="mb-4"
    />
    <!-- Password input -->
    <MDBInput
      type="password"
      label="Password"
      id="form2Password"
      v-model="form2Password"
      wrapperClass="mb-4"
    />
    <!-- 2 column grid layout for inline styling -->
    <MDBRow class="mb-4">
      <MDBCol class="d-flex justify-content-center">
        <!-- Checkbox -->
        <MDBCheckbox
          label="Remember me"
          id="form2LoginCheck"
          v-model="form2LoginCheck"
          wrapperClass="mb-3 mb-md-0"
        />
      </MDBCol>
      <MDBCol>
        <!-- Simple link -->
        <a href="#!">Forgot password?</a>
      </MDBCol>
    </MDBRow>
    <!-- Submit button -->
    <MDBBtn color="primary" block> Sign in </MDBBtn>

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
  export default {
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
  };
</script>

<style>

</style>