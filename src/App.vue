<script setup>
import { ref } from "vue";

let message = ref("Hello Vue");
let messageHtml = "<u>Hello Vue</u>";
let name = "content";
let checked = ref(true); // 將 checked 變數設為 ref
let refContent = ref("");
let multiSelect = ref([]);
let colorRadio = ref(null);
let colorSelect = ref("");
const colors = {
  "橘色":"orange",
  "粉色":"pink",
  "棕色":"brown"
};

const switchButton = () => {
  if (message.value === "Hello Vue" && checked.value === true) {
    message.value = "Goodbye";
    checked.value = false;
  } else {
    message.value = "Hello Vue";
    checked.value = true;
  }
};

const mouseover = () => {
  checked.value = !checked.value; // 使用取反運算符簡化
};
</script>

<template>
  <div class="image-container">
    <img src="/favicon.ico" alt="網站圖示" />
  </div>
  <main :class="checked ? 'yellow' : 'red'">
    <nav>基本導覽列</nav>
    <div class="message">
      <div>{{ message }}</div>
      <div v-html="messageHtml"></div>
      <div v-html="messageHtml.toUpperCase()"></div>
      <div :class="name">操作標籤的屬性</div>
    </div>
    <div class="button-container">
      <button @click="switchButton" class="switch-button">click me</button>
    </div>
  </main>
  <a @mouseover="mouseover" href="https://eipu.hpicorp.com.tw/repair"
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
.yellow {
  background-color: gold;
}

.red {
  background-color: red;
}

.image-container {
  display: flex;
  justify-content: center; /* 水平置中 */
  margin: 20px 0; /* 上下邊距 */
}

nav {
  background-color: aquamarine;
  margin: 10px 0;
  text-align: center; /* 將內容置中 */
  padding: 10px; /* 添加內邊距 */
}

.message {
  background-color: #dddddd;
  text-align: center; /* 將內容置中 */
  margin: 10px 0;
}

.content {
  color: brown;
  text-align: center; /* 將內容置中 */
}

.button-container {
  display: flex; /* 使容器成為 Flexbox */
  justify-content: center; /* 水平置中 */
  margin-top: 20px; /* 可選：添加上邊距 */
}

.switch-button {
  display: inline-block; /* 使其可設置 padding */
  padding: 10px 20px; /* 按鈕內邊距 */
  margin-top: 10px; /* 添加上邊距 */
}

.blue {color : blue}

.green {color : green}

.orange {color : orange}

.pink {color : pink}

.brown {color : brown}
</style>
