<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>{{ lambdaMsg }}</p>
    <p><button @click="callLambda">Click here</button></p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      lambdaMsg : "Click to call func"
    }
  },
  methods: {
    callLambda() {
      fetch("/.netlify/functions/hello").then(response=>response.json()).then((json)=>{
        this.lambdaMsg = json.msg
      })
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
