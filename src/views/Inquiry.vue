<template>
  <div class="inquiry">
    <v-form v-model="valid" ref="form" class="inquiry-container">
      <v-container class="inquiry-inner-container">
        <h1 class="inquiry-title">Submit an inquiry</h1>

        <v-text-field
          label="Company Name"
          v-model="companyName"
          outlined
          required
        ></v-text-field>

        <div class="form-line">
          <div class="left-container">
            <v-text-field
              v-model="email"
              :rules="emailRules"
              label="E-mail"
              outlined
              required
            ></v-text-field>
          </div>
          <div class="right-container">
            <v-text-field
              type="number"
              v-model="phone"
              :rules="phoneRules"
              label="Phone Number"
              outlined
              required
            ></v-text-field>
          </div>
        </div>

        <div class="position-input-container">
          <div>
            Position
          </div>
          <div class="checkbox-container">
            <v-checkbox
              v-model="checkbox"
              label="Buyer"
              value="buyer"
            ></v-checkbox>
            <v-checkbox
              v-model="checkbox"
              label="Buyer's Mandate"
              value="buyersMandate"
            ></v-checkbox>
            <v-checkbox
              v-model="checkbox"
              label="Broker"
              value="broker"
            ></v-checkbox>
          </div>
        </div>

        <v-text-field
          label="Country"
          v-model="country"
          outlined
        ></v-text-field>

        <div class="form-line">
          <div class="left-container">
            <v-text-field
              label="Payment Term"
              v-model="paymentTerm"
              outlined
            ></v-text-field>
          </div>
          <div class="right-container">
            <v-text-field
              label="Shipment Term"
              v-model="shipmentTerm"
              outlined
            ></v-text-field>
          </div>
        </div>

        <div class="form-line">
          <div class="left-container">
            <v-text-field
              label="Quantity"
              v-model="quantity"
              outlined
            ></v-text-field>
          </div>
          <div class="right-container">
            <v-text-field
              label="Price Target"
              v-model="priceTarget"
              outlined
            ></v-text-field>
          </div>
        </div>

        <div class="submit-button-container">
          <v-btn class="mr-4" @click="submit">submit</v-btn>
        </div>
      </v-container>
    </v-form>
  </div>
</template>

<script>
export default {
  name: "Inquiry",
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
    checkbox: ["buyer", "buyer's mandate", "broker"],
    country: "",
    companyName: "",
    quantity: "",
    paymentTerm: "",
    shipmentTerm: "",
    priceTarget: "",
  }),
  methods: {
    addResizeListener() {
      let checkBoxes = document.querySelector('.checkbox-container');
      let inquiryContainer = document.querySelector('.inquiry-container');

      if(window.innerWidth < 500) {
        checkBoxes.style.flexDirection = "column";
        inquiryContainer.style.width = "100%";
        inquiryContainer.style.border = "none";
      }
      else if (window.innerWidth < 1000) {
        checkBoxes.style.flexDirection = "column";
        inquiryContainer.style.width = "75%";
        inquiryContainer.style.border = "1px solid black";
      }
      else {
        checkBoxes.style.flexDirection = "row";
        inquiryContainer.style.width = "50%";
        inquiryContainer.style.border = "1px solid black";
      }

      window.onresize = function() {
        if(window.innerWidth < 500) {
          checkBoxes.style.flexDirection = "column";
          inquiryContainer.style.width = "100%";
          inquiryContainer.style.border = "none";
        }
        else if (window.innerWidth < 1000) {
          checkBoxes.style.flexDirection = "column";
          inquiryContainer.style.width = "75%";
          inquiryContainer.style.border = "1px solid black";
        }
        else {
          checkBoxes.style.flexDirection = "row";
          inquiryContainer.style.width = "50%";
          inquiryContainer.style.border = "1px solid black";
        }
      }
    },
    submit : function() {
      this.$refs.form.$el.submit()
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
    margin: 50px 0 50px 0;
  }

  .inquiry-title {
    text-align: center;
    font-size: 30px;
    margin-bottom: 20px;
  }

  .inquiry-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    border: 1px solid black;
    border-radius: 8px;
    width: 50%;
    max-width: 900px;
    padding: 30px;
  }

  .form-line {
    display: flex;
    flex-direction: row;
    justify-content: space-between;

    .left-container {
      margin-right: 20px;
      width: 50%;
    }

    .right-container {
      width: 50%;
    }
  }

  .position-input-container {
    border: 1px solid rgba(0, 0, 0, 0.42);
    color: rgba(0, 0, 0, 0.87);
    border-radius: 4px;
    margin-bottom: 34px;
    padding: 12px;

    .checkbox-container {
      display: flex;
      flex-direction: row;
      justify-content: space-around;
    }
  }

  .submit-button-container {
    display: flex;
    justify-content: center;
  }

  ::v-deep input::-webkit-outer-spin-button,
  ::v-deep input::-webkit-inner-spin-button {
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    margin: 0;
  }
</style>
