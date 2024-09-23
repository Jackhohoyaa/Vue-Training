<script setup>
import {ref} from "vue";
import Icon from "./Icon.vue";
import Main from "./Main.vue";
import Elements from "./Elements.vue";
let checked = ref(true);

const mouseover = () => {
  checked.value = !checked.value; // 使用取反運算符簡化
};

</script>

<template>
  <Icon></Icon>
  <Main color="white" backgroundColor="gray" title="這是標題" :checked="checked" @update:checked="checked = $event" />
  <Elements @mouseover="mouseover"></Elements>
</template>

<style scoped>
</style>
