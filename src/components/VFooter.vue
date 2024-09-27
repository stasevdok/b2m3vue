<template>
    <footer class="v-footer">
        <v-container>
            <v-row>
                <div class="footer-text">
                    <v-col>
                        <p>© 2024 to Home. Все права защищены.</p>
                    </v-col>
                </div>

                <v-row class="row-right">
                    <div class="pages">
                        <v-col>
                            <div class="column">
                                <p>Каталог</p>
                                <p>Покупателям</p>
                                <p>Контакты</p>
                            </div>
                        </v-col>

                        <v-col>
                            <div class="column">
                                <p>Оплата и доставка</p>
                                <p>Личный кабинет</p>
                                <p>Возврат и обмен</p>
                            </div>
                        </v-col>
                    </div>
                </v-row>
            </v-row>
        </v-container>
    </footer>
</template>

<script setup>
    import VCol from '@/components/UI/VCol.vue';
    import VContainer from '@/components/VContainer.vue';
    import VRow from '@/components/UI/VRow.vue';
</script>

<style>
    .v-footer {
        padding: 80px 0;
    }
    
    .pages {
        display: flex;
        gap: 128px;
    }

    .row-right {
        float: right;
    }

    .footer-icons {
        margin-bottom: 53px;
    }

    .footer-text {
        margin-right: 512px;
    }
</style>