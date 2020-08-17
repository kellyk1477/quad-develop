<template>
  <div class="inquiry">
    <h1>This is an inquiry page</h1>
    <v-form v-model="valid" ref="form">
      <v-container>
        <v-text-field
          label="Company Name"
          v-model="companyName"
          outlined
          required
        ></v-text-field>
        <v-text-field
          v-model="email"
          :rules="emailRules"
          label="E-mail"
          outlined
          required
        ></v-text-field>
        <v-text-field
          type="number"
          v-model="phone"
          :rules="phoneRules"
          label="Phone Number"
          outlined
          required
        ></v-text-field>
        <div class="position-input-container">
          <div>
            Position
          </div>
          <v-checkbox
            v-model="checkbox"
            :label="`Buyer`"
          ></v-checkbox>
          <v-checkbox
            v-model="checkbox"
            :label="`Buyer's Mandate`"
          ></v-checkbox>
          <v-checkbox
            v-model="checkbox"
            :label="`Broker`"
          ></v-checkbox>
        </div>
        <v-text-field
          label="Country"
          v-model="country"
          outlined
        ></v-text-field>
        <v-text-field
          label="Payment Term"
          v-model="paymentTerm"
          outlined
        ></v-text-field>
        <v-text-field
          label="Shipment Term"
          v-model="shipmentTerm"
          outlined
        ></v-text-field>
        <v-text-field
          label="Quantity"
          v-model="quantity"
          outlined
        ></v-text-field>
        <v-text-field
          label="Price Target"
          v-model="priceTarget"
          outlined
        ></v-text-field>
        <v-btn class="mr-4" @click="submit">submit</v-btn>
      </v-container>
    </v-form>
  </div>
</template>

<script>
export default {
  name: "Inquiry",
  data: () => ({
    valid: false,
    email: "",
    emailRules: [
      v => !!v || "E-mail is required",
      v => /.+@.+/.test(v) || "E-mail must be valid",
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
  }
  .inquiry-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    border: 1px solid black;

    .inquiry-input {
      border: 1px solid grey;
      border-radius: 8px;
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
