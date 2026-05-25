<template>
    <div class="header">
        <div class="title">
            {{ title }}
        </div>
        <div class="score-wrapper">
            <div class="score">
                {{ score }}
            </div>
            <AppIconHeart />
        </div>
    </div>
</template>

<script setup>
    import AppIconHeart from './Icons/Heart.vue';
    const { title, score } = defineProps({
        title: {type: String, default: 'Запомни слово'},
        score: {type: Number, default: 0},
    });
</script>

<style scoped>
    .header {
        padding: 49px 62px 49px 66px;
        display: flex;
        justify-content: space-between;
        font-size: var(--small-font-size);
        line-height: var(--small-line-height);
        font-weight: var(--bold-font-weight);
        text-transform: uppercase;
        align-items: center;
    }
    .title {
        letter-spacing: 12%;
    }
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