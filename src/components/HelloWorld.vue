<template>
  <div class="hello">
    <b-form inline @submit="onSubmit">
      <b-form-input type="text" placeholder="text" v-model="name"/>
      <b-button type="submit" variant="primary">Submit</b-button>
      <b-card title="Result"><span>{{ response }}</span></b-card>
    </b-form>
  </div>
</template>

<script>
import Axios from 'axios';
export default {
  name: 'HelloWorld',
  data() {
    return {
      name: '',
      response: 'wait...'
    };
  },
  methods: {
    async onSubmit(evt) {
      evt.preventDefault();
      this.response = 'wait...'
      await Axios.get(`http://192.168.1.3:3000/hoge/${this.name}`)
        .then(res => {
          this.response = res.data.result;
          console.log('Result = ' + this.response);
        })
        .catch(err => {
          console.log(err);
        });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
