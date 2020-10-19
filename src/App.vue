<template>
<div id="app">
  <h1>To-do List</h1>
  <form v-on:submit.prevent="addNewItem">
    <input id="new-item" type="text" v-model="newItem">
    <input type="radio" name="priority" id="high" value="true" v-model="picked">
    <label for="high">High</label>
    <input type="radio" name="priority" id="low" value="false" v-model="picked">
    <label for="low">Low</label>
    <input type="submit" value="Add to-do">
  </form>

  <ul>
    <li v-for="(item, index) in items" :key="index" :class="item.highPriority ? 'high-priority' : 'low-priority'">
      <span>{{ item.name }}</span>
    </li>


  </ul>
</div>  
</template>

<script>
export default {
  data() {
    return {
      items: [
        {name: "Add PDA evidence", highPriority: true},
        {name: "Cook the tea", highPriority: true},
        {name: "De-scale kettle", highPriority: true},
        {name: "Invent time machine", priority: false},   
      ],
      newItem: "",
      highPriority: false
    }
  },
  methods: {
    addNewItem: function() {
      this.items.push({
        name: this.newItem,
        highPriority: false
        });
        this.newItem =""
  },
  markHighPriority: function(index) {
    this.items[index].highPriority = true;
  }
}
}
</script>

<style>
#app {
  width: 60%;
  margin: 0 auto;
  font-family: 'Lato', sans-serif;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

li {
  margin: 20px 0;
  padding: 10px;
  display: flex;
  justify-content: space-between;
}

li span {
  padding: 8px;
}

li button {
  background: #f2360c;
  color: #fff;
  border: none;
  padding: 10px;
  cursor: pointer;
}

li.high-priority {
  border: 2px solid #1a681e;
  color: #1a681e;
}

li.low-priority {
  border: 2px solid #f2360c;
}

input[type="text"] {
  padding: 10px;
  width: 50%;
  margin:5px;
}

button, input[type="submit"]{
  margin: 5px;
  padding: 10px;
  background: #000;
  color: #fff;
  cursor: pointer;
  border: 1px solid #000;
}

</style>