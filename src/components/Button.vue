<template>
    <button class="button">
        <span>
            <slot></slot>
        </span>
    </button>
</template>

<script setup>
</script>

<style scoped>
    .button {
        display: inline-block;
        text-align: center;
        color: var(--color-button);
        background-color: var(--bg-button);
        padding: 16px 10px;
        font-size: var(--big-font-size);
        font-weight: var(--default-font-weight);
        cursor: pointer;
        border-radius: 100px;
        border-color: var(--bg-button);
        border: none;
    }
    .button span {
        display: inline-block;
        min-width: 315px;
    }
    .button:hover {
        background-color: var(--bg-button-hover);
        border-color: var(--bg-button-hover);
    }
</style>