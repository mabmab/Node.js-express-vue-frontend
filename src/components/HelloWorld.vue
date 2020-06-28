<template>
  <div class="hello">
    <form action>
      <input type="text" placeholder="text" v-model="text">
      <input type="submit" value="decide" @click="submitClick">
    </form>
  </div>
</template>

<script>
import Axios from "axios";
export default {
  name: 'HelloWorld',
  date() {
    return {
      text: ''
    };
  },
  methods: {
    submitClick() {
      Axios.get(`http://192.168.1.3:3000/hoge/${this.text}`)
        .then(res => {
          console.log(res.date.name)
        })
        .chtch(err => {
          console.log(err);
        });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
