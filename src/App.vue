<script setup lang="ts">
 import { ref } from 'vue'

const newItem = ref('')
const items = ref<string[]>([])

function addItem() {
  const name = newItem.value.trim()
  if (name) {
    items.value.push(name)
    newItem.value = ''
  }
}

function removeItem(idx: number) {
  items.value.splice(idx, 1)
}
</script>

<template>
  <div class="app-bg">
    <header>
      本周待办事项
    </header>
    <ul>
      <li v-for="(item, idx) in items" :key="idx">
        <span>{{ item }}</span>
        <button class="del" @click="removeItem(idx)">删除</button>
      </li>
    </ul>
    <div class="controls">
    <input type="text" v-model="newItem" @keyup.enter="addItem" placeholder="输入商品名称">
    <button @click="addItem">新增</button>
  
    
  </div>
    
  </div>
  
    

   



  
</template>

<style scoped>

.app-bg {
  min-height: 100vh;
  width: 100%;
  background-color: #cfcfcf;
  
  display: flex;
  flex-direction: column;
  align-items: center; 
   
}
div header{
  font-size:30px;
  font-weight: bold;
  padding-left: 200px;
  padding-right: 200px;
}
ul {
  list-style: none;
  padding: 0;
}
li {
  display: flex;
  width :500px;
  
  
  justify-content: space-between;
  align-items: center;
  padding: 6px 0;
  margin-bottom: 10px;
  
  
}
li span{
  height:28px;
  width :440px;
  background-color: #ffffff;
  border-radius: 4px;
}
.del {
  background: #c53b3b;
  color: #fff;
  border: none;
  padding: 4px 10px;
  border-radius: 4px;
  cursor: pointer;
}
.controls {
  margin-top: 20px;
  display: flex;
  gap: 8px;
}
input[type="text"] { 
            flex: 1; 
            padding: 8px; 
            border: 1px solid #ddd; 
            border-radius: 4px; 
            width:420px;
          }
        button { 
            padding: 8px 14px; 
            border: none; border-radius: 4px;
            background: #1677ff; 
            color: white;
            cursor: pointer; }

  
</style>


