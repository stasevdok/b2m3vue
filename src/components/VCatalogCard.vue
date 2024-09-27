<template>
    <article class="v-catalog-card">
        <br>
        <router-link :to="`/catalog/${category}/${id}`">
            <img class="v-catalog-card__image" :src="image" >
        </router-link>
        <br>
        <router-link :to="`/catalog/${category}/${id}`">
            {{ title }}
        </router-link>

        <br>

        <div class="catalog-price">
            {{ price }} ₽
        </div>
        <br>
    </article>
</template>

<script setup>
    import VButton from '@/components/UI/VButton.vue';

    const props = defineProps({
        category: {
            type: [String, Number]
        },
        id: {
            type: Number
        },
        price: {
            type: Number
        },
        title: {
            type: String
        },
        image: {
            type: String
        }
    });

    const emit = defineEmits([
        'addToCart'
    ]);


    function onAddToCart () {
        emit('addToCart', {
            title: props.title,
            image: props.image,
            price: props.price,
            id: props.id,
            quantity: 1
        });
    }

</script>

<style>
.v-catalog-card {
    border: 0px solid;
}

.v-catalog-card__image {
    display: block;
    width: 281px;
    height: 204px;
    object-fit: cover;
}

.v-button {
    display: block;
    border: 0px;
    float: right;
}

.v-button:hover {
    background-color: transparent;
}

.catalog-img {
    width: 28px;
    padding: 0px;
    background-color: transparent;
}
</style>