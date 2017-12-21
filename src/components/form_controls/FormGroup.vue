<template>
  <div>
    <br>
    <hr>
    <b-form-input
      type="number"
      v-model.number="group.one"
      name="one"
      @input="validate"
      v-validate="isEdit ? 'required' : ''" 
      :class="{'is-danger': errors.has('one') }" 
      placeholder="Enter one">
    </b-form-input>
    <span v-show="errors.has('one')">{{ errors.first('one') }}</span>

    <b-form-input
      type="number"
      v-model.number="group.two"
      name="two"
      @input="validate"
      v-validate="isEdit ? 'required' : ''" 
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

  computed: {
    groupField () {

    }
  },

  data () {
    return {
      group: {
        one: null,
        two: null
      },
      isEdit: false
    }
  },

  methods: {
    validate () {
      // for (let prop in this.group) {
      //   if (this.group.hasOwnProperty(prop)) {
      //     if (this.group[prop]) {
      //       this.isEdit = true
      //     }
      //   }
      // }
      if (this.group.one || this.group.two) {
         this.isEdit = true
         console.log('validate', this.isEdit)
      } else {
        this.isEdit = false
      }
      // console.log('validate', this.isEdit)
      this.$validator.validateAll()
    }
  }


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
