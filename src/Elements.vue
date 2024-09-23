<script setup>
import { ref } from "vue";

let refContent = ref("");
let multiSelect = ref([]);
let colorRadio = ref(null);
let colorSelect = ref("");
const colors = {
  "橘色":"orange",
  "粉色":"pink",
  "棕色":"brown"
};


</script>

<template>
  <a @mouseover="$emit('mouseover')" href="https://eipu.hpicorp.com.tw/repair"
    >導覽連結</a
  >
  <h3>單行輸入框</h3>
  <input type="text" v-model="refContent" />
  <div>輸入內容為 : {{ refContent }}</div>
  <h3>多選框</h3>
  <input type="checkbox" value="A" v-model="multiSelect" />A
  <input type="checkbox" value="B" v-model="multiSelect" />B
  <input type="checkbox" value="C" v-model="multiSelect" />C
  <input type="checkbox" value="D" v-model="multiSelect" />D
  <div>已選擇項目 :</div>
  <ul>
    <li v-for="select in multiSelect" :key="select">結果 : {{ select }}</li>
  </ul>
  <h3>單選框</h3>
  藍色 <input type="radio" value="blue" v-model="colorRadio" /> 
  綠色 <input type="radio" value="green" v-model="colorRadio" />
  <div :class="colorRadio">使用者選擇的顏色</div>
  <h3>下拉選單</h3>
  <select v-model="colorSelect">請選擇
    <option value="">請選擇</option>
    <option v-for="(value,key) in colors" :key="key" :value="value" >{{ key }}</option>
  </select>
  <div :class="colorSelect">使用者選擇的顏色</div>
</template>

<style scoped>

.blue {color : blue}

.green {color : green}

.orange {color : orange}

.pink {color : pink}

.brown {color : brown}
</style>
