<template>
  <div class="container mt-5 pt-4">
      <div class="row">
          <h2>Contact Us</h2>
          <div class="col-6 border pt-5 pb-4">
            <form>
              <!-- Name input -->
              <MDBInput
                type="text"
                label="Name"
                id="form4Name"
                v-model="form4Name"
                wrapperClass="mb-4"
              />

              <!-- Email input -->
              <MDBInput
                type="email"
                label="Email address"
                id="form4Email"
                v-model="form4Email"
                wrapperClass="mb-4"
              />

              <!-- Message input -->
              <MDBTextarea
                label="Message"
                id="form4Textarea"
                v-model="form4Textarea"
                wrapperClass="mb-4"
              />

              <!-- Checkbox -->
              <div class="form-check d-flex justify-content-center mb-4">
                <MDBCheckbox
                  label="Send me a copy of this message"
                  id="form4CopyCheck"
                  v-model="form4CopyCheck"
                />
              </div>

              <!-- Submit button -->
              <MDBBtn color="primary" block class="mb-4"> Send </MDBBtn>
            </form>
          </div>
          <div class="col-6">hello</div>
      </div>
  </div>
</template>

<script>
import {
    MDBInput,
    MDBBtn,
    MDBTextarea
  } from "mdb-vue-ui-kit";
  import { ref } from "vue";
  export default {
    components: {
      MDBInput,
      MDBBtn,
      MDBTextarea
    },
    setup() {
      const form4Name = ref("");
      const form4Email = ref("");
      const form4Password = ref("");
      const form4Textarea = ref("");
      const form4CopyCheck = ref(true);

      return {
        form4Name,
        form4Email,
        form4Password,
        form4Textarea,
        form4CopyCheck
      };
    },
  };
</script>

<style>

</style>