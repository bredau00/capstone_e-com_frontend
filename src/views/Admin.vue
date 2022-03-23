<template>
  <div class="container pt-5">
    <h3 class="pt-5">Products</h3>
    <MDBBtn 
    color="dark" 
    aria-controls="exampleModal"
    @click="exampleModal=true" 
    size="lg">
      addproduct
    </MDBBtn>
    <div class="container d-flex justify-content-end mt-5 pt-4"> 
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
      <div class="d-flex w-25 ms-3">
        <label for="" class="form-label">Sort by category</label>
        <select
          class="form-select"
          v-model="category"
          v-on:change="sortCategory(category)"
        >
          <option value="">All</option>
          <option value="Tops">Tops</option>
          <option value="Bottoms">Bottoms</option>
          <option value="Accessories">Accessories</option>
        </select>
      </div>
      <div class="d-flex w-25 ms-3">
        <label class="form-label">Sort name</label>
        <select class="form-select" v-model="title" v-on:change="sortTitle(title)">
          <option value="asc">Ascending</option>
          <option value="desc">Descending</option>
        </select>
      </div>
      <div class="d-flex w-25 ms-3">
        <label for="" class="form-label">Sort price</label>
        <select
          class="form-select"
          v-model="price"
          v-on:change="sortPrice(price)"
        >
          <option value=""></option>
          <option value="asc">Ascending</option>
          <option value="desc">Descending</option>
        </select>
      </div>
    </div>
    <div v-if="products.length" id="products" class="row pt-5">
      <div v-for="(product, index) in products" :key="index" class="col-6">
        <MDBCard class="" style="max-height: 300px" >
          <MDBCardBody>
            <MDBRow class="g-0">
              <MDBCol  md="4">
                <MDBCardImg style="max-width: 200px" :src="product.img_front" :alt="product.title" />
              </MDBCol>
              <MDBCol md="8">
                <MDBCardTitle>{{ product.title }}</MDBCardTitle>
                <MDBRow>
                  <MDBCardText>
                    {{ product.category }}
                    R{{ product.price }}
                  </MDBCardText>
                </MDBRow>
                <MDBRow>
                  <MDBCol>
                    <MDBBtn color="dark">edit</MDBBtn>
                    <MDBBtn color="dark">delete</MDBBtn>
                  </MDBCol>
                </MDBRow>
              </MDBCol>
            </MDBRow>
          </MDBCardBody>
        </MDBCard>
      </div>
    </div>
    <div v-else class="hollow-dots-spinner mx-auto" style="width: 200px" :style="spinnerStyle">
      <div class="dot"></div>
      <div class="dot"></div>
      <div class="dot"></div>
    </div>
  </div>

  <div class="container pt-5 pb-5">
    <h3 class="pt-5">users</h3>
    <div v-if="users.length" id="users" class="row pt-5 pb-5">
      
        <MDBCard v-for="(user, index) in users" :key="index" class="w-100 pt-5 col">
          <MDBCardBody>
            <MDBCardTitle>{{ user.name }}</MDBCardTitle>
            <MDBCardText>
              {{ user.email }}
              {{ user.contact }}
            </MDBCardText>
            <MDBBtn tag="a" href="#!" color="dark">Button</MDBBtn>
          </MDBCardBody>
        </MDBCard>
    </div>
    <div v-else class="hollow-dots-spinner mx-auto " style="width: 200px" :style="spinnerStyle">
      <div class="dot"></div>
      <div class="dot"></div>
      <div class="dot"></div>
    </div>
  </div>

  <MDBModal
    id="exampleModal"
    tabindex="-1"
    labelledby="exampleModalLabel"
    v-model="exampleModal"
  >
    <MDBModalHeader>
      <MDBModalTitle id="exampleModalLabel"> Add Product </MDBModalTitle>
    </MDBModalHeader>
    <MDBModalBody>
      <form @submit.prevent="createProduct">
        <!-- Name input -->
        <MDBInput
          type="text"
          label="Name of Product"
          id="title"
          v-model="title"
          wrapperClass="mb-4"
        />
  
        <!-- category input -->
          <select
            class="form-select"
            wrapperClass="mb-4"
            v-model="category"
          >
            <option value="Tops">Tops</option>
            <option value="Bottoms">Bottoms</option>
            <option value="Accessories">Accessories</option>
          </select>
          <br>

        <!-- img front input -->
        <MDBInput
          type="text"
          label="img front link"
          id="img_front"
          v-model="img_front"
          wrapperClass="mb-4"
        />
        <!-- img back input -->
        <MDBInput
          type="text"
          label="img back link"
          id="img_back"
          v-model="img_back"
          wrapperClass="mb-4"
        />
        <!-- price input -->
        <MDBInput
          type="text"
          label="price"
          id="price"
          v-model="price"
          wrapperClass="mb-4"
        />
        <MDBBtn color="dark" type="submit" class="form-btn neu-border">add</MDBBtn>
      </form>
    </MDBModalBody>
    <MDBModalFooter>
      <MDBBtn color="dark" @click="exampleModal = false">Close</MDBBtn>
    </MDBModalFooter>
  </MDBModal>
</template>

<script>
import { 
  MDBCard, 
  MDBRow,
  MDBCol, 
  MDBCardBody, 
  MDBCardTitle, 
  MDBCardText, 
  MDBBtn,
  MDBModal,
  MDBModalHeader,
  MDBModalTitle,
  MDBModalBody,
  MDBModalFooter,
  MDBInput,
  MDBCardImg
  } from "mdb-vue-ui-kit";
  import { ref } from 'vue';
  export default {
    props: ["id"],
    data() {
    return {
      product: null,
      products: [], 
      user: null,
      users: [],
      filterProducts: null,
      title: "",
      category: "",
      description: "",
      img: "",
      price: "",
      search:"",
      name:"",
      email:"",
      password:"",
      search:"",
    };
    },
    components: {
      MDBCard,
      MDBCardBody,
      MDBCardTitle,
      MDBCardText,
      MDBBtn,
      MDBRow,
      MDBCol,
      MDBModal,
      MDBModalHeader,
      MDBModalTitle,
      MDBModalBody,
      MDBModalFooter,
      MDBInput,
      MDBCardImg
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
        }),
        fetch("https://eccomerce-backend.herokuapp.com/users", {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      })
        .then((response) => response.json())
        .then((json) => {
          this.users = json;
        })
    },
    setup() {
      const form8Name = ref("");
      const form8Email = ref("");
      const exampleModal = ref(false);

      return {
        exampleModal,
        form8Name,
        form8Email
      };
    },
    methods: {
    createProduct() {
      if (!localStorage.getItem("jwt")) {
        alert("User not logged in");
        return this.$router.push({ name: "Login" });
      }
      fetch("https://eccomerce-backend.herokuapp.com/products", {
        method: "POST",
        body: JSON.stringify({
          title: this.title,
          category: this.category,
          img_front: this.img_front,
          img_back: this.img_back,
          price: this.price,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          alert("Product Created Successfuly");
        })
        .catch((err) => {
          alert(err);
        });
    },
     // SORT BY PRICE
      sortPrice(price) {
      this.products = this.products.sort(
        (a, b) => a.price - b.price
      );
      if (price == "desc") this.products.reverse();
      },

      // SORT BY NAME
      sortTitle(desc) {
      this.products = this.products.sort((a, b) => {
        if (a.title.toLowerCase() < b.title.toLowerCase()) {
          return -1;
        }
        if (a.title.toLowerCase() > b.title.toLowerCase()) {
          return 1;
        }
        return 0;
      });
      if (desc == "desc") this.products.reverse();
      },
      
      // FILLTER CATEGORY
      filterCategory(category) {
      if (category) {
        this.filterProducts = this.products.filter(
          (product) => product.category == category
        );
      } else {
        this.fillterProducts = this.products;
      }
    },
  },
  computed: {
    filterProducts: function () {
      return this.products.filter((product) => {;
        return product.title.toLowerCase().match(this.search.toLowerCase())
      });
    },
  },
}
</script>

<style>
/* .tab {
  background-color:#262626 ;
} */
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