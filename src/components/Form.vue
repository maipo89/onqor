<template>
   <form @submit="submitForm">
        <div class="form">
            <div class="inputs">
                <input :class="fName ? 'focus' : 'input'"
                       :style="(err && !firstName) ? {border: '1px solid red'} : {border: '1px solid #00AAFF'}"
                       @focus="fName = true"
                       @blur="fName = false"
                       v-model="firstName" 
                       type="text" 
                       name="first-name" 
                       placeholder="First Name"
                       autocomplete="off">
                <input :class="sName ? 'focus' : 'input'"
                       :style="err && !lastName ? {border: '1px solid red'} : {border: '1px solid #00AAFF'}"
                       @focus="sName = true"
                       @blur="sName = false"
                       v-model="lastName" 
                       type="text" 
                       name="last-name" 
                       placeholder="Last Name"
                       autocomplete="off"/>
            </div>
            <div>
                <textarea :class=" fFact ? 'focus-textarea' : 'textarea'"
                          :style="err && !funFact ? {border: '1px solid red'} : {border: '1px solid #00AAFF'}"
                       @focus="textAreaFocus"
                       @blur="textAreaBlur" 
                       v-model="funFact" 
                       type="textarea" 
                       name="fun-fact" 
                       :placeholder="placeholderTextArea"
                       autocomplete="off"/>
                <input class="submit" type="submit" value="Submit">
                <p class="error">{{error}}</p>
            </div>
        </div>
  </form>
</template>

<script>

export default {
  name: "Form",
  data() {
    return {
      firstName: "",
      lastName: "",
      funFact: "",
      fName: false,
      sName: false,
      fFact: false,
      placeholderTextArea: "Fun Fact",
      error: "",
      err: false 
  }},
  emits: ["user-data", "show-details"],
  methods: {
      textAreaFocus() {
        this.fFact = true;
        this.placeholderTextArea = "";
      },
      textAreaBlur() {
        if(this.funFact === "") {
           this.placeholderTextArea = "Fun Fact"
           this.fFact = false
        }else{
          this.funFact
          this.fFact = false;
        }
      },
      submitForm(e) {
          e.preventDefault();
          if (!this.firstName || !this.lastName || !this.funFact ) {
            this.error = "Please fill the required fields"
            this.err = true
          }else{

            const userData = {
                firstName: this.firstName,
                lastName: this.lastName,
                funFact: this.funFact
            };
            this.$emit('user-data', userData);
            this.$emit('show-details');

            this.firstName = "";
            this.lastName = "";
            this.funFact = "";
            this.error = "";

          }
        },
        capitalizeFirstLetter: (str) => {
          return str.charAt(0).toUpperCase() + str.slice(1);
        },
  },
  watch: {
      funFact: function(newValue) {
        this.funFact = this.capitalizeFirstLetter(newValue);
      },
  }
}

</script>

<style>

   @import url('https://fonts.googleapis.com/css2?family=Poppins&display=block');

   .form {
     width: 528px;
     height: 435px;
   }

   .inputs {
     display: flex;
     justify-content: space-between;
     width: 100%;
   }

   .input, .focus, .textarea, .focus-textarea {
     height: 58px;
     width: 252px;
     border: 1px solid #00AAFF;
     border-radius: 5px;
     background-color: #454545;
     display: flex;
     text-align: left;
     padding: 20px;
     font-family: 'Poppins';
     color: white;
     font-size: 14px;
     font-weight: 300;
     letter-spacing: 1px;
   }

   .input {
     text-transform: capitalize;
   }

   .input:hover, textarea:hover {
     background-color: #121212;
     color: white;
   }

   .focus-textarea:hover {
     background-color: white;
     color: black;
   }

   .focus, .focus-textarea { 
     outline: none;
     background-color: white;
     color: black;
   }

   .focus {
     text-transform: capitalize;
   }

   .textarea, .focus-textarea {
     width: 100%;
     margin-top: 24px;
     height: 265px;
     resize: none;
   }

   input::placeholder, .textarea::placeholder {
     margin-left: 20px;
     color: white;
   }

   .focus::placeholder {
     margin-left: 20px;
   }

   .submit {
     height: 50px;
     border-radius: 5px;
     width: 100%;
     background-color: #00AAFF;
     margin-top: 30px;
     border: none;
     padding: 0;
     font-family: 'Poppins';
     font-weight: bold;
     font-size: 16px;
     cursor: pointer;
     appearance: none;
     -webkit-appearence: none;
     -moz-appearence: none;
   }

   .submit:hover {
     background-color: #026EA3;
     border: 1px solid #00AAFF;
   }

   .error {
     color: #f13737;
     text-align: center;
     margin: 0;
     margin-top: 5px;
     font-family: 'Poppins';
     text-transform: uppercase;
   }

   @media screen and (max-width: 650px) {
     
    .form {
     width: 360px;
    }

    .input, .focus, .textarea, .focus-textarea {
      height: 37px;
      width: 170px;
      font-size: 11px;
    }

    .textarea, .focus-textarea {
     height: 265px;
     width: 100%;
    }

    .submit {
      font-size: 13px;
    }

    .error {
      font-size: 15px;
    }
  }
  
  @media screen and (max-width: 375px) {
    .input, .focus, .textarea, .focus-textarea {
        height: 40px;
        width: 135px;
        font-size: 12px;
        padding: 10px;
    }

    .form {
      width: 290px;
      height: 300px;
    }

    .textarea, .focus-textarea {
      height: 160px;
      width: 100%;
    }

    .textarea, .focus-textarea {
      width: 100%;
      margin-top: 20px;
    }

    .submit {
      margin-top: 20px;
      font-size: 12px;
    }

    .error {
      font-size: 12px;
    }

    @media (hover: none) {

      .input:hover, .textarea:hover {
        background-color: inherit;
        color: inherit;
      }
    }
}
   
</style>