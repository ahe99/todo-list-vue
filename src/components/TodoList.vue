<template>
<ul class="todolist">
  <list-item v-for='item in items' :item='item' :key='item.id' @delete='deleteItem(item)'></list-item>
</ul>
</template>

<script setup>
import ListItem from './ListItem.vue'
import {ref,defineProps} from 'vue'

const props=defineProps({items:Object})
const deleteItem = (item) => {
  props.items.splice(props.items.indexOf(item),1)
}
</script>

<style>
.todolist{
  width: 100%;
  height: 75%;
  left: 50%;
  margin: 0;
  margin-top: 5px;
  padding: 0;
  transform: translateX(-50%);
  position: absolute;
  overflow-y: scroll;
  overflow-x: hidden;
}
/* .todolist::-webkit-scrollbar {
  display: none;
} 
.todolist {
  -ms-overflow-style: none;  
  scrollbar-width: none;
}*/
</style>