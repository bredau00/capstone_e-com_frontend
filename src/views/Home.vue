<template>
  <div class="home pb-5">
    
    <div class="container mt-5 pt-2">
      <div v-if="products.length" class="row">
        <!-- Products display -->
        <div class="row">
          <h2>tops</h2>
          <div v-for="(product, index) in filterProducts" :key="index" class="col">
            <!-- Project Card -->
            <MDBCard  style="max-width: 300px">
              <a v-mdb-ripple="{ color: 'light' }" class="card">
                <MDBCardImg :src="product.img_front" :alt="product.title" />
                <MDBCardImg :src="product.img_back" class="img-top" :alt="product.title"/>
              </a>
              <MDBCardBody>
                <MDBCardTitle>{{ product.title }}</MDBCardTitle>
                  <MDBCardText>{{ product.category }}</MDBCardText>
                  <MDBCardText>R{{ product.price }}</MDBCardText>
                <MDBBtnGroup>
                <MDBBtn tag="a" href="#!" color="dark">add to cart</MDBBtn>
                <!-- Button trigger modal -->
                <MDBBtn
                  color="dark"
                  aria-controls="exampleModal"
                  @click="exampleModal=true"
                >
                  View Product
                </MDBBtn>
                </MDBBtnGroup>
              </MDBCardBody>
            </MDBCard>
          </div>
        
        </div>
        <div class="row pt-5">
          <h2>bottoms</h2>
          <div v-for="(product, index) in filterProducts" :key="index" class="col">
            <!-- Project Card -->
            <MDBCard  style="max-width: 300px">
              <a v-mdb-ripple="{ color: 'light' }" class="card">
                <MDBCardImg :src="product.img_front" :alt="product.title" />
                <MDBCardImg :src="product.img_back" class="img-top" :alt="product.title" />
              </a>
              <MDBCardBody>
                <MDBCardTitle>{{ product.title }}</MDBCardTitle>
                <MDBCardText>{{ product.category }}</MDBCardText>
                <MDBCardText>R{{ product.price }}</MDBCardText>
                <MDBBtnGroup>
                <MDBBtn tag="a" href="#!" color="dark">add to cart</MDBBtn>
                <!-- Button trigger modal -->
                <MDBBtn
                  color="dark"
                  aria-controls="exampleModal"
                  @click="exampleModal=true"

                >
                  View Product
                </MDBBtn>
                
                <!-- Single project modal -->
                      <MDBModal
                        id="exampleModal"
                        tabindex="-1"
                        labelledby="exampleModalLabel"
                        v-model="exampleModal"
                        size="xl"
                      >
                        <MDBModalHeader>
                          <MDBModalTitle id="exampleModalLabel">Single Product view</MDBModalTitle>
                        </MDBModalHeader>
                        <MDBModalBody>
                          <MDBCard class="mb-3">
                            <MDBRow class="g-0">
                              <MDBCol md="4"> 
                                <a class="card">
                                    <MDBCardImg :src="product.img_front" :alt="product.title" />
                                    <MDBCardImg :src="product.img_back" class="img-top" :alt="product.title" />
                                </a>
                              </MDBCol>
                              <MDBCol md="8">
                                <MDBCardBody>
                                  <MDBCardTitle> {{ product.title }} </MDBCardTitle>
                                  <MDBCardText>{{ product.category }}</MDBCardText>
                                  <MDBCardText>R{{ product.price }}</MDBCardText>
                                </MDBCardBody>
                              </MDBCol>
                            </MDBRow>
                          </MDBCard>
                        </MDBModalBody>
                        <MDBModalFooter>
                          <MDBBtn color="secondary" @click="exampleModal = false">Close</MDBBtn>
                          <MDBBtn tag="a" href="#!" color="dark">add to cart</MDBBtn>
                        </MDBModalFooter>
                      </MDBModal>

                </MDBBtnGroup>
              </MDBCardBody>
            </MDBCard>
          </div>
        </div>
      </div>

      <div v-else class="hollow-dots-spinner mx-auto" style="width: 200px" :style="spinnerStyle">
        <div class="dot"></div>
        <div class="dot"></div>
        <div class="dot"></div>
      </div>
    </div>

  </div>
    <div class="container pb-5">
      <div class="row pt-5 pb-5">
          <MDBCarousel
            v-model="carousel8"
            :items="items8"
            fade
            dark
          />
    </div>
  </div>

</template>

<script>
import axios from "axios";
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
  MDBInput,
  MDBCarousel,
  MDBBtnGroup,
  } from "mdb-vue-ui-kit";
  import { ref } from 'vue';

  export default {
    props: ["id"],
    data() {
    return {
      products: [],
      title: "",
      category: "",
      description: "",
      img: "",
      price: "",
      search:""
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
      MDBInput,
      MDBCarousel,
      MDBBtnGroup,
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

    setup() {
      const items8 = [
        {
          src: "https://mdbootstrap.com/img/Photos/Slides/img%20(19).webp",
          alt: "...",
          label: "First slide label",
          caption: "Nulla vitae elit libero, a pharetra augue mollis interdum."
        },
        {
          src: "https://mdbootstrap.com/img/Photos/Slides/img%20(35).webp",
          alt: "...",
          label: "Second slide label",
          caption: "Lorem ipsum dolor sit amet, consectetur adipiscing elit."
        },
        {
          src: "https://mdbootstrap.com/img/Photos/Slides/img%20(40).webp",
          alt: "...",
          label: "Third slide label",
          caption:
            "Praesent commodo cursus magna, vel scelerisque nisl consectetur."
        }
      ];
      const carousel8 = ref(0);
      return {
        items8,
        carousel8
      };
    },

    mounted() {
      fetch("https://eccomerce-backend.herokuapp.com/products", {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      })
        .then((response) => response.json())
        .then((json) => {
          this.products = json;
        })
    },

    methods: {
      getOne() {
        fetch("https://eccomerce-backend.herokuapp.com/products/" + this.id, {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      })
        .then((response) => response.json())
        .then((json) => {
          this.products = json;
        })
      },
    },

    computed: {
    filterProducts: function () {
      return this.products.filter((product) => {;
        return product.title.toLowerCase().match(this.search.toLowerCase())
      });
    },
  },
};

</script>

<style scoped>

.card {
  justify-content: center;
}

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

/* loading */
.hollow-dots-spinner, .hollow-dots-spinner * {
      box-sizing: border-box;
    }

    .hollow-dots-spinner {
      height: 15px;
      width: calc(30px * 3);
    }

    .hollow-dots-spinner .dot {
      width: 15px;
      height: 15px;
      margin: 0 calc(15px / 2);
      border: calc(15px / 5) solid black;
      border-radius: 50%;
      float: left;
      transform: scale(0);
      animation: hollow-dots-spinner-animation 1000ms ease infinite 0ms;
    }

    .hollow-dots-spinner .dot:nth-child(1) {
      animation-delay: calc(300ms * 1);
    }

    .hollow-dots-spinner .dot:nth-child(2) {
      animation-delay: calc(300ms * 2);
    }

    .hollow-dots-spinner .dot:nth-child(3) {
      animation-delay: calc(300ms * 3);

    }

    @keyframes hollow-dots-spinner-animation {
      50% {
        transform: scale(1);
        opacity: 1;
      }
      100% {
        opacity: 0;
      }
    }
</style>
