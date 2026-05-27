<template>
    <AppHeader />
    <div class="main-page" v-if="showMain">
        <AppButton>Начать игру</AppButton>
    </div>
    <div class="inner-page" v-else>
        <div class="cards-wrapper">
            <AppCard @rotated="console.log('rotated')" @completed="console.log('completed')" v-bind="card" />
        </div>
    </div>
</template>

<script setup>
    import AppButton from './components/Button.vue'
    import AppHeader from './components/Header.vue'
    import AppCard from './components/Card.vue'
    import { ref } from "vue";

    const showMain = ref(false);
    const card = ref({
        num: '03',
        word: 'Перевод',
        translation: 'Translation',
        state: 'closed',
        status: 'pending'
    });
</script>

<style scoped>
    .main-page {
        display: grid;
        place-items: center;
        align-content: center;
        min-height: 100vh;
    }
</style>