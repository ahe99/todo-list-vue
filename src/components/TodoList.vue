<template>
<ul class="todolist">
  <list-item v-for='(item,index) in items' :item='item' :key='item.id' 
  @delete='deleteItem(item)' @edit="editItem(index,$event)" @finish="finishItem(index)">
  </list-item>
</ul>
</template>

<script setup>
import ListItem from './ListItem.vue'
import {ref,reactive,defineExpose} from 'vue'
const items = reactive([])
const loadLocalStorage = ()=>{
  const itemList = JSON.parse(window.localStorage.getItem('itemList'))
  if(itemList && itemList.length !== 0){//already have some
    const itemList = JSON.parse(window.localStorage.getItem('itemList'))
    for(let item of itemList){
      items.push(item)
    }
  }else{//default
    let defaultItems = [{id:0,content:'do my homework',isFinished:false,isCreated:true},{id:1,content:'do the laundry',isFinished:true,isCreated:true}]
    for(let item of defaultItems){
      items.push(item)
    }
    refreshLocalStorage()
  }
}
const refreshLocalStorage = ()=>{
  window.localStorage.setItem('itemList',JSON.stringify(items))
}
const deleteItem = (item) => {
  items.splice(items.indexOf(item),1)
  refreshLocalStorage()
}
const editItem = (index,msg)=>{
  items[index].content = msg
  items[index].isFinished = false
  refreshLocalStorage()
}
const finishItem = (index) =>{
  items[index].isFinished = !items[index].isFinished
  refreshLocalStorage()
}
defineExpose({
  items,
  loadLocalStorage,
  refreshLocalStorage
})

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