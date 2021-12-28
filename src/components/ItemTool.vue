<template>
  <span class="itemtool">
    <button @click.stop="$emit('edit')"><img src="../assets/edit.png" alt=""></button>
    <button @click.stop="$emit('delete')"><img src="../assets/delete.png" alt=""></button>
  </span>
</template>

<script setup>
</script>

<style>
.itemtool{
  right: 5px;
  position: absolute;
}
.itemtool button{
  cursor: pointer;
}
.itemtool button img{
  height: 0.8rem;
  width: auto;
}
</style>