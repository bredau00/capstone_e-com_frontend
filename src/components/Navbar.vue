<template>
    <MDBNavbar expand="lg" light bg="light" container>
    <MDBNavbarBrand href="#">Moden Junkie</MDBNavbarBrand>
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

        <MDBNavbarItem>

          <!-- Navbar dropdown -->
          <MDBDropdown class="nav-item" v-model="dropdown1">
            <MDBDropdownToggle
              tag="a"
              class="nav-link"
              @click="dropdown1 = !dropdown1"
              >Dropdown</MDBDropdownToggle
            >
            <MDBDropdownMenu aria-labelledby="dropdownMenuButton">
              <MDBDropdownItem href="#">Action</MDBDropdownItem>
              <MDBDropdownItem href="#">Another Action</MDBDropdownItem>
              <MDBDropdownItem href="#"
                >Something else here</MDBDropdownItem
              >
            </MDBDropdownMenu>
          </MDBDropdown>
        </MDBNavbarItem>
        <MDBNavbarItem to="#" disabled>
          Disabled
        </MDBNavbarItem>
      </MDBNavbarNav>
      
      <!-- Search form -->
      <MDBNavbarNav class="mb-2 mb-lg-0">
        <MDBNavbarItem router-link :to="{name: 'Login'}">
          Login
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
</style>