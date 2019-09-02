<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div>
      <h2>{{title}}</h2>
      <p>
        <em>{{msg}}</em>
      </p>
    </div>
    <input type="text" v-model="input">
    <button @click = "increment">Add</button>
    <ul>
      <li v-for="n in parseInt(count)" :key="n">
        <div>
            <label><input type="checkbox"/>{{data[n - 1]}}</label>
        </div>
      </li>
    </ul>
    <button>ALL</button>
    <button>Active</button>
    <button>Complete</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      title: 'Jquery To Do List',
      msg: 'Simple Todo List with adding and filter by diff status.',
      count: 0,
      input: null,
      ALL: true,
      Active: false,
      Complete: false,
      data: []
    }
  },
  methods: {
    increment () {
      this.data.push(this.input)
      this.count++
    }
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
/* li {
  display: inline-block;
  margin: 0 10px;
} */
a {
  color: #42b983;
}
</style>
