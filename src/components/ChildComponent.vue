<template>
    <div class="child-component">
      <h2>Child Component</h2>
      <form @submit.prevent="sendData">
        <label for="childData">Enter Data:</label>
        <input v-model="childData" id="childData" type="text" />
        <button type="submit">Submit</button>
      </form>
      <div class="slot-container">
        <slot :slotData="childData"></slot>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ChildComponent',
    data() {
      return {
        childData: ''
      };
    },
    methods: {
      sendData() {
        this.$emit('data-updated', this.childData);
      }
    }
  }
  </script>
  
  <style scoped>
  .child-component {
    border: 1px solid #ccc;
    padding: 20px;
    margin: 10px;
  }
  .slot-container {
    border: 1px dashed #aaa;
    padding: 10px;
  }
  form {
    margin-bottom: 10px;
  }
  </style>
  