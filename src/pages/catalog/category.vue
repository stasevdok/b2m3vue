<template>
  <v-layout-default>
    <v-container>
      <v-row>
              <div class="filters">
                <div>
                  <h5 class="filter">По категории</h5>
                  <input type="radio" v-model="filter.category" value="Постельное белье"> Постельное белье<br>
                  <input type="radio" v-model="filter.category" value="Одеяла и подушки"> Одеяла и подушки<br>
                  <input type="radio" v-model="filter.category" value="Пижамы и халаты"> Пижамы и халаты<br>
                  <input type="radio" v-model="filter.category" value="Пледы"> Пледы
                </div>

                <div>
                  <h5 class="filter">По цвету</h5>
                  <input type="radio" v-model="filter.color" value="white"> Белый<br>
                  <input type="radio" v-model="filter.color" value="black"> Чёрный<br>
                  <input type="radio" v-model="filter.color" value="gray"> Серый<br>
                  <input type="radio" v-model="filter.color" value="pink"> Розовый
                </div>

                <br>
                <br>

                <v-button
                  theme="primary"
                  size="large"
                  wide
                  @click="onFilter"
                >
                  Применить
                </v-button>
              </div>
              <br><br>
        </v-row>


        <v-row>
            <v-col 
                v-for="product in products"
                span="3"
                md="6"
                sm="12"
            >
                <v-catalog-card 
                    :id="product.id"
                    :price="product.price"
                    :image="product.image"
                    :title="product.title"
                    :category="product.categoryId"
                    @add-to-cart="onAddToCart"
                />
            </v-col>
        </v-row>
    </v-container>
  </v-layout-default>
</template>

<script setup>
  import VButton from '@/components/UI/VButton.vue';
  import { ref } from 'vue';
  import { useRoute } from "vue-router";
  import { useCart } from '@/composables/useCart';
  import { useCatalogCategory } from '@/composables/useCatalogCategory';
  import VLayoutDefault from '@/components/Layouts/VLayoutDefault.vue';
  import VContainer from '@/components/VContainer.vue';
  import VRow from '@/components/UI/VRow.vue';
  import VCol from '@/components/UI/VCol.vue';
  import VCatalogCard from '@/components/VCatalogCard.vue';

  const route = useRoute();

  const filter = ref({
    brand: '',
    color: ''
  });

  const { products, getProductsCategory } = useCatalogCategory();
  const { onAddToCart } = useCart();

  getProductsCategory(route.params.category, filter.value);

  function onFilter () {
    getProductsCategory(route.params.category, filter.value);
  }
</script>

<style>
.filter {
  border: 1px solid var(--color-blue);
  border-radius: 32px;
  padding: 8px 8px 8px 16px;
  width: 120px;
}
</style>