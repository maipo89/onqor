<template>
  <div class="header">
       <h1>{{title}}<strong>.</strong></h1>
       <h3>{{subtitle}}</h3>
  </div>
</template>

<script>

export default {
  name: "Header",
  data() {
    return {
      subtitle: "Welcome to the",
      title: "Onqor Code Test",
      hideComponent: false
  }},
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
    
    @import url('https://fonts.googleapis.com/css2?family=Poppins&display=block');
    @import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&display=block');

    .header {
        width: 644px;
        height: 138px;
        border-radius: 20px 20px 0 0;
        background-image: url("../assets/background.png");
        background-position: center center;
        background-size: cover;
        display: flex;
        align-items: center;
        justify-content: center;
        position: relative;
    }

    .header h1 {
        font-family: 'Bebas Neue';
        color: white;
        font-size: 45px;
        font-weight: 400;
        letter-spacing: 1px;
        margin: 0;
    }

    h3 {
        font-family: 'Poppins';
        font-size: 14px;
        color: white;
        position: absolute;
        top: 14px;
        margin: 0;
        text-transform: uppercase;
        letter-spacing: 2px;
    }

    h1 strong {
        color: #00AAFF;
        font-weight: 500;
    }

    @media screen and (max-width: 650px) {
        .header {
            width: 400px;
        }
    }

    @media screen and (max-width: 375px) {
        .header {
            width: 330px;
        }
    }

</style>
