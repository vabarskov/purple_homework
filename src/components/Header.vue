<template>
    <div class="header">
        <div class="title">
            {{ title }}
        </div>
        <AppScore v-bind:score="score" />
    </div>
</template>

<script setup>
    import AppScore from './Score.vue';
    import {ref} from "vue";
    const { title } = defineProps({
        title: {type: String, default: 'Запомни слово'},
    });
    const score = ref(10);
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