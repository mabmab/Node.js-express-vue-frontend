<template>
  <div class="hello">
    <b-form inline @submit="onSubmit">
      <b-form-input type="text" placeholder="text" v-model="name"/>
      <b-button type="submit" variant="primary">Submit</b-button>
      <span>{{ response }}</span>
    </b-form>
  </div>
</template>

<script>
import Axios from "axios";
export default {
  name: 'HelloWorld',
  date() {
    return {
      _name: ''
    };
  },
  computed: {
    name: {
      get () {
        return this._name
      },
      set (value) {
        this._name = value
      }
    }
  },
  props:
  {
    response: String
  },
  methods: {
    async onSubmit(evt) {
      evt.preventDefault();
      await Axios.get(`http://192.168.1.3:3000/hoge/${this._name}`)
        .then(res => {
          this.response = "Result = " + res.data.result;
          console.log(this.response);
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
