<template>
    <div class="header">
        <div class="title">
            {{ title }}
        </div>
        <AppScore :score="117" />
    </div>
</template>

<script setup>
    import AppScore from './Score.vue';
    const { title } = defineProps({
        title: {type: String, default: 'Запомни слово'},
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
</style>