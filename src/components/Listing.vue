<template>
  <div class="hello">
    <h1>A Quick To-Do List</h1>
    <form @submit.prevent="addItem">
      <input type="text" v-model="item"/>
      <input type="submit" value="add">
    </form>
    <p v-if="item === ''">You haven't input anything</p>
    <p v-text="item"></p>
    <ul>
      <li v-for="(item, index) in list_items" :key='item'>{{ item.item }} <span style="cursor: pointer; color: darkred" v-on:click="removeItem(index)">&#8854;</span></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Listing',
  data () {
    return {
      list_items: [
        {'item': 'Learn Vue'},
        {'item': 'Make Webapps'},
        {'item': 'Be Happy'}
      ],
      item: ''
    }
  },
  methods: {
    addItem () {
      this.list_items.push({item: this.item})
      this.item = ''
    },
    removeItem (toRemove) {
      this.list_items.splice(toRemove, 1)
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
  list-style-position: inside;
  padding: 0;
}
li {
  margin: 0 10px;
}
input[type=text] {
  width: 50%;
  padding: .5% .5%;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
}
input[type=text]:focus {
  outline: none;
  border: 2px solid black;

}
input[type=submit] {
  background-color: #6c6ecf;
  border: none;
  color: white;
  padding: .5% .5%;
  cursor: pointer;
  box-sizing: border-box;
  -moz-box-sizing: border-box
}
a {
  color: #31925b;
}
</style>
