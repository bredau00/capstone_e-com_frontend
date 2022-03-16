<template>
  <div class="home pb-5">
    
    <div class="container mt-5 pt-2 pb-5"><h2>Home</h2>
      <div v-if="products.length=4" class="row p-b-5">
        <!-- Search form -->
        <form class="d-flex input-group w-auto">
          <input
            type="search"
            class="form-control"
            placeholder="search name"
            aria-label="Search"
            v-model="search"
            label="search"
          />
        </form>

        <!-- Products -->
        <div class="row">
          <h2>tops</h2>
          <div v-for="(product, index) in filterProducts" :key="index" class="col">
            <!-- Project Card -->
            <MDBCard  style="max-width: 255px">
              <a v-mdb-ripple="{ color: 'light' }" class="card">
                <MDBCardImg :src="product.img_front" :alt="product.title" />
                <MDBCardImg :src="product.img_back" class="img-top" :alt="product.title"/>
              </a>
              <MDBCardBody>
                <MDBCardTitle>{{ product.title }}</MDBCardTitle>
                  <MDBCardText>{{ product.category }}</MDBCardText>
                  <MDBCardText>R{{ product.price }}</MDBCardText>
                <MDBBtnGroup>
                <MDBBtn tag="a" href="#!" color="primary">add to cart</MDBBtn>
                <!-- Button trigger modal -->
                <MDBBtn
                  color="primary"
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
            <MDBCard  style="max-width: 255px">
              <a v-mdb-ripple="{ color: 'light' }" class="card">
                <MDBCardImg :src="product.img_front" :alt="product.title" />
                <MDBCardImg :src="product.img_back" class="img-top" :alt="product.title" />
              </a>
              <MDBCardBody>
                <MDBCardTitle>{{ product.title }}</MDBCardTitle>
                <MDBCardText>{{ product.category }}</MDBCardText>
                <MDBCardText>R{{ product.price }}</MDBCardText>
                <MDBBtnGroup>
                <MDBBtn tag="a" href="#!" color="primary">add to cart</MDBBtn>
                <!-- Button trigger modal -->
                <MDBBtn
                  color="primary"
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

        <div class="row pt-5 pb-5">
          <MDBCarousel
            v-model="carousel8"
            :items="items8"
            fade
            dark
          />
        </div>
      </div>

      <div v-else><p>loading...</p></div>

    </div>
  </div>

<!-- Single project modal -->
  <MDBModal
    @="getOne()"
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
              <MDBCardTitle>  </MDBCardTitle>
              <MDBCardText>
                
              </MDBCardText>
              <MDBCardText>
                <small class="text-muted"></small>
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

<style>

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
</style>
