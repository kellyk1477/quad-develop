<template>
  <div class="inquiry">

    <transition name="fade">
      <div v-if="success" class="submission-result">Thank you for your submission!</div>
    </transition>
    <transition name="fade">
      <div v-if="failed" class="submission-result red">Sorry, please try again</div>
    </transition>

    <v-form v-model="valid" ref="form" class="inquiry-container" action="https://formspree.io/xzbjqzpr" method="POST">
      <v-container class="inquiry-inner-container">
        <h1 class="inquiry-title">Submit an inquiry</h1>

        <div class="form-line">
          <div class="left-container">
            <v-text-field
              v-model="firstName"
              :rules="[v => !!v || 'First Name is required']"
              label="First Name"
              name="firstName"
              required
            ></v-text-field>
          </div>
          <div class="right-container">
            <v-text-field
              v-model="lastName"
              :rules="[v => !!v || 'Last Name is required']"
              label="Last Name"
              name="lastName"
              required
            ></v-text-field>
          </div>
        </div>

        <div class="form-line">
          <div class="left-container">
            <v-text-field
              label="Company Name"
              v-model="companyName"
              name="companyName"
            ></v-text-field>
          </div>
          <div class="right-container">
            <v-text-field
              label="Country"
              v-model="country"
              name="country"
            ></v-text-field>
          </div>
        </div>

        <div class="form-line">
          <div class="left-container">
            <v-text-field
              v-model="email"
              :rules="emailRules"
              label="E-mail"
              name="email"
              required
            ></v-text-field>
          </div>
          <div class="right-container">
            <v-text-field
              v-model="phone"
              :rules="phoneRules"
              label="Phone Number"
              name="phone"
              required
            ></v-text-field>
          </div>
        </div>

        <div class="form-line">
          <div class="left-container">
            <v-text-field
              label="Payment Term"
              v-model="paymentTerm"
              name="paymentTerm"
            ></v-text-field>
          </div>
          <div class="right-container">
            <v-text-field
              label="Shipment Term"
              v-model="shipmentTerm"
              name="shipmentTerm"
            ></v-text-field>
          </div>
        </div>

        <div class="form-line">
          <div class="left-container">
            <v-text-field
              label="Quantity"
              v-model="quantity"
              name="quantity"
              type="number"
            ></v-text-field>
          </div>
          <div class="right-container">
            <v-text-field
              label="Price Target"
              v-model="priceTarget"
              name="priceTarget"
              type="number"
            ></v-text-field>
          </div>
        </div>

        <div class="checkbox-container">
          <div class="checkbox-title">
            Position
          </div>
          <v-radio-group v-model="position" row class="radio-input-container">
            <v-radio
              key="1"
              label="Buyer"
              value="buyer"
              name="buyer"
              class="checkbox-item"
            ></v-radio>
            <v-radio
              key="2"
              label="Buyer's Mandate"
              value="buyersMandate"
              name="buyersMandate"
              class="checkbox-item"
            ></v-radio>
            <v-radio
              key="3"
              label="Intermediary / Consultant"
              value="intermediary|Consultant"
              name="intermediary|Consultant"
            ></v-radio>
          </v-radio-group>
        </div>

        <div>
          <v-textarea
            outlined
            name="comments"
            label="Addtional Comments"
            v-model="comments"
          ></v-textarea>
        </div>

        <div class="submit-button-container">
          <v-btn @click.prevent="submit" :disabled="!valid">Submit Inquiry</v-btn>
        </div>
      </v-container>
    </v-form>
  </div>
</template>

<script>
import emailjs from 'emailjs-com';

export default {
  name: "InquiryContent",
  mounted() {
    this.addResizeListener();
  },
  data: () => ({
    valid: false,
    firstName: "",
    lastName: "",
    email: "",
    emailRules: [
      v => !!v || "E-mail is required",
      v => /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/.test(v) || "E-mail must be valid",
    ],
    phone: "",
    phoneRules: [
      v => !!v || "Phone Number is required",
      v => /^\s*(?:\+?(\d{1,3}))?[-. (]*(\d{3})[-. )]*(\d{3})[-. ]*(\d{4})(?: *x(\d+))?\s*$/.test(v) || "Phone number must be valid"
    ],
    position: null,
    country: "",
    companyName: "",
    quantity: "",
    paymentTerm: "",
    shipmentTerm: "",
    priceTarget: "",
    comments: "",
    success: false,
    failed: false,
  }),
  methods: {
    styleElements : function (inquiryContainer) {
      if(window.innerWidth < 500) {
        inquiryContainer.style.width = "100%";
        inquiryContainer.style.border = "none";
      }
      else if (window.innerWidth < 1000) {
        inquiryContainer.style.width = "90%";
        inquiryContainer.style.border = "1px solid rgb(190, 188, 188)";
      }
      else {
        inquiryContainer.style.width = "60%";
        inquiryContainer.style.border = "1px solid rgb(190, 188, 188)";
      }
    },
    addResizeListener : function () {
      let inquiryContainer = document.querySelector('.inquiry-container');

      this.styleElements(inquiryContainer);

      window.onresize = () => {
        this.styleElements(inquiryContainer);
      }
    },
    clear : function() {
      this.$refs.form.reset();
    },
    submit : function() {
      var templateParams = {
          companyName: this.companyName,
          country: this.country,
          email: this.email,
          phone: this.phone,
          quantity: this.quantity,
          paymentTerm: this.paymentTerm,
          shipmentTerm: this.shipmentTerm,
          position: this.position,
          priceTarget: this.priceTarget,
          comments: this.comments,
      }
      emailjs.send('default_service', 'template_eFtx741h', templateParams, 'user_YxJ7rIxrLI2oK3z1cGPMO')
          .then((response) => {
            this.clear();
            this.success = true
            setTimeout(() => {
              this.success = false
            }, 5000);
            console.log('SUCCESS!', response.status, response.text)
          }, function(error) {
            this.failed = true
            setTimeout(() => {
              this.failed = false
            }, 5000);
            console.log('FAILED...', error)
          })
      // this.$refs.form.$el.submit()
      // Add in form # in email message
    }
  }
}
</script>

<style lang="scss" scoped>
  .submission-result {
    display: flex;
    align-items: center;
    position: fixed;
    top: 0;
    width: 100%;
    height: 40px;
    background: rgb(221, 239, 250);
    transition: all 2s;
    padding: 0px 20px;
    z-index: 100;
    font-weight: 300;
    font-family: "Assistant";
    font-size: 16px;
  }

  .fade-enter-active, .fade-leave-active {
    transition: opacity .5s;
  }
  .fade-enter, .fade-leave-to {
    opacity: 0;
  }

  ::v-deep .submission-result.red {
    background-color: rgba(197, 92, 92, 0.884) !important;
  }

  .inquiry {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 100%;
    margin-top: 100px;
  }

  .inquiry-title {
    font-size: 24px;
    font-weight: 300;
    letter-spacing: 1px;
    margin-bottom: 20px;
  }

  .inquiry-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 90%;
    max-width: 1000px;
    padding: 30px;
    margin-bottom: 80px;
    font-family: "Assistant";
  }

  .form-line {
    display: flex;
    flex-direction: row;
    justify-content: space-between;

    .left-container {
      margin-right: 40px;
      width: 50%;
    }

    .right-container {
      width: 50%;
    }
  }

  .checkbox-container {
    display: flex;
    flex-direction: row;
    align-items: center;
    margin-top: 10px;
    margin-bottom: 30px;

    .checkbox-title {
      margin-right: 20px;
      color: #666666;
    }

    .checkbox-item {
      margin-right: 20px;
    }
  }

  .submit-button-container {
    display: flex;
    justify-content: center;

    button {
      padding: 20px 0px !important;
      background: rgb(22, 22, 22) !important;
      width: 24%;
      min-width: 110px !important;
      color: white;
      font-size: 14px;
      font-weight: bold;
      letter-spacing: 0.8px;
      transition: all 0.3s;
      font-family: "Assistant" !important;
      text-transform: capitalize;

      &:hover {
        background: rgb(150, 148, 148) !important;
      }
    }
  }

  ::v-deep input::-webkit-outer-spin-button,
  ::v-deep input::-webkit-inner-spin-button {
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    margin: 0;
  }


  @media (max-width: 700px) {

    .inquiry-container {
      padding: 0px 8px;

      .radio-input-container {
        flex-direction: column;
        background: blue;
        padding-left: 30px;
      }
    }

    .checkbox-container {
      .checkbox-item {
        background: red;
        color: pink;
      }
    }

    .form-line {
      flex-direction: column;

      .left-container, .right-container {
        width: 100%;
        margin-right: 0px;
      }
    }

  } 
</style>
