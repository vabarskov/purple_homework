<template>
    <div class="main-page">
        <AppButton>Начать игру</AppButton>
    </div>
</template>

<script setup>
    import AppButton from './components/Button.vue'
</script>

<style scoped>
    .main-page {
        display: grid;
        place-items: center;
        align-content: center;
        min-height: 100vh;
    }
</style>