<script setup>
import { ref } from "vue";

const props = defineProps(["checked", "color", "backgroundColor", "title"]);
const emit = defineEmits(); // 导入 emit

let message = ref("Hello Vue");
let messageHtml = "<u>Hello Vue</u>";
let name = "content";

const switchButton = () => {
  if (message.value === "Hello Vue" && props.checked) {
    message.value = "Goodbye";
    emit('update:checked', false);
  } else {
    message.value = "Hello Vue";
    emit('update:checked', true);
  }
};

</script>

<template>
  <main :class="props.checked ? 'yellow' : 'red'">
    <nav>基本導覽列</nav>
    <div class="message">
      <div :style="{color: color, backgroundColor: backgroundColor}">{{ title }}</div>  
      <div>{{ message }}</div>
      <div v-html="messageHtml"></div>
      <div v-html="messageHtml.toUpperCase()"></div>
      <div :class="name">操作標籤的屬性</div>
    </div>
    <div class="button-container">
      <button @click="switchButton" class="switch-button">click me</button>
    </div>
  </main>
</template>

<style scoped>
.yellow {
  background-color: gold;
}
.red {
  background-color: red;
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
</style>
