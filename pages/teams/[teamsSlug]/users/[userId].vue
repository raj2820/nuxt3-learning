<template>
  <p>
   {{ message }}
  </p>
</template>
<script setup>
import { computed } from 'vue';

const route = useRoute();
const message = computed(() => ` I'am on team ${route.params.teamSlug}
    and my user id is ${route.params.userId }`);
</script>