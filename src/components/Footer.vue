<template>
  <MDBFooter class="fixed-bottom" :text="['center', 'white']">
    <!-- Grid container -->
    <MDBContainer class="p-4 pb-0">
      <!-- Section: Social media -->
      <section class="mb-4">
        <!-- Github -->
        <MDBBtn
          tag="a"
          color="primary"
          href="#!"
          floating
          style="background-color: #333333"
          class="m-1"
        >
          <MDBIcon iconStyle="fab" icon="github"></MDBIcon>
        </MDBBtn>
      </section>
      <!-- Section: Social media -->
    </MDBContainer>
    <!-- Grid container -->
    <!-- Copyright -->
    <div
      class="text-center p-3"
      style="background-color: rgba(0, 0, 0, 0.2)"
    >
      © 2020 Copyright:
      <a class="text-white" href="https://mdbootstrap.com/"
        >MDBootstrap.com</a
      >
    </div>
    <!-- Copyright -->
  </MDBFooter>
</template>

<script>
  import { MDBFooter, MDBContainer, MDBRow, MDBCol, MDBBtn } from 'mdb-vue-ui-kit';
  export default {
    components: {
      MDBFooter,
      MDBContainer,
      MDBRow,
      MDBCol,
      MDBBtn
    },
  };

</script>

<style>

</style>