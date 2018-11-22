<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      For a guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.
    </p>
    <h3>Installed CLI Plugins</h3>
    <ul id="example-1">
      <li v-for="item in Products">
        {{ item.Producto }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
import Products from '../data/products.json';
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
    created() {
    //this.getData();
  },
  data()
  {
       return {  Products}
  },
  methods: {
    getData() {
       axios({
        method: "GET",
        url: "../data/products.js"
      })
        .then(response => {
          console.log("success");
             //Api from amdocs has projections
            var rawData = response.data;
            this.items = rawData;
        })
        .catch(e => {
          console.log("error");
          console.log(e);
         // this.errors.push(e);
        });
    }
  }

}
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
