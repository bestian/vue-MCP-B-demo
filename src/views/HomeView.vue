<script setup lang="ts">
import { onMounted } from 'vue';
import { z } from 'zod';
import TheWelcome from '../components/TheWelcome.vue'


// eslint-disable-next-line @typescript-eslint/no-explicit-any
const props = defineProps<{ server: any }>();

onMounted(() => {
  props.server.tool('sayHello', 'Says hello', {
    name: z.string()
  }, async ({ name }: { name: string }) => ({
    content: [{ type: 'text', text: `Hello ${name}!` }]
  }));
});



</script>

<template>
  <main>
    <TheWelcome />
  </main>
</template>
