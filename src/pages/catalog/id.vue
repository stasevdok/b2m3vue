<template>
    <v-layout-default>
        <v-container v-if="product">
            <v-row>
                <v-col span="7">
                    <div>
                        <v-catalog-card
                            :image="product.image"
                            :class="v-catalog-card-bigger"
                        />
                    </div>
                </v-col>

                <v-col span="5">
                    <h3>{{ product.title }}</h3>

                    <div>
                        {{ product.price }} ₽
                    </div>

                    <br>

                    <div>
                        {{ product.description }}
                    </div>

                    <br>
                    <br>

                    <v-row>
                        <v-col span="6">
                            <v-button
                                theme="primary"
                                size="large"
                                wide
                                @click="onAddToCart({
                                    ...product,
                                    quantity: 1
                                })"
                            >
                                Добавить в корзину
                            </v-button>
                        </v-col>
                    </v-row>
                </v-col>
            </v-row>
        </v-container>
    </v-layout-default>
</template>

<script setup>
    import { ref, computed } from 'vue';
    import { useRoute } from "vue-router";
    import { CatalogApiService } from '@/services';
    import VLayoutDefault from '@/components/Layouts/VLayoutDefault.vue';
    import VRow from '@/components/UI/VRow.vue';
    import VCol from '@/components/UI/VCol.vue';
    import VButton from '@/components/UI/VButton.vue';
    import VContainer from '@/components/VContainer.vue';
    import { useCart } from '@/composables';
    import VCatalogCard from '@/components/VCatalogCard.vue';


    const route = useRoute();
    const { onAddToCart } = useCart();

    const product = ref();

    CatalogApiService.getProduct(route.params.id)
        .then(data => {
            product.value = data;
        });
</script>

<style>
.card-title {
    text-decoration: none;
    font-size: 20px;
}

.catalog-img, .catalog-price {
    display: none;
}

.v-catalog-card-bigger {
    width: 600px;
    height: 435px;
}
</style>