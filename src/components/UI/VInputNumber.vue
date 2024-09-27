<template>
    <div class="v-input-number">
        <button class="input--buttons" @click="onDecrement" :disabled="disabled">—</button>

        <input class="cart-number" type="number" readonly v-model="modelValue" 
    background-color="transparent"
    border="0px"
    width="10px">

        <button class="input--buttons" @click="onIncrement" :disabled="disabled">+</button>
    </div>
</template>

<script setup>
    const props = defineProps({
        theme: {
            type: String
        },
        size: {
            type: String
        },
        disabled: {
            type: Boolean
        },
        min: {
            type: Number,
            default: 0
        },
        max: {
            type: Number,
            default: Infinity
        }
    });

    const modelValue = defineModel({
        required: true
    });

    function onDecrement () {
        if (modelValue.value > props.min) {
            modelValue.value--;
        }
    }

    function onIncrement () {
        if (modelValue.value < props.max) {
            modelValue.value++;
        }
    }
</script>

<style>
    .v-input-number {
        border-radius: 32px;
        align-items: center;
        border: 2px solid;
        border-color: #000000;
        display: flex;
        height: 26px;;
        padding: 12px;
        width: 100px;
    }

    .input--buttons {
        border: 0px;
        background-color: transparent;

    }

    .cart-number {
        width: 27px;
        background-color: transparent;
        border: 0px;
    }
</style>