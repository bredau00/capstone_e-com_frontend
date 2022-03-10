<template>
  <div class="home">
    <h2>Home</h2>
    <div class="container">
      <div class="row">
        <div class="col-4">
          <MDBCard v-for="(product, index) in products" :key="index" >
            <a v-mdb-ripple="{ color: 'light' }">
              <MDBCardImg :src="product.img_front" :alt="product.title" />
            </a>
            <MDBCardBody>
              <MDBCardTitle>{{ product.title }}</MDBCardTitle>
                <MDBCardText>R{{ product.price }}</MDBCardText>
              <MDBBtn tag="a" href="#!" color="primary">Button</MDBBtn>
            </MDBCardBody>
          </MDBCard>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { MDBCard, MDBCardBody, MDBCardTitle, MDBCardText, MDBCardImg, MDBBtn, mdbRipple } from "mdb-vue-ui-kit";
  export default {
    data() {
    return {
      products: [],
      title: "",
      category: "",
      description: "",
      img: "",
      price: ""
    };
    },
    components: {
      MDBCard,
      MDBCardBody,
      MDBCardTitle,
      MDBCardText,
      MDBCardImg,
      MDBBtn
    },
    directives: {
      mdbRipple
    },
    mounted() {
    if (localStorage.getItem("jwt")) {
      fetch("https://eccomerce-backend.herokuapp.com/products", {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          this.products = json;
        })
        .catch((err) => {
          alert("User not logged in");
        });
    } else {
      alert("User not logged in");
      this.$router.push({ name: "Login" });
    }
  }
  };
  

</script>
