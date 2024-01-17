<script setup lang="ts">
import { convertFileSrc } from "@tauri-apps/api/tauri"
import { onMounted, ref } from "vue"
const output = ref<HTMLPreElement>()

onMounted(async () => {
  if (!output.value) throw new Error("output element not found")

  const assetUrl = convertFileSrc("/Users/corey/Desktop/thing-to-build/dist/thing-to-build.js")
  const theThing = (await import(assetUrl)).default
  console.log(`🌈 `, theThing)
  theThing(output.value)
})
</script>

<template>
  <div>Hi corey</div>
  <pre ref="output"></pre>
</template>

<style scoped></style>
