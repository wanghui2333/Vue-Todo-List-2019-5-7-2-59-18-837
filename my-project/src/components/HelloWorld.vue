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
      <li v-for="item in allData" :key="item">
        <div v-show="ALL">
            <label><input type="checkbox" v-on:click="CheckItem(item)" :checked="item.status"/>{{item.value}}</label>
        </div>
        <div v-show="Active && !item.status">
            <label><input type="checkbox" v-on:click="CheckItem(item)" :checked="item.status"/>{{item.value}}</label>
        </div>
        <div v-show="Complete && item.status">
            <label><input type="checkbox" v-on:click="CheckItem(item)" :checked="item.status"/>{{item.value}}</label>
        </div>
      </li>
    </ul>
    <button @click = "allOnClick">ALL</button>
    <button @click = "activeOnClick">Active</button>
    <button @click = "completeOnClick">Complete</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      title: 'Jquery To Do List',
      msg: 'Simple Todo List with adding and filter by diff status.',
      input: null,
      ALL: true,
      Active: false,
      Complete: false,
      allData: []
    }
  },
  methods: {
    increment () {
      let temp = {
        value: this.input,
        status: false
      }
      this.allData.push(temp)
    },
    allOnClick () {
      this.ALL = true
      this.Active = false
      this.Complete = false
    },
    activeOnClick () {
      this.ALL = false
      this.Active = true
      this.Complete = false
    },
    completeOnClick () {
      this.ALL = false
      this.Active = false
      this.Complete = true
    },
    CheckItem (item) {
      item.status = !item.status
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}
</style>
