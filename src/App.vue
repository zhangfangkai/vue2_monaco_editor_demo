<template>
  <div id="app">
    <MonacoEditor/>
  </div>
</template>

<script>
import MonacoEditor from './components/MonacoEditor.vue';
// import MymonacoEditor from './components/MymonacoEditor.vue';
export default {
  name: 'App',
  components: {
    MonacoEditor
  }
}
</script>

<style>
#app {
  color: #2c3e50;
  margin-top: 60px;
}
</style>
