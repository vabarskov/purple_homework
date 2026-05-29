<template>
    <div class="card">
        <div class="card__num">{{ props.num }}</div>
        <div class="card__pin" v-if="isCompleted">
            <AppTrueIcon v-if="isTrue" />
            <AppFalseIcon v-else />
        </div>
        <div class="card__content">
            {{ props.word }}
        </div>
        <div class="card__bottom" @click="rotate" v-if="!rotated">
            {{ props.rotateName }}
        </div>
        <template v-else>
            <div class="card__bottom__pins" v-if="!isCompleted && rotated">
                <AppTrueIcon />
                <AppFalseIcon />
            </div>
            <div class="card__bottom" @click="complete" v-else>
                {{ props.completeName }}
            </div>
        </template>
    </div>
</template>

<script setup>
    import { computed } from "vue";

    import AppTrueIcon from './Icons/True.vue';
    import AppFalseIcon from './Icons/False.vue';

    const props = defineProps({
        num: {type: String, default: '01'},
        word: {type: String, default: 'Имя карточки'},
        translation: {type: String, default: 'Card name'},
        rotateName: {type: String, default: 'Перевернуть'},
        completeName: {type: String, default: 'Завершено'},
        state: {type: String, default: 'closed'},
        status: {type: String, default: 'pending'}
    });
    const isCompleted = computed(() => {
        return props.status !== 'pending'
    });
    const isTrue = computed(() => {
        return props.status === 'true'
    });
    const rotated = computed(() => {
        return props.state === 'opened'
    });
    function rotate() {
        emit('rotated');
    }
    function complete() {
        emit('completed');
    }
    const emit = defineEmits({
        rotated() {
            return true;
        },
        completed() {
            return true;
        },
    });
</script>

<style scoped>
    .card {
        position: relative;
        min-width: 250px;
        height: 376px;
        background: var(--color-button);
        border-radius: 30px;
        padding: 40px 30px;
    }

    .card::before {
        content: "";
        position: absolute;
        inset: 28px 19px;
        border: 1px solid #b8d8ff;
        border-radius: 14px;
        z-index: 1;
    }

    .card__num {
        position: absolute;
        top: 20px;
        left: 35px;
        background: #f7f7f7;
        z-index: 2;
        font-size: 14px;
    }

    .card__bottom {
        position: absolute;
        bottom: 19px;
        left: 50%;
        transform: translateX(-50%);
        background: #f7f7f7;
        z-index: 2;
        font-weight: var(--bold-font-weight);
        font-size: 12px;
        line-height: 18px;
        letter-spacing: 12%;
        text-transform: uppercase;
        cursor: pointer;
    }

    .card__content {
        position: absolute;
        inset: 0;
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 2;
        font-size: 18px;
    }

    .card__pin {
        position: absolute;
        left: calc(50% - 18px);
        top: 15px;
        width: 36px;
        height: 36px;
        z-index: 2;
    }

    .card__pin svg {
        width: 100%;
        height: 100%;
    }

    .card__bottom__pins {
        position: absolute;
        bottom: 16px;
        padding-left: 5px;
        padding-right: 5px;
        left: calc(50% - 45px);
        display: flex;
        z-index: 2;
        background: var(--color-button);
    }

    .card__bottom__pins svg {
        width: 24px;
        height: 24px;
    }

    .card__bottom__pins svg:first-child {
        margin-right: 32px;
    }

</style>