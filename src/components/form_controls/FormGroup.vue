<template>
  <div>
    <br>
    <hr>
    <b-form-input
      type="number"
      v-model.number="group.one"
      name="one"
      v-validate:group="'required|numeric'" 
      :class="{'is-danger': errors.has('one') }" 
      placeholder="Enter one">
    </b-form-input>
    <span v-show="errors.has('one')">{{ errors.first('one') }}</span>

    <b-form-input
      type="number"
      v-model.number="group.two"
      name="two"
      v-validate:group="'required|numeric'" 
      :class="{'is-danger': errors.has('two') }" 
      placeholder="Enter two">
    </b-form-input>
    <span v-show="errors.has('two')">{{ errors.first('two') }}</span>
  </div>
</template>

<script>
export default {
  name: 'FormGroup',

  inject: {
    $validator: '$validator'
  },

  data () {
    return {
      group: {
        one: null,
        two: null
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
