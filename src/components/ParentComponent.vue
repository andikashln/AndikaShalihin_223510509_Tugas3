<template>
    <div>
      <h1>Parent Component</h1>
      <ChildComponent @data-updated="updateDataFromChild">
        <template v-slot:default="slotProps">
          <p>Data from slot: {{ slotProps.slotData }}</p>
        </template>
      </ChildComponent>
      <p>Data from child: {{ dataFromChild }}</p>
      <button @click="clearData">Clear Data</button>
      <button @click="setDefaultData">Set Default Data</button>
    </div>
  </template>
  
  <script>
  import ChildComponent from './ChildComponent.vue';
  
  export default {
    components: {
      ChildComponent
    },
    data() {
      return {
        dataFromChild: ''
      };
    },
    methods: {
      updateDataFromChild(data) {
        this.dataFromChild = data;
      },
      clearData() {
        this.dataFromChild = '';
        this.$refs.childComponent.childData = '';
      },
      setDefaultData() {
        this.dataFromChild = 'Default Data';
        this.$refs.childComponent.childData = 'Default Data';
      }
    }
  };
  </script>
  
  <style scoped>
  button {
    margin: 5px;
  }
  </style>
  