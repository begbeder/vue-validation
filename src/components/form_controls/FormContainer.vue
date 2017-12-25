<template>
  <div>
     <b-form @submit.prevent="onSubmit" @reset="onReset" v-if="formData">
      <b-form-group id="exampleInputGroup1"
                    label="Email address:"
                    label-for="exampleInput1"
                    >
        <b-form-input
          type="text"
          v-model="formData.name"
          name="name"
          v-validate="'required'" 
          :class="{'input': true, 'is-danger': errors.has('name') }" 
          placeholder="Enter name">
        </b-form-input>
        <span v-show="errors.has('name')" class="help is-danger">{{ errors.first('name') }}</span>
      </b-form-group>

      <div>
        <b-form-select 
          v-model="formData.selected" 
          :options="options"
          name="selected"
          v-validate="'required'" 
          :class="{'input': true, 'is-danger': errors.has('selected') }"
          class="mb-3"
          placeholder="Select variant"
          >
        </b-form-select>
        <span v-show="errors.has('selected')" class="help is-danger">{{ errors.first('selected') }}</span>
      </div>

      <form-input :formData="formData"></form-input>

      <form-local></form-local>
      <br>

      <form-group></form-group>
      <br>

      <form-regex></form-regex>
      <br>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
  </div>
</template>

<script>
import FormInput from './FormInput'
import FormLocal from './FormLocal'
import FormGroup from './FormGroup'
import FormRegex from './FormRegex'

export default {
  name: 'FormContainer',

  components: {
    FormInput,
    FormLocal,
    FormGroup,
    FormRegex
  },

  data () {
    return {
      show: true,
      options: [
        { text: '1', value: 1 },
        { text: '2', value: 2 },
        { text: '3', value: 3 }
      ],
    }
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
          console.log('From Validated!');
          return;
        } else {
          console.log('errors', this.errors)
        }

      });
    },
    onReset (evt) {
      evt.preventDefault();
      /* Reset our form values */
      this.formData.email = '';
      this.formData.name = '';
      this.formData.food = null;
      this.formData.checked = [];
      /* Trick to reset/clear native browser form validation state */
      this.show = false;
      this.$nextTick(() => { this.show = true });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
