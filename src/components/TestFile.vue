<template>
  <div class="h-full w-full p-10">
    <a-button @click="chooseFilePath">Choose Path</a-button>
    <a-button style="margin-left: 10px" type="primary" @click="clickFile"
      >Get All Files</a-button
    >
    <div class="p-2 font-bold text-lg">currentPath: {{ currentPath }}</div>
    <ul class="p-2">
      <li v-for="(item, index) in fileList" :key="index">{{ item }}</li>
    </ul>
  </div>
</template>

<script lang="ts" setup>
import { open } from "@tauri-apps/api/dialog";
import { appDir } from "@tauri-apps/api/path";
import { readDir, BaseDirectory } from "@tauri-apps/api/fs";
import { ref } from "vue";
import { e } from "@tauri-apps/api/fs-4bb77382";
const currentPath = ref("");
const fileList = ref<string[]>([]);
const chooseFilePath = async () => {
  // Open a selection dialog for directories
  const selected = await open({
    directory: true,
    // multiple: true,
    defaultPath: await appDir(),
  });
  if (Array.isArray(selected)) {
    // user selected multiple directories
  } else if (selected === null) {
    // user cancelled the selection
  } else {
    currentPath.value = selected;
  }
};

function processEntries(entries: e[]) {
  for (const entry of entries) {
    fileList.value.push(entry.path);
    console.log(`Entry: ${entry.path}`);
    if (entry.children) {
      processEntries(entry.children);
    }
  }
}
const clickFile = async () => {
  if (!currentPath.value) return;
  fileList.value = [];
  const entries = await readDir(currentPath.value, {
    dir: BaseDirectory.AppData,
    recursive: true,
  });
  processEntries(entries);
};
</script>

<style scoped lang="less"></style>
