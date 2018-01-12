<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <form id="create-group" action="http://localhost:8080/groups/new" method="PUT">
      <div>
        <label>Enter a name for your group:  </label>
        <input type="text" placeholder="Group Name">
      </div>
      <div>
        <label>Enter the number of members:  </label>
        <input type="number" placeholder="Number of Members">
      </div>
      <div>
        <label>Enter member name:  </label>
        <input type="text" placeholder="Group Name">
      </div>
      <div>
        <label>Enter member email:  </label>
        <input type="email" placeholder="Email">
      </div>
      <div>
        <label>Enter member preference:  </label>
        <textarea  placeholder="Enter your preferences"></textarea>
      </div>
      <input type="submit" value="Submit" name="Submit">    <!-- APPLY V-MODEL TO THE FORM TO SUBMIT -->
    </form>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: "",
      errors:[]
    }
  },
  created: function(){
    axios.get('http://localhost:8080/groups/all').then(response => {
      this.msg.data = response.data;
    }).catch(e => {
      this.errors.push(e);
    });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
