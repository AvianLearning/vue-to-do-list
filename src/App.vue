<template>
<div id="app">
  <h1>To-do List</h1>
  <form v-on:submit.prevent="addNewItem">
    <input id="new-item" type="text" v-model="newItem">
    <!-- <input type="radio" name="priority" id="high" value="high" checked>
    <label for="high">High</label>
    <input type="radio" name="priority" id="low" value="low" checked>
    <label for="low">Low</label> -->
    <input type="submit" value="Add to-do">
  </form>

  <ul>
    <li v-for="(item, index) in items" :key="index">
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
        {name: "Add PDA evidence", priority: "High"},
        {name: "Cook the tea", priority: "High"},
        {name: "De-scale kettle", priority: "Low"},
        {name: "Invent time machine", priority: "High"},   
      ],
      newItem: ""
    }
  },
  methods: {
    addNewItem: function() {
      this.items.push({
        name: this.newItem,
        priority: "Low"
        });
        this.newItem =""
  }
}
}
</script>

<style>

</style>