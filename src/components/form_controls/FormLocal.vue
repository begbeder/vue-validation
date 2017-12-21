<template>
  <div>
    <b-form-input
      type="text"
      v-model="local"
      name="local"
      v-validate="`${isRequired ? 'required|alpha' : ''}`" 
      :class="{'is-danger': errors.has('local') }" 
      placeholder="Enter local">
    </b-form-input>
    
    <span v-show="errors.has('local')" class="help is-danger">{{ errors.first('local') }}</span>

    <b-form-checkbox
     v-model="isRequired"
     unchecked-value="false">
    </b-form-checkbox>
    <span>isRequiredLocal: {{ isRequired }}</span>
  </div>
</template>

<script>
export default {
  name: 'FormLocal',

  inject: {
    $validator: '$validator'
  },

  data () {
    return {
      local: null,
      isRequired: true
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
