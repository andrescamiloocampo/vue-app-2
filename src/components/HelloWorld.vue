<template>
  <div class="hello">
    <h2>Students</h2>
    <ul class="students">
      <li v-for="student in students" v-bind:key="student.nit">
        {{ student.name }} {{ student.lastName }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'HelloWorld',
  data(){
    return {
      students: []
    };
  },
  async mounted(){
    axios.get('http://localhost:8080/index/all')
    .then(response => {
      this.students = response.data;
    })
    .catch(error => console.log(error))
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

.students{
  display: flex;
  flex-direction: column;
}
</style>
