<template>
    {{ date }}
</template>

<script setup>
    import { ref } from "vue";

    const date = ref(new Date());
</script>

<style scoped>
</style>