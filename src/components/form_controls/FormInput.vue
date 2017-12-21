<template>
  <div>
    <b-form-input
      type="text"
      v-model="formData.email"
      name="email"
      v-validate:email="`${!formData.isRequired ? 'required|email' : ''}`" 
      :class="{'input': true, 'is-danger': errors.has('email') }" 
      placeholder="Enter email">
    </b-form-input>
    <span>isReq {{ formData.isRequired }}</span>
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
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
