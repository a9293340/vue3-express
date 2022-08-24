<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button type="button" name="button" v-on:click="getmsg">get</button>
    <button type="button" name="button" v-on:click="postmsg">post</button>
  </div>
</template>

<script>
import {getCurrentInstance} from "vue";
import axios from "axios";

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  setup(){
    const { proxy } = getCurrentInstance()

    const getmsg = () => {
      axios.get('/api/personal?name=MUKI').then((res) => {
        console.log('res = ',res)
      } )
    }
    const postmsg = () => {
      axios.post('/api/favorite', {name: 'money'}).then(res => {
        console.log('post res = ', res)
      })
    }

    return{
      getmsg,
      postmsg
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
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
