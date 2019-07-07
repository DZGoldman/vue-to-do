<template>
  <div id="app">
    <Header v-bind:length="length"/>
    <ToDoList @length-update='updateLength'/>
   
  </div>
</template>

<script>
window.globalId = 1
window.updateGlobalId = ()=>{
  return window.globalId ++ 
}
import Header from './components/Header.vue'
import ToDoList from './components/ToDoList.vue'

export default {
  name: 'app',
  components: {
    Header, ToDoList
  },
  data: ()=>(
    {length: 2}
  ),
  methods: {
    updateLength(newLength){
      this.length = newLength
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
