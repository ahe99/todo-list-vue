<template>
<div class="container">
  <list-title></list-title>
  <section>
    <input type="text" v-model="msg" @keyup.enter="createTodo"
    @input="onCreateTodo" placeholder="Keep it!...">
    <todo-list :items="items"></todo-list>
  </section>
  <div class="insetshadow"></div>
</div>
</template>

<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import { ref,reactive } from 'vue'
import TodoList from './components/TodoList.vue'
import ListTitle from './components/ListTitle.vue'
const msg = ref('')
const items = reactive([{id:0,content:'do my homework',isFinished:false,isCreated:true},{id:1,content:'do the laundry',isFinished:true,isCreated:true}])
const onCreateTodo = () => {
  if(items.length){
    if(!items[0].isCreated){
      items[0].content = msg.value
    }else{
      items.unshift({id:items.length,content:msg.value,isFinished:false,isCreated:false})
    }
  }else{
    items.unshift({id:items.length,content:msg.value,isFinished:false,isCreated:false})
  }

}
const createTodo = ()=>{
  items[0].isCreated = true
  msg.value = ''
}
</script>

<style>
@font-face {
  font-family: qingsong;
  src: url("assets/fonts/qingsong.ttf");
  font-weight: 100;
}
#app {
  /* font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale; */
  width: 100vw;
  height: 100vh;
  margin: 0;
  padding: 0;
  text-align: center;
  color: #2c3e50;
  background-color: rgb(210, 186, 255);
  font-family: 'qingsong';
  font-size: 1.2rem;
}
input::-webkit-input-placeholder {
  font-family: 'qingsong';
}

input:-ms-input-placeholder {
  font-family: 'qingsong';
}

input:-moz-placeholder {
  font-family: 'qingsong';
}

input::-moz-placeholder {
  font-family: 'qingsong';
}

.container{
  width: 450px;
  height: 550px;
  top:50%;
  left: 50%;
  transform: translate(-50%,-50%);
  border-radius: 20px;
  background-color:rgb(200, 200, 200);
  box-shadow:0px 0px 20px rgb(0, 0, 0) ;
  position: absolute;
}
.insetshadow{
  top: 0;
  width: 100%;
  height: 100%;
  position: absolute;
  border-radius: 20px;
  box-shadow:0px 0px 20px rgb(61, 61, 61) inset;
  z-index: 5;
  pointer-events: none;
}
input{
  width:99.9%;
  padding: 0;
  text-align: center;
  font-size: 1.5rem;
  box-sizing: border-box;
}
section{
  top:10%;
  height: 85%;
  position: relative;
}
</style>
