<template>
    <button 
        class="v-button"
        :class="{
            'v-button--wide': wide,
            'v-button--plain': plain,
            [`v-button--size-${size}`]: size,
            [`v-button--theme-${theme}`]: theme
        }"
        :disabled="disabled"
    >
        <slot/>
    </button>
</template>

<script setup>
    defineProps({
        theme: {
            type: String
        },
        size: {
            type: String
        },
        disabled: {
            type: Boolean
        },
        wide: {
            type: Boolean
        },
        plain: {
            type: Boolean
        }
    });
</script>

<style>
    .v-button {
        border: 1px solid;
    }

    .v-button--wide {
        display: block;
        width: 100%;
    }

    .v-button:disabled {
        cursor: not-allowed;
        opacity: .6;
    }

    .v-button--theme-primary {
        background-color: #282828;
        border-color: var(--color-orange);

        color: var(--color-white);
    }

    .v-button--theme-primary:hover {
        background-color: #F9C887;
        border-color: #F9C887;
        color: var(--color-black);
    }

    .v-button--theme-secondary {
        background-color: transparent;
        background-color: var(--color-orange);

        color: var(--color-black);
    }

    .v-button--size-medium {
        padding: 6px 8px;
    }

    .v-button--size-large {
        padding: 8px 10px;
    }
</style>