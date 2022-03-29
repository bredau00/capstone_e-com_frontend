<template>
<div class="pt-5">

</div>
<div class="contaner pt-5">
  <h1>Product Details</h1>
  <MDBBtn
    color="black"
    onclick="history.back(-1)"
    class="link-button link-back-button"
  >
    Go Back
  </MDBBtn>
  <div class="container">
    <div v-if="product" class="row d-flex justify-content-center">
      <div class="card-item text-dark border shadow-5-strong mt-5 card">

        <div class="text-center">
          <p class="h5 names text-center">{{ product.title }}</p>
          <b class="category">{{ product.category }}</b>
          <div class=" ">
            <p class="text-center mt-3">R{{ product.price }}</p>
          </div>
        </div>
        <div class="my-2">
        </div>
      </div>
    </div>
    <div v-else>
      <p class="my-5">Loading product details...</p>
    </div>
  </div>
</div>
  
</template>

<script scoped>
import {
  MDBModal,
  MDBModalHeader,
  MDBModalTitle,
  MDBModalBody,
  MDBModalFooter,
  MDBBtn,
} from "mdb-vue-ui-kit";
import { ref } from "vue";
export default {
  props: ["id"],
  components: {
    MDBModal,
    MDBModalHeader,
    MDBModalTitle,
    MDBModalBody,
    MDBModalFooter,
    MDBBtn,
  },
  data() {
    return {
      id: "",
      product: null,    
      title: "",
      category: "",
      description: "",
      img_front: "",
      img_back: "",
      price: "",
    };
  },
  mounted() {
    fetch("https://eccomerce-backend.herokuapp.com/products" + this.id, {
      method: "GET",
      headers: {
        "Content-type": "application/json; charset=UTF-8",
      },
    })
      .then((response) => response.json())
      .then((json) => {
        this.product = json;
      })
      .catch((err) => {
        alert(console.log(err));
      });
  }
};
</script>

<style>
</style>