<template>
  <div>
    <b-form @submit="onSubmit" @reset="onReset">
      <b-form-group
        id="input-group-1"
        label="Name:"
        label-for="input-1"
        description="Department Name."
      >
        <b-form-input
          id="input-1"
          v-model="form.Name"
          type="Name"
          placeholder="Enter Department Name"
          required
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
    <b-card class="mt-3" header="Form Data Result">
      <pre class="m-0">{{ form }}</pre>
    </b-card>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        form: {
          Name: '',
        }
      }
    },
    methods: {
      onSubmit(event) {
        event.preventDefault()
        alert(JSON.stringify(this.form))
         fetch('http://localhost:9559/api/department', {
                method: 'post',
                headers: {
                    'Content-Type' : 'application/json'
                },
                body: JSON.stringify(this.form)
            }).then(function(response){
                return response.json(this.form);
            }).then(function(text){
                console.log(text);
            }).catch(function (error){
                console.error(error);
            })

      },
      onReset(event) {
        event.preventDefault()
        // Reset our form values
        this.form.Name = ''
        // Trick to reset/clear native browser form validation state
        this.show = false
        this.$nextTick(() => {
          this.show = true
        })
      }
    }
  }
</script>