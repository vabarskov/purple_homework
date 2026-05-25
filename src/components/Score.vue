<template>
    <div class="score-wrapper">
        <div class="score">
            {{ score }}
        </div>
        <AppIconHeart />
    </div>
</template>

<script setup>
    import AppIconHeart from "./Icons/Heart.vue";

    const { title, score } = defineProps({
        score: {type: Number, default: 0},
    });
</script>

<style scoped>
    .score-wrapper {
        padding: 12px 24px;
        display: flex;
        gap: 10px;
        align-items: center;
        justify-content: space-between;
        background-color: #CCE8FF;
        color: #008BFE;
        border-radius: 36px;
        border: none;
    }
</style>