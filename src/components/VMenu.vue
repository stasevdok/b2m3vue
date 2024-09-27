<template>
    <div class="v-full-menu">
        <nav class="v-menu">
            <router-link to="/catalog/1" class="v-menu__item">
                Постельное белье
            </router-link>
            <router-link to="/catalog/2" class="v-menu__item">
                Одеяла и подушки
            </router-link>
            <router-link to="/catalog/3" class="v-menu__item">
                Пижамы и халаты
            </router-link>
            <router-link to="/catalog/4" class="v-menu__item">
                Пледы
            </router-link>
        </nav>
    </div>
</template>

<script setup>
    import { useAuth } from '@/composables';

    const { isAuth } = useAuth();
</script>

<style>
    .v-menu {
        display: flex;
        flex-flow: row wrap;
        gap: 20px 20px;
        margin-left: 90px;
        margin-top: 128px;
        flex-direction: column;
        font-size: 20px;
    }

    .v-menu__item {
        color: var(--color-black);
        text-decoration: none;
    }

    .v-menu__item.router-link-active {
        color: var(--color-blue);
    }

    .v-full-menu {
        display: flex;
        flex-flow: row wrap;
        
    }

    .v-menu-3 {
        margin-top: 88px;
        margin-left: 0px;
    }
</style>