<template>


    <div class="v-cart-card">
        <div class="cart-card-text">
            <div class="cart-card-title">{{ title }}</div>

            <div class="cart-card-brand">Appa</div>

            <div class="cart-card-title cart-card-price">{{ price }} ₽ </div>
        </div>

    <div class="cart-card-right-side">
        <v-input-number 
            v-model="count"
            @update:modelValue="onChangeCount"
        />
        
        <v-button @click="onDelete" :style height="24px">
            <img src="/public/delete.png" width="16px" border="0px">
        </v-button>
    </div>

        <br><br>

        <hr>
    </div>
</template>

<script setup>
    import { ref } from 'vue';
    import VInputNumber from '@/components/UI/VInputNumber.vue';
    import VButton from '@/components/UI/VButton.vue';

    const props = defineProps({
        id: {
            type: Number
        },
        title: {
            type: String
        },
        image: {
            type: String
        },
        quantity: {
            type: Number
        },
        price: {
            type: Number
        },
        delay: {
            type: Boolean
        }
    });

    const emit = defineEmits([
        'changeCount',
        'changeDelay',
        'delete'
    ]);

    const count = ref(props.quantity);

    const checked = ref(props.delay);

    function onChangeCount () {
        emit('changeCount', {
            id: props.id,
            quantity: count.value
        });
    }

    function onChangeDelay () {
        emit('changeDelay', {
            id: props.id,
            delay: checked.value
        });
    }

    function onDelete () {
        emit('delete', props.id);
    }
</script>

<style>
    .v-cart-card {
        display: flex;
        margin-bottom: 40px;
    }

    .cart-card-title {
        font-size: 24px;
        font-weight: 600;
    }

    .cart-card-price {
        margin-top: 48px;
    }

    .cart-card-brand {
        margin-top: 12px;
    }
    
    .cart-card-right-side {
        display: flex;
        align-content: flex-start;
        margin-right: 32px;
    }
</style>