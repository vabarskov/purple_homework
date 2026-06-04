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
    const cards = ref([]);
    async function loadCards() {
        let cardsFetch = await fetch('http://localhost:8080/api/random-words');
        cardsFetch = await cardsFetch.json();
        let i = 1;
        for (let card of cardsFetch) {
            let cardOb = {};
            if (i < 10) {
                cardOb.num = '0' + i.toString();
            } else {
                cardOb.num = i.toString();
            }
            cardOb.word = card.translation;
            cardOb.translation = card.word;
            cardOb.state ='closed';
            cardOb.status = 'pending';
            cards.value.push(cardOb);
            i++;
        }
    };
    loadCards();
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