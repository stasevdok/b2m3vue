<template>
    <header class="v-header">
        <v-container>
            <v-row align="center" justify="beetwen" no-gutters>
                    
                    <v-col>
                        <v-logo/>
                    </v-col>
                    <v-col>
                        <v-sidebar-menu/>
                    </v-col>
                    <v-col/>
                    <v-col/>
                    <v-col/>
                    <v-col/>
                    <v-col/>
                    <v-col/>
                    <v-col/>
                    

                    <v-col>
                        <div class="fullinput-search">
                            <input type="text" v-model="search" class="input-search" placeholder="Введите название">

                            <button @click="onSearch" class="button--search">
                                <img src="/icons/search.png" alt="search" width="15px">
                            </button>
                        </div>
                    </v-col>

                    <v-col>
                        <router-link 
                            v-if="isAuth"
                            to="/profile" 
                            class="v-menu__item"
                        >
                            <template v-if="user">
                                {{ user.firstname }}
                            </template>
                        </router-link>

                        <router-link 
                            v-else
                            to="/auth/sign-in" 
                            class="v-menu__item"
                            >Профиль
                        </router-link>
                    </v-col>

                    <v-col>
                        <router-link 
                            to="/cart" 
                            class="v-menu__item">Корзина
                        </router-link>
                    </v-col>

            </v-row>
        </v-container>
    </header>
</template>

<script setup>
    import { ref } from 'vue';
    import { useRouter } from 'vue-router';
    import { useAuth } from '@/composables';
    import VRow from '@/components/UI/VRow.vue';
    import VCol from '@/components/UI/VCol.vue';
    import VLogo from '@/components/VLogo.vue';
    import VSidebarMenu from '@/components/VSidebarMenu.vue';
    import VContainer from '@/components/VContainer.vue';

    const search = ref();

    const router = useRouter();
    const { isAuth, user } = useAuth();

    function onSearch () {
        router.push({
            path: '/search',
            query: {
                q: search.value
            }
        });
    }
</script>

<style>
    .v-header {
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        z-index: 100;

        background-color: #F0F0F2;

        padding: 10px 0;
    }

    .button--search {
        border: 0px;
        background-color: transparent;

    }

    .input-search {
        height: 35px;
        width: 170px;
        font-family: Raleway;
        padding-left: 8px;
        border: 0px;
    }

    .fullinput-search {
        display: flex;
        justify-content: center;
        color: #A7A5D5;
    }

    .ideas {
        display: flex;
        gap: 12px;
        align-items: center;
    }

    .ideas-text {
        font-family: Raleway;
        font-size: 20px;
    }
</style>