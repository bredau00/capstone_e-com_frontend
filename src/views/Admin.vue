<template>
  <MDBTabs v-model="activeTabId4" vertical class="pt-5 mt-5 p-3 w-100">
    <!-- Tabs navs -->
    <MDBTabNav tabsClasses="mb-3 text-center">
      <MDBTabItem :wrap="false" tabId="ex4-1" href="ex4-1">Home</MDBTabItem>
      <MDBTabItem :wrap="false" tabId="ex4-2" href="ex4-2">Profile</MDBTabItem>
      <MDBTabItem :wrap="false" tabId="ex4-3" href="ex4-3">Messages</MDBTabItem>
    </MDBTabNav>
    <!-- Tabs navs -->
    <!-- Tabs content -->
    <MDBTabContent>
      <MDBTabPane tabId="ex4-1">Tab 1 content</MDBTabPane>
      <MDBTabPane tabId="ex4-2">Tab 2 content</MDBTabPane>
      <MDBTabPane tabId="ex4-3">Tab 3 content</MDBTabPane>
    </MDBTabContent>
    <!-- Tabs content -->
  </MDBTabs>
</template>

<script>
import {
    MDBTabs,
    MDBTabNav,
    MDBTabContent,
    MDBTabItem,
    MDBTabPane,
  } from 'mdb-vue-ui-kit';
  import { ref } from 'vue';
  export default {
    components: {
      MDBTabs,
      MDBTabNav,
      MDBTabContent,
      MDBTabItem,
      MDBTabPane,
    },
    setup() {
      const activeTabId4 = ref('ex4-1');
      return {
        activeTabId4,
      };
    },
  };
</script>

<style>

</style>