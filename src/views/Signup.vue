<template>
  <v-container>
    <v-row>
      <v-col>
        <h1>Signup</h1>
        <v-form ref="signUpForm" v-model="formValidity">
          <v-text-field
            label="Email"
            type="email"
            v-model="email"
            :rules="emailRules"
            required
          ></v-text-field>
          <v-autocomplete
            label="Which browser do you use?"
            :items="browsers"
          ></v-autocomplete>
          <v-file-input label="Attach profile picture"></v-file-input>
          <v-text-field
            label="Birthday"
            v-model="birthday"
            readonly
          ></v-text-field>
          <v-date-picker v-model="birthday"></v-date-picker>
          <v-checkbox
            v-model="agreeToTerms"
            :rules="agreeToTermsRules"
            label="Agree to terms & conditions"
            required
          ></v-checkbox>
          <v-btn class="mr-4" color="green" @click="validateForm">Validate Form</v-btn>
          <v-btn class="mr-4" type="submit" color="primary" :disabled="!formValidity">Submit</v-btn>
          <v-btn class="mr-4" color="warning" @click="resetValidation">Reset Validation</v-btn>
          <v-btn color="error" @click="resetForm">Reset</v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      formValidity: false,
      agreeToTerms: false,
      agreeToTermsRules: [
        (value) => !!value || "Please agree to terms and conditions",
      ],
      email: '',
      emailRules: [
        value => !!value || 'Email is required',
        value => value.indexOf('@') !== 0 || 'Email is invalid',
        value => value.includes('@') || 'Email should include an @ symbol',
        value => value.indexOf('.') - value.indexOf('@') > 1 || 'Email should contain a valid domain',
        value => value.indexOf('.') <= value.length - 3 || 'Email should contain a valid domain extension'
      ],
      birthday: "",
      browsers: ["Chrome", "Firefox", "Safari", "Edge", "Brave"],
    };
  },
  methods: {
    resetValidation() {
      this.$refs.signUpForm.resetValidation()
    },
    resetForm() {
      this.$refs.signUpForm.reset()
    },
    validateForm() {
      this.$refs.signUpForm.validate()
    }
  }
};
</script>

<style>
</style>