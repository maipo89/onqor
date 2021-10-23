<template>
  <div class="body">
    <Form v-if="showComponent" 
            @show-details="showDetails" 
            @user-data="saveDetails"/>
    <Userdetails v-if="hideComponent" 
                @back-to-form="backToForm" 
                :contacts="contacts"/> 
  </div>
</template>

<script>

import Userdetails from "./Userdetails";
import Form from "./Form";

export default {
  name: "Body",
  data() {
    return {
      contacts: [],
      showComponent: true,
      hideComponent: false
  }},
  components: {
    Userdetails,
    Form
  },
  methods: {
    saveDetails(contact) {
      this.contacts = [...this.contacts, contact] 
    },
    showDetails() {
      this.showComponent = !this.showComponent;
      this.hideComponent = !this.hideComponent;
    },
    backToForm() {
      this.showComponent = !this.showComponent;
      this.hideComponent = !this.hideComponent;
      this.contacts = [];
    }
  }
}
</script>

<style>
   .body {
       background-color: #454545;
       height: 489px;
       width: 644px;
       border-radius: 0 0 20px 20px;
       display: flex;
       align-items: center;
       justify-content: center;
   }

   @media screen and (max-width: 650px) {
        .body {
            width: 400px;
        }
    }

    @media screen and (max-width: 375px) {
        .body {
            width: 330px;
            height: 362px;
        }
    }
</style>