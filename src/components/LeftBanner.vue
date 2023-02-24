<template>
  <div class="h-full w-full bg-[#F9FAFB] py-10" data-tauri-drag-region>
    <img
      src="../assets/user.png"
      alt=""
      class="md:w-16 w-9 rounded-full mx-auto"
    />
    <div class="mt-5 hidden md:flex px-12 align-middle">
      <div class="flex-grow">
        <a-button type="text" block class="text-[#f5f5f5]"> 升级</a-button>
      </div>
      <div class="flex-grow-0">
        <a-divider
          type="vertical"
          style="height: 20px; background-color: #f2f2f2"
        />
      </div>
      <div class="flex-grow">
        <a-button type="text" block class="text-[#f5f5f5]"> 同步</a-button>
      </div>
    </div>
    <div class="w-28 mx-auto hidden md:block">
      <a-button type="primary" block title="新建">
        <template #icon><plus-outlined /></template
      ></a-button>
    </div>
    <div class="md:hidden text-center my-10">
      <a-button type="primary">
        <template #icon><PlusOutlined /></template>
      </a-button>
    </div>
    <MenuBar />
  </div>
</template>

<script lang="ts" setup>
import MenuBar from "./MenuBar.vue";
import { PlusOutlined } from "@ant-design/icons-vue";

</script>

<style scoped lang="less"></style>
