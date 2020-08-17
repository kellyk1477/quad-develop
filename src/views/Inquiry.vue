<template>
  <div class="inquiry">
    <v-form v-model="valid" ref="form" class="inquiry-container">
      <v-container class="inquiry-inner-container">
        <h1 class="inquiry-title">Submit an inquiry</h1>

        <div class="form-line">
          <div class="left-container">
            <v-text-field
              label="Company Name"
              v-model="companyName"
              required
            ></v-text-field>
          </div>
          <div class="right-container">
            <v-text-field
              label="Country"
              v-model="country"
            ></v-text-field>
          </div>
        </div>
        <div class="form-line">
          <div class="left-container">
            <v-text-field
              v-model="email"
              :rules="emailRules"
              label="E-mail"
              required
            ></v-text-field>
          </div>
          <div class="right-container">
            <v-text-field
              type="number"
              v-model="phone"
              :rules="phoneRules"
              label="Phone Number"
              required
            ></v-text-field>
          </div>
        </div>

        <div class="form-line">
          <div class="left-container">
            <v-text-field
              label="Payment Term"
              v-model="paymentTerm"
            ></v-text-field>
          </div>
          <div class="right-container">
            <v-text-field
              label="Shipment Term"
              v-model="shipmentTerm"
            ></v-text-field>
          </div>
        </div>

        <div class="form-line">
          <div class="left-container">
            <v-text-field
              label="Quantity"
              v-model="quantity"
            ></v-text-field>
          </div>
          <div class="right-container">
            <v-text-field
              label="Price Target"
              v-model="priceTarget"
            ></v-text-field>
          </div>
        </div>

          <div class="checkbox-container">
            <div class="checkbox-title">
              Position
            </div>
            <v-radio-group v-model="position" row>
              <v-radio
                key="1"
                label="Buyer"
                value="buyer"
                class="checkbox-item"
              ></v-radio>
              <v-radio
                key="2"
                label="Buyer's Mandate"
                value="buyersMandate"
                class="checkbox-item"
              ></v-radio>
              <v-radio
                key="3"
                label="Broker"
                value="broker"
              ></v-radio>
            </v-radio-group>
          </div>

        <div class="submit-button-container">
          <button @click.prevent="submit">Submit Inquiry</button>
        </div>
      </v-container>
    </v-form>
    <Footer />
  </div>
</template>

<script>
import emailjs from 'emailjs-com';
import Footer from '../components/Footer.vue'

export default {
  name: "Inquiry",
  components: {
    Footer,
  },
  mounted() {
    this.addResizeListener()
  },
  data: () => ({
    valid: false,
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
    submit : function() {
      var templateParams = {
          companyName: this.companyName,
          country: this.country,
          email: this.email,
          phone: this.phone,
          quantity: this.quantity,
          paymentTerm: this.paymentTerm,
          shipmentTerm: this.shipmentTerm,
          position: this.checkbox,
          priceTarget: this.priceTarget,
      }
      emailjs.send('default_service', 'template_eFtx741h', templateParams, 'user_YxJ7rIxrLI2oK3z1cGPMO')
          .then(function(response) {
            console.log('SUCCESS!', response.status, response.text)
            // alert('Success');
          }, function(error) {
            console.log('FAILED...', error)
          })
      // this.$refs.form.$el.submit()
      // Add in form # in email message
    }
  }
}
</script>

<style lang="scss" scoped>
  .inquiry {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 100%;
    margin: 50px 0 0 0;
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
      padding: 11px 20px;
      background: black;
      width: 50%;
      color: white;
      font-size: 14px;
      font-weight: bold;
      letter-spacing: 0.8px;
      transition: all 0.3s;
      border-radius: 5px;

      &:hover {
        background: rgb(150, 148, 148);
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
</style>
