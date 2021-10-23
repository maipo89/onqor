<template>
    <div class="filled-form" v-for='(contact, i) in contacts' :key='i'>
      <p>First Name: <strong>{{contact.firstName}}</strong></p>
      <p class="last-name">Last Name: <strong>{{contact.lastName}}</strong></p>
      <p>Fun Fact:</p> 
      <div class="fun-fact-container">
        <p>{{contact.funFact}}</p>
      </div>
      <button class="submit" @click='backToForm'>Back</button>
    </div>
</template>

<script>

export default {
  name: "Userdetails",
  data() {
    return {
      newText: " ",
    }
  },
  emits: ["back-to-form"],
  props: {
      contacts: Array
  },
  methods: {
      backToForm() {
        this.$emit('back-to-form')
      },
  }
}

</script>

<style scoped>
   
   @import url('https://fonts.googleapis.com/css2?family=Poppins&display=block');

   .filled-form {
     width: 528px;
     height: 435px;
   }

   .filled-form p {
     font-size: 16px;
     font-family: 'Poppins';
     color: white;
     margin: 0;
     padding: 0;
     text-transform: capitalize;
   }

   .fun-fact-container {
     height: 230px;
     width: 100%;
     border: 1px solid #00AAFF;
     border-radius: 5px;
     padding: 10px;
     word-wrap: break-word;
     white-space: pre-wrap;
     margin-top: 10px;
     overflow: auto;
     font-weight: 100;
   }

   .fun-fact-container:hover {
     background-color: #121212;
     color: white;
   }

   .fun-fact-container p {
     font-size: 14px;
   }

   .filled-form .last-name {
     margin: 17px 0 17px 0;
   }

   strong {
     margin-left: 5px;
     font-weight: 700;
     font-size: 16px;
   }

  @media screen and (max-width: 650px) {
     
    .filled-form {
     width: 360px;
    }

    .filled-form p {
      font-size: 14px;
    }
  }

  @media screen and (max-width: 375px) {
    .filled-form {
     height: 300px;
     width: 290px;
    }

    .filled-form p {
      font-size: 11px;
    }

    .fun-fact-container {
     height: 150px;
    }

    .fun-fact-container p {
      font-size: 12px;
    }

   .filled-form .last-name {
     margin: 12px 0 12px 0;
   }

   strong {
     margin-left: 5px;
     font-size: 13px;
   }

   @media (hover: none) {

    .fun-fact-container:hover {
     background-color: inherit;
     color: inherit;
    }
  }
  }
</style>