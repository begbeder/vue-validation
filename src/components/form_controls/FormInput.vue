<template>
  <div>
    <b-form-input
      type="text"
      v-model="formData.email"
      name="email"
      v-validate="'required|email'" 
      :class="{'input': true, 'is-danger': errors.has('email') }" 
      placeholder="Enter email">
    </b-form-input>
    <span v-show="errors.has('email')" class="help is-danger">{{ errors.first('email') }}</span>
  </div>
</template>

<script>
export default {
  name: 'FormContainer',

  inject: {
    $validator: '$validator'
  },
  
  props: {
    formData: {
      type: Object
    }
  },

  methods: {
    onSubmit (evt) {
      this.$validator.validateAll().then((result) => {
        if (result) {
          // eslint-disable-next-line
          console.log('From email Validated!');
          return;
        } else {
          console.log('errors email', this.errors)
        }

      });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
