<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { useClipboard, usePermission } from '@vueuse/core'

const input = ref('')

const { text, copied, copy, isSupported } = useClipboard({
  legacy:true,
})
const permissionRead = usePermission('clipboard-read')
const permissionWrite = usePermission('clipboard-write')

onMounted(async () => {
  console.log(`1`);

  // if copy something somewhere, will not get the value
  console.log(isSupported.value, copied.value, text.value)
  await copy("hello")

  console.log(copied.value, text.value) // here will be hello
})
</script>

<template>
  <div v-if="isSupported">
    <note>
      Clipboard Permission: read <b>{{ permissionRead }}</b> | write
      <b>{{ permissionWrite }}</b>
    </note>
    <p>
      Current copied: <code>{{ text || 'none' }}</code>
    </p>
    <input v-model="input" type="text">
    <button @click="copy(input)">
      Copy
    </button>
  </div>
  <p v-else>
    Your browser does not support Clipboard API
  </p>
</template>
