<script setup>
const route = useRoute()

const msg = computed(() => `I'm on team ${route.params.teamSlug} and my user ID is ${route.params.userId} `)
</script>

<template>
  <p>{{ msg }}</p>
</template>