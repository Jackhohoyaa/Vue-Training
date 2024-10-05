<template>
    <div>
      <div v-if="category.length === 0">資料載入中</div>
      <div v-else>
        <select v-model="selectedCategory">
            <option value="">請選擇</option>  
          <option v-for="item in category" :key="item.id" :value="item.id">
            {{ item.name }}
          </option>
        </select>
      </div>
    </div>
  </template>
  
  <script setup>
  import { onMounted, ref } from "vue";
  
  let category = ref([]); // 初始化为空数组
  let selectedCategory = ref(""); // 使用 ref() 使其可响应
  
  onMounted(async () => {
    try {
      let response = await fetch("https://eipu.hpicorp.com.tw/eip/public/category", {
        method:'Get',
        headers: {
          'token': `eyJhbGciOiJIUzUxMiJ9.eyJhY2NvdW50IjoiamFja19jaHVuZyIsImlhdCI6MTcyNzA3NTA2MiwiZXhwIjoxNzI3MDgyMjYyfQ.qYnSz2e5LmbW9Jm_68If3dZoG85iL4tBb8mn-LIPLePkadS1gVSw-v3diSXicUmZPaHuQ-5I9VN3ND79V6MP3w`,
          'Content-Type': 'application/json'
        }
      });
  
      if (!response.ok) {
        throw new Error("Network response was not ok");
      }
  
      let data = await response.json();
      // 提取 id 和 name 属性
      category.value = data.data.map(item => ({
        id: item.id,
        name: item.name,
      }));
  
      console.log(category.value); // 查看提取后的数据
    } catch (error) {
      console.error("Fetch error:", error);
    }
  });
  </script>
  
  <style scoped></style>
  