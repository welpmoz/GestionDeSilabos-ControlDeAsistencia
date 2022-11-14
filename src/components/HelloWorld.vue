<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button @click="getData">Obtener Datos</button>
    <ul>
      <li v-for="(e, i) in datos" :key="i">
        Elemento {{ e }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      datos: [],
    }
  },
  methods: {
    getData() {
      axios.get('http://127.0.0.1:8000/api/semestres/')
        .then(response => {
          this.datos = response.data
          console.log(response)
        })
        .catch(erro => {
          console.log(erro)
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
