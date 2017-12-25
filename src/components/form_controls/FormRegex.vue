<template>
  <div>
    <br>
    <hr>
    <!-- <b-form-input
      type="text"
      v-model="phone"
      name="phoneControl" 
      v-validate="{ regex: /\(\s*\d{3}\s*\)\s*\d{3}\s*\d{2}\s*\d{2}/ }"
      :class="{'is-danger': errors.has('phoneControl') }" 
      placeholder="phone">
    </b-form-input> -->

    <masked-input 
      v-model="phone"
      name="phoneControl" 
      v-validate="{ regex: /\(\s*\d{3}\s*\)\s*\d{3}\s*\d{2}\s*\d{2}/ }" 
      mask="( 111 ) 111 11 11" 
      placeholder="Phone" 
    />
    <span v-show="errors.has('phoneControl')">Error regex: {{ errors.first('phoneControl') }}</span>
  </div>
</template>

<script>
import MaskedInput from 'vue-masked-input'

export default {
  name: 'FormRegex',

  components: {
    MaskedInput
  },

  data () {
    return {
      phone: ''
    }
  },

  methods: {}


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
