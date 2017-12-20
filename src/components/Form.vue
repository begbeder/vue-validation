<template>
  <div>
    <h2>Form</h2>
    <div>
       <p>Name: {{ form.name }}</p>
       <p>Select: {{ form.selected }}</p>
       <p>Email: {{ form.email }}</p>
     </div>
     <FormContainer :formData="form"></FormContainer>
  </div>
</template>

<script>
import FormContainer from './form_controls/FormContainer'

export default {
  name: 'Form',

  components: {
    FormContainer
  },

  data () {
    return {
      form: {
        email: '',
        name: '',
        selected: null,
        checked: []
      },
      show: true
    }
  },

  methods: {
    onSubmit (evt) {
      evt.preventDefault();
      alert(JSON.stringify(this.form));
    },
    onReset (evt) {
      evt.preventDefault();
      /* Reset our form values */
      this.form.email = '';
      this.form.name = '';
      this.form.food = null;
      this.form.checked = [];
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
