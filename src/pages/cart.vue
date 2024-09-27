<template>
    <v-layout-default>
        <v-container>
        <div class="order">
            <div>
                Кол-во товаров: {{ cartTotalCount }}
            </div>

            <div>
                Сумма товаров: {{ cartTotalSum }} ₽.
            </div>
        </div>  
        

            <template v-if="cartNotDelay.length">
                <h2>Корзина</h2>
                <v-cart-card 
                    v-for="cartItem in cartNotDelay"
                    :id="cartItem.id"
                    :title="cartItem.title"
                    :price="cartItem.price"
                    :quantity="cartItem.quantity"
                    :image="cartItem.image"
                    :delay="cartItem.delay"
                    @change-count="onChangeCount"
                    @change-delay="onChangeDelay"
                    @delete="onDelete"
                />
            </template>


            <router-link to="/ordering">
                Перейти к оформлению
            </router-link>
        </v-container>
    </v-layout-default>
</template>

<script setup>
    import { useCart } from '@/composables';
    import VLayoutDefault from '@/components/Layouts/VLayoutDefault.vue';
    import VContainer from '@/components/VContainer.vue';
    import VCartCard from '@/components/VCartCard.vue';

    const { 
        cartNotDelay,
        cartTotalCount, 
        cartTotalSum, 
        getCart, 
        onChangeCount, 
        onChangeDelay, 
        onDelete 
    } = useCart();

    getCart();
</script>