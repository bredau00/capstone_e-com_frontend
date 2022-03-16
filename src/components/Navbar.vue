<template>
    <MDBNavbar expand="lg" light bg="light" container>
      <MDBNavbarBrand 
      data-hover="themodernman" 
      class="text" 
      href="#">
        現代人
      </MDBNavbarBrand>
    <MDBNavbarToggler
      @click="collapse1 = !collapse1"
      target="#navbarSupportedContent"
    ></MDBNavbarToggler>
    <MDBCollapse v-model="collapse1" id="navbarSupportedContent">
      <MDBNavbarNav class="mb-2 mb-lg-0">
        <MDBNavbarItem router-link :to="{name: 'Home'}">
          Home
        </MDBNavbarItem>
        <MDBNavbarItem router-link :to="{name: 'About'}">
          About
        </MDBNavbarItem>
        <MDBNavbarItem router-link :to="{name: 'Products'}">
          All Products
        </MDBNavbarItem>
        <MDBNavbarItem router-link :to="{name: 'Contact'}">
          Contact
        </MDBNavbarItem>
      </MDBNavbarNav>
      
      <!-- Search form -->
      <MDBNavbarNav class="mb-2 mb-lg-0">
        <MDBNavbarItem router-link :to="{name: 'Cart'}">
          Cart
        </MDBNavbarItem>
      </MDBNavbarNav>
      <MDBNavbarNav class="mb-2 mb-lg-0">
        <MDBNavbarItem router-link :to="{name: 'Login'}">
          Login
        </MDBNavbarItem>
        <MDBNavbarItem router-link :to="{name: 'Register'}">
          Register
        </MDBNavbarItem>
      </MDBNavbarNav>
      
    </MDBCollapse>
  </MDBNavbar>
</template>

<script>
   import {
    MDBBtn,
    MDBNavbar,
    MDBNavbarToggler,
    MDBNavbarBrand,
    MDBNavbarNav,
    MDBNavbarItem,
    MDBCollapse,
    MDBDropdown,
    MDBDropdownToggle,
    MDBDropdownMenu,
    MDBDropdownItem
  } from 'mdb-vue-ui-kit';
  import { ref } from 'vue';
  export default {
    components: {
      MDBBtn,
      MDBNavbar,
      MDBNavbarToggler,
      MDBNavbarBrand,
      MDBNavbarNav,
      MDBNavbarItem,
      MDBCollapse,
      MDBDropdown,
      MDBDropdownToggle,
      MDBDropdownMenu,
      MDBDropdownItem
    },
    setup() {
      const collapse1 = ref(false);
      const dropdown1 = ref(false);
      return {
        collapse1,
        dropdown1
      }
    }
  };
</script>

<style>
template {
  font-family: Arial,Helvetica,sans-serif!important;
}

.text:hover{
    font-size: 0%;
    }

.text:hover:after{
  content: attr(data-hover);
  font-size: 20px;
    }
</style>