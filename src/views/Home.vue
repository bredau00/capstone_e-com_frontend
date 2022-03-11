<template>
  <div class="home">
    <h2>Home</h2>
    <div class="container">
      <div class="row">
        <div class="col-3">
          <MDBCard v-for="(product, index) in products" :key="index" >
            <a v-mdb-ripple="{ color: 'light' }" class="card">
              <MDBCardImg :src="product.img_front" :alt="product.title" />
              <MDBCardImg :src="product.img_back" class="img-top" :alt="product.title" />
            </a>
            <MDBCardBody>
              <MDBCardTitle>{{ product.title }}</MDBCardTitle>
                <MDBCardText>R{{ product.price }}</MDBCardText>
              <MDBBtn tag="a" href="#!" color="primary">add to cart</MDBBtn>

              <!-- Button trigger modal -->
              <MDBBtn
                color="primary"
                aria-controls="exampleModal"
                @click="exampleModal=true"
              >
                View Product
              </MDBBtn>
            </MDBCardBody>
          </MDBCard>
        </div>
      </div>
    </div>
  </div>
  <MDBModal
    id="exampleModal"
    tabindex="-1"
    labelledby="exampleModalLabel"
    v-model="exampleModal"
    size="xl"
  >
    <MDBModalHeader>
      <MDBModalTitle id="exampleModalLabel"> Modal title </MDBModalTitle>
    </MDBModalHeader>
    <MDBModalBody>
      <MDBCard class="mb-3">
        <MDBRow class="g-0">
          <MDBCol md="4">
            <MDBCardImg fluid src="https://mdbootstrap.com/wp-content/uploads/2020/06/vertical.webp" alt="..."/>
          </MDBCol>
          <MDBCol md="8">
            <MDBCardBody>
              <MDBCardTitle>Card title</MDBCardTitle>
              <MDBCardText>
                This is a wider card with supporting text below as a natural lead-in to
                additional content. This content is a little bit longer.
              </MDBCardText>
              <MDBCardText>
                <small class="text-muted">Last updated 3 mins ago</small>
              </MDBCardText>
            </MDBCardBody>
          </MDBCol>
        </MDBRow>
      </MDBCard>
    </MDBModalBody>
    <MDBModalFooter>
      <MDBBtn color="secondary" @click="exampleModal = false">Close</MDBBtn>
      <MDBBtn color="primary">Save changes</MDBBtn>
    </MDBModalFooter>
  </MDBModal>
</template>

<script>
import { 
  MDBCard, 
  MDBCardBody, 
  MDBCardTitle, 
  MDBCardText, 
  MDBCardImg, 
  MDBBtn, 
  mdbRipple,
  MDBModal,
  MDBModalHeader,
  MDBModalTitle,
  MDBModalBody,
  MDBModalFooter,
  MDBRow,
  MDBCol,
  } from "mdb-vue-ui-kit";
  import { ref } from 'vue';

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
      MDBModal,
      MDBModalHeader,
      MDBModalTitle,
      MDBModalBody,
      MDBModalFooter,
      MDBBtn,
      MDBRow,
      MDBCol,
    },
    directives: {
      mdbRipple
    },
    setup() {
      const exampleModal = ref(false);
      return {
        exampleModal,
      };
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
    }
  }
  };
  

</script>

<style>

.card:hover .img-top {
        display: inline;
    }

.card .img-top {
        display: none;
        position: absolute;
        top: 0;
        left: 0;
        z-index: 99;
    }
</style>
