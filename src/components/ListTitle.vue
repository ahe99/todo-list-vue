<template>
<header id='title'>
  <h1>{{title}}</h1>
</header>
</template>

<script setup>
const title = 'My ToDo List!'

</script>

<style scoped>
#title{
  top:5%;
  height: 15%;
  position: relative;
  background-color: rgba(240, 240, 240,0.7);
}
h1{
  padding: 0;
  margin: 0;
  top:50%;
  transform: translateY(-50%);
  position: relative;
}
</style>