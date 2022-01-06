<template>
  <li class="listitem"
  :class='{preview:!item.isCreated}' 
  @click="$emit('finish')"> 
    <p :class='{finished:item.isFinished}' v-if="!onEdit">
      {{item.content}}
    </p>
    <input type="text" v-model="msg" @keyup.enter="submitEditItem" v-else>
    <item-tool @edit='onEditItem' @delete="$emit('delete')" v-if="!onEdit"></item-tool>
  </li>
</template>

<script setup>
import { ref } from 'vue'
import ItemTool from './ItemTool.vue'

const emit = defineEmits(['edit','finish'])
const props = defineProps({
  item: Object})
const onEdit = ref(false)
const msg = ref('')
const onEditItem = () => {
  onEdit.value = true;  
}
const submitEditItem = () => {
  emit('edit',msg.value)
  msg.value = ''
  onEdit.value = false;
}
</script>

<style scoped>
.listitem{
  width: 100%;
  margin-bottom: 5px;
  background-color: rgba(255, 255, 255, 0.7);
  box-sizing: border-box;
  list-style: none;
  font-size: 1.5rem;
  cursor: pointer;
  transition: 1.1s;
}
.listitem:hover{
  color:rgb(136, 200, 243);
  background-color: rgba(255, 255, 255, 1);

}
.listitem p{
  margin:0;
  padding: 0;
  display: inline-block;
  pointer-events: none;
}
.finished {
  text-decoration: line-through;
}
.preview{
  opacity: 0.4;
}
</style>