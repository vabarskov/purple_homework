<template>
    <AppHeader />
    <div class="main-page" v-if="showMain">
        <AppButton>Начать игру</AppButton>
    </div>
    <div class="inner-page" v-else>
        <div class="cards-wrapper">
            <AppCard @rotated="console.log('rotated')" @completed="console.log('completed')" v-for="card in cards" :key="card.num" v-bind="card" />
        </div>
    </div>
</template>

<script setup>
    import AppButton from './components/Button.vue'
    import AppHeader from './components/Header.vue'
    import AppCard from './components/Card.vue'
    import { ref } from "vue";

    const showMain = ref(false);
    const cards = ref([
        {
            num: '01',
            word: 'Перевод',
            translation: 'Translation',
            state: 'closed',
            status: 'pending'
        },
        {
            num: '02',
            word: 'Машина',
            translation: 'Car',
            state: 'closed',
            status: 'false'
        },
        {
            num: '03',
            word: 'Клавиатура',
            translation: 'Keyboard',
            state: 'closed',
            status: 'true'
        },
        {
            num: '04',
            word: 'Телефон',
            translation: 'Phone',
            state: 'opened',
            status: 'false'
        },
        {
            num: '05',
            word: 'Медиатор',
            translation: 'Pick',
            state: 'opened',
            status: 'pending'
        },
    ]);
</script>

<style scoped>
    .main-page {
        display: grid;
        place-items: center;
        align-content: center;
        min-height: 100vh;
    }
    .cards-wrapper {
        display: flex;
        justify-content: flex-start;
        flex-wrap: wrap;
        column-gap: 107px;
        row-gap: 66px;
    }
</style>