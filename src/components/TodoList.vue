<template>
  <input type="text" @change="addToList" v-model="text">
  <ul>
    <li v-for="(item, index) in list" :key="index">
     <span> {{item}} </span>
     <span @click="deleteFromList(index)"> || delete</span>
    </li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      list: [],
      text: ''
    }
  },
  created() {
    this.list = JSON.parse(localStorage.getItem('list')) || [];
  },
  methods: {
    addtoList() {
      this.list.unshift(this.text);
      this.updateLocalStorage();
      this.text = '';
    },
    deleteFromList(index) {
      this.list.splice(index, 1);
      this.updateLocalStorage();
    },
    updateLocalStorage() {
      localStorage.setItem('list', JSON.stringify(this.list));
    }
  }
}
</script>

<style>

</style>